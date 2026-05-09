# subtraction-skill

**A guardrail against instruction bloat in AI-facing docs.**

给 AI 文档加法之前，先设一道门槛。

## 这是什么

`减法` 是一个克制型 skill：当你准备往 `SKILL.md`、`AGENTS.md`、`CLAUDE.md`、系统提示词等 instruction-like 文档里继续加规则、例外、示例、checklist 或流程说明时，它会先拦一下。

目标不是不加，而是只加现有规则推不出、不可再压缩的有效语义。

## 三关

每加一条前，先问三关：

1. **这是新事实 / 约束 / 例外，还是重复信息？** 重复或可以从上层推出的不加。
2. **删掉后还能不能由上层规则推出？** 能就不加。
3. **复杂度是真的降了，还是转移了？** 移给用户 / 默认行为 / 隐藏依赖都不算降。

一句话概括：先证明新增规则值得存在，再把它写进 AI 的脑子里。

## 安装

这是复制式安装，不是包管理器。把 `SKILL.md` 放到对应 agent 的 skills 目录即可。

**Claude Code 端：**

```bash
mkdir -p ~/.claude/skills/减法 && cp SKILL.md ~/.claude/skills/减法/SKILL.md
```

**Codex 端：**

```bash
mkdir -p ~/.codex/skills/减法 && cp SKILL.md ~/.codex/skills/减法/SKILL.md
```

## 灵感

这个 skill 的迭代灵感来自 [neat-freak](https://github.com/KKKKhazix/khazix-skills/tree/main/neat-freak)。感谢它把"整理"和"克制"这件事讲得很清楚。

## 适合谁

适合会长期维护 agent 指令、团队规范、项目级 AI 协作文件的人。

规则越多，agent 不一定越聪明。很多时候，更少的规则才更稳定。
