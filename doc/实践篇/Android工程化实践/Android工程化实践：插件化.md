# 大型Android项目的工程化实践：插件化

**关于作者**

>郭孝星，程序员，吉他手，主要从事Android平台基础架构方面的工作，欢迎交流技术方面的问题，可以去我的[Github](https://github.com/guoxiaoxing)提issue或者发邮件至guoxiaoxingse@163.com与我交流。

**文章目录**

它们之间的关系如下所示：


- 插件化：插件化是体现在功能拆分方面的，它将某个功能独立提取出来，独立开发，独立测试，再插入到主应用中。依次来较少主应用的规模。
- 热修复：热修复是体现在bug修复方面的，它实现的是不需要重新发版和重新安装，就可以去修复已知的bug。



随着公司业务的增长，应用的体积越来越大，公司也在不断的收购小公司和内部孵化新项目，这些新产生的应用都需要接入主应用里进行客户引流。这就代码了
工程维护和团队协作上的问题。

面临的问题

1. 工程越来越大，难以维护。
2. 公司内部应用需要接入主客户端。
3. 需求如同滚雪球，发布时间不可控。
4. 牵扯方多，对线上bug反应迟缓。

解决方案

1. 并行开发。
2. 功能解耦。
3. 插件化接入。
4. 动态部署。


APK运行容器，把APK里的文件解压出来，放到APK容器中去执行。

- DEX
- Manifest
- Resource

具体流程

1. 运行时校验兼容性
2. APK完整性校验
3. APK解析
4. 运行沙箱
5. APK 组件容器
6. 信息交互

具体实现类

- ActivityThread：运行时环境。
- LoadedApk：Apk数据结构。
- PackageParser：Apk解析器。
- ContextImpl：运行时上下文。
- ActivityManagerNative：Android组件管理器。

影响

- 运行时环境的破坏性
- 对主客户端的侵入性
- 对插件的侵入性

安全性

- 插件的可靠性
- 插件的完整性
- 运行时校验

插件和主客户端的兼容性

- 版本管理
- 插件与主客户端的兼容
- 插件与框架的兼容性
- 插件之间的兼容性

数据共享

- 配置数据共享
- 登录数据共享
- 数据的冲突

服务共享

- 组件间模块共享
- 推送服务共享