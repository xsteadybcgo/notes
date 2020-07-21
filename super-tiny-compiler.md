[super-tiny-compiler仓库](https://github.com/jamiebuilds/the-super-tiny-compiler/blob/master/the-super-tiny-compiler.js)

绝大多数的compiler包含三大步骤： 词法、句法分析（Parsing）, 代码转换（Transformation）, 和 代码生成（Code Generation）

- Parsing 将代码抽象.
- Transformation 对抽象出来的代码做一些编译需要的工作.
- Code Generation 将转换后的抽象代码生成平台代码

### Parsing
- tokenizer 程序做词法分析，tokens是用对象数组来描述一些独立部分的，如数字、符号等等
- 句法分析生成AST，深层嵌套的对象，用于表示token之间的联系。

例子：`(add 2 (subtract 4 2))`

Tokens 看上去是这样的:
 ```

  
     [
       { type: 'paren',  value: '('        },
       { type: 'name',   value: 'add'      },
       { type: 'number', value: '2'        },
       { type: 'paren',  value: '('        },
       { type: 'name',   value: 'subtract' },
       { type: 'number', value: '4'        },
       { type: 'number', value: '2'        },
       { type: 'paren',  value: ')'        },
       { type: 'paren',  value: ')'        },
     ]
```
  
AST看上去是这样的：
```  
     {
       type: 'Program',
       body: [{
         type: 'CallExpression',
         name: 'add',
         params: [{
           type: 'NumberLiteral',
           value: '2',
         }, {
           type: 'CallExpression',
           name: 'subtract',
           params: [{
             type: 'NumberLiteral',
             value: '4',
           }, {
             type: 'NumberLiteral',
             value: '2',
           }]
         }]
       }]
     }
```

### Transformation
以 _visitor_ 的方式来处理，创建另外一个tree
```
     -> Program (enter)
       -> CallExpression (enter)
         -> Number Literal (enter)
         <- Number Literal (exit)
         -> Call Expression (enter)
            -> Number Literal (enter)
            <- Number Literal (exit)
            -> Number Literal (enter)
            <- Number Literal (exit)
         <- CallExpression (exit)
       <- CallExpression (exit)
     <- Program (exit)
     
     
     // 保证在enter 和 exit 都有处理能力
      var visitor = {
        NumberLiteral: {
          enter(node, parent) {},
          exit(node, parent) {},
        }
      };
```
### Code Generation
有很多种方式，有的是复用之前的tokens，有的是创建了线性打印代码节点的代码表示，或者干脆直接在AST上递归处理



