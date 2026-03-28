# ab-test-setup

**Nguồn:** 18_marketingskills (Corey Haines — Conversion Factory)
**File:** `/home/admin88/1_active_projects/spy-skills/18_marketingskills/skills/ab-test-setup/SKILL.md`

## Đánh giá (Score: 9/10)

**Lý do:** Skill tốt nhất trong nhóm marketing về mặt rigor và structure. Hypothesis framework + statistical rigor + "peeking problem" warning = professional-grade experimentation guide.

---

## Ưu & Nhược điểm

### Ưu điểm
- **Structured hypothesis format:** Because X → we believe Y → will cause Z → we'll know when → metrics
- **Sample size quick-reference tables:** Baseline CR% × lift target → required traffic — actionable
- **Statistical significance guidance:** p-value < 0.05, minimum detectable effect
- **"Peeking problem" warning:** Critical gotcha that kills most A/B tests — rare to see in skill docs
- **3 metric types:** Primary (hypothesis), Secondary (interpretation), Guardrail (don't regress)
- **Traffic allocation options:** 50/50, conservative 90/10, ramping approaches
- **Common mistakes section:** Test design + execution + analysis errors — comprehensive
- **4 test types:** A/B, A/B/n, MVT, Split URL với traffic requirements
- **Documentation template:** Record everything for institutional memory

### Nhược điểm
- **Tool-specific (not tool-agnostic):** Mentions specific tools but doesn't integrate with APIs
- **No Bayesian alternative:** Only covers frequentist statistics approach
- **Conversion rate assumptions:** Sample size tables assume CR-based metrics only
- **Complex for beginners:** Statistical rigor is great but may overwhelm non-technical marketers

---

## Khả năng tích hợp vào hệ thống hiện tại

### Với viec/OMC
- Task: "Setup A/B test cho [hypothesis]" → trigger ab-test-setup
- Output test plan → lưu vào self-explores/decisions/ (test decision log)
- Kết quả test → lưu vào self-explores/learnings/

### Với marketing workflows
- Input: copywriting (variants to test), content-strategy (which content to test)
- Output feeds: analytics-tracking, page-cro
- Best pair: email-sequence + ab-test-setup (test subject lines)

### Installation
```bash
cp -r /home/admin88/1_active_projects/spy-skills/18_marketingskills/skills/ab-test-setup/ ~/.claude/skills/
```

---

## Ghi chú kỹ thuật (Technical Decisions)

### Hypothesis Framework (★ Best Pattern)
```
Because [observation/insight],
we believe [change]
will cause [effect] for [audience],
we'll know when [measurable outcome].
```

Example:
```
Because our landing page headline is generic,
we believe a benefit-focused headline
will increase conversions for trial signups,
we'll know when conversion rate increases by ≥10%.
```

### 3 Metric Types
```
PRIMARY:    The one metric tied directly to hypothesis
            (can only have one — forces clarity)

SECONDARY:  Support interpretation, don't decide winner
            (e.g., click rate, time on page, scroll depth)

GUARDRAIL:  Should NOT get worse
            (e.g., bounce rate, revenue per visitor, unsubscribes)
```

### 4 Test Types
```
A/B:       2 variants, clean comparison
A/B/n:     3+ variants, needs more traffic
MVT:       Multiple variables simultaneously, complex
Split URL: Different pages entirely, major redesign
```

### Sample Size Quick Reference (at 5% significance, 80% power)
```
Baseline CR  |  10% lift needed  |  20% lift needed
1%           |  ~250,000/variant |  ~65,000/variant
2%           |  ~125,000/variant |  ~32,000/variant
5%           |  ~50,000/variant  |  ~13,000/variant
10%          |  ~25,000/variant  |  ~6,500/variant
```

### The Peeking Problem (Critical Warning)
```
❌ WRONG: Check results daily, stop when p < 0.05
✓ RIGHT: Decide sample size BEFORE starting,
          run until that sample size is reached,
          THEN analyze

Reason: Peeking inflates false positive rate. If you
        check at 50%, 75%, and 100%, you haven't run
        one test — you've run three, tripling your
        chance of a false positive.
```

### Traffic Allocation Guidelines
```
Standard:      50/50 — Maximum statistical efficiency
Conservative:  90/10 or 80/20 — Protect against bad variant
Ramping:       5% → 25% → 50% → 100% — Catch bugs first
```

### Pre-Launch Checklist
```
□ Hypothesis documented with measurable success criteria
□ Sample size calculated (not guessed)
□ Test duration estimated (minimum 1-2 full business cycles)
□ Tracking verified (fire test event in both variants)
□ Guardrail metrics defined
□ SRM (Sample Ratio Mismatch) check planned
□ Analysis plan documented BEFORE launch
```

### Common Mistakes
```
TEST DESIGN:
- Testing too many things (not A/B, it's A/B/C/D)
- No statistical power calculation
- Changing test mid-run

EXECUTION:
- Stopping early (peeking)
- Not checking for SRM
- Traffic not properly split

ANALYSIS:
- Declaring winner without checking guardrail metrics
- Not considering seasonal effects
- Ignoring segment differences
```

### Teachable Patterns
1. **Structured hypothesis** → force clarity before testing
2. **3-metric-type** framework (primary/secondary/guardrail)
3. **The peeking problem** — most important stat concept
4. **Pre-launch checklist** → reduce execution errors
5. **Traffic allocation** decision framework
