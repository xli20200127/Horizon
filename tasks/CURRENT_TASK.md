# 当前任务

Status: WAITING_FOR_CLAUDE_PLANNING

- ID：COLLAB-001
- 日期：2026-10-17
- 目标：完成协作文件审核与同步后，等待 Claude 规划科研日报的下一项任务。
- Claude = Research Director / Product Manager / Planner / Reviewer。
- Codex = Execution Engineer / Developer / Tester。

## 当前允许范围
本轮只审核、轻微修正并提交同步 7 个协作 Markdown 文件；保留 tasks/completed/.gitkeep 目录占位文件。不得修改 src/、tests/、.env.example、现有 GitHub Actions、运行配置或依赖；不创建真实 .env、不改凭证、不删除文件、不实现新功能。

## 协作交接
1. Claude 阅读项目目标、研究范围、README、当前架构和最新审核记录。
2. Claude 明确下一项任务的问题、最小范围、非目标、允许文件、验收标准和测试计划。
3. Codex 根据用户授权执行该计划，记录变更与实际验证结果。
4. Claude 审核 diff 和验证证据；Codex 修复确认的问题。不得将 Codex 自检写成 Claude 独立审核。

## 已完成的准备
协作规则、项目目标、科研范围与待办已建立；本轮检查文件内容、角色、路径和敏感信息，并核对 Git 提交范围。具体记录见 ../reviews/latest_review.md。

## 当前未授权工作
不执行 backlog.md 中的功能。不假定 API 已获批、模型可调用或邮件服务已配置。业务测试、API调用、定时任务和投递均不属于本轮范围。

## 同步说明
代码同步目标为用户 Fork，而非上游仓库。提交与推送结果以 Git 实际输出为准；本文件保持等待 Claude 规划状态，不因文档同步而启动业务开发。
