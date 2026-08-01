# initialize-project

一个用于初始化新项目或增量整理已有项目的 Codex Skill。它会先检查仓库现状，再与用户确认项目边界、技术方案、交付阶段和验收标准，最后生成或更新项目规则与设计资料。

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

在需要初始化的项目目录中发送：

```text
请使用 $initialize-project 初始化当前项目。
```

## License

MIT
