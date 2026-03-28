# seo-audit

**Nguồn:** 18_marketingskills (Corey Haines — Conversion Factory)
**File:** `/home/admin88/1_active_projects/spy-skills/18_marketingskills/skills/seo-audit/SKILL.md`

## Đánh giá (Score: 7/10)

**Lý do:** Framework audit đầy đủ nhưng thiên về checklist hơn là actionable AI skill. Điểm mạnh là site-type-specific guidance và Core Web Vitals targets cụ thể.

---

## Ưu & Nhược điểm

### Ưu điểm
- **Core Web Vitals targets cụ thể:** LCP, INP, CLS với số liệu — không generic
- **Site-type specific guidance:** SaaS, e-commerce, content/blog, local business — không one-size-fits-all
- **Prioritized action plan format:** Executive summary + findings + action plan — deliverable-ready
- **E-E-A-T framework:** Experience, Expertise, Authoritativeness, Trustworthiness — Google-aligned
- **Common issues by site type:** Practical, maps to real problems
- **Honest limitation note:** Schema markup detection limitation với web_fetch — transparency

### Nhược điểm
- **Tool-dependent:** Nhiều checks yêu cầu Screaming Frog, browser tools — Claude không làm được standalone
- **Schema detection impossible:** Skill tự nhận không detect được structured data — significant gap
- **Không có tool access:** Không integrate với Ahrefs, Semrush — manual lookup needed
- **Checklist-heavy:** Nhiều phần là checklists, ít decision framework
- **Không có benchmark data:** "Good" title tag length — cần examples

---

## Khả năng tích hợp vào hệ thống hiện tại

### Với viec/OMC
- Task: "Audit SEO cho trang X" → trigger seo-audit
- Output report → lưu vào self-explores/tasks/ worklog
- Prioritized action plan → tạo tasks trong beads

### Với marketing workflows
- Input: content-strategy (biết content plan)
- Output feeds: programmatic-seo, schema-markup tasks

### Installation
```bash
cp -r /home/admin88/1_active_projects/spy-skills/18_marketingskills/skills/seo-audit/ ~/.claude/skills/
```

---

## Ghi chú kỹ thuật (Technical Decisions)

### Core Web Vitals Targets
```
LCP (Largest Contentful Paint): < 2.5s (good), < 4.0s (needs improvement)
INP (Interaction to Next Paint): < 200ms (good), < 500ms (needs improvement)
CLS (Cumulative Layout Shift):  < 0.1 (good), < 0.25 (needs improvement)
```

### Technical SEO Audit Categories
```
1. Crawlability:   robots.txt, XML sitemap, crawl budget, site architecture
2. Indexation:     index status, canonicalization, duplicate content
3. Site Speed:     Core Web Vitals (see above)
4. Mobile:         mobile-friendliness, responsive design
5. Security:       HTTPS, mixed content
6. URL Structure:  clean URLs, hierarchy, redirects
```

### On-Page SEO Checklist
```
□ Title tags: 50-60 chars, primary keyword, unique per page
□ Meta descriptions: 150-160 chars, compelling, includes CTA
□ H1: One per page, includes primary keyword
□ H2-H6: Logical hierarchy, LSI keywords
□ Content: Depth, E-E-A-T signals, user engagement
□ Images: Alt text, file names, compression
□ Internal links: Logical structure, anchor text variety
```

### Site-Type Specific Issues
```
SaaS:        Indexing app pages, feature vs use-case landing pages,
             help docs SEO strategy
E-commerce:  Faceted navigation, product duplicate content,
             category page optimization
Content:     Pillar/cluster structure, content freshness,
             author authority
Local:       Google Business Profile, NAP consistency,
             local schema
```

### Audit Report Format
```markdown
## Executive Summary
- Top 3-5 critical findings
- Overall SEO health score (subjective)
- Quick wins vs long-term improvements

## Technical Findings
| Issue | Severity | Pages Affected | Recommendation |

## On-Page Findings
[Same table format]

## Content Findings
[Same table format]

## Prioritized Action Plan
1. Critical (fix now)
2. High impact (this month)
3. Long-term (ongoing)
```

### Schema Detection Limitation (Important Note)
```
web_fetch CANNOT reliably detect structured data.
Use instead:
- Browser DevTools → View Source → search "application/ld+json"
- Google Rich Results Test
- Screaming Frog (custom extraction)
```

### Teachable Patterns
1. **Site-type specific** issue lists
2. **Core Web Vitals** as specific numeric targets
3. **E-E-A-T** evaluation framework
4. **Prioritized action plan** output format
5. **Honest tool limitations** documentation
