# 在谷歌云平台上使用 Scikit-learn

> 原文：<https://medium.datadriveninvestor.com/using-scikit-learn-on-google-cloud-platform-82ab2e06eeb9?source=collection_archive---------1----------------------->

![](img/ef8dd04bc016c54f5b8465e6dc1ec81c.png)

Photo by [Mitchell Luo](https://unsplash.com/@mitchel3uo?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

有了大数据，如果不花费大量时间，很难在本地计算机上训练机器学习模型。正因为如此，我使用了谷歌云平台(GCP)。GCP 的人工智能平台管理云中的计算资源，以训练 TensorFlow、scikit-learn 和 XGBoost 模型。您创建一个培训应用程序(本地或云上)并提交一个培训作业。AI 平台训练服务将其输出写入您的云存储桶，并创建日志。本博客将解释如何在 GCP 的人工智能平台上使用 scikit-learn。

# 开始之前..

1.  如果你还没有谷歌云项目,那就创建一个[。您可以使用现有的。](https://console.cloud.google.com/projectselector2/home/dashboard?_ga=2.45381604.-1992316389.1574440320)
2.  激活 [AI 平台 API](https://console.cloud.google.com/flows/enableapi?apiid=ml.googleapis.com,compute_component&_ga=2.45381604.-1992316389.1574440320) 。
3.  如果你还没有一个[云存储桶](https://console.cloud.google.com/storage/create-bucket)，那就设置好吧。确保铲斗与您将训练的模型位于同一个项目中。

# 如何在 AI 平台上训练你的模型

1.  创建您的 Python 模型文件-用于从云存储桶下载数据并在训练模型后将模型导出并保存到云存储的代码
2.  准备培训申请包
3.  提交培训作业

## 创建 Python 模型文件

你可以在本地或者通过 AI 平台笔记本在云上完成这项工作。以下步骤针对 AI 平台笔记本。

在 [AI 平台笔记本](https://console.cloud.google.com/ai-platform/notebooks/instances)下，点击新建实例，然后 Python，为 scikit-learn 训练创建一个笔记本(可以为 R、TensorFlow、XGBoost 创建一个)。

创建并启动实例后，您可以单击 OPEN JUPYTERLAB 并创建一个 Jupyter 笔记本。ipynb 文件来编写您的 Python 模型文件。在接下来的部分中，我将分享我在项目中使用的代码。我用< >表示必须根据你的项目和桶进行修改的区域。

设置环境变量:

```
%env PROJECT_ID <project_id>
%env BUCKET_ID <bucket_name>
%env JOB_DIR gs://<bucket_id>/scikit_learn_job_dir
%env REGION us-east4%env TRAINER_PACKAGE_PATH ./hp_tuning
%env MAIN_TRAINER_MODULE hp_tuning.train
%env RUNTIME_VERSION 1.9
%env PYTHON_VERSION 3.5
%env HPTUNING_CONFIG hptuning_config.yamlmkdir hp_tuning
```

导入包

*   我在这个项目中使用了 RandomForestRegressor。你可以导入其他库(SVM，KNN，逻辑回归，XGBoost 等。)取决于您使用的型号。

```
%%writefile ./hp_tuning/train.py
#!/usr/bin/env pythonimport argparse
import datetime
import os
import sys
import pandas as pd
import subprocessfrom google.cloud import storage
import hypertunefrom sklearn.externals import joblib
from sklearn.preprocessing import LabelEncoder
from sklearn.ensemble import RandomForestRegressor
from sklearn.model_selection import train_test_split
from sklearn.metrics import r2_score
```

建立要优化的超参数(如果您不打算优化您的模型，可以省略这一部分。

*   您可以使用或多或少的超参数进行优化。

```
%%writefile -a ./hp_tuning/train.pyparser = argparse.ArgumentParser()
parser.add_argument(
        '--job-dir',
        help='GCS location to write checkpoints and export models',
        required=True
)
parser.add_argument(
        '--maxDepth',
        help='Depth of trees',
        type=int,
        default=None
)
parser.add_argument(
        '--nEstimators',
        help='Number of trees',
        type=int,
        default=10
)
parser.add_argument(
        '--minSamplesSplit',
        help='Number of samples to split',
        type=int,
        default=2
)
parser.add_argument(
        '--minSamplesLeaf',
        help='Number of samples at leaf node',
        type=int,
        default=1
)
parser.add_argument(
        '--maxFeatures',
        help='Number of features',
        type=str,
        default='auto'
)

args = parser.parse_args()
```

导入数据并为培训做准备

```
%%writefile -a ./hp_tuning/train.pydata_filename = '<filename>'
data_dir = 'gs://<bucket_name>'subprocess.check_call(['gsutil', 'cp', os.path.join(data_dir, data_filename), data_filename], stderr=sys.stdout)cols = list(pd.read_csv(data_filename, nrows=1))
training_data = pd.read_csv(data_filename, usecols =[i for i in cols if i != '<target_column>'])# Remove the column we are trying to predict from our features list
# Convert the DataFrame to a lists of lists
X = training_data.drop('<target_column>', axis=1)# Encode categorical variables
for col in X.columns:
    if X[col].dtype == 'O':
        le = LabelEncoder()
        le.fit(list(X[col].astype(str).values))
        X[col] = le.transform(list(X[col].astype(str).values))

X = X.values.tolist()# Create our training labels list, convert the DataFrame to a lists of lists
y = training_data['<target_column>'].values.tolist()X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2)
```

创建模型

```
%%writefile -a ./hp_tuning/train.py# Create the regressor.
# Here is where we set the variables used during HP Tuning from
# the parameters passed into the python script
rf_regressor = RandomForestRegressor(max_depth=args.maxDepth, n_estimators=args.nEstimators, min_samples_split=args.minSamplesSplit, min_samples_leaf=args.minSamplesLeaf, max_features=args.maxFeatures, random_state=220)# Transform the features and fit them to the regressor
rf_regressor.fit(X_train, y_train)
```

评估模型

*   我使用 r2 分数来评估我的回归模型。您可以用 r2_score 替换您想要使用的任何其他[评估指标](https://scikit-learn.org/stable/modules/model_evaluation.html#classification-metrics)。
*   如果不打算调优超参数，可以省略最后两部分

```
%%writefile -a ./hp_tuning/train.py# Calculate the mean accuracy on the given test data and labels.
score = rf_regressor.score(X_test, y_test)# Create metric for hyperparameter tuning
y_pred = rf_regressor.predict(X_test)
r2 = r2_score(y_test, y_pred)hpt = hypertune.HyperTune()
hpt.report_hyperparameter_tuning_metric(
        hyperparameter_metric_tag='r2',
        metric_value=r2,
        global_step=0)
```

将模型导出到 Google Cloud

```
%%writefile -a ./hp_tuning/train.py# Export the model to a file
model_filename = 'rf_model.joblib'
joblib.dump(rf_regressor, model_filename)job_dir =  args.job_dir.replace('gs://', '')
# Get the Bucket Id
bucket_id = job_dir.split('/')[0]
# Get the path
bucket_path = job_dir.lstrip('{}/'.format(bucket_id))# Upload the model to GCS
bucket = storage.Client().bucket(bucket_id)
blob = bucket.blob('{}/{}'.format(
    bucket_path,
    model_filename))
blob.upload_from_filename(model_filename)
```

## 创建培训应用程序包

初始化文件

```
%%writefile ./hp_tuning/__init__.py
#!/usr/bin/env python
```

超参数包

*您可以调整同时运行的试验次数(maxParallelTrials)和运行的最大试验次数(maxTrials)。

```
%%writefile ./hptuning_config.yaml
#!/usr/bin/env python# hyperparam.yaml
trainingInput:
  hyperparameters:
    goal: MAXIMIZE
    hyperparameterMetricTag: 'r2'
    maxTrials: 30
    maxParallelTrials: 5
    enableTrialEarlyStopping: True
    params:
      - parameterName: maxDepth
        type: DISCRETE
        discreteValues: [5.0, 8.0, 15.0, 25.0, 30.0]
      - parameterName: nEstimators
        type: DISCRETE
        discreteValues: [120.0, 300.0, 500.0, 800.0, 1200.0]
      - parameterName: minSamplesSplit
        type: DISCRETE
        discreteValues: [2.0, 5.0, 10.0, 15.0, 100.0]
      - parameterName: minSamplesLeaf
        type: DISCRETE
        discreteValues: [2.0, 5.0, 10.0]
      - parameterName: maxFeatures
        type: CATEGORICAL
        categoricalValues: ['log2', 'sqrt']
```

设置培训

```
%%writefile ./setup.py
#!/usr/bin/env pythonfrom setuptools import find_packages
from setuptools import setupREQUIRED_PACKAGES = ['cloudml-hypertune']setup(
    name='hp_tuning',
    version='0.1',
    install_requires=REQUIRED_PACKAGES,
    packages=find_packages(),
    include_package_data=True,
    description='sklearn HP tuning training application'
)
```

## 提交培训工作

在与上面相同的笔记本中运行以下代码。

```
! gcloud ai-platform jobs submit training hp_tuning_$(date +"%Y%m%d_%H%M%S") \
  --job-dir $JOB_DIR \
  --package-path $TRAINER_PACKAGE_PATH \
  --module-name $MAIN_TRAINER_MODULE \
  --region $REGION \
  --runtime-version=$RUNTIME_VERSION \
  --python-version=$PYTHON_VERSION \
  --scale-tier BASIC \
  --config $HPTUNING_CONFIG
```

您应该会看到以下输出。

```
Job [hp_tuning_[DATE]_[TIME]] submitted successfully.
Your job is still active. You may view the status of your job with the command

  $ gcloud ai-platform jobs describe hp_tuning_[DATE]_[TIME]

or continue streaming the logs with the command

  $ gcloud ai-platform jobs stream-logs hp_tuning_[DATE]_[TIME]
jobId: hp_tuning_[DATE]_[TIME]
state: QUEUED
```

# 检查培训工作的进度

提交培训工作后，您可以进入您的 AI 平台中的[工作](https://console.cloud.google.com/mlengine/jobs?_ga=2.116317126.-1992316389.1574440320)部分。它将向您显示所有已提交的作业。

*   加载符号表示作业当前正在执行
*   红色感叹号表示作业因错误而停止
*   灰色停止标志表示作业已被取消。
*   绿色复选标记表示作业已经完成。

您可以单击作业 ID 来查看作业的详细信息、正在执行的进度或结果(最终结果或停止的原因)。

[](https://cloud.google.com/ml-engine/docs/scikit/training-scikit-learn) [## 使用 scikit 进行培训-在人工智能平台上学习|人工智能平台|谷歌云

### AI 平台训练服务管理云中的计算资源来训练你的模型。本页描述了…

cloud.google.com](https://cloud.google.com/ml-engine/docs/scikit/training-scikit-learn)