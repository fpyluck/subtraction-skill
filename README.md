# 减法 — 让 AI 指令文档保持精简

> AI 指令文档越长，agent 越容易出错——研究和实践均有佐证。

AI 指令文档有个规律性陷阱：每次遇到问题都往里加一条规则，越加越长，最终 agent 反而更容易搞错。

`减法` 是一道门槛。每次往 `SKILL.md` / `AGENTS.md` / `CLAUDE.md` 加东西之前，先过三关硬判断。

## 三关

1. **这是新信息，还是已有规则能推出来的？** 能推出来就不加。
2. **删掉之后行为会变吗？** 不会变就不加。
3. **复杂度真的降了，还是转移给用户 / 默认行为了？** 转移不算降。

目标不是不加——而是只加**现有规则推不出、不可再压缩的有效语义**。

## 触发范围

往以下文档加规则 / 示例 / 流程 / checklist 时自动触发：

- `SKILL.md`（任何 skill）
- `AGENTS.md`
- `CLAUDE.md`
- 系统提示 / agent memory

不管普通业务代码、测试、错误处理——那是别的 skill 的事。

## 具体不加什么

- **滚动式经验日志**：每次任务后追加 lesson 的文件必膨胀；经验本要编辑维护，合并/改写优先于追加
- **假想 corner case**：没真实出现过的场景不预防性写入
- **冗余示例**：同一原则只配最典型的一个
- **模型能自处理的 fail-safe**：信任模型和框架的默认能力
- **代码已表达的结构事实**：只补 WHY、约束、非显然边界

## 例外（加无妨）

会丢失的事实（路径 / 兼容性 / 安全边界）；反复失败后的针对性修复；用户明确要求。

## 安装

**Bash / macOS / Linux**

```bash
mkdir -p ~/.claude/skills/减法
curl -sL https://raw.githubusercontent.com/fpyluck/subtraction-skill/main/SKILL.md \
  > ~/.claude/skills/减法/SKILL.md
```

**Windows PowerShell**

```powershell
New-Item -ItemType Directory -Force "$HOME\.claude\skills\减法" | Out-Null
Invoke-WebRequest -Uri "https://raw.githubusercontent.com/fpyluck/subtraction-skill/main/SKILL.md" `
  -OutFile "$HOME\.claude\skills\减法\SKILL.md"
```

## 致谢

灵感来自 [neat-freak](https://github.com/KKKKhazix/khazix-skills/tree/main/neat-freak)。

