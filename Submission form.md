# Monday.com Form — Medical Tax Credit via Payroll (Employee Submission)

Build spec for Kirst to configure the Monday.com form/board.

- Public form link: <INSERT_MONDAY_COM_FORM_LINK>
- Board owners: <INSERT_BOARD_OWNERS>
- Reference docs:
  - Employee guide: c:/AI-Working/SEM-Medical Aid project/Details-for-employees.md
  - Policy: c:/AI-Working/SEM-Medical Aid project/Policy details.md

Use this template to configure the Monday.com form/board. Fields marked Required must be set to required in the form. Use the conditional logic as noted.

---

## Section 1: Employee details
- __Employee full name__ (Text) — Required
- __Employee number__ (Text/Number) — Required
- __SA ID number / Passport__ (Text) — Required
- __SARS Tax number__ (Text) — Required
- __Work email__ (Email) — Required
- __Personal contact number__ (Phone) — Optional

---

## Section 2: Medical scheme details
- __Medical scheme name__ (Dropdown/Text) — Required
- __Membership number__ (Text) — Required
- __Principal member full name__ (Text) — Required
- __Principal member SA ID/Passport__ (Text) — Required
- __Are you the principal member?__ (Yes/No) — Required
  - If No, show Section 2A (Payer confirmation if paying for spouse/parent)

---

## Section 2A: If you pay for spouse/parent
- __Relationship to principal member__ (Dropdown: Spouse, Parent, Other dependant) — Required (conditional)
- __I confirm the principal member will NOT claim the credit in their own return for the same period__ (Checkbox declaration) — Required (conditional)
- __Principal member email/phone for verification__ (Text) — Optional (conditional)

---

## Section 3: Beneficiaries on the medical scheme
- __Total number of beneficiaries covered on this membership__ (Number) — Required
  - Validation: Must be >= 1
- __List beneficiary names and relationship__ (Long text) — Required
  - Example: "Jane Doe (self), John Doe (spouse), Kid Doe (child)"

---

## Section 4: Proofs and documents (Uploads)
- __Membership certificate (current) listing beneficiaries__ (File upload: PDF/JPG/PNG) — Required
- __Proof that you pay the contribution__ (File upload: Bank statement showing debit/EFT for last 2 months OR proof of deduction) — Required
- __Principal member ID document__ (File upload) — Required if you are NOT the principal member
- __Your ID document__ (File upload) — Required
- __Optional supporting docs__ (File upload) — Optional

> Notes for validation: Redact unrelated bank transactions if preferred; statement must still show your name, bank, date range, and debit/EFT to the scheme.

---

## Section 5: Period and payroll
- __Requested start month__ (Date/month picker) — Required
  - Note: Cannot be earlier than submission/approval month; subject to payroll cut‑off 20th of each month.
- __Current payroll entity/cost centre__ (Dropdown/Text) — Optional

> Initial rollout: Targeting the September payroll — please aim to submit documents by 15 September for inclusion.

---

## Section 6: Declarations and acknowledgements
- __Accuracy confirmation__ (Checkbox): "I confirm the information and documents provided are true and correct." — Required
- __Change notification__ (Checkbox): "I undertake to notify Finance immediately of any changes (scheme/member/payer/cancellation)." — Required
- __Duplicate claim avoidance__ (Checkbox): "I confirm these beneficiaries will not be claimed by another person for the same period." — Required if Section 2A applies; Optional otherwise
- __Privacy notice__ (Read-only text): "Your documents are processed for payroll tax credit purposes per company policy and POPIA."
- __Signature/typed name__ (Text) — Required
- __Submission date__ (Auto)

---

## Section 7: For Finance use (hidden on public form)
- __Eligibility check result__ (Status: Eligible / Incomplete / Not eligible) — Finance
- __SARS credit rate set applied__ (Text/Link to rate table) — Finance
- __Beneficiary count confirmed__ (Number) — Finance
- __Payroll effective month__ (Date/month) — Finance
- __Notes__ (Long text) — Finance
- __Reviewer__ (Person) — Finance
- __Date reviewed__ (Date) — Finance

---

## Automations (suggested)
- When item created -> notify Finance channel.
- When status changes to Eligible -> notify Payroll and set due date to payroll cut‑off.
- When status Incomplete -> auto-reply to requester with missing items.

---

## Data retention
- Retain documents for minimum 5 years (audit), per policy. Restrict access to Finance/Payroll only.