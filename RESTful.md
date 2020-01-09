# REST 的 6个限制
- CS架构 关注点分离、简单性、可移植性
- stateless 不依赖上下文信息，如请求页码下一页，必须传递第几页，c端会话信息对服务端是透明的，不依赖上下文
- cache 服务端响应都要被标为 _可缓存_ or _不可缓存_
- **统一接口** 接口设计尽可能统一通用，与实现解偶
- 分层系统，只知道相邻的一层，如代理。分层：安全、负载均衡、缓存
- 按需下载，c端可按需 下载s端的js代码

### 统一接口
- 资源标识，REST都是围绕**资源**展开，都是些名词，而非动词
- client通过**表述**操作资源，如json，而不是通过执行sql
- 每个消息（请求）必须有足够的信息：是否缓存、用什么方法（get post patch delete）, 媒体类型（application/json, text/html）
- 超媒体作为应用状态引擎，点击链接跳转到另一个资源（json/html） 

uri + http方法 + 媒体类型

> github api 是教科书一般的存在，建议多查阅学习

### 请求设计规范
- URI用名词，尽量复数，如 /users
- URI使用嵌套表示关联关系，如/users/12/repos/5 id为12的用户的id为5的仓库
- 使用正确的HTTP方法，GET/POST/PUT/PATCH
- 不符合CRUD
  + 使用post/action/子资源 如:转移仓库 post repos/transfer
  + 查询字符串中加action 如：?action=transfer
  + 设计成子资源 如：users/repos不喜欢的 users/repos/star喜欢的 
  
### 响应设计规范
- 查询 符合查询条件 如：?since=1000 ?page=2&per_page=100
- 分页 第几页等分页信息
- 字段过滤 返回指定字段 如可返回姓名 性别 年龄，过滤只返回 _姓名_ ?fields=name
- 状态码规范 
- 错误处理 
```json
  {
    "message": "xxxx",
    "errors": [{
       "resource": "issue",
       "field": "title",
       "code": "missing_field"
    }]
  }
```

### 安全
- https
- 鉴权
- 限流 分层中加分流层

### 开发者友好
- 文档
- 超文本链接

### 响应规范
- get 返回查询的对象或列表
- post 返回新建的对象
- put 返回修改后的项
- delete status 204 

### 参数
- query string 一般为可选参数 `?q=age`
- router params 一般必选可放在这 如：`/user/:id`
- body 如 `{name: "Teady"}`
- header 请求头




