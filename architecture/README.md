# 系统架构


```mermaid
flowchart TB
    subgraph 客户端
        A[Web端\nReact+Ant Design] -->|HTTP API| D
        B[移动端\nReact Native] -->|HTTP API| D
        C[微信小程序\nTaro] -->|HTTP API| D
    end

    subgraph 服务端
        D[NestJS API Server] --> E[业务模块]
        E --> F[用户鉴权]
        E --> G[Todo管理]
        E --> H[数据同步]
        D --> I[(MongoDB)]
        D --> J[Redis缓存]
        F -->|微信开放平台| K[微信登录]
    end

    subgraph 基础设施
        L[阿里云ECS] --> M[Docker容器]
        N[HTTPS证书] --> D
        O[ELK日志系统] --> D
        P[Prometheus监控] --> D
    end

    style D fill:#F0F4C3
    style E fill:#C8E6C9
    style I fill:#BBDEFB
    classDef tech fill:#fff,stroke:#666;
    class A,B,C,D,E,F,G,H,I,J,K,L,M,N,O,P tech
```

## 技术栈选择依据：

1. **服务端**：
   - **NestJS**：TypeScript支持、模块化架构、集成Swagger文档
   - **MongoDB**：灵活存储Todo数据结构（支持标签/分类/时间戳）
   - **Redis**：缓存高频访问的Todo列表数据
   - **JWT**：结合微信UnionID实现跨端用户体系

2. **Web端**：
   - **React 18**：函数组件+Hooks开发模式
   - **Ant Design**：企业级UI组件库（Table/Form/Calendar）
   - **Zustand**：轻量级状态管理
   - **Vite**：快速构建工具

3. **移动端**：
   - **React Native**：复用Web业务逻辑（共享TypeScript类型定义）
   - **React Navigation**：实现底部Tab导航
   - **SQLite**：本地离线存储（同步冲突解决方案）

4. **微信小程序**：
   - **Taro 3**：React语法统一多端开发
   - **Taro UI**：适配小程序样式的组件库
   - **WXS**：优化性能关键路径

## 关键架构设计：

1. **数据同步方案**：
```mermaid
sequenceDiagram
    客户端->>服务端: 发起同步请求（携带lastSyncTime）
    服务端->>MongoDB: 查询变更记录（where updatedAt > lastSyncTime）
    MongoDB-->>服务端: 返回增量数据
    服务端->>客户端: 返回{ updates: [], deletes: [] }
    客户端->>本地存储: 合并数据（冲突处理策略）
    客户端->>服务端: 上报本地变更队列
```

2. **微信登录流程**：
```mermaid
flowchart LR
    小程序端 -->|wx.login| 微信服务器 -->|code| 服务端
    服务端 -->|code+secret| 微信开放平台 -->|unionid| 服务端
    服务端 -->|生成JWT| 小程序端
    服务端 -->|关联用户系统| MongoDB
```

3. **性能优化措施**：
   - **CDN加速**：静态资源部署到OSS
   - **分页加载**：Todo列表无限滚动
   - **Web Worker**：复杂计算（如Todo统计分析）
   - **差分同步**：仅传输变更数据
