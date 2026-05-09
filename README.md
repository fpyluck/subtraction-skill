# 减法

**AI 指令文档越长，越可能帮倒忙。**

每次 agent 出错，本能反应是：再加一条规则。这条规则加完，下次出错，再加一条。三个月后，你的 `AGENTS.md` 长达 200 行，里面一半是模型本来就会做的事，另一半互相矛盾。

最糟的是，没人敢删。每条规则都像某次事故留下的便利贴，贴到最后，墙已经看不见了。

`减法` 在你加东西之前拦你一下，问三个问题。

## 三个问题

每次准备往 `SKILL.md` / `AGENTS.md` / `CLAUDE.md` 里加内容，先回答：

1. **这是新信息，还是已有规则能推出来的？**
   "请认真思考" 不是新信息。"修改数据库迁移前必须先运行 `npm run db:check`" 是新信息。

2. **删掉之后，AI 的行为会变吗？**
   "不要破坏用户改动" 通常是默认协作规则，不该写三遍。不会变的，删掉。

3. **复杂度真的降了，还是转移了？**
   把麻烦推给用户、推给默认行为——不算降低复杂度。

## 什么不该加

`减法` 不是反对规则。它反对的是那种"因为害怕再出错，所以把恐惧写进系统提示"的规则。

- 每次任务完成后追加的 lesson（经验本要编辑维护，合并优先于追加）
- 预防性的 corner case（没真实出现过的场景，别提前写）
- 同一原则的第二个示例（最典型的那个就够了）
- 模型本来就会做的事（信任它）
- 重述代码结构的注释（代码自己会说话）

## 什么可以加

路径、版本、安全边界这类**不写就会丢的事实**——比如"这个仓库的生成文件在 `dist/generated`，不要手改"。反复失败后的**针对性修复**。用户明确要求的。

## 主动修剪

不要为了整理而整理。下一次你本来就要打开这份文档时，顺手带走一条过期规则。像出门顺手倒垃圾，不要专门办一场垃圾治理会议。

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

Codex 端同上，把 `.claude` 换成 `.codex`。

---

灵感来自 [neat-freak](https://github.com/KKKKhazix/khazix-skills/tree/main/neat-freak)。

