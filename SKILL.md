---
name: jianfa
description: 'Jianfa (减法)：Triggers when user writes "减法", "/jianfa", or "jianfa" as a standalone message or invocation, and when adding rules, exceptions, examples, checklists, reflection mechanisms, or workflows to skill / AGENTS.md / CLAUDE.md / system prompt / agent memory style documents. Preserve local semantics that change future behavior; merge or remove duplicate, generic, or model-obvious instructions.'
---

# 减法

**目标**：不是少写，而是保留会改变后续行为的最小语义；需要精确的地方要精确，模型自己能做好的地方不要写成规则。过度删除同样有害：锚点缺失后，模型的推断自由可能漂向错误方向。

每加一行前先判断：

1. **这是新事实 / 约束 / 例外，还是重复信息？** 重复或可以从上层推出的不加。
2. **删掉后还能不能由上层规则或模型常识推出？** 能就合并、精简或删除。
3. **复杂度是真的降了，还是转移了？** 移给用户 / 默认行为 / 隐藏依赖都不算降。
4. **这句话是在增加可执行的辨别力，还是只是在增加字数 / 姿态？** 删掉后是变自由，还是变含混？含混了就保留或换更紧凑的锚点。

## 分类标准

- **KEEP / 精化**：本地路径、命令、协议标记、数据结构或模板锚点、能区分两种行为的示例（非重复、非装饰性）、安全边界、权限和不可逆操作边界、用户明确要求、反复失败后的针对性修复、模型无法推断的领域事实。
- **合并 / 精简 / 删除**：通用最佳实践、动机性说明、重复示例、角色标签、模型显然能处理的流程旁白、推测性 corner case、过详尽 fail-safe、代码本身已表达的说明。

## 编辑姿态

- 优先合并 / 改写 / 删除旧条目，再追加新条目；有其他编辑需求时顺手修剪，不为修剪单独开一轮。
- 经验记录只写会改变后续行为的约束；避免流水账式 lesson 仓库，已有条目先合并或替换。
- 用户明确要求丰富探索 / 想象空间时，可以保留启发性内容；但要把运行协议、必做项和可选思路分清。

## 范围

只管上下文文档（skill / AGENTS.md / CLAUDE.md / 系统提示 / agent memory 等）。测试覆盖、错误处理、依赖管理是别的 skill 的事。
