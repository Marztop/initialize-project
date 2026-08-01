# 分离初始化资料与项目资产

项目初始化 Skill 将内部初始化资料收敛到 `.init_repo/design/`、`.init_repo/research/` 和 `.init_repo/records/`，根目录只保留供 Agent 自动发现的 `AGENTS.md`。测试、工具、依赖清单和交付文档继续遵循目标项目的既有结构，避免隐藏目录破坏构建工具约定，也避免初始化记录散落在项目根目录。
