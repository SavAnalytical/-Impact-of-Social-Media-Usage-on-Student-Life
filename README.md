## Impact of Social Media Usage on Student Life (Ages 18–24)

## over-view
 This file walks through what the EDA and hypothesis tests actually found, and what those findings do  and don't  support.

## 🛠️ Tools and Technologies

The following tools and technologies were used:

- **R**
- **RStudio**
- **R Markdown**
- **dplyr**
- **ggplot2**
- **tidyverse**


## 🔎 Executive Summary

This analysis examined how daily social media usage relates to sleep, mental health, and academic performance among students aged 18–24 across Europe, South America, and Asia. Three formal hypothesis tests were run. Two produced statistically significant results; one did not — and that "no effect" finding is just as informative as the significant ones.


| Question | Test | Result |
|---|---|---|
| Does usage level affect sleep? | Welch two-sample t-test | ✅ **Significant** — high-usage students sleep ~1.8 hrs less/night |
| Does mental health score differ by platform? | One-way ANOVA | ✅ **Significant** — at least one platform differs from the others |
| Is academic impact associated with gender? | Chi-square test | ❌ **Not significant** — no meaningful gender association |

---

## 🖼️ EDA Insights

### Distribution of Daily Social Media Usage
The histogram, centered with a dashed mean-usage reference line, shows where the "typical" student in the sample falls.

<img width="1163" height="782" alt="Screenshot 2026-07-25 165120" src="https://github.com/user-attachments/assets/3a2fa71c-b021-4022-a0f7-38759a162503" />


### Most Used Platform
Based on the  platform-count chart, **Instagram and TikTok are the clear leaders**, each drawing roughly three times the usage of most other platforms, while regionally specific apps (KakaoTalk, LINE, VKontakte, WeChat) show much smaller counts.
**NOTE:**  Any platform-level comparison (like the ANOVA below) is more heavily powered for Instagram/TikTok/Facebook than for the smaller platforms.


<img width="1202" height="787" alt="image" src="https://github.com/user-attachments/assets/3fb40644-0072-49a4-96c5-c427a9927afc" />


### Average Usage Hours by Platform
 A platform can have fewer total users but higher per-user usage hours (or vice versa).
 **NOTE:** This table is what makes the later ANOVA result interpretable — it tells you not just *that* mental health scores differ by platform, but gives a plausible mechanism (heavier per-platform usage) worth checking as a follow-up.

---

## 🧪 Hypothesis Testing Results

### 1. Does Social Media Usage Affect Sleep?
**H₀:** No difference in sleep hours between high and low social media users.
**H₁:** A significant difference exists.

A Welch two-sample t-test compared sleep duration between students using social media for  more than 5 hours/day ("High Usage") versus 5 hours or less ("Low Usage").

> **Result:** *t*(1637.6) = -46.44, **p < 0.001**. High-usage students slept significantly less (M = 5.70 hrs) than low-usage students (M = 7.51 hrs) — a mean difference of roughly 1.7–1.9 hours per night (95% CI: -1.88 to -1.73).

**View:** This is a large, highly significant effect — not a marginal one. A gap of nearly two hours of sleep per night is clinically meaningful, not just statistically detectable.

**What this doesn't mean:** the design is cross-sectional, so this cannot establish that social media usage *causes* sleep loss. students who already sleep poorly may use social media more during wakeful hours, or a third factor (stress, workload, time-zone/lifestyle differences across the sampled countries) could drive both.


### 2. Does Mental Health Score Differ Across Platforms?
**H₀:** No difference in mean mental health score across platforms.
**H₁:** At least one platform differs from the others.

A one-way ANOVA tested the mental health score across all platforms in the dataset.

> **Result:** *F*(11, 1693) = 8.02, **p < 0.001**. At least one platform differs significantly from the others in associated mental health score.

**What this means:** platform choice is not statistically neutral with respect to reported mental health — some platforms are associated with meaningfully different scores than others.

**What this doesn't mean:** because no post-hoc test (e.g., Tukey HSD) was run, this result **cannot tell you which specific platform(s)** differ from which. It would be inaccurate to single out any one platform (e.g., "TikTok is worse") from this result alone — the honest claim is limited to "platform matters somewhere in this set," not "platform X is the problem."

### 3. Is Academic Impact Associated with Gender?
**H₀:** No association between gender and academic performance impact.
**H₁:** An association exists.

A Pearson Chi-square test examined the relationship between gender and whether students reported social media affecting their academic performance.

> **Result:** χ²(1) = 0.00014, **p = 0.9905**. No statistically significant association found.

**What this means:** male and female students in this sample report being affected academically by social media at essentially identical rates. This is a genuinely useful negative result — it means academic impact is not a gendered phenomenon in this dataset, and any intervention or discussion of the issue shouldn't be gender-targeted based on this data.

---

## 🧠 Logical, Evidence-Based Discussion

Putting the three results together tells a more coherent story than any one test alone:

- **Sleep is the strongest, most defensible finding.** The t-test result is large, highly significant, and behaviorally intuitive (late-night usage displacing sleep hours is a well-documented pattern in existing sleep research generally). Of the three findings, this is the one most worth leading with in a summary or abstract.
- **Platform differences are real but require humility.** The ANOVA confirms platform matters, but resist the temptation to name a "worst" platform without a post-hoc test — doing so would overstate what the data actually supports and could unfairly stigmatize a platform's user base without justification.

## ⚠️ Limitations 

- **Self-reported data** — `Mental_Health_Score` and `Affects_Academic_Performance` reflect perception, not clinical/academic records.
- **Cross-sectional design** — all relationships reported here are associations. None of the three tests can establish causation or direction.
- **Uneven platform sample sizes** — smaller platforms (KakaoTalk, LINE, VKontakte, WeChat) carry less statistical weight in the ANOVA than Instagram or TikTok.
- **No post-hoc testing** — the ANOVA result identifies that platforms differ, not which ones.


---
*This document is intended to sit alongside your rendered `.Rmd`/`.html` output in the repository, giving readers a fast, narrative way to understand your findings without re-running the code.*
