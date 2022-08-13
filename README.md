<h1 align="center">Welcome to hamibot-starter 👋</h1>
<p align="center">
  <a href="https://www.npmjs.com/package/script-template" target="_blank">
    <img alt="Version" src="https://img.shields.io/npm/v/script-template.svg">
  </a>
  <a href="#" target="_blank">
    <img alt="License: MPL--2.0" src="https://img.shields.io/badge/License-MPL--2.0-yellow.svg" />
  </a>
</p>

> 一个用来快速开始编写 `Hamibot` 脚本的模板，使用 `TypeScript` 编写。
>
> 通过声明文件提供 `Hamibot` 绝大部分函数的代码提示、类型检查和文档，帮你减少键入次数和查询官方文档的时间。提供常用的代码片段，直接调用可以辅助更快完成开发，并让你能专注于核心功能。
>
> 欢迎各位大佬帮我一起完善这个项目！

## 安装依赖

```sh
npm install
```

## 使用方法

1. 下载本仓库，有两种方式可选：
   1. 点击 [Use this template](https://github.com/batu1579/hamibot-starter/generate) 按钮以此仓库为模板创建一个自己的仓库，然后将仓库克隆到本地。
   2. 如果你不准备使用 Git 作为版本管理工具，可以直接通过 `Code` -> `Download ZIP` 下载压缩包。
2. 在 `.\src` 文件夹下编写代码，程序入口为 `src\index.ts` 。
3. 完成编写后打包项目，有两种方式可选：
   1. 使用 VSCode 快捷键 `ctrl + shift + b` 打开任务菜单，然后选择 `npm build` 打包。
   2. 使用命令打包项目：

      ```sh
      npm run build
      ```

4. 在控制台上传打包后的文件: `.\dist\index.js` 。

## 注意事项

1. 编写 UI 或悬浮窗时请记得将文件扩展名修改成 `tsx` 。
2. UI 模块的类型提示目前我还没试过，如果发现了 BUG 拜托大大们帮我提一下 issue 。
3. 如果有用到暂时没有声明过的模块，可以使用 ts 忽略:

   > 注意：忽略会跳过所有检查，除了语法错误。使用时会有风险，请在确保肯定不会出现问题后再使用。

    ```typescript
    // 多行忽略（取消两个标记间的代码检查。）
    // 可以不使用结束标记，即忽略到文件结尾。
    // 注意：必须在文件顶部使用。
    // @ts-nocheck

    // 要跳过检查的某段代码
    canvas.drawLine(0, 0, 1080, 1920, paint);

    // @ts-check

    // 单行忽略（取消下一行的代码检查。）
    // @ts-ignore
    canvas.drawLine(0, 0, 1080, 1920, paint);
    ```

## 建议

1. 设置默认值时可以使用空值合并运算符 `??` 。

    ```typescript
    // 不使用空值合并运算符
    let appName = app.getAppName('yyy');

    if (appName === null) {
        appName = '未找到应用';
    }

    // 使用空值合并运算符
    let appName = app.getAppName('yyy') ?? '未找到应用';
    ```

2. 某些只针对特定情况的代码可以使用可选链运算符 `?.` 。在问号左侧的表达式为 `null` 或 `undefined` 时跳过代码。

    ```typescript
    // 查找跳过并点击，但是有时并没有跳过可以点击。
    // 这时必须判断而不能使用非空断言，否则会出现 `undefined` 没有对应方法的问题。

    // 不使用可选链运算符
    let skipButton = textContains('skip').findOne(1000);
    if (skipButton) {
        skipButton.click();
    }

    // 使用可选链运算符
    textContains('skip').findOne(1000)?.click();
    ```

3. 有时候函数的返回值可能会根据某个参数或者设置而改变，或者有的函数会返回 `null` 。一般的建议是通过判断或其他方式收窄类型，这样可以保证程序的鲁棒性。但是如果某些情况下你十分确定不会出现另一种类型，可以使用类型断言收窄类型或者非空断言来排除 `null` 类型。

    > 注意：这种方式相当于强行让编辑器修改类型，但是在编译后的代码里并不会有任何验证。所以请谨慎使用。

    ```typescript
    // 类型断言
    let xxx = sensors.register("xxx") as SensorEventEmitter;

    // 非空断言（推荐，因为有的类型被隐藏了，想要使用还需要手动导入。）
    let yyyy = sensors.register("yyy")!;
    ```

## TODO List

- [ ] 添加声明文件 [24/26]
  - [ ] Util
  - [ ] Canvans
- [ ] 使用 `Eslint` 在提交前统一代码风格
- [ ] 将所有的预制函数使用 `TypeScript` 重写
- [ ] 检查泛型注释
- [ ] 检查回调函数注释
- [ ] 检查注释中的类和方法是否使用行内代码格式
- [ ] 检查注释中的示例代码是否都能够运行
- [ ] 统一函数类型（Function、function）

## 作者

👤 **BATU1579**

- Github: [@batu1579](https://github.com/batu1579)

## 支持

如果有帮到你的话，帮我点颗小星星叭~ ⭐️

***
_This README was generated with ❤️ by [readme-md-generator](https://github.com/kefranabg/readme-md-generator)_
