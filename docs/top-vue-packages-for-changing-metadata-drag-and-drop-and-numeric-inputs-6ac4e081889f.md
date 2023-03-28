# 用于更改元数据、拖放和数字输入的顶级 Vue 包

> 原文：<https://medium.datadriveninvestor.com/top-vue-packages-for-changing-metadata-drag-and-drop-and-numeric-inputs-6ac4e081889f?source=collection_archive---------17----------------------->

![](img/a3005535731854921e3a6b5bda17d212.png)

Photo by [Mike Benna](https://unsplash.com/@mbenna?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

Vue.js 是一个易于使用的 web 应用框架，我们可以用它来开发交互式前端应用。

在这篇文章中，我们将看看如何改变我们的应用程序的元数据，添加拖放和添加数字输入的最佳包。

[](https://www.datadriveninvestor.com/2020/06/26/understanding-software-project-management/) [## 关于成为软件项目经理|数据驱动投资者的思考

### 我做程序员已经 3 年了，我想是时候领导我自己的团队了。作为项目经理，我现在可以…

www.datadriveninvestor.com](https://www.datadriveninvestor.com/2020/06/26/understanding-software-project-management/) 

# 真空头

vue-head 包让我们改变应用程序的 meta 标签，以获得更好的 SEO。

首先，我们通过运行以下命令安装它:

```
npm i vue-head
```

然后我们可以通过写来使用它:

`main.js`

```
import Vue from "vue";
import App from "./App.vue";
import VueHead from "vue-head";Vue.use(VueHead);
Vue.config.productionTip = false;new Vue({
  render: h => h(App)
}).$mount("#app");
```

注册插件。

然后在我们的组件中，我们可以写:

```
<template>
  <div></div>
</template>

<script>
export default {
  data(){
    return {
      title: 'title'
    }
  },
  head: {
    title() {
      return {
        inner: this.title
      };
    },
    meta: [{ name: "description", content: "My description", id: "desc" }]
  }
};
</script>
```

设置我们认为合适的`title`和`meta`标签值。

我们也可以将一些选项传递给`Vue.use`:

```
import Vue from "vue";
import App from "./App.vue";
import VueHead from "vue-head";Vue.use(VueHead, {
  separator: "-",
  complement: "complement"
});
Vue.config.productionTip = false;new Vue({
  render: h => h(App)
}).$mount("#app");
```

然后，我们添加分隔符和分隔符后的补充文本。

# 可嵌套的

我们可以使用 vue-nestable 创建一个树形视图，其中包含可以拖放的项目。

要安装它，我们运行:

```
npm i vue-nestable
```

然后我们通过书写来使用它:

`main.js`

```
import Vue from "vue";
import App from "./App.vue";
import VueNestable from "vue-nestable";Vue.use(VueNestable);
Vue.config.productionTip = false;new Vue({
  render: h => h(App)
}).$mount("#app");
```

`App.vue`

```
<template>
  <div>
    <vue-nestable v-model="nestableItems">
      <vue-nestable-handle slot-scope="{ item }" :item="item">{{ item.text }}</vue-nestable-handle>
    </vue-nestable>
  </div>
</template>

<script>
export default {
  data() {
    return {
      nestableItems: [
        { id: 0, text: "foo" },
        { id: 1, text: "bar" },
        { id: 2, text: "baz" }
      ]
    };
  }
};
</script>
```

我们注册了插件并使用了`vue-nestable`组件。

`v-model`拥有我们想要渲染的项目。当项目被拖放时，它将被设置为最新的值。

`vue-nestable-handle`具有要呈现的项目列表。

他们是可拖动的，他们可以在不同的水平下降。

最大深度和样式可以改变。

# vue 滑块组件

vue-slider-component 让我们可以创建一个滑块，我们可以用它作为一个数字输入组件。

我们通过运行以下命令来安装它:

```
npm i vue-slider-component
```

然后我们可以通过写来使用它:

```
<template>
  <div>
    <vue-slider v-model="value"/>
    <p>{{value}}</p>
  </div>
</template>

<script>
import VueSlider from "vue-slider-component";
import "vue-slider-component/theme/antd.css";export default {
  components: {
    VueSlider
  },
  data() {
    return {
      value: 0
    };
  }
};
</script>
```

我们导入并注册了`vue-slider`组件。

我们还导入了捆绑的 CSS 文件。

`v-model`绑定到滑块的值。

# vue 屏幕尺寸

我们可以使用 vue-screen-size 包来获取显示应用程序的屏幕大小。

要安装它，我们运行:

```
npm i vue-screen-size
```

然后我们可以通过写来使用它:

```
<template>
  <div>{{$vssWidth }}x{{$vssHeight}}</div>
</template>

<script>
import VueScreenSize from "vue-screen-size";export default {
  mixins: [VueScreenSize.VueScreenSizeMixin]
};
</script>
```

我们添加软件包的捆绑 mixin。

然后我们可以使用`$vssWidth`变量获得屏幕的宽度，使用`$vssHeight`获得屏幕的高度。

# 数字输入

vue-numeric-input 为我们提供了一个容易添加的数字输入，它有增量和减量按钮，让我们可以改变数值。

要安装它，我们运行:

```
npm i vue-numeric-input
```

然后我们可以通过写来使用它:

`main.js`

```
import Vue from "vue";
import App from "./App.vue";
import VueNumericInput from "vue-numeric-input";Vue.use(VueNumericInput);Vue.config.productionTip = false;new Vue({
  render: h => h(App)
}).$mount("#app");
```

`App.vue`

```
<template>
  <div>
    <vue-numeric-input v-model="value" :min="1" :max="10" :step="2"></vue-numeric-input>
  </div>
</template>

<script>
export default {
  data() {
    return {
      value: 0
    };
  }
};
</script>
```

`v-model`将输入值绑定到`value`状态。

`max`是输入允许的最大值。

`min`是输入允许的最小值。

`step`是我们按下按钮时数值递增或递减的数字。

![](img/07b0f5cceb4d6bd4343f820eccf2d705.png)

Photo by [Victor Malyushev](https://unsplash.com/@malyushev?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

# 结论

我们可以用 vue-slider-component 和 vue-numeric-input 添加数字输入。

vue-screen-size 让我们观察屏幕大小的变化。

vue-head 允许我们为应用程序设置元数据。

vue-nestable 允许我们创建一个可拖动列表。

**访问专家视图—** [**订阅 DDI 英特尔**](https://datadriveninvestor.com/ddi-intel)