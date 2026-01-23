---

# Scoring model (to pick final Top 3 orgs)

To shortlist logically, each org is scored using:

* **Language fit (0–5):** how strongly the org matches my strongest languages (C++ > Python > JS > Java)
* **Interest fit (0–5):** CP/DSA + Software Engineering + tooling alignment
* **Contribution accessibility (0–5):** how easy it is to build, find starter issues, and submit PRs
* **Acceptance probability (0–5):** realistic odds given complexity and competition

> **Total = 20 points** (higher is better).

---

## Org scoring table

| Org                             | Language fit (0–5) | Interest fit (0–5) | Contribution accessibility (0–5) | Acceptance probability (0–5) | Total / 20 | Notes                                                 |
| ------------------------------- | -----------------: | -----------------: | -------------------------------: | ---------------------------: | ---------: | ----------------------------------------------------- |
| LLVM                            |                  5 |                  5 |                                2 |                            2 |         14 | Best C++/DSA fit; very competitive + complex build    |
| KDE                             |                  5 |                  4 |                                4 |                            4 |         17 | Strong C++ fit; good contributor onboarding           |
| Linux Foundation (subprojects)  |                  4 |                  4 |                                3 |                            3 |         14 | Depends heavily on chosen subproject                  |
| Git                             |                  4 |                  4 |                                3 |                            2 |         13 | Great tooling; strict reviews and high bar            |
| Python ecosystem (PSF umbrella) |                  4 |                  4 |                                4 |                            4 |         16 | Excellent for Python tooling; good acceptance chances |
| Boost                           |                  5 |                  4 |                                2 |                            2 |         13 | Elite C++; fewer beginner issues                      |
| SymPy                           |                  4 |                  4 |                                4 |                            4 |         16 | Strong Python + algorithmic work; good onboarding     |
| GNU Radio                       |                  3 |                  3 |                                3 |                            3 |         12 | Mixed stack; depends on project                       |
| Meshery                         |                  2 |                  3 |                                4 |                            4 |         13 | Great if choosing Kubernetes/tooling ideas            |
| Jitsi                           |                  2 |                  3 |                                3 |                            3 |         11 | Good real-world codebase; stack not primary           |
| Internet Archive                |                  3 |                  3 |                                3 |                            3 |         12 | Data tooling; project-specific                        |
| AboutCode                       |                  3 |                  4 |                                4 |                            4 |         15 | Developer tooling + easier entry                      |

---

## Top 3 (recommended)

These give the best balance of **fit + ability to contribute early + acceptance probability**:

1. **KDE Community**
2. **Python ecosystem (PSF umbrella)**
3. **SymPy**

## Stretch pick (if I want a high-reward challenge)

* **LLVM** (amazing outcome if selected)

## Backups (smart choices)

* AboutCode
* Linux Foundation (choose one subproject)
* Meshery (if I want Kubernetes-heavy work)

---
# GSoC Org Evaluation Template

Use this template to evaluate and compare mentoring organizations objectively.
Copy this into `01-org-research/<org-name>/overview.md` and fill it.

---

## 1) Organization Details
- **Organization name:**
- **Website:**
- **GitHub org / repo links:**
- **Primary communication channel:** (Discord / Zulip / IRC / Mailing List)
- **Project ideas page link:**
- **Tech stack:** (Languages / frameworks / tools)

---

## 2) Why I’m Interested (Motivation)
Write 3–5 bullets about why this org excites you.

- 
- 
- 

---

## 3) Community & Communication (Score: __/10)
Evaluate how beginner-friendly + responsive the community is.

### Signals to check
- [ ] clear onboarding docs (`CONTRIBUTING.md`, setup steps)
- [ ] active maintainers in issues/PRs
- [ ] active chat/mailing list
- [ ] polite responses to beginner questions
- [ ] labelled beginner issues (good-first-issue)

### Notes
- First impression:
- Mentor responsiveness:
- Community culture:

---

## 4) Project Quality & Codebase Health (Score: __/10)

### Repository signals
- [ ] recent commits in last 1–2 weeks
- [ ] proper CI/tests present
- [ ] issue tracker active
- [ ] PR review activity
- [ ] clear roadmap/architecture docs

### Notes
- Build difficulty:
- Test suite:
- Code readability:
- Documentation quality:

---

## 5) My Skill Match (Score: __/10)

### Languages required
- Required:
- Optional:

### My current skill level (self-rating)
| Skill | Level (0–10) | Notes |
|------|--------------|------|
| C++ |  |  |
| Python |  |  |
| JS/TS |  |  |
| Git/GitHub |  |  |
| Linux |  |  |

### Match Notes
- Strong match areas:
- Weak areas / learning required:

---

## 6) Contribution Entry Difficulty (Score: __/10)

### Setup
- [ ] easy to setup locally
- [ ] clear build instructions
- [ ] starter tasks available

### Contribution opportunities
- [ ] docs issues available
- [ ] beginner bugs available
- [ ] tests needed / improvements possible

### Notes
- First contribution target idea:
- blockers encountered:

---

## 7) Project Ideas Evaluation
List and rate the top project ideas.

### Idea A
- Title:
- Link:
- Difficulty: (Easy/Medium/Hard)
- Why it matters:
- Expected deliverables:
- Risks / unknowns:
- My confidence: __/10

### Idea B
- Title:
- Link:
- Difficulty:
- Why it matters:
- Expected deliverables:
- Risks / unknowns:
- My confidence: __/10

---

## 8) Mentorship & Support (Score: __/10)

### Signals
- [ ] mentors reply within 24–72 hours
- [ ] project is actively mentored
- [ ] mentors ask clarifying questions
- [ ] mentors guide properly (not just assign tasks)

### Notes
- People I interacted with:
- Mentor feedback received:
- Any red flags:

---

## 9) Long-Term Value (Score: __/10)
Does this org help my career + skill growth after GSoC?

- [ ] project has real users
- [ ] skills are industry relevant
- [ ] can contribute after GSoC

Notes:
- 

---

## 10) Final Decision Summary

### Pros
- 
- 
- 

### Cons
- 
- 
- 

### Red Flags (if any)
- 
- 

---

## 11) Final Score (Out of 100)
| Category | Score |
|---------|------:|
| Community & Communication |  |
| Codebase Health |  |
| Skill Match |  |
| Contribution Entry |  |
| Ideas Quality |  |
| Mentorship |  |
| Long-term value |  |
| **Total** | **__/100** |

---

## 12) Decision
- [ ] Strongly consider (Top priority)
- [ ] Backup option
- [ ] Not suitable

Reason:

