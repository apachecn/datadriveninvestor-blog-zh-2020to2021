# 使用 Fail2Ban 保护您的私有云服务器

> 原文：<https://medium.datadriveninvestor.com/secure-your-cloud-server-from-hackers-with-fail2ban-69097a23b92b?source=collection_archive---------5----------------------->

设置你的 SSH 配置和 Fail2Ban 自动监禁黑客 IP 地址。

![](img/d885235addc9137435a84a095cedd2cf.png)

Photo by [Kaur Kristjan](https://unsplash.com/@badgerblack?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

Video showing all the steps

在之前的一篇文章中，我讨论了如何在自己的私有服务器上托管一系列云服务。在这篇文章中，我将讨论如何使用 Fail2Ban 和配置 SSH 来提高服务器的安全性。

与传统的密码验证码不同，SSH 在默认情况下不限制您猜测密码的次数。这意味着试图访问您的服务器的黑客可以使用暴力攻击成为根用户。这通常需要运行一个密码破解工具，比如 Hydra，使用一系列常用的密码。

我将向您展示如何自动禁止 IP 地址时，他们这样做。如果你想知道更多的细节，你可以看看我上面的视频。

## 技术细节

[](https://github.com/BiasedRiot/SaorTech-cloud-services) [## BiasedRiot/SaorTech-云服务

### 这个项目的目的是建立和配置谷歌，Dropbox 等开源替代品...作为…

github.com](https://github.com/BiasedRiot/SaorTech-cloud-services) 

Fail2Ban 是一种检测 IP 地址登录失败的次数并在特定时间内禁止它们(将它们关进监狱)的服务。我创建了一个基本的 shell 脚本，它可以自动安装 Fail2Ban 并使用 SSH 禁用 rootlogin。你可以在上面显示的 GitHub repo 中查看我的脚本，或者运行下面的命令。

```
git clone [https://github.com/BiasedRiot/SaorTech-cloud-services.git](https://github.com/CoogyEoin/SaorTech-cloud-services.git)
cd SaorTech-cloud-services.git/security
sudo ./setup_ssh_security.sh
```

设置 Fail2Ban 就是这样。如果你想让你的服务器更加安全，你也应该取消使用用户密码登录的功能。相反，您可以将您的公共 SSH 密钥添加到授权用户，这样当您通过 SSH 登录到该用户时，它会自动验证您的身份。它还使访问变得更加简单，因为您不必每次都键入那么长的密码:)

首先在本地机器上生成一个 SSH 密钥(如果其他服务没有使用它，我建议创建一个新的)。我在使用旧的 SSH 公钥时遇到了麻烦)。

```
ssh-keygen
```

接下来要做的是从本地机器复制 SSH 密钥。记得更换你的用户和 IP 地址。

```
ssh-copy-id <user>@<server ip or domain>
```

最后，只需编辑服务器上的 sshd 配置文件。它应该在/etc/ssh/sshd_config 下，并确保它包含以下几行。

```
PasswordAuthentication no
PubkeyAuthentication yes
```

基本就是这样。只需重新启动服务器上的 sshd 服务，您就可以开始工作了。现在不仅用户(包括你自己)不可能登录你的服务器，除非他们知道你的 SSH 私人密钥，而且任何试图登录的人都将被禁止一天。你可以放心，你的服务器会更安全一点，不会被黑客攻击。

保持快乐，保持隐私。

【https://biasedriot.co】我的网站:

**Youtube:** [https://www.youtube.com/channel/UCehh50T6qtDpt_kEUF33GJw/](https://www.youtube.com/channel/UCehh50T6qtDpt_kEUF33GJw/)

**Monero:** 84Y4FZiTbLeR5qc1fBrBhB1♠5agKtEdoixq2w1ysXJv486MiBCz3czGT15bqeXDPpdLoNyF93inxY3BCk6g8mrDMNKoArS

**Bitcoin:** 1Dmn9jEtWAhdLk1HHWkUVNeDdAaBCwNajm