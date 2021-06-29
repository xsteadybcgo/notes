### 1. 用户界面
#### 文档中提到的各个功能模块对应的用户界面
- Editor（编辑器） - 编辑你的文件的主要区域。你可以随心所欲地垂直和水平地打开多个编辑器。
- **Side Bar**（侧边栏） - 包含不同的**View**，如**Explorer**，以帮助你在你的项目上工作。
- Status Bar（状态栏） - 关于打开的项目和你编辑的文件的信息。
- Activity Bar（活动栏） - 位于最左边，它让你在不同的视图之间切换，并提供额外的特定上下文指示器，比如当 Git 启用时，文件变化修改的数量。
- Panels（面板） - 你可以在编辑器区域下面显示不同的面板，用于输出或调试信息，错误和警告，或一个集成终端。面板也可以移到右边以获得更多的垂直空间。
![image](https://user-images.githubusercontent.com/19681921/123568817-b1835400-d7f7-11eb-8bd6-2d2f27d8ab80.png)


### 2. Hello world 扩展
>从一个最简单的vscode扩展来认识插件开发的 key point

开发插件的三个关键点解释：
- [Activation Event](https://code.visualstudio.com/api/references/activation-events) _identifier_
- [Contribution Point](https://code.visualstudio.com/api/references/contribution-points)  定制化用户界面：设置、icon、when子句、菜单等等
- [VS Code API](https://code.visualstudio.com/api/references/vscode-api) 搜索技巧：[api_url](https://code.visualstudio.com/api/references/vscode-api)_#api key word_

`activate`函数的第一个参数为[ExtensionContext](https://code.visualstudio.com/api/references/vscode-api#ExtensionContext.workspaceState)

### 3. VSCODE EXTENSITON的能力
+ Command [通用]
  - 自定义命令，包括使用vscode[内建命令](https://code.visualstudio.com/api/references/commands)来构建上层命令
  - 命令触发可以通过Command Palette，或者菜单，并且可以通过when子句条件显示。
+ Configuration [通用]
  - 设置界面设置与读取
+ Keybinding [通用]
  - 绑定快捷键
+ Context Menu [通用]
  - 右键菜单，右键菜单可以通过控制explorer/editor/scm 等等控制显示在不同区域的菜单中
+ [workspace 上下文](https://code.visualstudio.com/docs/editor/workspaces)
+ 不同类型气泡通知 [通用]
+ 文件选择 [通用]
  - vscode-extension-samples/source-control-sample 示例
+ output 日志输出 [通用]
+ 进度条 [通用]
+ 主题定制化
  - 编辑区域背景
  - 代码高亮
  - icon主题定制
+ Workbench 
  - 各个主要区域的扩展![image](https://user-images.githubusercontent.com/19681921/123679604-3fa01e80-d87a-11eb-9355-db4f5a6eedce.png)
  - Webview 自定义editor、view、panel，甚至集成React/Svelte等生成webview，功能十分强大但必要性需要考虑，“重”。
  - Debugger调试工具集成，使用vscode的ui，通过DA与DAP集成调试工具
  - Notebook etc
+ 语言类型扩展

### 4. 文档延伸阅读
- [DOCS](https://code.visualstudio.com/docs) 可以更好更全面的来评估vscode插件的能力
- [YouTube - How to Code a VSCode Extension](https://www.youtube.com/watch?v=a5DX5pQ9p5M) 油管上一个vscode插件开发的视频，建议将文档文档梗概看完后观看视频作为开发指南的补充。
- [官方仓库示例](https://github.com/microsoft/vscode-extension-samples) 
- [插件开发指南](https://code.visualstudio.com/api/references/extension-guidelines) 插件最佳实践的指导意见
