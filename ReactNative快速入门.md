## 前置知识

-   [Javascript 基础](https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/JavaScript_basics)
-   [ES6 入门教程](https://es6.ruanyifeng.com/)
-   [React 基础](https://react.dev/)
-   [ReactNative 基础](https://reactnative-archive-august-2023.netlify.app/docs/0.62/getting-started), [中文](https://reactnative.cn/)

## 搭建环境

开发面板，需要安装：

-   **nvm:** node 版本管理器
-   **nrm:** npm 的镜像源管理工具

### 安装开发工具

面板开发前，自行下载安装下列推荐的编辑器：

-   **Visual Studio Code**：（推荐）自带格式化、代码跳转等常用功能，社区贡献与活跃度较高。
-   WebStorm：集成度较高的 IDE。
-   Sublime Text：小巧轻便。
-   Atom：小巧轻便。

### 安装 nvm

1. 安装 nvm 参考[nvm 官方文档](https://github.com/nvm-sh/nvm?tab=readme-ov-file#installing-and-updating)

2. 输入 `nvm -v`，确认 nvm 已正常安装

3. 输入 `nvm install 16.0.0`, 安装 Node.js 16.0.0 版本

    > 由于 RN 的版本为 0.62.3，建议安装 Node.js 16 系列的版本。

4. 支持通过 `nvm use` 命令切换至指定 Node.js 版本

### 安装 yarn

1. 打开终端。

2. 输入 `npm install -g yarn`，安装 yarn

3. 输入 `yarn -v`，确认 Yarn 已正常安装

### 安装 nrm

1. 打开终端。

2. 输入 `npm install -g nrm`，安装 nrm

3. 输入 `nrm -v`，确认 nrm 已正常安装

4. 输入 `nrm ls`, 查看可选择源列表

5. 输入 `nrm add yr http://172.16.49.78:4873/`, 添加猿人 npm 私有源

6. 输入 `nrm use yr`，使用猿人 npm 私有源

## 初始化工程

1. 初始化

```js
npx react-native@0.62.3 init AwesomeProject --template yr-panel-init-template

完成后安装依赖报错没有关系, 项目可以正常运行
✔ Downloading template
✔ Copying template
✔ Processing template
✖ Installing CocoaPods dependencies (this may take a few minutes)
error Could not locate Gemfile or .bundle/ directory
✖ Installing CocoaPods dependencies (this may take a few minutes)
error Looks like your iOS environment is not properly set. Please go to https://reactnative.dev/docs/environment-setup?os=macos&platform=android and follow the React Native CLI QuickStart guide for macOS and iOS.
```

2. 目录结构

```js
├── App.js
├── app.json
├── babel.config.js
├── cli                         // 打包脚本
├── index.android.js
├── index.ios.js
├── index.js
├── metro.config.js
├── package.json
└── src
    ├── api                     // 网络请求业务逻辑封装
    ├── assets                  // 基本静态资源结构
    │   ├── nooie
    │   ├── osaio
    │   ├── index.js
    ├── pages                   // 页面
    │   ├── HomeScreen.js
    │   ├── TestScreen.js
    │   └── index.js
    └── utils                   // 工具方法
        └── global.js
```

### 开发调试

更改 `app.json` 文件中的项目名称, 修改为 APP 中已经加载的的 RN 包名称，比如 `YRHelpPannel`，进行实时调试

1. nooie 调试：`yarn start:nooie`
2. osaio 调试：`yarn start:osaio`
3. 默认 `8081端口`, `yarn start:nooie --port 8082`指定端口

### 打包调试

#### 本地打包

1. 打开`package.json`文件, 找到`scripts`
2. 打 nooie ios 包: 运行`yarn build-ios:nooie`
3. 打 nooie ios 和 android 包: 运行`yarn build-ios-android:nooie`
4. 其他同理，打包后的目录为根目录`out文件夹`下

#### Jenkins 打包上线

1. 本地开发完毕, 更新版本号，提交代码到 gitlab
2. 登录 jenkins 找到对应面板, 选择 App、品牌、分支打包
3. 下载推送至飞书群的面板包上传至 nooie/osaio 管理后台
