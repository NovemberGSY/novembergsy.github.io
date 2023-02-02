### 为wordpress添加固定链接，使得访问更快

## 1、问题发现

  在为自己的网站添加SSL安全证书后，发现每次打开自己的博客变的异常的耗时，平时自己访问其他网站的时候，加载超过5秒都会觉得非常慢，没想到加载自己的网站会超过15秒，甚至直接访问失败（超过40秒）

####   当时怀疑以下可能是造成访问变慢的原因：

- **添加SSL证书后，经过长时间再次访问会进行安全验证，使得加载变慢（排除）**

​       从理论上来说，因为HTTPS比HTTP多出了SSL握手环节，而事实上，这个环节耗费的时间仅有几百毫秒(0.1秒=100毫秒)。不了解的人可能会认为这一环节的增加会使得网站的访问速度变慢，但这几百毫秒我们很难发觉速度上的变化，这就好比身上落了一粒灰尘我们并不会感觉到体重增加了

- **网站需要加载的文件过大（图片、音频）（未知）**

​       之前在Wordpress配置文件中，将上传文件的大小从2MB更改到64MB（设置的壁纸有些超过了2MB，所以干脆设置大些）

- **同时启动了自己的Java项目，怀疑内存占用过多（排除）**

  ```shell
  ps aux 查看各个进程时，发现运行的Java项目占了11%的内存
  ```

  关闭Java项目后，网站仍存在同样的问题

- **云服务器带宽太小了，只有1Mbps的带宽（排除）**

​       有网友说他的云服务器带宽有10Mbps，即使在这么高的带宽下，也会出现相同的情况，访问网站依旧很慢，排除此原因

- **Wordpress系统默认使用谷歌字体（已解决）**

  在国内谷歌域名被屏蔽，所以导致操作反应慢。对于很多商业主题默认使用了谷歌字体、谷歌ajax库、谷歌地图等谷歌服务，所以导致网站前台访问速度慢。

  有两种解决方案：

  1. 修改wordpress的PHP文件，具体做法如下：

  https://www.trustauth.cn/wiki/8918.html

  2. 下载插件，禁用/删除Google字体：

  

  ![如何解决wordpress访问速度慢的问题](https://exp-picture.cdn.bcebos.com/3d002dbad341037d32e75fc2a9bc7dc5ce672d65.jpg?x-bce-process=image%2Fresize%2Cm_lfit%2Cw_500%2Climit_1)

  ![如何解决wordpress访问速度慢的问题](https://exp-picture.cdn.bcebos.com/d4071b96b814f4d068d35e66cdfe474ec3832365.jpg?x-bce-process=image%2Fresize%2Cm_lfit%2Cw_500%2Climit_1)

  ![如何解决wordpress访问速度慢的问题](https://exp-picture.cdn.bcebos.com/b57fb6db574afa32794cba4354b2dc19cf2c1465.jpg?x-bce-process=image%2Fresize%2Cm_lfit%2Cw_500%2Climit_1)

  ---

  ## 2、解决问题

    **使用插件“WP Super Cache”，一款WordPress的快速缓存插件**

    WP Super Cache 是 WordPress 官方开发人员 Donncha 开发，是当前最高效也是最灵活的 WordPress 静态[缓存插件](https://www.wpdaxue.com/tag/缓存插件)。它把整个网页直接生成 HTML 文件，这样 Apache 就不用解析 PHP 脚本，通过使用这个插件，能使得 WordPress 博客获将显著的提速。

    在使用WP Super Cache插件时，遇到了固定链接的问题：

  1. WP Super Cache插件的使用前提是网站需要开启固定链接

  ![wordpress设置固定链接后页面404错误怎么办](https://exp-picture.cdn.bcebos.com/5c9c964ce54a2f2719b20ab5e00192dd3240f4f0.jpg?x-bce-process=image%2Fresize%2Cm_lfit%2Cw_500%2Climit_1)

  2. 个人博客开启固定链接时，整个博客会出现404，导致整个网站崩溃：

  ![wordpress设置固定链接后页面404错误怎么办](https://exp-picture.cdn.bcebos.com/90c61d1c99c0affce9d8069c2372941fbfe4eaf0.jpg?x-bce-process=image%2Fresize%2Cm_lfit%2Cw_500%2Climit_1)

  #### 解决办法：

- ```shell
  vim /etc/httpd/conf/httpd.conf		打开Apache配置文件
  ```

   （找这个文件耗了非常久的时间，一是找到apache配置，wordpress配置）

- 在该文件中，修改配置

注意：需要在<Directory "/var/www/html">配置下的

```shell
AllOverride None 进行修改
```

把“None”修改为“All”

![wordpress设置固定链接后页面404错误怎么办](https://exp-picture.cdn.bcebos.com/df087f0f8b56ad040c36355adae10ef85956d0f0.jpg?x-bce-process=image%2Fresize%2Cm_lfit%2Cw_500%2Climit_1)

- 最后重启Apache服务，问题解决！

  

  ### 补充一下关于Apcahe相关的知识：

  ​    对于Linux系统中服务的配置就是在修改其配置文件，因此还需要知道这些配置文件分别干什么用的，以及存放到了什么位置：

  | 服务目录     | /etc/httpd                 |
  | ------------ | -------------------------- |
  | 主配置文件   | /etc/httpd/conf/httpd.conf |
  | 网站数据目录 | /var/www/html              |
  | 访问日志     | /var/log/httpd/access_log  |
  | 错误日志     | /var/log/httpd/error_log   |

  （采用自：https://blog.csdn.net/shj_php/article/details/79495861）

  ### 补充一下关于固定链接的相关知识：

  ​    固定链接是你个人博客里的文章、分类以及其他页面的固定链接地址。通过固定链接，别的博友可以链到你写的博客，你也可以将这个链接地址写在邮件里发给其他人看。如果博客的链接地址变来变去，会造成其他人通过之前的链接地址来浏览博客时出错，所以每篇博客的链接地址都应该固定，而且永久不改———这也是*固定*链接名字的由来。

  更多：https://codex.wordpress.org/zh-cn:%E4%BD%BF%E7%94%A8%E5%9B%BA%E5%AE%9A%E9%93%BE%E6%8E%A5

  （wordpress官方文档）

