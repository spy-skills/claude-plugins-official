---
updated: 2026-03-27
type: context
topic: skill-priority-ranking
task: cpo-epi
---

# Xếp hạng ưu tiên Skills — 31_claude-plugins-official

**Tiêu chí đánh giá:**
- **Tính ứng dụng thực tế** (utility trong workflow hàng ngày)
- **Độ phức tạp học** (complexity để master)
- **Khả năng tích hợp vào OMC/viec** (synergy với hệ thống hiện tại)
- **Tính học được** (teachable patterns)

**Thang điểm:** 1 = thấp nhất, 5 = cao nhất

---

## ⭐⭐⭐⭐⭐ Ưu tiên 5/5 — PHẢI HỌC NGAY

### 1. feature-dev ⭐⭐⭐⭐⭐
**Lý do quan trọng:** 7-phase structured development workflow với multi-agent orchestration là blueprint xuất sắc cho cách tổ chức công việc AI-assisted.
- Discovery → Explore → Questions → Architecture → Implement → Review → Summary
- 3 loại agents: code-explorer, code-architect, code-reviewer
- Parallel agent pattern (2-3 agents chạy cùng lúc)
- **Học được:** How to decompose complex tasks, parallel agent patterns

### 2. code-review ⭐⭐⭐⭐⭐
**Lý do quan trọng:** Template tốt nhất cho automated QA pipeline.
- 4 parallel review agents với confidence scoring (threshold 80)
- CLAUDE.md compliance checking
- Comment chỉ high-confidence issues
- **Học được:** Confidence-based filtering, parallel review orchestration

### 3. plugin-dev ⭐⭐⭐⭐⭐
**Lý do quan trọng:** Meta-skill để xây dựng tất cả skills khác — 7 skills, 1 command.
- hook-development, mcp-integration, plugin-structure, command-development, agent-development, skill-development
- 8-phase plugin creation workflow
- **Học được:** Full plugin architecture, all component types

### 4. hookify ⭐⭐⭐⭐⭐
**Lý do quan trọng:** Regex-based hook creation — automation backbone.
- 4 commands: `/hookify`, `/hookify:list`, `/hookify:configure`, `/hookify:help`
- Multiple event types: bash, file, stop, prompt, all
- Actions: warn hoặc block
- YAML frontmatter format
- **Học được:** Hook patterns, behavior modification, automation triggers

---

## ⭐⭐⭐⭐ Ưu tiên 4/5 — NÊN HỌC

### 5. commit-commands ⭐⭐⭐⭐
**Lý do:** Core git workflow commands — daily use.
- `/commit`: Auto-generate commit message
- `/commit-push-pr`: Full workflow
- `/clean_gone`: Branch cleanup
- **Học được:** Git workflow automation patterns

### 6. pr-review-toolkit ⭐⭐⭐⭐
**Lý do:** 6 specialized agents = best-practice multi-agent bundle.
- comment-analyzer, pr-test-analyzer, silent-failure-hunter, type-design-analyzer, code-reviewer, code-simplifier
- Rating system (1-10 cho type design)
- **Học được:** Specialized agent design, multi-dimension review

### 7. skill-creator ⭐⭐⭐⭐
**Lý do:** Core tool cho vòng lặp cải thiện skills.
- Create new skills từ scratch
- Update/optimize existing
- Run evals + benchmark
- **Học được:** Skill lifecycle management, eval methodology

### 8. claude-code-setup ⭐⭐⭐⭐
**Lý do:** Intelligent codebase analysis — "doctor" cho project setup.
- Scans codebase để recommend hooks, skills, MCP servers
- Read-only, non-destructive
- **Học được:** Pattern recognition, recommendation systems

### 9. ralph-loop ⭐⭐⭐⭐
**Lý do:** Self-referential iteration loop — iteration philosophy.
- `/ralph-loop` + `/cancel-ralph`
- "Iteration over perfection" philosophy
- Clear success criteria requirement
- **Học được:** Loop patterns, autonomous iteration

---

## ⭐⭐⭐ Ưu tiên 3/5 — HỌC KHI CÓ THỜI GIAN

### 10. agent-sdk-dev ⭐⭐⭐
Interactive SDK scaffolding — useful khi xây agent apps.

### 11. claude-md-management ⭐⭐⭐
CLAUDE.md audit + improvement — niche nhưng valuable.

### 12. frontend-design ⭐⭐⭐
Auto-trigger trên frontend work, production-grade UI generation.

### 13. playground ⭐⭐⭐
Interactive HTML playgrounds — creative visualization tool.

### 14. explanatory-output-style ⭐⭐⭐
Educational output format — tốt cho teaching/learning workflows.

### 15. learning-output-style ⭐⭐⭐
Interactive learning hook — học by doing approach.

---

## ⭐⭐ Ưu tiên 2/5 — NẾU CÓ NHU CẦU CỤ THỂ

### External MCP Integrations
- **github** ⭐⭐⭐ — Nếu dùng GitHub nhiều
- **slack** ⭐⭐ — Nếu dùng Slack
- **stripe** ⭐⭐⭐ — Nếu làm payment features
- **supabase** ⭐⭐⭐ — Nếu làm backend
- **linear** ⭐⭐ — Nếu dùng Linear
- **playwright** ⭐⭐⭐ — Nếu làm web testing
- **context7** ⭐⭐⭐ — Docs lookup, useful

### LSP Plugins
⭐⭐ — Utility cao khi cần, nhưng không có gì để "học" về skill design.
Chỉ cần biết: `clangd-lsp`, `pyright-lsp`, `typescript-lsp`, `rust-analyzer-lsp` là phổ biến nhất.

---

## ⭐ Ưu tiên 1/5 — THẤP

- `security-guidance`: Minimal documentation
- `example-plugin`: Chỉ reference, không dùng trực tiếp
- Các LSP ít phổ biến (kotlin, lua, php, swift, csharp, jdtls)

---

## 📊 Tóm tắt Roadmap

```
TUẦN 1 — Core Workflow (⭐⭐⭐⭐⭐)
  Day 1-2:  feature-dev     → Master 7-phase workflow + parallel agents
  Day 3:    code-review      → 4-agent parallel review pattern
  Day 4-5:  plugin-dev       → Full plugin architecture (meta-skill)
  Day 6-7:  hookify          → Hook automation system

TUẦN 2 — Workflow Enhancement (⭐⭐⭐⭐)
  Day 1-2:  commit-commands  → Git automation
  Day 3:    pr-review-toolkit → Specialized agents
  Day 4:    skill-creator    → Skill lifecycle
  Day 5-6:  claude-code-setup → Project setup optimization
  Day 7:    ralph-loop       → Iteration patterns

TUẦN 3 — Marketing Skills (External Reference)
  (từ marketing-skills.md — cần tải từ marketingskills repo)
  content-strategy, copywriting, seo-audit, email-sequence, ab-test-setup
```

---

## So sánh với Marketing Skills (từ marketing-skills.md)

| Dimension | 31_claude-plugins-official | marketingskills (Corey Haines) |
|-----------|--------------------------|-------------------------------|
| Domain | Dev Tools / Dev Workflow | Marketing / Conversion |
| Skill count | 42 total | 26 marketing skills |
| Quality | 8/10 (top plugins) | 8/10 |
| Agent patterns | Yes (feature-dev, code-review) | Limited |
| Context file pattern | CLAUDE.md | product-marketing-context.md |
| Teachable patterns | High | Medium |

**Kết luận:** Repo chính thức có **pattern quality cao hơn** (multi-agent, hooks, structured workflow) nhưng **domain coverage hẹp hơn** (chỉ dev tools). Marketing skills từ external repos bổ sung domain coverage.
