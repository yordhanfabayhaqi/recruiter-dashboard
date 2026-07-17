# Recruiter Dashboard

A single-file Google Apps Script that turns an ordinary Google Sheet of applicants
into a lightweight recruiting operations console: a live pipeline funnel, stage-by-stage
scans, weekly interviewer health checks, round-robin assignment, and per-reviewer
payroll recaps — all driven from custom menus, with an optional AI-generated executive
insight on the pipeline report.

It is published as a **generic, reusable template**. Nothing about any specific company,
role, or process is hardcoded. You configure everything through a **⚙️ Setup** menu.

## What it does

- **Pipeline report** — a horizontal funnel (Applicant → Responded → Passed Screening →
  Assessment → Stage-2 Interview → Offered → Accepted) with per-stage conversion and
  drop-off, broken down by role and by channel, emailed on demand.
- **AI executive insight** *(optional)* — sends the pipeline numbers to an AI provider of
  your choice and appends three plain-language insight points to the report.
- **Scans** — one-click lists of who is *pending assessment*, *ready for interview*, or
  *ready for an offer*, grouped by reviewer or assignee.
- **Interview health check-up** — weekly volume vs. active-reviewer analysis with a
  Very Healthy / Healthy / At Risk / Heavy Risk classification and staffing recommendation.
- **Processing helpers** — copy qualified candidates into a review queue with round-robin
  assignment to the least-loaded interviewer, and promote passed candidates into an
  Offers sheet.
- **Payroll & reviewer reports** — a period payroll recap summary, individual reviewer
  report cards, and a stage-1 follow-up recap, all with a test-mode send.
- **Dashboard** — an in-sheet HTML modal with tabs for pipeline, scans, and health.

## Setup

1. Open your Google Sheet → **Extensions → Apps Script**, paste `RecruiterDashboard.gs`,
   save, and reload the sheet.
2. Use the **⚙️ Setup** menu to configure everything (values are stored in Script
   Properties, never in code):
   - **Set AI API Key** and **Set AI Model** — only needed for the optional insight.
   - **Set Admin Email & Domain** — where audit logs go, and the domain that quick-send
     recipients are restricted to.
   - **Set CC Recipients** — optional CC list for outgoing recaps.
   - **Set Pay Rate & Currency** — per-interview fee and currency label.
   - **Set Program Start Dates** — the cutoff for legacy rows and stage-2 counting.
   - **Set Sheet Names** — the tab names for applicants, review queue, stage-2, offers,
     roster, and imported interviews.
3. Use **📊 Recruiter Dashboard → Manage Reviewer Roster** to create the roster sheet,
   then fill in reviewer name, email, stage (`Screening`/`Interview`), and `Active`.
4. **Adapt the schema.** Near the top of the file, the `COLUMNS`, `STATUS`, and `ROLE`
   objects define an **example** column layout and label set. Remap them to match your
   own sheet before running the reports.

## Caveat on data-source logic

Some data-source and lookup logic in this template is **deliberately simplified or
example-only**. The author works with confidential HR data and cannot publish production
specifics, so the sheet schema (column positions, status strings, role labels, and the
import/lookup formulas) is a **synthetic demonstration mapping**, not a real one. It runs,
but you must supply your own column mapping and status vocabulary for it to reflect real
data. The AI insight call also points at a placeholder endpoint (`api.example.com`) and a
generic request/response shape — repoint it at your provider and adjust the parsing.

## Attribution

100% AI-generated, 100% human-directed. Directed and iterated by Yordhan Fitrians
Akhmad B. based on real HR pain points — refined repeatedly for business fit, user
experience, and workflow comfort.

## License

Choose and add a license (e.g. MIT) before publishing if you want reuse terms to be explicit.
