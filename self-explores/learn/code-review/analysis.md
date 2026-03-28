# code-review

## Đánh giá (Score: 9/10)

**Lý do:** Template chuẩn cho automated QA pipeline. 5-agent parallel review với confidence scoring là pattern có thể áp dụng cho bất kỳ review workflow nào.

---

## Ưu & Nhược điểm

### Ưu điểm
- **5 parallel review agents:** Mỗi agent focus vào 1 dimension (CLAUDE.md compliance, bugs, git history, previous PRs, code comments)
- **Confidence scoring 0-100:** Rubric chi tiết, có thể áp dụng cho mọi review context
- **Threshold 80 filtering:** Chỉ report high-confidence issues — actionable output
- **Auto-skip logic:** Đóng PRs, draft PRs, trivial PRs, đã-reviewed PRs → skip — không waste
- **Double-check step:** Haiku agent verify lại eligibility trước khi post comment
- **CLAUDE.md integration:** Compliance checking against project-specific guidelines
- **Precise link format:** Full SHA + line range → GitHub renders perfectly
- **Historical context:** Agent #3 đọc git blame, Agent #4 đọc previous PRs — context-aware

### Nhược điểm
- **GitHub-dependent:** Requires `gh` CLI + GitHub remote — không work với GitLab/Bitbucket
- **Haiku for pre-checks:** Dùng Haiku cho screening (nhanh/rẻ) nhưng có thể miss edge cases
- **Repetitive eligibility check:** Step 1 và step 7 đều check eligibility — over-engineering nhẹ
- **Post-only output:** Kết quả post comment lên GitHub, không return cho user trực tiếp

---

## Khả năng tích hợp vào hệ thống hiện tại

### Với OMC
- **Tốt:** Có thể dùng `/code-review` trong `team-verify` phase của OMC
- Pattern confidence scoring → có thể tích hợp vào `verifier` agent

### Với /viec workflow
- Sau khi `/viec xong` → auto-trigger `/code-review` nếu có PR
- Hoặc tạo task con: "Code review cho task X"

### Integration steps
1. Cần `gh` CLI: `gh auth login`
2. Trigger trên branch có PR: `/code-review`
3. Kết quả post lên GitHub PR

---

## Ghi chú kỹ thuật (Technical Decisions)

### Agent Configuration
```markdown
# code-review.md command frontmatter
---
allowed-tools: Bash(gh issue view:*), Bash(gh pr comment:*), Bash(gh pr diff:*), Bash(gh pr view:*)
description: Code review a pull request
---
```

### 5 Review Dimensions
```
Agent 1: CLAUDE.md compliance (đọc guidelines file)
Agent 2: Bug scanning (shallow, chỉ changes, tránh pre-existing)
Agent 3: Git blame/history context
Agent 4: Previous PRs comments về same files
Agent 5: Code comments compliance
```

### Confidence Rubric (copy để dùng lại)
```
0:   False positive, không stand up to scrutiny, pre-existing issue
25:  Might be real, không verify được, stylistic không explicit trong CLAUDE.md
50:  Real nhưng nitpick, không quan trọng relative to PR
75:  Double-checked, very likely real, impacts functionality, explicitly in CLAUDE.md
100: Confirmed real, happens frequently, evidence directly confirms
```

### Output Format Template
```markdown
### Code review

Found N issues:

1. <brief description> (CLAUDE.md says "<...")
https://github.com/owner/repo/blob/{FULL_SHA}/path/file.ext#L{start}-L{end}

2. <brief description> (bug due to <file snippet>)
https://github.com/owner/repo/blob/{FULL_SHA}/path/file.ext#L{start}-L{end}

🤖 Generated with [Claude Code](https://claude.ai/code)
<sub>- If useful, react 👍. Otherwise 👎.</sub>
```

### False Positives List (quan trọng để loại)
- Pre-existing issues (không introduced bởi PR)
- Linter/typechecker sẽ catch (format, imports, types)
- General quality issues trừ khi có trong CLAUDE.md
- Issues đã có lint-ignore comment
- Intentional functionality changes

### Teachable Patterns
1. **Multi-agent parallel review** với role specialization
2. **Confidence scoring** để filter noise
3. **Auto-skip conditions** (draft/closed/trivial/already-reviewed)
4. **Double eligibility check** pattern
5. **Precise code linking** với full SHA
