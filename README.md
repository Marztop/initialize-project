# initialize-project

`initialize-project` 是一个用于初始化新项目或增量整理已有项目的 Codex Skill。

它不会直接复制固定模板，也不会在初始化过程中安装依赖或开始实现功能。Skill 会先检查仓库现状，再和用户逐项确认项目边界、技术方案、运行环境、验收方式和交付阶段，最后生成适合当前项目的规则与设计资料。

## 适用场景

- 初始化空仓库或新项目。
- 为已有代码仓库补齐项目规则、设计资料和阶段路线图。
- 重新梳理项目范围、技术约束、运行环境和验收标准。
- 将长期约束整理为 Agent 可以持续遵守的项目级工作约定。

Skill 只在用户明确要求初始化时工作，不会因为项目缺少 `AGENTS.md` 或 `.init_repo/` 就自动介入普通开发任务。

## 安装

### 让 Codex 安装

在 Codex 中发送：

```text
请使用 skill-installer 从 GitHub 仓库 Marztop/initialize-project 的根目录安装 Skill，名称使用 initialize-project。
```

安装完成后，Skill 会从下一轮对话开始可用。

### PowerShell

也可以直接运行内置安装脚本：

```powershell
python "$env:USERPROFILE\.codex\skills\.system\skill-installer\scripts\install-skill-from-github.py" `
  --repo Marztop/initialize-project `
  --path . `
  --name initialize-project
```

## 使用

在目标项目目录中发送：

```text
请使用 $initialize-project 初始化当前项目。先检查仓库现状，只询问无法从项目中确认的决策；每次给出推荐方案。在我确认最终汇总前，不要创建文件、安装依赖或开始实现。
```

已有项目也可以直接说明目标：

```text
请使用 $initialize-project 为当前已有项目执行增量初始化。保留已有 AGENTS.md 和文档，只补充确认后的缺口。
```

## 操作流程

1. 检查仓库结构、现有规则、文档、代码、依赖清单和测试配置。
2. 从项目中提取已知事实，只对缺失、冲突或会改变结果的决策逐项提问。
3. 为每个问题给出推荐答案，并说明实际取舍。
4. 提出完整的交付阶段划分，再逐阶段确认目标、范围、依赖、交付物和验收标准。
5. 让用户决定 `.init_repo/` 是否进入版本控制。
6. 汇总全部事实、决策、阶段计划和文件修改范围，等待最终确认。
7. 确认后才创建或增量更新初始化资料，并重新读取文件完成验证。

## 生成结构

```text
项目根目录/
├── AGENTS.md
└── .init_repo/
    ├── design/
    │   └── design_doc.md
    ├── research/
    └── records/
```

- `AGENTS.md`：只记录 Agent 的工作方式、确认边界和验证义务。
- `.init_repo/design/design_doc.md`：记录项目目标、技术选型、架构、运行环境和阶段路线图，是项目决策的事实来源。
- `.init_repo/research/`：记录事实调研、依赖调查和实验结论。
- `.init_repo/records/`：记录阶段报告、修复过程和验证结果。

测试、工具、依赖清单、源代码和用户文档仍使用目标项目原有或技术栈约定的位置，不会被移动到 `.init_repo/`。

如果用户选择不提交 `.init_repo/`，Skill 会使用仓库本地的 `.git/info/exclude`，不会修改目标项目的 `.gitignore`。已有 `AGENTS.md` 时，只有用户明确批准的新项目级工作约定才会被追加。

## 仓库内容

- `SKILL.md`：核心触发条件和初始化流程。
- `agents/openai.yaml`：Codex Skill 界面元数据。
- `references/interview-guide.md`：访谈与阶段确认规则。
- `references/document-contracts.md`：生成文档的内容边界。
- `references/version-control.md`：共享和本机私有模式的 Git 处理规则。

## License

MIT
