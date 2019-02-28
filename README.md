[TOC]

# Git使用
## 新建代码库
* 在当前目录新建一个Git代码库

	`$ git init`

* 新建一个目录，将其初始化为Git代码库

	`$ git init [project-name]`

* 下载一个项目和它的整个代码历史

	`$ git clone [url]`

## 配置
* 显示当前的Git配置

	`$ git config --list`

* 编辑Git配置文件

	`$ git config -e [--global]`

* 设置提交代码时的用户信息

	`$ git config [--global] user.name "[name]"`
	
	`$ git config [--global] user.email "[email address]"`

##增加/删除文件
* 添加指定文件到暂存区

	`$ git add [file1] [file2] ...`

* 添加指定目录到暂存区，包括子目录

	`$ git add [dir]`

* 添加当前目录的所有文件到暂存区

	`$ git add .`

* 添加每个变化前，都会要求确认
* 对于同一个文件的多处变化，可以实现分次提交

	`$ git add -p`

* 删除工作区文件，并且将这次删除放入暂存区

	`$ git rm [file1] [file2] ...`

* 停止追踪指定文件，但该文件会保留在工作区

	`$ git rm --cached [file]`

* 改名文件，并且将这个改名放入暂存区

	`$ git mv [file-original] [file-renamed]`
	

## 代码提交
* 提交暂存区到仓库区

	`$ git commit -m [message]`

* 提交暂存区的指定文件到仓库区

	`$ git commit [file1] [file2] ... -m [message]`

* 提交工作区自上次commit之后的变化，直接到仓库区

	`$ git commit -a`

* 提交时显示所有diff信息

	`$ git commit -v`

* 使用一次新的commit，替代上一次提交
* 如果代码没有任何新变化，则用来改写上一次commit的提交信息

	`$ git commit --amend -m [message]`

* 重做上一次commit，并包括指定文件的新变化

	`$ git commit --amend [file1] [file2] ...`

## 分支
* 列出所有本地分支

	`$ git branch`

* 列出所有远程分支

	`$ git branch -r`

* 列出所有本地分支和远程分支

	`$ git branch -a`

* 新建一个分支，但依然停留在当前分支

	`$ git branch [branch-name]`

* 新建一个分支，并切换到该分支

	`$ git checkout -b [branch]`

* 新建一个分支，指向指定commit

	`$ git branch [branch] [commit]`

* 新建一个分支，与指定的远程分支建立追踪关系

	`$ git branch --track [branch] [remote-branch]`

* 切换到指定分支，并更新工作区

	`$ git checkout [branch-name]`

* 切换到上一个分支

	`$ git checkout -`

* 建立追踪关系，在现有分支与指定的远程分支之间

	`$ git branch --set-upstream [branch] [remote-branch]`

* 合并指定分支到当前分支

	`$ git merge [branch]`

* 选择一个commit，合并进当前分支

	`$ git cherry-pick [commit]`

* 删除分支

	`$ git branch -d [branch-name]`

* 删除远程分支

	`$ git push origin --delete [branch-name]`
	
	`$ git branch -dr [remote/branch]`
	

## 查看信息
* 显示有变更的文件

	`$ git status`

* 显示当前分支的版本历史

	`$ git log`

* 显示commit历史，以及每次commit发生变更的文件

	`$ git log --stat`

* 搜索提交历史，根据关键词

	`$ git log -S [keyword]`

* 显示某个commit之后的所有变动，每个commit占据一行

	`$ git log [tag] HEAD --pretty=format:%s`

* 显示某个commit之后的所有变动，其"提交说明"必须符合搜索条件

	`$ git log [tag] HEAD --grep feature`

* 显示某个文件的版本历史，包括文件改名

	`$ git log --follow [file]`

	`$ git whatchanged [file]`

* 显示指定文件相关的每一次diff

	`$ git log -p [file]`

* 显示过去5次提交

	`$ git log -5 --pretty --oneline`

* 显示所有提交过的用户，按提交次数排序

	`$ git shortlog -sn`

* 显示指定文件是什么人在什么时间修改过

	`$ git blame [file]`

* 显示暂存区和工作区的差异

	`$ git diff`

* 显示暂存区和上一个commit的差异

	`$ git diff --cached [file]`

* 显示工作区与当前分支最新commit之间的差异

	`$ git diff HEAD`

* 显示两次提交之间的差异

	`$ git diff [first-branch]...[second-branch]`

* 显示今天你写了多少行代码

	`$ git diff --shortstat "@{0 day ago}"`

* 显示某次提交的元数据和内容变化

	`$ git show [commit]`

* 显示某次提交发生变化的文件

	`$ git show --name-only [commit]`

* 显示某次提交时，某个文件的内容

	`$ git show [commit]:[filename]`

* 显示当前分支的最近几次提交

	`$ git reflog`

## 远程同步
* 下载远程仓库的所有变动

	`$ git fetch [remote]`

* 显示所有远程仓库

	`$ git remote -v`

* 显示某个远程仓库的信息

	`$ git remote show [remote]`

* 增加一个新的远程仓库，并命名

	`$ git remote add [shortname] [url]`

* 取回远程仓库的变化，并与本地分支合并

	`$ git pull [remote] [branch]`

* 上传本地指定分支到远程仓库

	`$ git push [remote] [branch]`

* 强行推送当前分支到远程仓库，即使有冲突

	`$ git push [remote] --force`

* 推送所有分支到远程仓库

	`$ git push [remote] --all`

## 撤销
* 恢复暂存区的指定文件到工作区

	`$ git checkout [file]`

* 恢复某个commit的指定文件到暂存区和工作区

	`$ git checkout [commit] [file]`

* 恢复暂存区的所有文件到工作区

	`$ git checkout .`

* 重置暂存区的指定文件，与上一次commit保持一致，但工作区不变

	`$ git reset [file]`

* 重置暂存区与工作区，与上一次commit保持一致

	`$ git reset --hard`

* 重置当前分支的指针为指定commit，同时重置暂存区，但工作区不变

	`$ git reset [commit]`

* 重置当前分支的HEAD为指定commit，同时重置暂存区和工作区，与指定commit一致

	`$ git reset --hard [commit]`

* 重置当前HEAD为指定commit，但保持暂存区和工作区不变

	`$ git reset --keep [commit]`

* 新建一个commit，用来撤销指定commit
* 后者的所有变化都将被前者抵消，并且应用到当前分支

	`$ git revert [commit]`

* 暂时将未提交的变化移除，稍后再移入

	`$ git stash`

	`$ git stash pop	`

# Objective-C基础
## objc消息传递

* 第一步 resolveInstanceMethod或resolveClassMethod

* 第二步 forwardingTargetForSelector

* 第三步 forwardInvocation

三步都没找到对应方法，则返回

# runtime

# 经典第三方库
## SDWebImage

## AFNetworking

# 多线程

# AOP埋点

# CocoaPods

CocoaPods 是开发 OS X 和 iOS 应用程序的一个第三方库的依赖管理工具。利用 CocoaPods，可以定义自己的依赖关系 (称作 pods)，并且随着时间的变化，以及在整个开发环境中对第三方库的版本管理非常方便。

CocoaPods 背后的理念主要体现在两个方面。首先，在工程中引入第三方代码会涉及到许多内容。针对 Objective-C 初级开发者来说，工程文件的配置会让人很沮丧。在配置 build phases 和 linker flags 过程中，会引起许多人为因素的错误。CocoaPods 简化了这一切，它能够自动配置编译选项。

其次，通过 CocoaPods，可以很方便的查找到新的第三方库。当然，这并不是说你可以简单的将别人提供的库拿来拼凑成一个应用程序。它的真正作用是让你能够找到真正好用的库，以此来缩短我们的开发周期和提升软件的质量。

本文中，我们将通过分析 pod 安装 (pod install) 的过程，一步一步揭示 CocoaPods 背后的技术。

## 核心组件

CocoaPods是用 Ruby 写的，并由若干个 Ruby 包 (gems) 构成的。在解析整合过程中，最重要的几个 gems 分别是： `CocoaPods/CocoaPods`, `CocoaPods/Core`, 和 `CocoaPods/Xcodeproj` (是的，CocoaPods 是一个依赖管理工具 -- 利用依赖管理进行构建的！)。
	
### CocoaPods/CocoaPod
这是是一个面向用户的组件，每当执行一个 `pod` 命令时，这个组件都将被激活。该组件包括了所有使用 CocoaPods 涉及到的功能，并且还能通过调用所有其它的 gems 来执行任务。

### CocoaPods/Core
Core 组件提供支持与 CocoaPods 相关文件的处理，文件主要是 Podfile 和 podspecs。

### Podfile
Podfile 是一个文件，用于定义项目所需要使用的第三方库。该文件支持高度定制，你可以根据个人喜好对其做出定制。更多相关信息，请查阅 Podfile 指南。

### Podspec
`.podspec` 也是一个文件，该文件描述了一个库是怎样被添加到工程中的。它支持的功能有：列出源文件、framework、编译选项和某个库所需要的依赖等。

### CocoaPods/Xcodeproj
这个 gem 组件负责所有工程文件的整合。它能够对创建并修改 `.xcodeproj` 和 `.xcworkspace` 文件。它也可以作为单独的一个 gem 包使用。如果你想要写一个脚本来方便的修改工程文件，那么可以使用这个 gem。

## 运行 pod install 命令
当运行 `pod install` 命令时会引发许多操作。要想深入了解这个命令执行的详细内容，可以在这个命令后面加上 `-verbose`。

## 读取 Podfile 文件
你是否对 Podfile 的语法格式感到奇怪过，那是因为这是用 Ruby 语言写的。相较而言，这要比现有的其他格式更加简单好用一些。

在安装期间，第一步是要弄清楚显示或隐式的声明了哪些第三方库。在加载 podspecs 过程中，CocoaPods 就建立了包括版本信息在内的所有的第三方库的列表。Podspecs 被存储在本地路径 `~/.cocoapods` 中。

### 版本控制和冲突
CocoaPods 使用语义版本控制 - Semantic Versioning 命名约定来解决对版本的依赖。由于冲突解决系统建立在非重大变更的补丁版本之间，这使得解决依赖关系变得容易很多。例如，两个不同的 pods 依赖于 CocoaLumberjack 的两个版本，假设一个依赖于 `2.3.1`，另一个依赖于 `2.3.3`，此时冲突解决系统可以使用最新的版本 `2.3.3`，因为这个可以向后与 `2.3.1` 兼容。

但这并不总是有效。有许多第三方库并不使用这样的约定，这让解决方案变得非常复杂。

当然，总会有一些冲突需要手动解决。如果一个库依赖于 `CocoaLumberjack` 的 `1.2.5`，另外一个库则依赖于 `2.3.1`，那么只有最终用户通过明确指定使用某个版本来解决冲突。

## 加载源文件
CocoaPods 执行的下一步是加载源码。每个 `.podspec` 文件都包含一个源代码的索引，这些索引一般包裹一个 git 地址和 git tag。它们以 commit SHAs 的方式存储在 `~/Library/Caches/CocoaPods` 中。这个路径中文件的创建是由 Core gem 负责的。

CocoaPods 将依照 `Podfile`、`.podspec` 和缓存文件的信息将源文件下载到 Pods 目录中。

## 生成 Pods.xcodeproj
每次 pod install 执行，如果检测到改动时，CocoaPods 会利用 Xcodeproj gem 组件对 Pods.xcodeproj 进行更新。如果该文件不存在，则用默认配置生成。否则，会将已有的配置项加载至内存中。

## 安装第三方库
当 CocoaPods 往工程中添加一个第三方库时，不仅仅是添加代码这么简单，还会添加很多内容。由于每个第三方库有不同的 target，因此对于每个库，都会有几个文件需要添加，每个 target 都需要：

* 一个包含编译选项的 .xcconfig 文件
* 一个同时包含编译设置和 CocoaPods 默认配置的私有 .xcconfig 文件
* 一个编译所必须的 prefix.pch 文件
* 另一个编译必须的文件 dummy.m

一旦每个 pod 的 target 完成了上面的内容，整个 Pods target 就会被创建。这增加了相同文件的同时，还增加了另外几个文件。如果源码中包含有资源 bundle，将这个 bundle 添加至程序 target 的指令将被添加到 `Pods-Resources.sh` 文件中。还有一个名为 `Pods-environment.h` 的文件，文件中包含了一些宏，这些宏可以用来检查某个组件是否来自 pod。最后，将生成两个认可文件，一个是 plist，另一个是 markdown，这两个文件用于给最终用户查阅相关许可信息。

## 写入至磁盘
直到现在，许多工作都是在内存中进行的。为了让这些成果能被重复利用，我们需要将所有的结果保存到一个文件中。所以 `Pods.xcodeproj` 文件被写入磁盘，另外两个非常重要的文件：`Podfile.lock` 和 `Manifest.lock` 都将被写入磁盘。

### Podfile.lock
这是 CocoaPods 创建的最重要的文件之一。它记录了需要被安装的 pod 的每个已安装的版本。如果你想知道已安装的 pod 是哪个版本，可以查看这个文件。推荐将 `Podfile.lock` 文件加入到版本控制中，这有助于整个团队的一致性。

### Manifest.lock
这是每次运行 `pod install` 命令时创建的 Podfile.lock 文件的副本。如果你遇见过这样的错误 沙盒文件与 `Podfile.lock` 文件不同步 (The sandbox is not in sync with the Podfile.lock)，这是因为 Manifest.lock 文件和 Podfile.lock 文件不一致所引起。由于 Pods 所在的目录并不总在版本控制之下，这样可以保证开发者运行 app 之前都能更新他们的 pods，否则 app 可能会 crash，或者在一些不太明显的地方编译失败。

### xcproj
如果你已经依照我们的建议在系统上安装了 xcproj，它会对 Pods.xcodeproj 文件执行一下 touch 以将其转换成为旧的 ASCII plist 格式的文件。为什么要这么做呢？虽然在很久以前就不被其它软件支持了，但是 Xcode 仍然依赖于这种格式。如果没有 xcproj，你的 Pods.xcodeproj 文件将会以 XML 格式的 plist 文件存储，当你用 Xcode 打开它时，它会被改写，并造成大量的文件改动。

# iOS设计模式
## 软件设计原则
### 单一职责原则
	理解：不同的类具备不同的职责，各司其职。做系统设计是，如果发现有一个类拥有了两种职责，那么就要问一个问题：可以将这个类分成两个类吗？如果真的有必要，那就分开，千万不要让一个类干的事情太多。
	
	总结：一个类只承担一个职责
### 开闭原则
	理解：类、模块、函数，可以去扩展，但不要去修改。如果要修改代码，尽量用继承或组合的方式来扩展类的功能，而不是直接修改类的代码。当然，如果能保证对整个架构不会产生任何影响，那就没必要搞的那么复杂，直接改这个类吧。
	
	总结：对软件实体的改动，最好用扩展而非修改的方式。
### 里氏替换原则
	理解：一个对象在其出现的任何地方，都可以用子类实例做替换，并且不会导致程序的错误。换句话说，当子类可以在任意地方替换基类且软件功能不受影响时，这种继承关系的建模才是合理的。
	
	总结：子类可以扩展父类的方法，但不应该复写父类的方法。
### 依赖倒转原则
	理解：高层模块不应该依赖低层模块，二者都应该依赖其抽象；抽象不应该依赖细节；细节应该依赖抽象。
	
	总结：面向接口编程，提取出事务的本质和共性。
### 接口隔离原则
	理解：一个类实现的接口中，包含了它不需要的方法。将接口拆分成更小和更具体的接口，有助于解耦，从而更容易重构、更改。
	
	总结：对象不应被强迫依赖它不使用的方法。
### 合成复用原则
	理解：合成/聚合复用原则就是在一个新的对象里面使用一些已有的对象，使之成为新对象的一部分；新的对象通过向这些对象的委派达到复用已有功能的目的。它的设计原则是：要尽量使用合成/聚合，尽量不要使用继承。
	
	总结：就是说要少用继承，多用合成关系来实现。
### 迪米特法则
	理解：一个对象对另一个对象了解得越多，那么，它们之间的耦合性也就越强，当修改其中一个对象时，对另一个对象造成的影响也就越大。
	
	总结：一个对象应该对其他对象保持最少的了解，实现低耦合、高内聚。
## 创建型模式
### 抽象工厂模式
	提供一个接口，用于创建与某些对象相关或依赖于某些对象的类家族，而又不需要指定它们的具体类。通过这种模式可以去除客户代码和来自工厂的具体对象细节之间的耦合关系。
	
	类簇是一种把一个公共的抽象超类下的一些私有的具体子类组合在一起的架构。抽象超类负责声明创建私有子类实例的方法，会根据被调用方法的不同分配恰当的具体子类，每个返回的对象都可能属于不同的私有子类。
	
	Cocoa将类簇限制在数据存储可能因环境而变的对象生成上。Foundation框架为NSString、NSData、NSDictionary、NSSet、和NSArray对象定义了类簇。公共超类包括上述的不可变类和与其相互补充的可变类NSMutableString、NSMutableData、NSMutableDictionary、NSMutableSet、和NSMutableArray。

### 建造者模式
	将一个复杂对象的构建与它的表示分离，使得同样的构建过程可以创建不同的表示。
	
	当创建复杂对象的算法应该独立于该对象的组成部分以及它们的装配方式时。
	
	当构造过程必须允许被构造的对象有不同的表示时。

### 工厂方法模式
	定义一个用于创建对象的接口，让子类决定实例化哪一个类。Factory Method 使一个类的实例化延迟到其子类。
	
	当一个类不知道它所必须创建的对象的类的时候。
	当一个类希望由它的子类来指定它所创建的对象的时候。
	当类将创建对象的职责委托给多个帮助子类中的某一个，并且你希望将哪一个帮助子类是代理者这一信息局部化的时候。

### 原型模式
	用原型实例指定创建对象的种类，并且通过拷贝这些原型创建新的对象。
	原型模式是非常简单的一种设计模式, 在多数情况下可被理解为一种深复制的行为。在Objective-C中使用原型模式, 首先要遵循NSCoping协议(OC中一些内置类遵循该协议, 例如NSArray, NSMutableArray等)。

### 单例模式
	保证一个类仅有一个实例，并提供一个访问它的全局访问点。该类需要跟踪单一的实例，并确保没有其它实例被创建。单例类适合于需要通过单个对象访问全局资源的场合。
	有几个Cocoa框架类采用单例模式，包括NSFileManager、NSWorkspace、和NSApplication类。这些类在一个进程中只能有一个实例。当客户代码向该类请求一个实例时，得到的是一个共享的实例，该实例在首次请求的时候被创建。


[参考：iOS设计模式详解](https://www.jianshu.com/p/e5c69c7b8c00)
[参考：iOS设计模式](https://www.kancloud.cn/thinkphp/ios-design-pattern/36212)
# 响应链
[参考资料](https://www.tuicool.com/articles/6VFn2q)

N叉树、UIResponder


# iOS逆向

# 多媒体 
FFMpeg内容加密
IJKPlayer
YUV420P
WebGL texImage2D
DLNA投屏

# 持续集成 
## Jenkins
## CI
## fastlane

# 性能优化

## Instrument

# iOS签名原理
iOS 签名机制挺复杂，各种证书，Provisioning Profile，entitlements，CertificateSigningRequest，p12，AppID，概念一堆，也很容易出错，本文尝试从原理出发，一步步推出为什么会有这么多概念，希望能有助于理解 iOS App 签名的原理和流程。

## 目的

先来看看苹果的签名机制是为了做什么。在 iOS 出来之前，在主流操作系统(Mac/Windows/Linux)上开发和运行软件是不需要签名的，软件随便从哪里下载都能运行，导致平台对第三方软件难以控制，盗版流行。苹果希望解决这样的问题，在 iOS 平台对第三方 APP 有绝对的控制权，一定要保证每一个安装到 iOS 上的 APP 都是经过苹果官方允许的，怎样保证呢？就是通过签名机制。

## 非对称加密
通常我们说的签名就是数字签名，它是基于非对称加密算法实现的。对称加密是通过同一份密钥加密和解密数据，而非对称加密则有两份密钥，分别是公钥和私钥，用公钥加密的数据，要用私钥才能解密，用私钥加密的数据，要用公钥才能解密。

简单说一下常用的非对称加密算法 RSA 的数学原理，理解简单的数学原理，就可以理解非对称加密是怎么做到的，为什么会是安全的：

1. 选两个质数 p 和 q，相乘得出一个大整数n，例如 p=61，q=53，n=pq=3233
2. 选 1-n 间的随便一个质数 e，例如 e = 17
3. 经过一系列数学公式，算出一个数字 d，满足：
	* 通过 n 和 e 这两个数据一组数据进行数学运算后，可以通过 n 和 d 去反解运算，反过来也可以。
	* 如果只知道 n 和 e，要推导出 d，需要知道 p 和 q，也就是要需要把 n 因数分解。
	

上述的 (n,e) 这两个数据在一起就是公钥，(n,d) 这两个数据就是私钥，满足用公钥加密，私钥解密，或反过来公钥加密，私钥解密，也满足在只暴露公钥（只知道 n 和 e）的情况下，要推导出私钥 (n,d)，需要把大整数 n 因数分解。目前因数分解只能靠暴力穷举，而n数字越大，越难以用穷举计算出因数 p 和 q，也就越安全，当 n 大到二进制 1024 位或 2048 位时，以目前技术要破解几乎不可能，所以非常安全。

若对数字 d 是怎样计算出来的感兴趣，可以详读这两篇文章：RSA 算法原理[（一）](http://www.ruanyifeng.com/blog/2013/06/rsa_algorithm_part_one.html)[（二）](http://www.ruanyifeng.com/blog/2013/07/rsa_algorithm_part_two.html)

## 数字签名
现在知道了有非对称加密这东西，那数字签名是怎么回事呢？

数字签名的作用是我对某一份数据打个标记，表示我认可了这份数据（签了个名），然后我发送给其他人，其他人可以知道这份数据是经过我认证的，数据没有被篡改过。

有了上述非对称加密算法，就可以实现这个需求：

![Alt Image Text](https://wereadteam.github.io/img/sign0.png "Optional Title")

1. 首先用一种算法，算出原始数据的摘要。需满足 a.若原始数据有任何变化，计算出来的摘要值都会变化。 b.摘要要够短。这里最常用的算法是MD5。
2. 生成一份非对称加密的公钥和私钥，私钥我自己拿着，公钥公布出去。
3. 对一份数据，算出摘要后，用私钥加密这个摘要，得到一份加密后的数据，称为原始数据的签名。把它跟原始数据一起发送给用户。
4. 用户收到数据和签名后，用公钥解密得到摘要。同时用户用同样的算法计算原始数据的摘要，对比这里计算出来的摘要和用公钥解密签名得到的摘要是否相等，若相等则表示这份数据中途没有被篡改过，因为如果篡改过，摘要会变化。

之所以要有第一步计算摘要，是因为非对称加密的原理限制可加密的内容不能太大（不能大于上述 n 的位数，也就是一般不能大于 1024 位/ 2048 位），于是若要对任意大的数据签名，就需要改成对它的特征值签名，效果是一样的。

好了，有了非对称加密的基础，知道了数字签名是什么，怎样可以保证一份数据是经过某个地方认证的，来看看怎样通过数字签名的机制保证每一个安装到 iOS 上的 APP 都是经过苹果认证允许的。

## 最简单的签名
要实现这个需求很简单，最直接的方式，苹果官方生成一对公私钥，在 iOS 里内置一个公钥，私钥由苹果后台保存，我们传 App 上 AppStore 时，苹果后台用私钥对 APP 数据进行签名，iOS 系统下载这个 APP 后，用公钥验证这个签名，若签名正确，这个 APP 肯定是由苹果后台认证的，并且没有被修改过，也就达到了苹果的需求：保证安装的每一个 APP 都是经过苹果官方允许的。

![Alt Image Text](https://wereadteam.github.io/img/sign1.png "Optional Title")


如果我们 iOS 设备安装 APP 只有从 AppStore 下载这一种方式的话，这件事就结束了，没有任何复杂的东西，只有一个数字签名，非常简单地解决问题。

但实际上因为除了从 AppStore 下载，我们还可以有三种方式安装一个 App：

1. 开发 App 时可以直接把开发中的应用安装进手机进行调试。
2. In-House 企业内部分发，可以直接安装企业证书签名后的 APP。
3. AD-Hoc 相当于企业分发的限制版，限制安装设备数量，较少用。

苹果要对用这三种方式安装的 App 进行控制，就有了新的需求，无法像上面这样简单了。

## 新的需求
我们先来看第一个，开发时安装APP，它有两个需求：

1. 安装包不需要传到苹果服务器，可以直接安装到手机上。如果你编译一个 APP 到手机前要先传到苹果服务器签名，这显然是不能接受的。
2. 苹果必须对这里的安装有控制权，包括
	* 经过苹果允许才可以这样安装。
	* 不能被滥用导致非开发app也能被安装。
为了实现这些需求，iOS 签名的复杂度也就开始增加了。

苹果这里给出的方案是使用了双层签名，会比较绕，流程大概是这样的：

![Alt Image Text](https://wereadteam.github.io/img/sign2.png "Optional Title")

1. 在你的 Mac 开发机器生成一对公私钥，这里称为公钥L，私钥L。L:Local
2. 苹果自己有固定的一对公私钥，跟上面 AppStore 例子一样，私钥在苹果后台，公钥在每个 iOS 设备上。这里称为公钥A，私钥A。A:Apple
3. 把公钥 L 传到苹果后台，用苹果后台里的私钥 A 去签名公钥 L。得到一份数据包含了公钥 L 以及其签名，把这份数据称为证书。
4. 在开发时，编译完一个 APP 后，用本地的私钥 L 对这个 APP 进行签名，同时把第三步得到的证书一起打包进 APP 里，安装到手机上。
5. 在安装时，iOS 系统取得证书，通过系统内置的公钥 A，去验证证书的数字签名是否正确。
6. 验证证书后确保了公钥 L 是苹果认证过的，再用公钥 L 去验证 APP 的签名，这里就间接验证了这个 APP 安装行为是否经过苹果官方允许。（这里只验证安装行为，不验证APP 是否被改动，因为开发阶段 APP 内容总是不断变化的，苹果不需要管。）

## 加点东西
上述流程只解决了上面第一个需求，也就是需要经过苹果允许才可以安装，还未解决第二个避免被滥用的问题。怎么解决呢？苹果再加了两个限制，一是限制在苹果后台注册过的设备才可以安装，二是限制签名只能针对某一个具体的 APP。

怎么加的？在上述第三步，苹果用私钥 A 签名我们本地公钥 L 时，实际上除了签名公钥 L，还可以加上无限多数据，这些数据都可以保证是经过苹果官方认证的，不会有被篡改的可能。

![Alt Image Text](https://wereadteam.github.io/img/sign3.png "Optional Title")


可以想到把 允许安装的设备 ID 列表 和 App对应的 AppID 等数据，都在第三步这里跟公钥L一起组成证书，再用苹果私钥 A 对这个证书签名。在最后第 5 步验证时就可以拿到设备 ID 列表，判断当前设备是否符合要求。根据数字签名的原理，只要数字签名通过验证，第 5 步这里的设备 IDs / AppID / 公钥 L 就都是经过苹果认证的，无法被修改，苹果就可以限制可安装的设备和 APP，避免滥用。

## 最终流程
到这里这个证书已经变得很复杂了，有很多额外信息，实际上除了 设备 ID / AppID，还有其他信息也需要在这里用苹果签名，像这个 APP 里 iCloud / push / 后台运行 等权限苹果都想控制，苹果把这些权限开关统一称为 Entitlements，它也需要通过签名去授权。

实际上一个“证书”本来就有规定的格式规范，上面我们把各种额外信息塞入证书里是不合适的，于是苹果另外搞了个东西，叫 Provisioning Profile，一个 Provisioning Profile 里就包含了证书以及上述提到的所有额外信息，以及所有信息的签名。

所以整个流程稍微变一下，就变成这样了：

![Alt Image Text](https://wereadteam.github.io/img/sign4.png "Optional Title")

因为步骤有小变动，这里我们不辞啰嗦重新再列一遍整个流程：

1. 在你的 Mac 开发机器生成一对公私钥，这里称为公钥L，私钥L。L:Local
2. 苹果自己有固定的一对公私钥，跟上面 AppStore 例子一样，私钥在苹果后台，公钥在每个 iOS 设备上。这里称为公钥A，私钥A。A:Apple
3. 把公钥 L 传到苹果后台，用苹果后台里的私钥 A 去签名公钥 L。得到一份数据包含了公钥 L 以及其签名，把这份数据称为证书。
4. 在苹果后台申请 AppID，配置好设备 ID 列表和 APP 可使用的权限，再加上第③步的证书，组成的数据用私钥 A 签名，把数据和签名一起组成一个 Provisioning Profile 文件，下载到本地 Mac 开发机。
5. 在开发时，编译完一个 APP 后，用本地的私钥 L 对这个 APP 进行签名，同时把第④步得到的 Provisioning Profile 文件打包进 APP 里，文件名为 embedded.mobileprovision，把 APP 安装到手机上。
6. 在安装时，iOS 系统取得证书，通过系统内置的公钥 A，去验证 embedded.mobileprovision 的数字签名是否正确，里面的证书签名也会再验一遍。
7. 确保了 embedded.mobileprovision 里的数据都是苹果授权以后，就可以取出里面的数据，做各种验证，包括用公钥 L 验证APP签名，验证设备 ID 是否在 ID 列表上，AppID 是否对应得上，权限开关是否跟 APP 里的 Entitlements 对应等。

开发者证书从签名到认证最终苹果采用的流程大致是这样，还有一些细节像证书有效期/证书类型等就不细说了。

## 概念和操作
上面的步骤对应到我们平常具体的操作和概念是这样的：

1. 第 1 步对应的是 keychain 里的 “从证书颁发机构请求证书”，这里就本地生成了一堆公私钥，保存的 CertificateSigningRequest 就是公钥，私钥保存在本地电脑里。
2. 第 2 步苹果处理，不用管。
3. 第 3 步对应把 CertificateSigningRequest 传到苹果后台生成证书，并下载到本地。这时本地有两个证书，一个是第 1 步生成的，一个是这里下载回来的，keychain 会把这两个证书关联起来，因为他们公私钥是对应的，在XCode选择下载回来的证书时，实际上会找到 keychain 里对应的私钥去签名。这里私钥只有生成它的这台 Mac 有，如果别的 Mac 也要编译签名这个 App 怎么办？答案是把私钥导出给其他 Mac 用，在 keychain 里导出私钥，就会存成 .p12 文件，其他 Mac 打开后就导入了这个私钥。
4. 第 4 步都是在苹果网站上操作，配置 AppID / 权限 / 设备等，最后下载 Provisioning Profile 文件。
5. 第 5 步 XCode 会通过第 3 步下载回来的证书（存着公钥），在本地找到对应的私钥（第一步生成的），用本地私钥去签名 App，并把 Provisioning Profile 文件命名为 embedded.mobileprovision 一起打包进去。这里对 App 的签名数据保存分两部分，Mach-O 可执行文件会把签名直接写入这个文件里，其他资源文件则会保存在 _CodeSignature 目录下。
6. 第 6 - 7 步的打包和验证都是 Xcode 和 iOS 系统自动做的事。

这里再总结一下这些概念：

1. 证书：内容是公钥或私钥，由其他机构对其签名组成的数据包。
2. Entitlements：包含了 App 权限开关列表。
3. CertificateSigningRequest：本地公钥。
4. p12：本地私钥，可以导入到其他电脑。
5. Provisioning Profile：包含了 证书 / Entitlements 等数据，并由苹果后台私钥签名的数据包。

## 其他发布方式
前面以开发包为例子说了签名和验证的流程，另外两种方式 In-House 企业签名和 AD-Hoc 流程也是差不多的，只是企业签名不限制安装的设备数，另外需要用户在 iOS 系统设置上手动点击信任这个企业才能通过验证。

而 AppStore 的签名验证方式有些不一样，前面我们说到最简单的签名方式，苹果在后台直接用私钥签名 App 就可以了，实际上苹果确实是这样做的，如果去下载一个 AppStore 的安装包，会发现它里面是没有 embedded.mobileprovision 文件的，也就是它安装和启动的流程是不依赖这个文件，验证流程也就跟上述几种类型不一样了。

据猜测，因为上传到 AppStore 的包苹果会重新对内容加密，原来的本地私钥签名就没有用了，需要重新签名，从 AppStore 下载的包苹果也并不打算控制它的有效期，不需要内置一个 embedded.mobileprovision 去做校验，直接在苹果用后台的私钥重新签名，iOS 安装时用本地公钥验证 App 签名就可以了。

那为什么发布 AppStore 的包还是要跟开发版一样搞各种证书和 Provisioning Profile？猜测因为苹果想做统一管理，Provisioning Profile 里包含一些权限控制，AppID 的检验等，苹果不想在上传 AppStore 包时重新用另一种协议做一遍这些验证，就不如统一把这部分放在 Provisioning Profile 里，上传 AppStore 时只要用同样的流程验证这个 Provisioning Profile 是否合法就可以了。

所以 App 上传到 AppStore 后，就跟你的 证书 / Provisioning Profile 都没有关系了，无论他们是否过期或被废除，都不会影响 AppStore 上的安装包。

到这里 iOS 签名机制的原理和主流程大致说完了，希望能对理解苹果签名和排查日常签名问题有所帮助。

## P.S.一些疑问
最后这里再提一下我关于签名流程的一些的疑问。

## 企业证书
企业证书签名因为限制少，在国内被广泛用于测试和盗版，fir.im / 蒲公英等测试平台都是通过企业证书分发，国内一些市场像 PP 助手，爱思助手，一部分安装手段也是通过企业证书重签名。通过企业证书签名安装的 App，启动时都会验证证书的有效期，并且不定期请求苹果服务器看证书是否被吊销，若已过期或被吊销，就会无法启动 App。对于这种助手的盗版安装手段，苹果想打击只能一个个吊销企业证书，并没有太好的办法。

这里我的疑问是，苹果做了那么多签名和验证机制去限制在 iOS 安装 App，为什么又要出这样一个限制很少的方式让盗版钻空子呢？若真的是企业用途不适合上 AppStore，也完全可以在 AppStore 开辟一个小的私密版块，还是通过 AppStore 去安装，就不会有这个问题了。

## AppStore 加密
另一个问题是我们把 App 传上 AppStore 后，苹果会对 App 进行加密，导致 App 体积增大不少，这个加密实际上是没卵用的，只是让破解的人要多做一个步骤，运行 App 去内存 dump 出可执行文件而已，无论怎样加密，都可以用这种方式拿出加密前的可执行文件。所以为什么要做这样的加密呢？想不到有什么好处。

## 本地私钥
我们看到前面说的签名流程很绕很复杂，经常出现各种问题，像有 Provisioning Profile 文件但证书又不对，本地有公钥证书没对应私钥等情况，不理解原理的情况下会被绕晕，我的疑问是，这里为什么不能简化呢？还是以开发证书为例，为什么一定要用本地 Mac 生成的私钥去签名？苹果要的只是本地签名，私钥不一定是要本地生成的，苹果也可以自己生成一对公私钥给我们，放在 Provisioning Profile 里，我们用里面的私钥去加密就行了，这样就不会有 CertificateSigningRequest 和 p12 的概念，跟本地 keychain 没有关系，不需要关心证书，只要有 Provisioning Profile 就能签名，流程会减少，易用性会提高很多，同时苹果想要的控制一点都不会少，也没有什么安全问题，为什么不这样设计呢？

能想到的一个原因是 Provisioning Profile 在非 AppStore 安装时会打包进安装包，第三方拿到这个 Provisioning Profile 文件就能直接用起来给他自己的 App 签名了。但这种问题也挺好解决，只需要打包时去掉文件里的私钥就行了，所以仍不明白为什么这样设计。

[参考资料](https://wereadteam.github.io/2017/03/13/Signature/)
