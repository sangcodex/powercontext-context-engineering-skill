# powercontext-context-engineering

给 AI Agent 用的「上下文工程」技能：把工作现场变成可追溯的来源、可更新的记忆、可解释的检索和可控的预算。

## 这个 Skill 解决什么

上下文工程的难点从来不是"塞更多文本进 prompt"，而是四个约束同时成立：

1. **来源可追溯** —— 每个结论都能回到原始证据
2. **记忆可更新** —— 撤回、恢复、修订都是事件，而不是覆盖
3. **检索可解释** —— 能说清"这段上下文为什么会被选上"
4. **预算可控制** —— 装配函数带显式预算，超了有据可查

## 核心模型

```
Source（来源） → Observation（原始记录） → Memory（记忆） → Prepared Context（装配结果）
       ↑                                          ↓
   捕获 / 撤回(tombstone) / 恢复              citation 回查原始证据
```

## 内容结构

- 何时使用：新数据源接入、记忆生命周期、检索排序、上下文压缩、上下文质量验收
- 五步工作流：采集 → 记忆写入与生命周期 → 检索与重排 → 装配与预算 → 验收
- 反模式表：6 个常见错误做法及其后果
- 快速自检清单：7 条可勾选项

## 使用方式

把 `SKILL.md` 放进你的 Agent 的 skill 目录即可，例如：

```bash
mkdir -p ~/.claude/skills/powercontext-context-engineering
cp SKILL.md ~/.claude/skills/powercontext-context-engineering/
```

支持 Claude Code、Cursor、Codex 等兼容 Agent Skills 格式的客户端。

## 来源

本 Skill 提炼自 [OceanBase PowerContext](https://github.com/oceanbase/powercontext)（Apache-2.0）的上下文生命周期设计，以及 2026 OceanBase 训练营中实际交付的十项能力实践：

| 能力 | 对应问题 |
| --- | --- |
| 采集 | CSV 行级采集、Pi 会话分支恢复、PDF 页级证据 |
| 检索 | HTTP 重排服务、单 SQL 混合检索 |
| 上下文 | 增量上下文包、按查询与预算选择原文证据 |
| 记忆 | 数量触发处理、Embedding 批次合并、来源撤回与恢复 |

## License

Apache-2.0
