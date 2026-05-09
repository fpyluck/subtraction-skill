# subtraction-skill

**Stop adding rules to your AI docs. Most of them make things worse.**

ETH Zurich 2026 研究：AGENTS.md 越详细，agent 成功率反而降 3%，成本多 20%。`减法` 是一道门槛，让你在往 `SKILL.md` / `AGENTS.md` / `CLAUDE.md` 里加东西之前先过三关。

## 三关

每加一条前问：

1. **这是新信息，还是已有规则能推出来的？** 能推出来就不加。
2. **删掉之后行为会变吗？** 不会变就不加。
3. **复杂度真的降了，还是转移给用户 / 默认行为了？** 转移不算降。

目标不是不加——而是只加现有规则推不出、不可再压缩的有效语义。

## 具体不加什么

- 每次任务后追加 lesson 的滚动文件（必膨胀）
- 没真实出现过的 corner case
- 同一原则的第二个示例
- 模型能自己处理的 fail-safe
- 重述文档已有内容或代码本身就表达的结构事实

## 安装

```bash
# Claude Code 端
mkdir -p ~/.claude/skills/减法 && cp SKILL.md ~/.claude/skills/减法/SKILL.md

# Codex 端
mkdir -p ~/.codex/skills/减法 && cp SKILL.md ~/.codex/skills/减法/SKILL.md
```

## 致谢

迭代灵感来自 [neat-freak](https://github.com/KKKKhazix/khazix-skills/tree/main/neat-freak)，感谢。
