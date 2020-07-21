绝大多数的compiler包含三大步骤： 词法、句法分析（Parsing）, 代码转换（Transformation）, 和 代码生成（Code Generation）

- Parsing 将代码抽象.
- Transformation 对抽象出来的代码做一些编译需要的工作.
- Code Generation 将转换后的抽象代码生成平台代码

### Parsing
- tokenizer 程序做词法分析，tokens是用对象数组来描述一些独立部分的，如数字、符号等等
- 句法分析生成AST，深层嵌套的对象，用于表示token之间的联系。
