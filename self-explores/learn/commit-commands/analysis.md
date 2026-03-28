# commit-commands

## Đánh giá (Score: 7/10)

**Lý do:** Utility cao, daily-use, nhưng patterns đơn giản hơn so với các skills khác. Không có nhiều architectural insights để học, chủ yếu là convenience automation.

---

## Ưu & Nhược điểm

### Ưu điểm
- **3 commands hữu ích:** `/commit`, `/commit-push-pr`, `/clean_gone` — cover full git workflow
- **Context injection trong command:** `!git status`, `!git diff HEAD`, `!git log` tự động inject
- **Style learning:** Phân tích recent commits để match repo commit style
- **All-in-one:** `/commit-push-pr` = commit + push + create PR in one step
- **PR description quality:** Phân tích ALL commits in branch (không chỉ latest)
- **Branch cleanup:** `/clean_gone` handles cả worktree branches
- **Minimal tool permissions:** `allowed-tools` chỉ include git/gh commands cần thiết
- **Single-message execution:** Tất cả actions trong 1 message ("Do NOT send any other text or messages")

### Nhược điểm
- **GitHub-only:** `/commit-push-pr` yêu cầu `gh` CLI + GitHub
- **Không interactive:** Commit message được tự động tạo, không có review step
- **Over-trusting auto-commit:** Có thể accidentally commit sensitive files nếu không careful
- **No pre-commit hook integration:** Không tích hợp với pre-commit hooks
- **Không có dry-run mode:** Không preview được gì sẽ commit

---

## Khả năng tích hợp vào hệ thống hiện tại

### Với OMC/viec
- **Tốt:** Dùng `/commit` sau mỗi `/viec xong`
- Flow: `viec xong` → capture output → `/commit` → optional `/commit-push-pr`
- `/clean_gone` → maintenance task sau project completion

### Integration steps
1. Plugin đã available mặc định trong Claude Code
2. Dùng ngay: `/commit`, `/commit-push-pr`, `/clean_gone`

---

## Ghi chú kỹ thuật (Technical Decisions)

### Command Frontmatter Pattern
```markdown
---
allowed-tools: Bash(git add:*), Bash(git status:*), Bash(git commit:*)
description: Create a git commit
---
```

**Quan trọng:** `allowed-tools` restrict tools Claude được phép dùng trong command — security best practice.

### Context Injection Pattern (`!` prefix)
```markdown
## Context

- Current git status: !`git status`
- Current git diff: !`git diff HEAD`
- Recent commits: !`git log --oneline -10`

## Your task
Based on the above context, ...
```

**Pattern:** `!` trước backtick = execute command và inject output vào prompt. Rất powerful cho dynamic context.

### "Single Message" Pattern
```markdown
You have the capability to call multiple tools in a single response.
Do NOT send any other text or messages besides these tool calls.
```

Đây là pattern để đảm bảo command execution không có intermediate messages.

### Commit Message Style Learning
```markdown
- Analyzes recent commit messages to match your repository's style
- Follows conventional commit practices
- Examines both staged and unstaged changes
```

Agent tự học từ `git log --oneline -10` để match style.

### PR Description Format
```markdown
## Summary
- bullet points (1-3)

## Test plan
- [ ] checklist items

🤖 Generated with [Claude Code](https://claude.ai/code)
```

### Branch Cleanup Script Pattern
```bash
git branch -v | grep '\[gone\]' | sed 's/^[+* ]//' | awk '{print $1}' | while read branch; do
  # Find worktree
  worktree=$(git worktree list | grep "\\[$branch\\]" | awk '{print $1}')
  if [ ! -z "$worktree" ]; then
    git worktree remove --force "$worktree"
  fi
  git branch -D "$branch"
done
```

### Teachable Patterns
1. **`!` context injection** trong command files
2. **`allowed-tools` restriction** cho security
3. **"Single message execution"** pattern
4. **Style learning** từ git history
5. **Worktree cleanup** trước branch delete
