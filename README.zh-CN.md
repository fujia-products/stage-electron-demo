<div align="center">
  <a href="https://github.com/fujia-cli/electron-webpack-react-template" target="_blank">
    <img alt="logo" width="200" src="./resource/unrelease/png/256x256.png"/>
  </a>
</div>

<div align="center">
  <h1>stage-electron-demo</h1>
</div>

<div align="center">

应用简介...

</div>

<div align="center">

[English](./README.md) | 简体中文

</div>

## 开始

首先，通过下面的命令安装相应的 cli tools:

```sh
npm i -g @fujia/cli-core

# or using yarn
yarn global add @fujia/cli-core
```

然后, 通过上面全局安装的 cli tools 使用模板初始化项目：

```sh
# step1. create project folder
mkdir [project name]; cd $_;

# step2. initial project via the template
stage init

# step3. select "default" option.

# step4. select "app" option.

# step5. entering project name and version.

# step3. select "electron-react-webpack" option.
```

当然, 如果你不想在全局安装@fujia/cli-core，你也可以使用下面的命令快速初始化一个项目：

```sh
# step1. create project folder
mkdir [project name]; cd $_;

# step2. initial project via the template
npm init stage@latest

# the other steps follow above.
```

就是这样, 项目会自动安装依赖并启动。

## 开发

在 dev 环境下启动应用:

```sh
npm start
```

为当前宿主机的操作系统打包应用:

```sh
npm run release
```

构建一个未打包的应用，便于测试。

```sh
npm run pack
```

## 注意

默认情况下，我们禁用了 node integration, 为什么? [查看这里](https://www.electronjs.org/docs/latest/tutorial/security#2-do-not-enable-nodejs-integration-for-remote-content)

如果你想启用 node integration 或使用原生模块，请按照下面的步骤修改对应的配置：

webpack.config.renderer.base.js

```js
- target: ['web', 'electron-renderer'],
+ target: 'electron-renderer',

- library: {
-  type: 'umd',
- },
```

webpack.config.main.prod.js

```js
entry: {
   main: srcMainEntryPath,
-  preload: srcMainPreloadPath,
},
```

main.ts

```ts
webPreferences: {
+  nodeIntegration: true,
+  contextIsolation: false,
-  preload: app.isPackaged
-    ? path.join(__dirname, 'preload.js')
-    : path.join(__dirname, '../../release/bundled/preload.js'),
},
```

## Maintainers

- [fujia](https://github.com/fushenguang)

## License

MIT © [electron-webpack-react-template](https://github.com/fujia-cli/electron-webpack-react-template)

## 参考资料

1. 《深入浅出 Electron：原理、工程与实践》

2. [electron-react-boilerplate](https://electron-react-boilerplate.js.org/docs/installation/)

