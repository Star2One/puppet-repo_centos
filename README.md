# 配置 CentOS yum 仓库

# 关于
这是一个用于配置CentOS 系统yum源的puppet模块。   
默认使用<http://mirror.centos.org/centos>作为默认源仓库。  

可以通过如下方式修改默认配置

```
class {'repo_centos':
   repourl       => 'http://myrepo/centos',
   enable_scl    => true,
}
```

以上命令中
同时设置enable_scl选项为true，表示选择启用scl源。


另外一种修改默认配置的方式是通过hiera 的YAML配置。
例如：
```
repo_centos::repourl: 'http://myrepo/centos'
repo_centos::enable_scl: true
```
默认会自动导入GPG Keys.

默认启用的仓库如下：

  * centos-base
  * centos-extras
  * centos-updates

默认禁用的仓库如下：

  * centos-contrib
  * centos-cr
  * centos-plus
  * scl

## 说明

该模块Fork于puppetlabs网站的flakrat-repo_centos模块
感谢原作者。


#安装
该模块依赖"puppetlabs/stdlib"模块，请自行下载安装。

#配置
该模块是自定义Facter，获取系统的版本号，如CentOS5，简略版本号为5
建议打开puppet的"pluginsync = true"选项。


# 测试

该模块以及在Centos6和5系统上测试通过。  
Puppet Client测试版本为3.4.2。  

# License
Apache Software License 2.0
