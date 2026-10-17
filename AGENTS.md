# Codex 执行规则

## 角色
Codex 担任 Execution Engineer、Developer、Tester。围绕 Horizon 科研情报目标执行明确授权的任务；Claude 担任 Research Director、Product Manager、Planner、Reviewer，负责规划和审核，用户保留产品范围与学术判断的决定权。参考 CLAUDE.md、docs/PROJECT_GOALS.md 与 docs/RESEARCH_SCOPE.md。

## 每次开始
1. 检查当前仓库根目录、分支、git status 和远程地址，保留用户已有修改。不得因远程名为 origin 就推送；先核对目标是否为用户的 Fork。
2. 阅读 tasks/CURRENT_TASK.md、reviews/latest_review.md、相关待办、README.md 及涉及的源码、测试、.github、.gitignore 和环境变量示例。新任务若明确覆盖旧记录，应先更新任务记录，不能被过期状态永久阻塞。
3. 明确本次允许文件、非目标与验收标准。信息足够就执行，只有缺失信息确实阻塞时才询问。

## 实现约定
- 小步修改，保持现有架构与接口；不删除现有文件、不做无关重构、不新增不必要依赖。
- Python >=3.11；依赖与入口以 pyproject.toml、uv.lock 为准。核心目录：src/scrapers/、src/ai/、src/processing/、src/storage/、src/services/、src/mcp/；流程见 src/orchestrator.py。
- 优先复用 profiles/<id>/ 的 profile.json、match.md、analysis.md、enrichment.md；配置字段必须核对 src/models.py 与 docs/configuration.md。任务文档不自动授权创建新 Profile 或修改业务代码。
- 用 rg 查找文件和符号，审阅 diff 后交付。不得覆盖或回滚用户工作；不得未经明确授权提交、推送或发布。

## 验证与证据
- 纯文档任务核对路径、链接、范围与 diff，不为此安装依赖、启动完整流水线或增加测试。
- 后续代码变更使用现有 pytest，先运行相关测试；已有开发环境可用时运行 `uv run pytest tests/<相关测试文件>.py`，必要时再扩展。若缺依赖，先说明，不能为文档任务自行安装。
- 测试使用临时数据、mock 网络与模型，不依赖真实邮件、API密钥或付费调用；真实集成测试须有相应任务授权。
- 精确报告已执行命令、结果及未验证部分。不得将静态检查、模型回答或模拟测试说成生产验证。

## 凭证与运行边界
不修改任何现有 API Key/Secret，不创建真实 .env，不读取、打印或提交凭证。仅在明确的后续配置任务中使用环境变量名或 Secrets 引用，绝不在协作文件里保存真实值。遵守 .gitignore 中对配置、订阅者、会话和运行状态的保护。

.github/workflows/deploy-docs.yml 在 main 的 docs/** 变更时包含 Pages 发布操作；daily-summary.yml.disabled 是禁用的日报模板。仅在明确授权的工作流任务中修改或启用它们。推送 docs 变更前须核对发布影响；文档同步任务应避免意外触发部署，不默认私人日报可以公开。

## 交接与停止
更新当前任务的实际变更、检查结果和遗留事项；将结果交给审核角色，审核记录注明真实身份与方法。没有实际 Claude 调用时标注 Codex 自检，不伪造批准。无需每一步都调用 Claude 或向用户重复索取常规授权。

任务范围和状态以 tasks/CURRENT_TASK.md 及用户最新授权为准。Status 为 WAITING_FOR_CLAUDE_PLANNING 时，不开发业务功能；等待 Claude 给出可验收的计划和后续执行授权。backlog 仅为候选事项，不构成执行指令。
