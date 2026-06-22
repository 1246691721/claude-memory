---
name: github-memory-manual-push
description: "User prefers manual GitHub memory sync via conversation commands, not automatic push"
metadata: 
  node_type: memory
  type: feedback
  originSessionId: eb4118f3-51fe-4fdd-91d3-fb39605126ef
---

用户希望通过对话中的明确指令来推送记忆到GitHub，而不是每次写入记忆时自动推送。

**Why:** 用户想要手动控制推送时机，避免频繁的自动提交。

**How to apply:** 当用户在对话中说以下指令时，执行 `/Users/lizr/.claude/scripts/github-memory-save.sh`：
- "推送记忆"
- "推送记忆到GitHub"
- "sync memory"
- "push memory to github"
- "保存记忆到GitHub"

执行脚本并返回结果即可，无需额外确认。
