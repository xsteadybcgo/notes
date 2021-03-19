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
