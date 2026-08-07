# qwqnt-community-indexes

一个基于 **Node.js + GitHub Actions** 的自动化工具，用于**定时获取 GitHub 组织及第三方仓库的最新信息**，并将更新内容**转发到
Telegram 群**，同时利用仓库的 `data` 分支进行**持久化状态存储**。

## 项目目标

- 每天 **0 点** 自动检查指定 GitHub 仓库的最新 Release
- 仅追踪 **带有 `qwqnt-framework-plugin` topic 的仓库**
- 当最新 Release 的版本 tag 变化：
    - 删除 Telegram 群中上一条对应仓库的消息
    - 发送包含 Release 说明的新消息
    - 更新并持久化仓库状态数据
- 相同版本 tag 的 Release 正文修改不会触发重新发送
- 尚未发布 Release 的仓库会保持追踪，但不会发送消息
- 支持通过 **GitHub Actions workflow\_dispatch**：
    - 手动添加第三方仓库进行追踪
    - 手动删除不再需要追踪的仓库
