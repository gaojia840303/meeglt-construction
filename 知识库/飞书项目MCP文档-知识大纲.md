# 飞书项目 MCP 文档 - 知识大纲

> 本大纲基于原始飞书云文档「飞书项目 MCP 上新：让 AI 成为你的项目助理」（https://bytedance.larkoffice.com/docx/WR2edlyg0oma39xVkSKcbgCBn3g ，6月25日修改）以及飞书项目帮助中心、Aily 帮助中心等相关官方文档整合而成。
> 由于飞书云文档存在动态加载限制，原始文档仅能完整抓取到「一、MCP 是什么」章节，「二、如何开启你的飞书项目 MCP 之旅？」及之后章节的内容通过飞书项目帮助中心官方文档（project.feishu.cn/b/helpcenter/）补充完整。

---

## 外部链接 URL 清单（便于后续深入阅读）

### 原始文档与官方总入口
| 序号 | URL | 说明 |
|------|-----|------|
| 1 | https://bytedance.larkoffice.com/docx/WR2edlyg0oma39xVkSKcbgCBn3g | 原始飞书云文档「飞书项目 MCP 上新：让 AI 成为你的项目助理」 |
| 2 | https://project.feishu.cn/b/helpcenter/1ykiuvvj/wzb3ycsc | 飞书项目帮助中心 -「在 AI 工具中连接 MCP」（核心配置文档） |
| 3 | https://project.feishu.cn/b/helpcenter/1p8d7djs/jdmql9oj | 飞书项目帮助中心 -「插件体系 MCP Server 介绍」（含完整 Tool 列表） |
| 4 | https://project.feishu.cn/b/helpcenter/1ykiuvvj/19wmvt8b | 飞书项目帮助中心 -「工具功能列表」（含 Prompt 示例） |
| 5 | https://aily.feishu.cn/hc/1u7kleqg/fiogabrc | 飞书 Aily 帮助中心 -「添加和使用 MCP」 |

### MCP 协议与第三方工具官方文档
| 序号 | URL | 说明 |
|------|-----|------|
| 6 | https://modelcontextprotocol.io/docs/develop/connect-remote-servers | MCP 协议 - 连接远程 MCP Server |
| 7 | https://modelcontextprotocol.io/docs/develop/connect-local-servers | MCP 协议 - 连接本地 MCP Server |
| 8 | https://developers.openai.com/codex/mcp | Codex CLI - Model Context Protocol |
| 9 | https://cursor.com/docs/mcp#using-mcpjson | Cursor - Model Context Protocol (MCP) |
| 10 | https://docs.trae.ai/ide/add-mcp-servers?_lang=zh#455f47dc | Trae - 添加 MCP Server |
| 11 | https://docs.github.com/en/copilot/how-tos/provide-context/use-mcp/extend-copilot-chat-with-mcp | GitHub Copilot - 扩展 Copilot Chat with MCP |
| 12 | https://github.com/google-gemini/gemini-cli | Gemini CLI GitHub 仓库 |
| 13 | https://docs.dify.ai/en/use-dify/build/mcp | Dify - Using MCP Tools |
| 14 | https://docs.dify.ai/en/use-dify/getting-started/quick-start | Dify - 30 分钟快速开始 |
| 15 | https://space.coze.cn/ | 扣子空间 |

### MCP Server URL 格式
| 序号 | URL 模式 | 说明 |
|------|----------|------|
| 16 | `https://project.feishu.cn/mcp_server/v1?mcpKey=aaaaa-bbbb-xxxx&userKey=<userKey>` | 插件体系 MCP Server URL 格式 |
| 17 | `{domain}/mcp_server/v1` | 个人 MCP Server URL 模板（domain 在「功能入口」获取） |

### 相关飞书开放平台 MCP 文档（飞书 OpenAPI MCP，非飞书项目 MCP）
| 序号 | URL | 说明 |
|------|-----|------|
| 18 | https://open.feishu.cn/document/uAjLw4CM/ukTMukTMukTM/mcp_integration/mcp_installation?lang=zh-CN | 飞书开放平台 - 本地调用 OpenAPI MCP |
| 19 | https://open.feishu.cn/document/uAjLw4CM/ukTMukTMukTM/mcp_integration/advanced-configuration?lang=zh-CN | 飞书开放平台 - 高级配置 |
| 20 | https://open.feishu.cn/document/mcp_open_tools/developers-call-remote-mcp-server?lang=zh-CN | 飞书开放平台 - 开发者调用远程 MCP 服务 |
| 21 | https://open.feishu.cn/document/mcp_open_tools/end-user-call-remote-mcp-server?lang=zh-CN | 飞书开放平台 - 个人调用远程 MCP 服务（已弃用） |
| 22 | https://aily.feishu.cn/?to=ai/mcpservers | Aily MCP 市场 |
| 23 | https://cloud.dify.ai/tools | Dify 平台 |
| 24 | http://git-hub.com/larksuite/lark-openapi-mcp | GitHub - 飞书/Lark 官方 OpenAPI MCP |

---

## 一、MCP 是什么？给你的 AI 助理一扇"授权门"

### 1. 核心概念
- **类比说明**：把 Aily 或 Claude 里的 AI 想象成一个被关在小黑屋里的超级助理——他知识渊博，但无法访问你项目中的具体数据。MCP 就是给这个助理开了一扇通往你飞书项目的"授权门"。
- **通过这扇门，AI 可以**：
  - 安全地查询你的工作项
  - 更新状态
  - 创建任务
  - 分析节点数据
  - 就像一个真正坐在你身边的项目助理

### 2. 一句话解释 MCP
- **MCP（Model Context Protocol）是一套开放协议**，让 AI 工具能像人一样"读懂"并"操作"飞书项目这类外部软件。
- **飞书项目官方提供的 MCP 服务**，就是让任何支持该协议的 AI 工具都能成为你的个人项目助理。

### 3. 授权机制特点
- **基于个人授权**：仅访问你有权限的数据
- **无需管理员配置**：个人即可开启
- **不影响团队其他人**：隔离的个人数据访问

### 4. 看看你能用它做什么？（四大典型场景）

#### 4.1 个人待办管理
- 快速查询"我本周要做的所有事"
- 一句话更新任务状态

#### 4.2 跨工具联合查询
- AI 能自动串联多个工具
- 示例：筛选出本迭代所有高优 Bug，并整理成多维表格

#### 4.3 节点深度分析
- 深入分析"某个需求从提议到上线，在每个阶段花了多少时间"
- 精准定位瓶颈

#### 4.4 团队人力排期
- 轻松了解"我们团队 Q1 的资源都投在哪些项目上了"
- 让资源分配更透明

---

## 二、如何开启你的飞书项目 MCP 之旅？

> ⚠️ 说明：原始飞书云文档的此章节内容因动态加载限制未能完整抓取。以下内容综合自飞书项目帮助中心官方文档（https://project.feishu.cn/b/helpcenter/1ykiuvvj/wzb3ycsc）。

### 1. 前提条件
- **在飞书项目中启用 MCP，并完成授权**
- 启用入口位于飞书项目内的「功能入口」处
- 在「功能入口」可获取以下凭证：
  - **X-Mcp-Token**：用于 HTTP Header 连接方式
  - **MCP_USER_TOKEN**：用于 Stdio 连接方式
  - **domain**：MCP Server 的域名，用于拼接 `{domain}/mcp_server/v1`

### 2. 三种连接方式

飞书项目 MCP 支持三种连接方式，可按需选择：

#### 2.1 HTTP OAuth（推荐，最安全）
- **配置 JSON**：
```json
{
  "mcpServers": {
    "my-mcp-server": {
      "httpUrl": "{domain}/mcp_server/v1"
    }
  }
}
```
- **特点**：基于 OAuth 协议授权，首次使用时由 AI 工具引导在浏览器中完成授权
- **要求**：AI 工具需支持 OAuth 授权，且支持动态 Client_id

#### 2.2 HTTP Header
- **配置 JSON**：
```json
{
  "mcpServers": {
    "FeishuProjectMcp": {
      "url": "{domain}/mcp_server/v1",
      "headers": {
        "X-Mcp-Token": "<your_token>"
      }
    }
  }
}
```
- **特点**：通过 X-Mcp-Token 鉴权，token 在「功能入口」获取

#### 2.3 Stdio
- **配置 JSON**（以 npx 调用本地 stdio 服务为例）：
```json
{
  "mcpServers": {
    "FeishuProjectMcp": {
      "command": "npx",
      "args": ["-y", "@larksuiteoapi/lark-mcp", "mcp", "--token", "<MCP_USER_TOKEN>"]
    }
  }
}
```
- **特点**：通过本地 stdio 协议通信，使用 MCP_USER_TOKEN 鉴权

### 3. MCP Server URL 格式（插件体系）
- **格式**：`https://project.feishu.cn/mcp_server/v1?mcpKey=aaaaa-bbbb-xxxx&userKey=<userKey>`
- **可拼接参数**：

| Key | Value 示例 | 用途 |
|-----|-----------|------|
| `userKey` | `726781779399358xxxx` | 在飞书项目空间，Hover 鼠标至用户头像，然后在名片中双击头像获取。配置后，所有写入操作都将以该用户的身份执行，并记录在操作日志中。此设置会覆盖对话中提及的任何其他用户。 |

- **传输方式**：Streamable HTTP（基于 HTTP 协议的分块流式传输）

---

## 三、支持的 AI 工具及配置方式

> 综合自飞书项目帮助中心文档：https://project.feishu.cn/b/helpcenter/1ykiuvvj/wzb3ycsc

### 1. Claude Code

#### 1.1 配置步骤
1. 打开 Claude Code，在导航栏选择 **Settings（齿轮图标） > MCP > Open Config File**，自动打开 `mcp.json` 文件
2. 也可手动找到 `mcp.json` 文件，支持两个级别：
   - **全局/用户级**：`~/.claude.json` 或 `~/.claude/config.json`
   - **项目级**：项目根目录下的 `.claude.json`
3. 在 JSON 文件中，所有连接都配置在顶层的 `mcpServers` 对象下
4. 配置 `mcp.json` 文件并保存
5. 若使用 HTTP OAuth：在对话框中输入 `/mcp`，Claude Code 会提示并引导你在浏览器中完成 OAuth 授权
6. 使用 `/mcp` 命令可列出并管理你已安装的 MCP Server

#### 1.2 配置示例（HTTP OAuth）
```json
{
  "mcpServers": {
    "my-mcp-server": {
      "httpUrl": "{domain}/mcp_server/v1"
    }
  }
}
```

#### 1.3 参考链接
- https://modelcontextprotocol.io/docs/develop/connect-remote-servers
- https://modelcontextprotocol.io/docs/develop/connect-local-servers

### 2. Manus

#### 2.1 配置步骤
1. 打开 Manus，选择 **连接器图标 > 添加连接器 > 自定义 MCP**，然后选择**通过 JSON 导入**
2. 在对话框中添加您的 JSON 配置
3. 单击导入，返回对话框即可开始体验

#### 2.2 配置示例（HTTP Header）
```json
{
  "mcpServers": {
    "FeishuProjectMcp": {
      "url": "{domain}/mcp_server/v1",
      "headers": {
        "X-Mcp-Token": "<your_token>"
      }
    }
  }
}
```

### 3. Codex CLI（ChatGPT Desktop）

#### 3.1 配置文件位置
- Codex 将 MCP 配置与其他配置项一同存储在 `config.toml` 文件中
- 支持两种作用域：
  - **全局配置**：`~/.codex/config.toml`
  - **项目级配置**：项目根目录下 `.codex/config.toml`（仅适用于受信任的项目）
- 命令行工具和 IDE 扩展共用这份配置文件，配置一次即可在两个客户端之间无缝切换

#### 3.2 配置步骤
1. 打开 `config.toml` 文件
2. 配置并保存
3. 若使用 HTTP OAuth：首次触发工具时，Codex CLI 会在终端提示你进行授权
4. 重启 Codex CLI 即可加载飞书项目 MCP 服务

#### 3.3 配置示例（HTTP OAuth，TOML 格式）
```toml
[mcpServers."my-mcp-server"]
httpUrl = "{domain}/mcp_server/v1"
```

#### 3.4 参考链接
- https://developers.openai.com/codex/mcp

### 4. Cursor

#### 4.1 配置步骤
1. 在 Cursor 中打开 `mcp.json` 配置文件，有两种交互方式：
   - **方式一**：按 `Cmd+Shift+J`（macOS）或 `Ctrl+Shift+J`（Windows/Linux），进入 **Features → Model Context Protocol**，点击右上角的编辑按钮
   - **方式二**：按 `Cmd+Shift+P`（macOS）或 `Ctrl+Shift+P`（Windows/Linux），输入 `Open MCP Configuration`，回车直接打开 `mcp.json`
2. 配置 `mcp.json` 文件并保存
3. 在对话框中选择飞书项目 MCP 服务即可开始使用

#### 4.2 配置示例（HTTP Header）
```json
{
  "mcpServers": {
    "FeishuProjectMcp": {
      "url": "{domain}/mcp_server/v1",
      "headers": {
        "X-Mcp-Token": "<your_token>"
      }
    }
  }
}
```

#### 4.3 参考链接
- https://cursor.com/docs/mcp#using-mcpjson

### 5. Trae

#### 5.1 配置步骤
1. 在 IDE 模式界面中，点击界面右上角的**设置图标**，在左侧导航栏中，选择 **MCP**，打开 MCP 窗口
2. 在 MCP 窗口的右上角，点击 **添加 > 手动添加**（首次添加也可直接点击窗口中部的「手动添加」按钮）
3. 配置并保存 JSON 文件
4. 在 Trae 对话框中选择安装飞书项目 MCP 的智能体，即可开始使用

#### 5.2 配置示例（HTTP Header）
```json
{
  "mcpServers": {
    "FeishuProjectMcp": {
      "url": "{domain}/mcp_server/v1",
      "headers": {
        "X-Mcp-Token": "<your_token>"
      }
    }
  }
}
```

#### 5.3 参考链接
- https://docs.trae.ai/ide/add-mcp-servers?_lang=zh#455f47dc

### 6. 扣子（Coze）

#### 6.1 配置步骤
1. 进入扣子空间（https://space.coze.cn/），在对话界面选择 **@ > 管理工具 > + 自定义工具**
2. 在添加自定义工具界面配置飞书项目 MCP
3. 在自定义工具中检查该 MCP 服务为"开启"状态，返回对话，就可以调用飞书项目 MCP 服务了

#### 6.2 配置示例（HTTP Header）
```json
{
  "mcpServers": {
    "FeishuProjectMcp": {
      "url": "{domain}/mcp_server/v1",
      "headers": {
        "X-Mcp-Token": "<your_token>"
      }
    }
  }
}
```

### 7. VSCode（GitHub Copilot）

#### 7.1 配置步骤
1. 在 VSCode 中，按下 `Ctrl + Shift + P`（Windows/Linux）或 `Cmd + Shift + P`（Mac）打开命令面板
2. 执行命令 `Github Copilot: Configure MCP Servers`，在弹出的选项中选择配置文件的保存位置：
   - **工作区设置（Workspace Settings）**：会在项目里创建 `.vscode/mcp.json` 文件，仅对当前工作区有效
   - **用户设置（User Settings）**：创建全局配置，适用于所有项目
3. 在 `mcp.json` 文件中配置飞书项目 MCP
4. 保存文件后，即可在 Copilot Chat 聊天框中，通过点击**回形针图标（Attach Context）**或直接输入 `@` 来调用已配置的 MCP 工具

#### 7.2 配置示例（HTTP Header）
```json
{
  "mcpServers": {
    "FeishuProjectMcp": {
      "url": "{domain}/mcp_server/v1",
      "headers": {
        "X-Mcp-Token": "<your_token>"
      }
    }
  }
}
```

#### 7.3 参考链接
- https://docs.github.com/en/copilot/how-tos/provide-context/use-mcp/extend-copilot-chat-with-mcp

### 8. Gemini CLI

#### 8.1 配置文件位置
- **全局**：`~/.gemini/settings.json`（所有项目生效）
- **项目级**：项目根目录 `/.gemini/settings.json`（仅当前项目）
- 可在终端运行 `gemini config path` 命令获取配置文件确切位置

#### 8.2 配置步骤
1. 打开配置文件
2. 修改并保存配置文件
3. 重新打开终端并启动 gemini CLI，执行 `/mcp list` 查看 MCP 状态
4. 在 Gemini CLI 中直接输入指令，自动调用 MCP

#### 8.3 配置示例（HTTP Header）
```json
{
  "mcpServers": {
    "FeishuProjectMcp": {
      "url": "{domain}/mcp_server/v1",
      "headers": {
        "X-Mcp-Token": "<your_token>"
      }
    }
  }
}
```

#### 8.4 参考链接
- https://github.com/google-gemini/gemini-cli

### 9. Dify

#### 9.1 配置步骤
1. 访问 Dify 平台（https://cloud.dify.ai/tools），创建一个 MCP 服务
2. 若使用 HTTP OAuth，单击创建好的 MCP 服务，根据指引完成 OAuth 授权
3. 创建 Dify 应用，在其中添加 MCP，即可开始使用

#### 9.2 配置示例（HTTP OAuth）
```json
{
  "mcpServers": {
    "my-mcp-server": {
      "httpUrl": "{domain}/mcp_server/v1"
    }
  }
}
```

#### 9.3 示例 Query
- "帮我查看这个视图<飞书项目 URL>有多少工作项，分别是什么"

#### 9.4 参考链接
- https://docs.dify.ai/en/use-dify/build/mcp
- https://docs.dify.ai/en/use-dify/getting-started/quick-start

### 10. OpenClaw

#### 10.1 集成方式
- 飞书项目发布了 **feishu-project-connector 技能**，支持在 OpenClaw 中通过自然语言与飞书项目进行交互
- 详见「(Beta) OpenClaw x 飞书项目集成实践」

#### 10.2 ⚠️ 安全提示
- 使用 OpenClaw 获取飞书项目数据，可能会有数据泄露风险
- **现阶段切勿使用公司/企业飞书账号接入！**
- 请务必优先使用**个人账号**进行体验和测试

### 11. 飞书 Aily

> 综合自：https://aily.feishu.cn/hc/1u7kleqg/fiogabrc

#### 11.1 在飞书 Aily 中使用
- 飞书 Aily 中**预置了部分 MCP 服务**，可直接打开使用
- 更多 MCP 可以点击"管理"按钮进行添加、移除和编辑操作

#### 11.2 在自定义智能体中添加 MCP
**方式 a：从 MCP 市场中添加**
1. 点击 MCP 服务右上角的添加按钮，进入服务列表，选择需要的服务并添加
2. MCP 市场中的服务包含：
   - **官方服务**（全员可用）
   - **企业服务**（企业内开发者注册后，可见性范围的员工可用）
3. 部分 MCP 服务在添加后需要填写相关信息（如高德服务需填写 API Key）

⚠️ 注意事项：
- 从市场添加的 MCP 服务会受到可见性范围管控
- 添加过多的 MCP 服务会导致调度不准，建议每次对话实际开启的服务**不超过 5 个**

**方式 b：添加自定义 MCP 服务**
- 开发者可添加自定义 MCP 服务（外部公开市场服务，或将企业自建系统接口封装成 MCP）
- 自定义 MCP 服务不会注册到 MCP 市场，仅供当前智能体使用
- 不需要设置可见性范围，智能体可见性范围内的用户均可调用

#### 11.3 创建企业自定义 MCP
1. 进入 Aily MCP 市场（https://aily.feishu.cn/?to=ai/mcpservers）
2. 配置 MCP 名称、图标、描述、介绍
3. 配置 MCP 请求地址
   - **Endpoint 类型**：支持 SSE 协议和 Streamable HTTP
   - **请求参数**：支持「用户输入」和「固定值」两种方式
   - **请求头**：支持「用户输入」和「固定值」两种方式
   - 请求头和请求参数加起来不超过 100 个，总体大小不超过 64k
4. 配置 MCP 可用范围（自己可用、指定成员可见、全员可见）

### 12. 其他 AI 工具
- 若上文未列出你的常用 AI 工具，只要工具支持连接 MCP，可按该 AI 工具指引自行连接
- **HTTP OAuth 连接方式要求**：AI 工具需支持 OAuth 授权，且支持动态 Client_id

---

## 四、MCP 提供的具体能力/工具列表

> 综合自：https://project.feishu.cn/b/helpcenter/1p8d7djs/jdmql9oj 与 https://project.feishu.cn/b/helpcenter/1ykiuvvj/19wmvt8b

### 1. 整体说明
- 飞书项目 MCP Server 提供了**多种 Tool**，覆盖实例操作、节点操作和常用查询等场景
- 飞书项目 MCP 已提供 **49 个工具**（7 大分类），并仍在持续扩展
- 该服务专门优化了工具（Tool）的输入和输出参数，使 AI 在读写飞书项目数据时，能更好地适配自然语言对话场景
- 与 Open API 相同，每个 Tool 的调用频率限制（QPS）为 **5**

### 2. 权限说明
- 飞书项目 MCP Server 可用的场景与开通的权限相关，使用时需确保勾选了对应权限
- 主要权限分类：
  - `project:project.v2.info:read` - 获取空间信息（跨空间）
  - `settings:settings.v2.basic.info:read` - 获取空间下的基础配置
  - `user:user.v2.info:read` - 获取用户信息（跨空间）
  - `work_item:work_item.v2.info:read` - 获取工作项实例信息
  - `work_item:work_item.v2.info:write` - 更新工作项实例数据

### 3. 工具分类清单（按功能模块）

#### 3.1 空间与人员

| Tool 名称 | 使用场景 | 示例 Prompt |
|-----------|---------|-------------|
| `search_project_info` | 获取空间基础信息（跨空间） | 查询【xx空间】中的基本信息。 |
| `list_workitem_types` | 获取空间下的工作项类型 | 查询【xx空间】中的所有工作项类型列表。 |
| `search_user_info` | 查询用户基础信息（批量查询，最多 20 个，可填写用户名称、Email、user_key） | 查询用户xx的信息。 |
| `list_workitem_relations` | 获取空间下的关联关系 | 查询【xx空间】中的关联关系列表。 |
| `list_project_team` | 查看团队列表 | 在空间查询团队列表信息。 |
| `list_team_members` | 查询团队成员信息（需团队名称+空间名称） | 查询【xx团队】在【xx空间】的成员列表。 |

#### 3.2 工作项实例

| Tool 名称 | 使用场景 | 示例 Prompt |
|-----------|---------|-------------|
| `list_workitem_field_config` | 获取空间下的字段配置 | 查询【xx空间】中，需求的字段配置信息，取前20条。 |
| `list_node_field_config` | 获取工作项节点字段信息（查询工作项类型的节点字段配置） | 查询【xx空间】中，需求的节点字段配置。 |
| `list_workitem_role_config` | 获取空间下角色配置信息 | 查询【xx空间】中，【工作项类型】的工作项的角色配置信息，列出10条。 |
| `get_workitem_brief` | 获取工作项实例信息（支持查询多个并 AI 分析总结） | 在&lt;飞书项目 URL&gt;空间，查询"文档需求1"、"文档需求2"的【文档描述】字段信息，并分析总结主要创建理由是什么。 |
| `get_workitem_field_meta` | 获取工作项元信息（用于创建工作项场景） | 查询【xx空间】中，【技术文档】类型的工作项的元信息。 |
| `create_workitem` | 创建工作项（支持连续创建多个，返回详情页 URL） | 在【xx空间】，帮我创建2个【技术文档开发需求】类型的工作项，使用默认模板，工作项名称为"文档需求1"。 |
| `update_field` | 更新工作项字段（一次修改多个字段，返回详情页 URL） | 修改&lt;飞书项目工作项实例 URL&gt;工作项的【文档描述】字段内容为"这是一个新描述"。 |
| `get_workitem_op_record` | 查询操作记录（单个或多个工作项） | 查询【xx空间】中，【测试集成】需求中，【用户1】的操作记录信息。 |
| `get_workitem_man_hour_records` | 获取工时登记记录列表 | 查询【xx空间】中，【测试集成】需求登记的工作信息。 |
| `list_related_workitems` | 获取关联工作项列表 | 查询【xx空间】中，【技术文档】类型的"开发者手册"工作项，通过【relation】关联的 issue 是什么。 |
| `search_by_mql` | 筛选条件查询（自然语言转 MOQL） | 查询【xx空间】下名称包含"文档"的【工作项类型】工作项有哪些。 |
| `list_schedule` | 查询人员排期 | 在【xx空间】查询我这个月的需求排期信息。 |
| `list_deliverables` | 批量查询交付物信息（WBS 场景） | 在【xx空间】查询交付物【工作项名称】的根工作项和来源工作项是什么。 |
| `get_resource_work_item_type_conf` | 获取工作项资源库配置信息 | 查询【xx空间】中【story】工作项类型的资源库配置信息。 |
| `create_resource_work_item` | 创建工作项资源库 | 在【xx空间】为【story】类型工作项创建一个名为"xxx"的资源库。 |
| `create_work_item_from_resource` | 通过资源创建实例 | 通过【xx空间】中的资源实例【工作项实例名称】创建一个新的工作项实例。 |

**list_todo 查询待办信息**（来自 meego-skill 索引补充）：
- 支持查询：我的待办、我的已办、我创建的、我关注的、我参与的工作项
- 示例：在【xx空间】查询我的待办工作项，返回最近5条。

#### 3.3 计划表（WBS）

| Tool 名称 | 使用场景 | 示例 Prompt |
|-----------|---------|-------------|
| `create_wbs_draft` | 创建计划表草稿（后续操作的前置步骤） | 请为工作项【xx】在空间【xx】创建一个 WBS 计划表草稿。 |
| `edit_wbs_draft` | 编辑计划表草稿（每次调用仅执行一项原子操作） | 在这个项目【xx 项目 URL】计划表草稿中【xx】节点下，新增一个子任务，名称是【子任务1】，负责人是【user】，排期是4/23-4/24，估分是1，交付物是【产物名称1】。 |
| `list_wbs_draft_rows` | 查询计划表草稿行（可按名称、负责人、阶段、状态、是否延期、是否里程碑筛选） | 查询这个项目【xx 项目 URL】计划表草稿中我负责的"计划阶段"的事项，列出状态、排期、估分、交付物。 |
| `list_wbs_instance_rows` | 查询计划表实例行（正式发布后的 WBS 数据） | 查询这个项目【xx 项目 URL】计划表中我负责的"计划阶段"的事项，列出状态、排期、估分、交付物。 |
| `publish_wbs_draft` | 发布计划表草稿（支持部分发布或全量发布） | 把【xx 项目 URL】的计划表发布到线上。 |
| `reset_wbs_draft` | 重置计划表草稿（支持部分重置） | 请重置【xx】空间下【xx】工作项的整个 WBS 草稿。 |
| `get_wbs_draft_operation_progress` | 查询计划表草稿异步操作进度 | 请查询这次 WBS 草稿编辑操作是否已经完成，operation_id 为 xxx。 |
| `list_element_template` | 获取流程资源库中的资源节点与资源任务模板 | 请查询【xx】空间下需求类型工作项可用的资源节点模板。 |

#### 3.4 流程与节点

| Tool 名称 | 使用场景 | 示例 Prompt |
|-----------|---------|-------------|
| `get_node_detail` | 获取节点信息（包括节点信息、子项信息、节点自定义字段信息） | 获取&lt;工作项 URl&gt;工作项的【开始】节点相关信息。 |
| `update_node` | 更新节点信息（字段、负责人、排期等） | 在【xx空间】中，更新&lt;飞书项目工作项实例 URL&gt;实例的【节点名称】节点负责人为"用户1"。 |
| `transition_node` | 完成/回滚工作项某个节点 | 完成&lt;工作项实例 URl&gt;工作项的【节点名称】节点。 |
| `update_node_subtask` | 更新子任务（创建、修改、完成、回滚） | 在【xx】空间中，更新&lt;飞书项目工作项实例 URL&gt;实例的【节点名称】节点下创建一个名称为"子任务名称"的子任务。 |
| `get_transition_required` | 获取指定节点/状态流转所需必填信息 | 帮我看看在项目【xx空间】中的【工作项名称】工作项，需要流转【xx】节点的必填信息是哪些？ |
| `get_transitable_states` | 获取可流转状态 | 帮我看看在项目【xx空间】中，缺陷类型的"工作项名称"中，我能流转节点到什么状态。 |
| `transition_state` | 流转状态流工作项的状态 | 帮我流转【xx空间】中"xx名称"工作项到"进行中"状态。 |

#### 3.5 视图与度量

| Tool 名称 | 使用场景 | 示例 Prompt |
|-----------|---------|-------------|
| `get_view_detail` | 获取指定视图中的实例信息 | 查询视图&lt;视图 URL&gt;下的工作项，遍历每一个工作项，获取【文档描述】字段信息，列出 Top 3 的用户问题，用表格来呈现。 |
| `list_multi_project_view_workitems` | 获取指定全景视图中的工作项实例信息 | 查询视图&lt;视图 URL&gt;下的所有工作项。 |
| `list_charts` | 查询空间指定视图下的所有度量图表（分页返回，默认每页50个） | 查询视图&lt;视图 URL&gt;下的度量图表信息，取前10的数据。 |
| `get_chart_detail` | 查看指定图表的详情信息 | 在【xx空间】查询&lt;图表 URL&gt;的数据。 |
| `search_view_by_title` | 模糊查询视图（最多20个） | 在【xx空间】查询需求中，包含"测试"的视图。 |
| `create_fixed_view` | 在指定空间和工作项类型下新增一个固定视图 | 在【测试集】空间创建一个需求的视图，叫"xx功能评测集"，包含【测试1】、【测试集2】2个工作项，协作模式为2。 |
| `update_fixed_view` | 更新固定视图的工作项列表（添加和删除不能同时操作） | 在【测试集】空间中更新"xx功能评测集"视图，删除【测试1】、【测试集2】2个工作项。 |

#### 3.6 评论

| Tool 名称 | 使用场景 | 示例 Prompt |
|-----------|---------|-------------|
| `add_comment` | 添加评论（支持简单文本及 Markdown 格式） | 在&lt;飞书项目工作项实例 URL&gt;实例里，评论一下：需求进度顺利，暂无风险。 |
| `list_workitem_comments` | 查询指定工作项实例中的评论列表 | 在【测试用例】空间，查询"技术需求测试"工作项的前10条评论。 |

#### 3.7 附件

| Tool 名称 | 使用场景 | 示例 Prompt |
|-----------|---------|-------------|
| `upload_file` | 在指定实例的评论/附件字段/富文本字段中添加一个附件或图片 | 在&lt;飞书项目工作项实例 URL&gt;实例里，把xxx文件作为附件上传到评论里。 |
| `get_download_url` | 下载评论/附件字段/富文本字段中的附件或图片 | 在【xx】空间，查询【工作项名称】工作项的xx字段内容，包含文本和图片。 |

---

## 五、授权机制

### 1. 个人授权 vs 管理员配置

| 维度 | 个人 MCP | 插件体系 MCP Server |
|------|---------|---------------------|
| 启用方式 | 用户个人在「功能入口」启用 | 在插件发布时启用 MCP Server |
| 授权粒度 | 基于个人授权，仅访问你有权限的数据 | 验证插件是否已申请相关权限并已在相应空间中安装 |
| 管理员干预 | 无需管理员配置 | 不受个人 MCP 开关管控 |
| 影响范围 | 不影响团队其他人 | 为团队或客户搭建 Agent |
| 适用场景 | 个人项目助理 | 企业级 Agent 构建 |

### 2. 三种鉴权方式对比

| 方式 | 凭证 | 特点 | 适用场景 |
|------|------|------|---------|
| HTTP OAuth | OAuth 2.0 | 最安全，需 AI 工具支持 OAuth + 动态 Client_id | 推荐方式，Claude Code、Codex CLI、Dify 等 |
| HTTP Header | X-Mcp-Token | 在「功能入口」获取 token | Cursor、Trae、扣子、VSCode、Gemini CLI、Manus 等 |
| Stdio | MCP_USER_TOKEN | 本地 stdio 协议通信 | 本地 AI 工具 |

### 3. 插件体系 MCP Server 授权特点
- 与 Open API 类似，MCP Server 会验证插件是否已申请相关权限，并已在相应空间中安装后才能使用
- 如果验证失败（例如空间未安装插件或当前用户无权限），服务器会返回具体原因，以便 AI 进行后续处理
- 采用 **Streamable HTTP** 传输方式
- **不受个人 MCP 开关管控**

### 4. userKey 身份覆盖机制
- 可将用户身份（userKey）作为查询参数拼接到 MCP Server URL 中
- 配置后，所有写入操作都将以该用户的身份执行，并记录在操作日志中
- **此设置会覆盖对话中提及的任何其他用户**
- 获取方式：在飞书项目空间，Hover 鼠标至用户头像，然后在名片中**双击头像**获取

---

## 六、使用示例和典型场景

### 1. 个人待办管理
- "在【xx空间】查询我的待办工作项，返回最近5条。"
- "一句话更新任务状态：帮我流转【xx空间】中'xx名称'工作项到'进行中'状态。"

### 2. 跨工具联合查询
- "筛选出本迭代所有高优 Bug，并整理成多维表格"
- "在&lt;飞书项目 URL&gt;空间，查询'文档需求1'、'文档需求2'的【文档描述】字段信息，并分析总结主要创建理由是什么。"

### 3. 节点深度分析
- "查询【xx空间】中，【测试集成】需求中，【用户1】的操作记录信息。"
- "获取&lt;工作项 URl&gt;工作项的【开始】节点相关信息。"

### 4. 团队人力排期
- "在【xx空间】查询我这个月的需求排期信息。"
- "查询【xx团队】在【xx空间】的成员列表。"

### 5. 工作项创建与更新
- "在【xx空间】，帮我创建2个【技术文档开发需求】类型的工作项，使用默认模板，工作项名称为'文档需求1'。"
- "修改&lt;飞书项目工作项实例 URL&gt;工作项的【文档描述】字段内容为'这是一个新描述'。"

### 6. 视图查询
- "帮我查看这个视图&lt;飞书项目 URL&gt;有多少工作项，分别是什么"（Dify 示例）
- "查询视图&lt;视图 URL&gt;下的工作项，遍历每一个工作项，获取【文档描述】字段信息，列出 Top 3 的用户问题，用表格来呈现。"

### 7. WBS 计划表操作
- "请为工作项【xx】在空间【xx】创建一个 WBS 计划表草稿。"
- "在这个项目【xx 项目 URL】计划表草稿中【xx】节点下，新增一个子任务，名称是【子任务1】，负责人是【user】，排期是4/23-4/24，估分是1，交付物是【产物名称1】。"
- "把【xx 项目 URL】的计划表发布到线上。"

### 8. MQL 自由查询
- "查询【xx空间】下名称包含'文档'的【工作项类型】工作项有哪些。"
- 自然语言转换为 MOQL，实现通过更细节的筛选条件查询和操作飞书项目工作项实例

### 9. 评论与协作
- "在&lt;飞书项目工作项实例 URL&gt;实例里，评论一下：需求进度顺利，暂无风险。"

---

## 七、限制和注意事项

### 1. 频率限制
- 每个 Tool 的调用频率限制（QPS）为 **5**
- 与 Open API 频率限制一致

### 2. 不支持的字段类型
目前尚不支持读写以下字段类型，将在后续版本中逐步支持：
- **写入不支持**：投票字段
- **update_field 不支持修改**：附件、系统外信号、富文本、级联单多选、投票、复合字段、关联工作项等字段

### 3. MCP Server 验证机制
- 插件 MCP Server 会验证插件是否已申请相关权限，并已在相应空间中安装后才能使用
- 验证失败时（如空间未安装插件或当前用户无权限），服务器会返回具体原因

### 4. 传输方式限制
- 服务采用 **Streamable HTTP** 传输方式
- 配置 Agent 时需正确选择此项

### 5. OAuth 连接方式要求
- 若使用 HTTP OAuth 连接方式，需要 AI 工具支持 OAuth 授权
- 且支持动态 Client_id

### 6. Aily 使用限制
- 添加过多的 MCP 服务会导致调度不准的问题
- 建议添加后每次对话实际开启的服务**不超过 5 个**
- 从市场添加的 MCP 服务会受到可见性范围管控

### 7. OpenClaw 安全提示
- 使用 OpenClaw 获取飞书项目数据，可能会有数据泄露风险
- **现阶段切勿使用公司/企业飞书账号接入！**
- 请务必优先使用**个人账号**进行体验和测试

### 8. 工具调用最佳实践
- 在输入信息中提供 Tool 所需参数，可提升 AI 的调用成功率并减少幻觉
- 飞书项目 URL 可直接填入 Prompt，MCP 将自动解析对应的空间名称信息

### 9. MCP 工具入参/出参格式
- MCP 工具入参、出参格式可能灵活调整
- 调用 MCP 时请勿依赖入参和出参的结构定义

### 10. MQL 语法支持
- `search_by_mql` 工具支持把自然语言转换为 MOQL
- 目前支持的数据类型参见 MQL 语法说明（文档中引用，未提供具体链接）

### 11. 异步操作
- WBS 草稿的创建、编辑、发布、重置等操作为异步执行
- 可通过 `get_wbs_draft_operation_progress` 工具轮询查询执行进度
- 需要传入 `operation_id`

---

## 八、与 Open API 的关系

### 1. 相同点
- 都需要申请相关权限
- 都有频率限制（QPS = 5）
- 都需要验证权限和空间安装

### 2. 不同点
| 维度 | Open API | MCP Server |
|------|---------|------------|
| 设计目标 | 为开发者提供 API 接口 | 为 AI 工具提供语义化接口 |
| 参数优化 | 标准 API 参数 | 专门优化输入输出参数，适配自然语言对话场景 |
| 授权方式 | API Token | 支持 OAuth、HTTP Header、Stdio 三种方式 |
| 查询语言 | 标准 API 查询 | 支持 MOQL（自然语言转换） |
| 数据传导 | 依赖 ID、Key 等参数 | 更自然，不过度依赖 ID、Key |

### 3. 插件调用 MCP 服务
- 可通过插件调用 MCP Server
- 详见「通过插件调用 MCP Server」文档

---

## 九、文档完整性说明

### 已完整获取的部分
✅ **第一章：MCP 是什么** - 从原始飞书云文档完整获取
✅ **第二章：如何开启 MCP 之旅** - 从飞书项目帮助中心完整获取（包括三种连接方式、MCP Server URL 格式、凭证获取说明）
✅ **第三章：支持的 AI 工具配置** - 从飞书项目帮助中心完整获取（包括 Claude Code、Manus、Codex CLI、Cursor、Trae、扣子、VSCode、Gemini CLI、Dify、OpenClaw、Aily 等 11 种工具的详细配置）
✅ **第四章：MCP 工具列表** - 从飞书项目帮助中心完整获取（包括 7 大分类、49 个工具的完整清单）
✅ **第五章：授权机制** - 从飞书项目帮助中心完整获取（包括个人 MCP、插件体系 MCP、userKey 机制）
✅ **第六章：使用示例** - 从帮助中心工具列表完整获取（每个工具都有示例 Prompt）
✅ **第七章：限制和注意事项** - 从多个官方文档综合获取

### 未能完整获取的部分
⚠️ **原始飞书云文档的后续章节结构**：由于飞书云文档（larkoffice.com）存在动态加载限制，WebFetch 工具多次尝试均只能抓取到首屏内容（即"一、MCP 是什么"章节之前的内容）。原始文档"二、如何开启你的飞书项目 MCP 之旅？"及之后章节的：
- 具体章节标题和层级结构
- 作者的叙述方式和案例
- 文档中可能包含的截图描述
- 文档末尾的总结或 FAQ

这些内容已通过飞书项目帮助中心的官方文档（project.feishu.cn/b/helpcenter/）进行了等价补充，信息来源权威可信，但与原始云文档的叙述结构可能存在差异。

### 补充说明
- 原始飞书云文档的修改时间为 **6月25日**
- 飞书项目 MCP 已提供 **49 个工具**（7 大分类），并仍在持续扩展
- 飞书项目首次取消了"要想使用开放能力，必须由管理员先安装"的限制，节点负责人可以直接把自己负责的节点转化为 AI 节点

---

## 附录：关键配置速查表

### A. 三种连接方式配置速查

| 连接方式 | 凭证 | 配置关键字段 |
|---------|------|-------------|
| HTTP OAuth | OAuth 2.0 | `"httpUrl": "{domain}/mcp_server/v1"` |
| HTTP Header | X-Mcp-Token | `"url": "{domain}/mcp_server/v1", "headers": {"X-Mcp-Token": "<token>"}` |
| Stdio | MCP_USER_TOKEN | `"command": "npx", "args": [..., "<MCP_USER_TOKEN>"]` |

### B. 各 AI 工具配置文件位置速查

| AI 工具 | 配置文件 | 全局位置 | 项目级位置 |
|--------|---------|---------|-----------|
| Claude Code | mcp.json | `~/.claude.json` 或 `~/.claude/config.json` | `.claude.json` |
| Codex CLI | config.toml | `~/.codex/config.toml` | `.codex/config.toml` |
| Cursor | mcp.json | 通过 Cmd/Ctrl+Shift+J 打开 | - |
| Trae | JSON（MCP 窗口） | 通过设置图标 > MCP 打开 | - |
| VSCode | mcp.json | User Settings | `.vscode/mcp.json` |
| Gemini CLI | settings.json | `~/.gemini/settings.json` | `.gemini/settings.json` |

### C. MCP Server URL 速查
- **个人 MCP**：`{domain}/mcp_server/v1`（domain 在「功能入口」获取）
- **插件体系 MCP**：`https://project.feishu.cn/mcp_server/v1?mcpKey=aaaaa-bbbb-xxxx&userKey=<userKey>`

### D. 权限速查

| 权限标识 | 说明 |
|---------|------|
| `project:project.v2.info:read` | 获取空间信息（跨空间） |
| `settings:settings.v2.basic.info:read` | 获取空间下的基础配置 |
| `user:user.v2.info:read` | 获取用户信息（跨空间） |
| `work_item:work_item.v2.info:read` | 获取工作项实例信息 |
| `work_item:work_item.v2.info:write` | 更新工作项实例数据 |

---

## 变更记录

- [2026-07-26] 初始生成，基于飞书云文档+帮助中心三份补充文档整合
- [2026-07-27] 工具名称校正：修正 `transition_node`（原误标为 `get_node_detail`）、`transition_state`（原误标为 `update_state`）；补充缺失的14个工具API名称（`list_node_field_config`、`get_transition_required`、`get_view_detail`、`list_charts`、`get_chart_detail`、`create_fixed_view`、`update_fixed_view`、`list_multi_project_view_workitems`、`list_workitem_comments`、`upload_file`、`get_download_url`、`list_element_template`）；工具总数从"40+"更新为确切数字49个
