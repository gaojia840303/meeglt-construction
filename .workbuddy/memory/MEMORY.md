# 飞书项目建设 - 项目长期记忆

> 本文件记录本项目的稳定约定、决策和可复用知识。日常临时信息记入 YYYY-MM-DD.md。

## 项目定位
本项目的核心目标：搭建和运维公司的飞书项目（Meego）。
我是用户的「飞书项目专家」，协助解决搭建过程中的所有问题，给出简单、直接、明确的解法。

## 知识库（核心资产）
位置：D:\AI提效\5、workbuddy\4、飞书项目建设\知识库\
- 飞书项目知识体系总纲.md — 三合一整合大纲（先看这份，含第四部分：行业方案参考）
- 飞书项目产品手册-知识大纲.md — 17大模块详细
- 飞书项目开发者手册-知识大纲.md — 8大模块详细
- 飞书项目MCP文档-知识大纲.md — 9章节+49工具+11种AI配置+速查表
- 飞书项目消费行业新品研发AI方案-知识大纲.md — 行业方案（非官方参考，来自飞书Wiki，不纳入更新自动化跟踪）

## 文档源（飞书官方，持续更新）
- 产品手册：https://project.feishu.cn/b/helpcenter/1ykiuvvj/1afedyby （分类ID: 1ykiuvvj）
- 开发者手册：https://project.feishu.cn/b/helpcenter/1p8d7djs/nh4exbsn （分类ID: 1p8d7djs）
- MCP说明：https://bytedance.larkoffice.com/docx/WR2edlyg0oma39xVkSKcbgCBn3g （飞书云文档，动态加载限制，WebFetch只能抓首屏）
- 帮助中心URL规律：https://project.feishu.cn/b/helpcenter/{分类ID}/{文章ID}
- MCP等价补充文档：jdmql9oj（插件体系MCP+工具列表）、wzb3ycsc（AI工具连接配置）、19wmvt8b（工具功能列表+Prompt示例）

## 文档更新追踪自动化
- 自动化名称：飞书项目文档更新检查
- ID: automation-1785075378493
- 频率：每周一 9:00 执行
- 逻辑：读取知识库MD章节清单 → 抓取三URL当前目录 → 对比 → 有变化则更新MD+报告 → 追加工作日志
- 日常对话中也可手动说"检查飞书文档更新"触发即时检查
- **跟踪范围仅限三个官方文档源**（产品手册/开发者手册/MCP说明）；行业方案等非官方参考文档不纳入跟踪

## 关键技术认知
- 飞书项目核心抽象：空间 → 工作项 → 节点流 → 节点
- 两种模式：敏捷开发 + IPD（含WBS/计划表/基线/评审/泳道图）
- MCP：个人授权（无需管理员），三种连接方式（HTTP OAuth / HTTP Header / Stdio），QPS=5，Streamable HTTP，支持MOQL自然语言查询
- 插件开发6步：创建→添加构成→客户端开发→服务端开发→测试→发布；命令 lpm start / lpm release
- 飞书云文档动态加载限制：WebFetch只能抓首屏，需用帮助中心官方文档等价补充

## 全局技能（C盘根目录）
- lark-shared：飞书office操作，CLI路径 C:\Users\YQSL\.workbuddy\skills\lark-shared\lark-cli.exe
- meegle：飞书项目操作，CLI路径 C:\Users\YQSL\AppData\Local\meegle\meegle.exe
- 涉及飞书office和飞书项目操作时，启动这两个全局skill

## meegle CLI 实战坑与套路（已验证，2026-09-15）
- 环境：本机 PowerShell 工具不显示命令 stdout，必须 `$out = & "exe" ... 2>&1 | Out-String` 再用 `[System.IO.File]::WriteAllText(路径, $out, [System.Text.UTF8Encoding]::new($false))` 写文件 → 用 Read 工具读；直接重定向/Start-Process 均拿不到输出
- 中文乱码：CLI 输出中文在 PowerShell 显示为乱码，但写入 UTF-8 文件后用 Read 读取正常 → 不要依据控制台显示判断内容
- 无 `--json` 参数；`--set` 不支持数组下标（会生成字面 key `role_operate[0]` 报 unknown_params）
- **数组对象参数必须走 `--params`，且内层双引号要用反斜杠转义**（PowerShell 会吞掉内层引号）：`$p = '{\"role_operate\":[{\"op\":\"add\",\"role_key\":\"xxx\",\"user_keys\":[\"userkey\"]}]}'`，先加 `--dry-run` 验证 params 结构再正式执行
- 关键命令：project search / workitem meta-types / workitem meta-roles / workitem meta-fields / view get / workitem get --fields '["_all"]' / workitem update --params
- 视图 URL 解析：https://project.feishu.cn/{simple_name}/workObjectView/{work_item_type_api_name}/{view_id}；simple_name 需先 `project search` 换成 projectKey

## 飞书项目角色机制（已验证的硬结论）
- **角色槽位是实例级数据**：给工作项类型新增角色后，只对之后创建的实例生效，**不会回填存量实例**
- 存量实例无该角色时：视图列显示「无效字段，不支持编辑」，详情页角色区整体不渲染（也就没有"添加角色"入口），后台详情页布局怎么改都无效
- 判定方法：`view get` / `workitem get` 看实例的 `role_members` 是否包含目标 role_id；全无 = 槽位缺失
- 修复唯一路径：`workitem update --role-operate/--params` 对实例注入角色（op=add, role_key=xxx, user_keys=[...]），逐个实例执行，已终止实例通常无需处理
- 角色配置查询：`workitem meta-roles --work-item-type {api_name}`

