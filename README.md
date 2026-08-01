# initialize-project

一个用于初始化新项目或增量整理已有项目的 Codex Skill，可以为 Codex 补充持久化的背景上下文，适合作为vibe coding项目的起点，或让Codex快速进入一个现有项目进行开发。

它会先检查仓库现状，再与用户确认项目边界、技术方案、交付阶段和验收标准，最后生成或更新项目规则与设计资料。

## 安装

### npx

```powershell
npx --yes --registry=https://registry.npmjs.org skills@latest add Marztop/initialize-project --global --agent codex --yes
```

### 自然语言

在 Codex 中发送：

```text
请使用 skill-installer 从 https://github.com/Marztop/initialize-project 安装 initialize-project Skill。
```

## 使用

在目标项目目录中发送：

```text
请使用 $initialize-project 初始化当前项目。
```

已有项目也可以直接说明目标：

```text
请使用 $initialize-project 为当前已有项目执行增量初始化。
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

## License

MIT
