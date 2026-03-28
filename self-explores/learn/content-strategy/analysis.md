# content-strategy

**Nguồn:** 18_marketingskills (Corey Haines — Conversion Factory)
**File:** `/home/admin88/1_active_projects/spy-skills/18_marketingskills/skills/content-strategy/SKILL.md`

## Đánh giá (Score: 8/10)

**Lý do:** Skill phong phú nhất trong marketingskills repo (357 lines). Kết hợp framework tư duy chiến lược với công cụ thực hành. Pattern "product context file" là đặc điểm nổi bật.

---

## Ưu & Nhược điểm

### Ưu điểm
- **Product context file pattern:** Check `.claude/product-marketing-context.md` trước khi hỏi — giảm repetitive setup
- **Searchable vs Shareable framework:** Rõ ràng và actionable — searchable = SEO foundation, shareable = virality
- **Content pillar với 4 approaches:** Product-led, audience-led, search-led, competitor-led
- **Keyword research by buyer stage:** Awareness → Consideration → Decision → Implementation — full funnel
- **Scoring framework có trọng số:** Customer impact (40%) + Content-market fit (30%) + Search potential (20%) + Resources (10%)
- **Ideation sources đa dạng:** Keyword data, call transcripts, forum research, competitor analysis
- **Hub-and-spoke structure:** SEO architecture pattern rõ ràng
- **Related skills ecosystem:** Links to copywriting, seo-audit, programmatic-seo, email-sequence

### Nhược điểm
- **Yêu cầu context file:** Nếu không có `.claude/product-marketing-context.md`, phải gather nhiều context
- **Không có tool integrations:** Không mention Ahrefs, SEMrush, Moz — abstract hơn seo-audit
- **Output format hơi generic:** Content pillars + priority topics + topic cluster map — cần customize
- **No competitive analysis deep dive:** Chỉ nhắc "competitor analysis" không có framework chi tiết

---

## Khả năng tích hợp vào hệ thống hiện tại

### Với viec/OMC workflow
- Tạo task: "Lập kế hoạch content" → trigger content-strategy skill
- Product context file = `/viec context` pattern — đã có trong self-explores/context/
- Scoring framework tích hợp vào `/viec xếp hạng` logic

### Với marketing workflows
- Input cho copywriting skill (related)
- Foundation cho seo-audit (cần biết content plan trước khi audit)
- Link với email-sequence (content → nurture)

### Installation
```bash
# Copy skill vào Claude Code skills folder
cp -r /home/admin88/1_active_projects/spy-skills/18_marketingskills/skills/content-strategy/ ~/.claude/skills/
```

---

## Ghi chú kỹ thuật (Technical Decisions)

### Product Context File Pattern (★ Best Pattern)
```markdown
# Check trước khi bắt đầu:
~/.claude/product-marketing-context.md (global)
.claude/product-marketing-context.md (project-specific)
```
Nội dung context file nên có: product name, target audience, value proposition, current content gaps.

### Searchable vs Shareable Framework
```
SEARCHABLE (priority):
- Solves specific problems people search for
- Evergreen content
- Long-form, comprehensive
- Examples: How-to guides, tutorials, comparisons

SHAREABLE:
- Thought leadership, data, stories
- Timely, trend-driven
- Examples: Original research, expert roundups, case studies
```

### Content Pillar (Topic Cluster) Structure
```
Core Pillar Page (10x content)
├── Supporting Topic 1 (cluster page)
├── Supporting Topic 2 (cluster page)
├── Supporting Topic 3 (cluster page)
└── Supporting Topic N (cluster page)
```

### Keyword Stage Mapping
```
Awareness:       "what is", "how does", "why"
Consideration:   "best", "top", "vs", "alternatives"
Decision:        "review", "pricing", "[brand] + use case"
Implementation:  "how to set up", "tutorial", "integration"
```

### Priority Scoring Weights
```
Customer impact    40%  → Directly helps target customer?
Content-market fit 30%  → Can we create this well?
Search potential   20%  → Volume + competition?
Resources          10%  → Time + effort needed?
```

### Teachable Patterns
1. **Product context file** để avoid repetitive setup
2. **Searchable-first** content strategy
3. **Hub-and-spoke** topic cluster architecture
4. **Buyer stage keyword mapping**
5. **Weighted scoring** cho content prioritization
