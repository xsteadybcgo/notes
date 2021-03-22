- `as const`
- ts can only narrow down to a explict type
- Discriminated unions break the union type，then narrow down them
- Call Signatures -- 为函数添加额外的 properties :

```
type DescribableFunction = {
  description: string;
  (someArg: number): boolean;
};
```

- Constraints, 限制generic特定属性 : `Type extends { length: number }`
- `unknown` is safer than `any`, unknown 和 narrow down 一起控制更nice
- 下面的`Function`类型可以被调用，该类型返回值为`any`类型
```
function doSomething(f: Function) {
  f(1, 2, 3);
}
```
不推荐这么使用。
如果想创建不调用的函数类型，可以使用`()=>void`

- literal function 和 arrow function 在使用void return type上不太一样，前者强一致性，后者忽略不一致类型
