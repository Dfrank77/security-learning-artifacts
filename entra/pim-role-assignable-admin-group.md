# Entra ID PIM Lab: Role-Assignable Admin Group (Request + Approval)

## Goal
Use a role-assignable Entra admin group to provide just-in-time privileged access via PIM, with a request + approval workflow and a complete audit trail.

## Environment
- Platform: Microsoft Entra ID (lab tenant)
- Objects: Role-assignable security group, Entra admin role assignment, PIM for Groups
- Users: test admin + test requester

## Configuration
1. Created a **role-assignable** security group (admin group).
2. Assigned an **Entra admin role** to the group.
3. Used **PIM for Groups** to make a lab user **eligible** for group membership.
4. Enabled **activation with request + approval** (no standing membership).

## Validation Steps
1. Verified admin action: user was made **eligible** for group membership.
2. User submitted an **activation request** to become a group member.
3. Approver approved the request.
4. Confirmed PIM completed the membership activation for the requested duration.

## Evidence / Audit Chain Confirmed
Audit logs show the full sequence:
- Admin made the user eligible for the role-assignable group
- User requested group membership activation
- Approval was recorded
- PIM completed the membership activation event

## Why this matters (real-world)
- Centralizes privileged access via group-based role assignment (easier governance than direct user role assignments)
- Enforces JIT elevation with approval and accountability
- Produces a clear audit trail for compliance and incident review

## Next Improvements
- Require MFA + justification for activation
- Add alerts for privileged group activations (high-risk monitoring)
- Periodic access reviews for eligible members of privileged groups
