# API设计

## RESTful API

RESTful API可以用OpenAPI定义，参见 [openapi.yaml](openapi.yaml)，文档参见[Todo.md](./Todo.md)。

在线预览： https://dm7m2v24p4.apifox.cn/

1. **资源关系**

   - `Todo` 关联 `Category` 和多个 `Tag`，通过 `categoryId` 和 `tagIds` 字段引用
   - `Reminder` 作为 `Todo` 的子资源（嵌套路由 `/todos/{todoId}/reminders`）
   - `Memo` 作为独立资源，通过 `todo.memoId` 关联

2. **通用模式复用**

   - 使用 `components` 定义可复用的模型和响应
   - 统一错误处理（`Error` schema）

3. **安全认证**

   - 全局安全方案使用 JWT Bearer Token

4. **过滤与分页**

   - Todo 列表支持按状态过滤和分页参数

5. **符合 REST 规范**
   - 正确使用 HTTP 方法语义（GET/POST/PUT/DELETE）
   - 资源标识使用 UUID

## 工具

- **Swagger UI**：生成可视化文档
- **OpenAPI Generator**：生成服务端/客户端代码
- **Postman**：导入并测试接口

## gRPC

除了RESTful API，还可以使用 [gRPC](https://grpc.io/) ，其定义参见[todo.proto](todo.proto)。
