# feature-dev

## Đánh giá (Score: 9/10)

**Lý do:** Blueprint tốt nhất cho structured AI-assisted development workflow. 7-phase workflow + multi-agent orchestration là template có thể áp dụng cho nhiều domain khác.

---

## Ưu & Nhược điểm

### Ưu điểm
- **7-phase workflow rõ ràng:** Discovery → Explore → Questions → Architecture → Implement → Review → Summary — không bỏ sót bước nào
- **Parallel agent execution:** 2-3 agents chạy đồng thời (code-explorer, code-architect, code-reviewer) — tối đa hóa throughput
- **Confidence-based filtering:** Code reviewer chỉ báo cáo issues ≥80% confidence — giảm false positives
- **Explicit approval gates:** Phase 5 (Implementation) không bắt đầu nếu chưa có user approval — tránh waste
- **Architecture choices:** Đề xuất 3 approaches (minimal, clean, pragmatic) với trade-offs rõ ràng
- **Phase 3 "DO NOT SKIP":** Làm rõ ambiguities trước khi code — rất thực tế
- **Progress tracking với todos:** Visibility xuyên suốt

### Nhược điểm
- **Overhead cho tasks nhỏ:** 7 phases quá nặng cho bug fixes đơn giản
- **Yêu cầu Git + CLAUDE.md:** Không portable cho projects không dùng Git
- **Phase 4 cần user decision:** User phải hiểu trade-offs để chọn architecture
- **Agent model cố định:** Dùng Sonnet cho tất cả — không flexible

---

## Khả năng tích hợp vào hệ thống hiện tại

### Với OMC (oh-my-claudecode)
- **Rất cao:** OMC đã có team pipeline tương tự (team-plan → team-exec → team-verify)
- `feature-dev` cụ thể hóa từng phase với tool assignments
- Có thể extract pattern: code-explorer → code-architect → code-reviewer agents cho OMC executor

### Với /viec workflow
- Phase 1 (Discovery) = `/viec chitiet` (detail task trước khi làm)
- Phase 3 (Clarifying Questions) = `/viec phanbien` pattern
- Phase 6 (Quality Review) = `/viec review` concept
- **Suggestion:** Tích hợp `/feature-dev` như một template trong `/viec samples chitiet`

### Integration steps
1. Install plugin: copy `plugins/feature-dev/` vào `~/.claude/plugins/`
2. Trigger: `/feature-dev [description]`
3. Agents sẽ tự động available

---

## Ghi chú kỹ thuật (Technical Decisions)

### Parallel Agent Pattern
```markdown
# command file syntax cho parallel agents
Launch 2-3 code-explorer agents in parallel, each targeting different aspects:
- Agent 1: Similar features and their implementation
- Agent 2: Architecture and abstractions
- Agent 3: UI patterns and extension points
```

### Confidence Scoring System
```
0   = False positive
25  = Might be real
50  = Real but minor
75  = Highly confident, important
100 = Absolutely certain
Threshold: ≥80 để report
```

### Agent Tool Permissions
```markdown
---
tools: [Glob, Grep, LS, Read, NotebookRead, WebFetch, TodoWrite, WebSearch]
model: sonnet
color: yellow  # code-explorer
# color: green  # code-architect
# color: red    # code-reviewer
---
```

### Phase Gate Pattern
```
Phase 5 (Implementation) gate:
"Does NOT start without explicit user approval of architecture choice"
```

### Key Files
- `commands/feature-dev.md` — 126 lines, main orchestration logic
- `agents/code-explorer.md` — Deep codebase analysis
- `agents/code-architect.md` — Architecture design với 3 approaches
- `agents/code-reviewer.md` — Confidence-based code review

### Teachable Patterns
1. **7-phase decomposition** cho complex tasks
2. **Parallel agent orchestration** với role specialization
3. **Confidence filtering** để reduce noise
4. **Approval gates** trước actions có impact cao
5. **Architecture options presentation** (3 approaches)
