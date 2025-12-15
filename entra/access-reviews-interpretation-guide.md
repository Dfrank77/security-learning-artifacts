# Entra Access Reviews: Interpreting Results + Building Reviews That Work

## What Access Reviews are (in one sentence)
A recurring control to confirm users still need access to a group/app/role, with optional auto-remediation when they don’t respond or are denied.

---

## How to interpret Access Review outcomes
### Approved
- Reviewer explicitly approved continued access.
- If "Auto-apply results" is enabled, access stays.

### Denied
- Reviewer explicitly denied access.
- If auto-apply is enabled, access is removed at the end of the review.

### Not reviewed
- No decision was submitted (reviewer didn’t act).
- What happens depends on your settings:
  - If you configured "If reviewers don’t respond": **Remove access** → user gets removed (common for guests / high-risk groups).
  - If set to **Keep access** → user stays (common if you want to avoid accidental removals).
  - If set to **Take recommendations** → system uses its recommendation logic (use carefully; validate first).

### Don’t confuse these:
- “Denied” = someone made an explicit decision.
- “Not reviewed” = nobody decided; the system applies your fallback rule.

---

## The 3 settings that decide what actually happens
1) **Auto-apply results**
- ON: changes apply automatically at end of review (real governance)
- OFF: review produces a report only (good for first-run / validation)

2) **If reviewers don’t respond**
- Remove / Keep / Recommendations
- This single setting explains most “why did it deny?” confusion.

3) **Scope**
- Groups (most common)
- Apps
- Directory roles (high impact—use carefully)

---

## Recommended review patterns (enterprise-style)
### Guests (B2B)
- Frequency: quarterly (or monthly for sensitive apps)
- Default for no response: **Remove**
- Auto-apply: ON (after first cycle validation)

### Privileged groups / admin access
- Frequency: monthly or quarterly depending on risk
- Reviewers: app/role owner + security (or dual review)
- Default for no response: often **Remove** (high assurance)
- Auto-apply: ON once the process is proven reliable

### Department app groups (HR/Finance)
- Frequency: quarterly
- Default for no response: often **Keep** (to avoid business disruption), but require escalation and reminders

---

## What I validate each time
- Review created for the correct group/app/role (scope correct)
- Reviewer assignment makes sense (owner who actually knows the users)
- Auto-apply behavior matches risk
- Outcome is visible and consistent (who approved/denied/not reviewed)
- Access changes applied as expected (membership removed/retained)

---

## Common failure modes
- Reviewers ignore it → everything becomes "Not reviewed" → fallback rule drives removals unexpectedly
- Wrong scope (reviewing the wrong group)
- Auto-apply ON too early (without a dry run)
- No clear ownership (nobody knows who should approve)
