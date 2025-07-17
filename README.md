# -start-up-
新入职通用篇

## 介绍
这篇文章介绍了新人入职后需要了解的重点内容，主要包括工作流程中涉及到的 git权限申请、项目环境配置和项目构建 3 部分内容，它们是开展工作的前提。除此之外，文章后面还列举了日常开发流程中会用到的几个内部平台，从需求任务管理到代码提交再到测试、灰度，基本包含了整个工作流。
由于是通用篇，主要针对git权限申请、项目环境配置和项目构建 进行通用介绍，工作流的话可以类比。

## gitlab 权限申请
gitlab
找团队相关同事申请。

## 环境配置
> 对于一个新人来说，能在尽量短的时间内把项目跑起来是最重要的，因此配置项目环境到运行项目的流程需要详细说明。

### 梯子
> 对于开发人员来说，第一步chrome+梯子，日常必用，环境配置时有些工具需要使用梯子

介绍两个比较好用的梯子：[魔戒](https://mojie.me/#/dashboard)、[天航](https://tianhang.lol/user)

工具clashX，天航里有相关教程
> 更多设置里配置 忽略的域 192.168.0.0/16,10.0.0.0/8,172.16.0.0/12,127.0.0.1,localhost,*.local,timestamp.apple.com,sequoia.apple.com,seed-sequoia.siri.apple.com,.xiaojukeji.com,.didi.com,.didistatic.com,.didi.cn,.didichuxing.com,.diditaxi.com.cn,.intra.xiaojukeji.com,.didiglobal.com,.intra.hongyibo.com.cn,.artifactory.intra.xiaojukeji.com,git.xiaojukeji.com

### 配置brewhome(Mac系统或Linux系统比较好用的软件管理工具）

#### 安装（终端执行命令）
         官方文档安装脚本：/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"   
         注：可能会安装失败，因为官方文档链接是外网链接，可能会造成网络连接失败
         国内安装Homebrew的正确姿势：(基于gitee上某大神的自动安装脚本)：
         /bin/zsh -c "$(curl -fsSL https://gitee.com/cunkai/HomebrewCN/raw/master/Homebrew.sh)"
         安装过程中会要求我们输入电脑登陆密码和选择国内下载源，根据自己需求填写即可。
         注：安装过程会有cask和core工具的下载选择，记得选择。
输入'brew -v'可查看是否安装成功

#### 卸载（终端输入命令）
  /bin/zsh -c "$(curl -fsSL https://gitee.com/cunkai/HomebrewCN/raw/master/HomebrewUninstall.sh)"
       安装brewhome过程中会提示安装git，建议先安装git。
      git安装（官网直接安装即可）：
      官方下载网站：https://git-scm.com/download  
  git安装不多介绍，mac上安装一般很简单，根据提示安装即可

   输入'git -v'查看是否安装成功

####  安装完brewhome后即可下载自己所需求的软件
**常规语法：brew install [XXX] --cask**
**例：更新git**
1. 查看git的版本是否是最新的，终端语句：'git -v'
2. 利用brew更型git，终端语句：'brew install git --cask'
3. 重新链接git，终端语句：brew link git --overwrite
4. 关闭终端，重新查看Git版本，查看版本同（1）
5. 查看本地安装路径，终端语句：'which git'

### ITerm2 + Oh My Zsh配置for mac
详细流程向大模型提问吧

### Android studio
Android Studio下载就比较简单，直接到官网下载安装即可，官网地址：https://developer.android.com/studio

**下载Android SDK**
1. 首次打开未创建项目页面直接打开到Android SDK页面
Tools -> SDK Manager

下载SDK Platforms
下载SDK latforms Tools
build-tools : 主要是Android开发中所需要的工具
emulator: 主要是用于管理模拟器
platforms: 存放下载的所有的sdk platforms包
platforms-tools:主要用我们常用的adb.exe等  

**切换jdk版本**
本地编译项目时，如出现jdk版本不匹配导致的编译问题，可以修改项目的jdk运行的版本
as路径：Preferences | Build, Execution, Deployment | Build Tools | Gradle

### 配置系统变量（mac）
打开你的shell配置文件，如~/.bash_profile，.zprofile，.zshrc，不同shell会有差异，可以在用户根目录通过 ls -a查看对应的profile文件
使用open命令打开对应的配置文件，将如下配置增加到文件内容里，并保存文件
```
# Java环境变量
export JAVA_HOME=/Users/didi/Library/Java/JavaVirtualMachines/corretto-17.0.14/Contents/Home
export PATH=$JAVA_HOME/bin:$PATH

# Android环境变量配置
export ANDROID_HOME="/Users/didi/Library/Android/sdk/platform-tools"
export PATH=$PATH:$ANDROID_HOME

# 自动驾驶fakecar
export FAKECAR_HOME="/Users/didi/fakecar_Darwin_all_v0.5.8"
export PATH=$PATH:$FAKECAR_HOME
```

3.执行 source ~/.bash_profile，然后输入adb version,打印出信息则说明配置成功了

### charles
教程不再细赘述，注：配置网络代理和PC端打开Charles可能会导致网络无法用
工具箱：关闭短链转长链
