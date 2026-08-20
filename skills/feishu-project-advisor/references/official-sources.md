# 官方来源与核验方法

## 来源登记

最后完整核验：`2026-08-20`，时区 `Asia/Shanghai`。

| 来源 | 入口 | 主要用途 |
|---|---|---|
| 产品手册 | https://project.feishu.cn/b/helpcenter/1ykiuvvj/1afedyby | 产品配置、使用方式、AI、视图、WBS、自动化与版本说明 |
| 开发者手册 | https://project.feishu.cn/b/helpcenter/1p8d7djs/nh4exbsn | 插件、AI 应用、OpenAPI、事件、文件 API 与开发工具 CLI |
| MCP 文档 | https://bytedance.larkoffice.com/docx/WR2edlyg0oma39xVkSKcbgCBn3g | MCP 连接、案例、排错、个人/插件 MCP 与工具概览 |

入口可能只锚定一个页面。检查“是否有新增”时必须遍历整本目录，不能只读取入口页。

## 核验规则

1. 优先比较目录节点的 `created_at`、`publish_at` 和 `updated_at`。
2. `created_at` 判断新页面，`publish_at` 判断旧草稿新公开，`updated_at` 只说明可能修改，不能单独证明正文发生了什么变化。
3. 对高影响页面继续读取章节标题或正文，确认能力、入口和限制，而不是只看页面名称。
4. 登录或权限失败时明确标注未验证范围，不绕过权限。
5. 版本、计费、限制、工具数量、参数和功能入口在使用前重新核验。
6. 保存核验日期和官方链接，不复制整本手册。

## 已知注意事项

- 产品视图 MQL 和 OpenAPI/CLI MQL 是不同使用面；不要混用语法片段。
- MCP 文档在 `2026-08-20` 的标题写“48 个实例侧读写工具”，正文仍出现“34 个实例侧读写工具”，数量口径不一致。把工具 schema 或当前 CLI/服务返回作为执行依据。
- 帮助中心公开目录可以从页面的 `window._ROUTER_DATA` 中读取；目录元数据是变更线索，正文才是能力结论。
- MCP 云文档使用现有飞书用户身份只读获取；禁止输出 Token、访问凭证或页面中的敏感配置。
