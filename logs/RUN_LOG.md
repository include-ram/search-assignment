# RUN LOG

## Run — 2026-06-24

### What was built
A `search/` workspace for a job-search assignment, plus this `logs/` directory:
- **`.gitignore`** — ignores `search/private-notes.md`.
- **`search/profile.yml`** — job-search profile: target roles (SWE / AI / ML), F-1 visa constraints, geography (Boston base, open to anywhere in the USA + remote), industry (any, no exclusions), company size (any), and `sponsorship_required: true` as a hard gate.
- **`search/resume.json`** — typed extraction of the resume (one entry per job, project, degree, achievement, skill; `certifications` empty — none on the resume), with an attestation block at the top.
- **`search/gaps.md`** — gap analysis vs. the SWE/AI/ML target, every Evidence cell citing a real source (O\*NET 15-1252.00 + observed posting patterns + 2026 ML-engineer requirement roundups).

### The three attestation errors (corrected in resume.json)
1. **Accenture title — promotion collapsed into one title.** The extraction listed "Custom Software Engineering Analyst" for the full Jul 2021–Jun 2024 span. The candidate actually started as **Associate Software Engineer** and was promoted within ~8 months. Split into a `title_history` (Associate Software Engineer → Custom Software Engineering Analyst, ~Feb 2022).
2. **Distributed Super Resolution project date.** Originally extracted as `2025-01`; the candidate's corrected/updated resume showed **January 2026**. Fixed to `2026-01`.
3. **Graduation date precision.** Originally `2026-08` (month only); corrected to the specific **2026-08-29**.

(Note: error #1 was a genuine extraction over-collapse; errors #2 and #3 stemmed from the candidate uploading a second, corrected resume mid-session — owned honestly, not agent inflation. The GCP skill tag was flagged but confirmed valid and kept.)

### Top gap
**System design at scale.** Major-employer new-grad SWE postings expect the ability to design a distributed system handling 100M+ users from scratch [gaps.md S2]. The candidate has microservices, async processing, a Pinecone microservice, and multi-GPU DDP/FSDP training, but no artifact demonstrating end-to-end high-scale distributed system design. Closing plan: build/document a project with an explicit scale story and work through a system-design curriculum.

### Killed row and why
**Row 4 — "Automated testing / QA tooling."** Killed by the candidate. Reason: it was generated from general SWE posting patterns and O\*NET's broad Software Developer profile, but the candidate's target is specifically SWE/AI/ML. In ML/AI engineer postings, testing frameworks (pytest/unittest) appear only occasionally and are never a primary requirement or screening criterion. The agent over-indexed on broad SWE postings and misapplied them to a narrower AI/ML target — a gap for a backend SWE role, not this one.

### profile.yml field that had to be corrected
The **OPT timeline / STEM extension field**. The first draft expressed only `standard_opt_months: 12` with STEM eligibility uncertain. The candidate corrected this to make the **24-month STEM extension explicit** (`stem_extension_months: 24`, stacking on the 12-month standard OPT for 36 months total), with `stem_extension_eligible: uncertain` retained pending DSO confirmation. The graduation date in profile.yml was also confirmed as 2026-08-29.

---

### Step 4 — Verification check questions and honest answers

**Q1 — resume.json: Is every job entry traceable to something verifiable? Or did the agent promote a title, extend a date, or add a skill you cannot defend?**
> Yes, both jobs are real and verifiable through LinkedIn and my offer letters. The agent did catch some real errors though. The biggest one was my Accenture title — it listed me as "Custom Software Engineering Analyst" for the full 3 years, but I actually started as an Associate Software Engineer and got promoted within 8 months. That's a meaningful difference. The other two corrections came from me uploading a second updated resume mid-session — the Super Resolution project date was 2025 in my first file and 2026 in the corrected one, and my graduation date was month-only instead of the specific August 29th. So two of the three fixes came from my own resume inconsistency, not the agent inflating something. I'm owning that honestly.

**Q2 — profile.yml: Does the visa constraint section reflect your actual documents — or your hope for how the timeline might work out?**
> Yes, this reflects my actual situation. I haven't applied for OPT yet since I'm still finishing my degree. STEM eligibility is marked uncertain because I genuinely haven't checked with my DSO — that's not a hedge, that's just the truth. Everything else like the 90-day ceiling and buffer target matches what I understand about OPT rules.

**Q3 — gaps.md: Does every gap in the evidence column cite something real — or did the agent invent the demand signal?**
> The evidence cells pull from ONET 15-1252.00 and job posting patterns Claude Code searched live. I opened ONET 15-1252.00 myself and confirmed that Making Decisions and Solving Problems appears under Work Activities, so that citation is verified. I did not personally check every URL for S2 and S3, and the S2 aggregator links may be stale. I am noting that as a limitation rather than pretending I verified everything.
