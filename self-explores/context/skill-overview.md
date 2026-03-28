---
updated: 2026-03-27
type: context
topic: skill-overview
task: cpo-sau
---

# Tổng quan Skills — Repo 31_claude-plugins-official

## Repo Info
- **Nguồn:** Official Claude Code plugins marketplace (agentskills.io / claude.ai)
- **Plugins chính thức:** 29 plugins trong `plugins/`
- **External integrations:** 13 MCP integrations trong `external_plugins/`
- **Total:** 42 skills/plugins

---

## Phân nhóm theo lĩnh vực

### 1. LANGUAGE SERVERS (LSP) — 11 plugins
Tools cung cấp code intelligence cho từng ngôn ngữ lập trình.

| Plugin | Ngôn ngữ | Extensions |
|--------|---------|------------|
| clangd-lsp | C/C++ | .c, .h, .cpp, .cc, .cxx, .hpp |
| csharp-lsp | C# | .cs |
| gopls-lsp | Go | .go |
| jdtls-lsp | Java | .java |
| kotlin-lsp | Kotlin | .kt, .kts |
| lua-lsp | Lua | .lua |
| php-lsp | PHP | .php |
| pyright-lsp | Python | .py, .pyi |
| rust-analyzer-lsp | Rust | .rs |
| swift-lsp | Swift | .swift |
| typescript-lsp | TypeScript/JS | .ts, .tsx, .js, .jsx, .mts, .cts |

**Đánh giá nhóm:** Utility cao nhưng generic — không học được nhiều về skill design.

---

### 2. DEVELOPMENT WORKFLOW — 5 plugins
Core development tools, rất thiết thực.

| Plugin | Chức năng chính | Command |
|--------|----------------|---------|
| **commit-commands** | Git workflow: commit, push, PR | `/commit`, `/commit-push-pr`, `/clean_gone` |
| **code-review** | PR review với 4 parallel agents | `/code-review` |
| **feature-dev** | 7-phase feature development workflow | `/feature-dev` |
| **pr-review-toolkit** | 6 specialized review agents | per-agent trigger |
| **code-simplifier** | Code simplification agent | agent trigger |

---

### 3. AI/AGENT PATTERNS — 4 plugins
Patterns về cách xây dựng agent-based workflows.

| Plugin | Pattern | Type |
|--------|---------|------|
| **feature-dev** | Multi-agent parallel orchestration | Command + 3 agents |
| **pr-review-toolkit** | Specialized agent bundle | 6 agents |
| **ralph-loop** | Self-referential iteration loop | Command + Hook |
| **agent-sdk-dev** | SDK scaffolding + verification | Command + 2 agents |

---

### 4. PLUGIN DEVELOPMENT META-TOOLS — 3 plugins
Tools để xây dựng plugin khác.

| Plugin | Chức năng | Type |
|--------|----------|------|
| **plugin-dev** | Comprehensive plugin creation toolkit | 7 skills + 1 command |
| **skill-creator** | Create/improve/eval skills | Skill |
| **example-plugin** | Reference implementation | Template |

---

### 5. HOOKS & CONFIGURATION — 4 plugins
Custom automation và behavior modification.

| Plugin | Chức năng | Type |
|--------|----------|------|
| **hookify** | Create regex-based hooks | Plugin + 4 commands |
| **claude-code-setup** | Analyze + recommend automations | Skill |
| **claude-md-management** | CLAUDE.md maintenance | Skill + Command |
| **security-guidance** | Security hooks | Hooks |

---

### 6. OUTPUT STYLES — 2 plugins
Thay đổi cách Claude hiển thị output.

| Plugin | Chức năng |
|--------|----------|
| **explanatory-output-style** | Educational insights format |
| **learning-output-style** | Interactive learning format |

---

### 7. CREATIVE/INTERACTIVE — 2 plugins
UI và interactive experiences.

| Plugin | Chức năng |
|--------|----------|
| **frontend-design** | Production-grade frontend interfaces |
| **playground** | Interactive HTML playgrounds |

---

### 8. EXTERNAL INTEGRATIONS (MCP) — 13 plugins
Third-party service connections.

| Plugin | Service | Use Case |
|--------|---------|---------|
| github | GitHub | PRs, issues, repos |
| gitlab | GitLab | Repos |
| slack | Slack | Messaging, channels |
| linear | Linear | Issue tracking |
| asana | Asana | Project management |
| stripe | Stripe | Payments, checkout |
| supabase | Supabase | Backend (PostgreSQL, Auth) |
| firebase | Firebase | Cloud services |
| playwright | Playwright | Browser automation |
| context7 | Context7 | Library documentation |
| greptile | Greptile | AI code review |
| laravel-boost | Laravel | PHP framework |
| serena | Serena | Platform integration |

---

## Tham chiếu Marketing Skills (từ marketing-skills.md)

**Ngữ cảnh:** File `/home/admin88/1_active_projects/spy-skills/self-explores/learnings/marketing-skills.md` phân tích 3 external marketing skill repos:

1. **marketingskills** (Corey Haines) — 26 skills, 8/10 quality
   - Top skills: content-strategy, copywriting, seo-audit, email-sequence, ab-test-setup
   - Pattern đặc biệt: Product context file (`~/.claude/product-marketing-context.md`)

2. **ai-marketing-skills** (Brian Wagner) — 17 skills, 6/10 quality
   - "Framework AI executes" philosophy

3. **agentkits-marketing** (AiTyTech) — Multi-agent workflow, 7/10
   - Pattern: Marketing team orchestrator (content writer, SEO specialist, email marketer)

**Lưu ý:** Các marketing skills này KHÔNG có trong repo hiện tại nhưng là nguồn tham chiếu để so sánh patterns.

---

## Key Insights

1. **Repo này thiên về Dev Tools** — 60% là LSP + Development Workflow
2. **Agent orchestration là theme nổi bật** — feature-dev (7 phases), code-review (4 agents), pr-review-toolkit (6 agents)
3. **Plugin-building meta-tools** — Đặc biệt có plugin-dev (7 skills) và skill-creator
4. **External MCP ecosystem** — 13 integrations, most are minimal config files
5. **Thiếu Marketing domain** — Không có marketing skills nào trong official repo
