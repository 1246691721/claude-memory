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

**How to apply:** 当用户在对话中说以下指令时，执行对应操作：

**推送记忆** ("推送记忆"、"push memory"):
```bash
cd /Users/apple/.claude/projects/-Users-apple/memory
git add .
git commit -m "Update memory: $(date '+%Y-%m-%d %H:%M:%S')"
git push origin main
```

**同步记忆** ("同步记忆"、"sync memory"):
```bash
cd /Users/apple/.claude/projects/-Users-apple/memory
git pull origin main --rebase
```

执行后返回结果即可，无需额外确认。
