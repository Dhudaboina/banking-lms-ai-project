# Mortgage Lending Requirements

**Project:** Banking Loan Management System  
**Document ID:** LMS-REQ-003  
**Version:** 1.0  
**Status:** Draft

## 1. Purpose

Define the functional requirements and validation rules for the educational mortgage lending workflow.

## 2. Customer Onboarding

- Customers must provide all required registration details.
- Email addresses must follow the configured validation rules.
- Duplicate email addresses must be rejected.
- Invalid or missing required fields must produce clear validation messages.
- Passwords must never be stored in plain text.

## 3. Mortgage Application

Each application must capture:

- Customer reference
- Property value
- Requested loan amount
- Annual interest rate
- Loan tenure in months
- Employment and income details
- Application reference and submission timestamp

The system must reject missing or invalid values and generate a unique application reference for each successful submission.

## 4. Document Management

The educational application will simulate document submission and validation.

- Support configured document categories, such as identity proof, income proof, and property documents.
- Reject unsupported file types and files exceeding the configured size limit.
- Track document status as Pending, Accepted, or Rejected.
- Record a reason when a document is rejected.
- Do not claim that simulated checks establish the authenticity of real documents.

## 5. Underwriting and Eligibility

- Evaluate applications using configurable educational business rules.
- Validate the requested amount, income, tenure, and other configured eligibility conditions.
- Return an eligibility result and explanatory reasons.
- Keep eligibility evaluation separate from the final authorized loan decision.
- Do not represent the rules as actual bank lending policy.

## 6. Loan Decision

- Only authorized loan officers may approve or reject applications under review.
- Rejection must include a reason.
- Applications in invalid states must not be approved.
- Every decision must be recorded in audit history.

## 7. Disbursement and Repayment

- Simulate disbursement only for approved applications.
- Generate an EMI repayment schedule using the principal, annual interest rate, and tenure.
- Record simulated repayments against an existing loan.
- Reject duplicate payment references.
- Prevent repayment amounts from exceeding the permitted outstanding balance.
- Close a loan only when all required repayment obligations are settled.

## 8. API Requirements

The backend will expose documented APIs for:

- Customer registration
- Mortgage application submission and retrieval
- Eligibility evaluation
- Loan decision
- Simulated disbursement
- Repayment recording
- Loan status and repayment schedule retrieval

Each API must validate input and return appropriate success or error responses. Authorization must be enforced on the server.

## 9. UI and Automation Requirements

- Provide screens for registration, application submission, document status, and loan tracking.
- Automate critical workflows using TypeScript and Playwright.
- Cover positive, negative, boundary, and authorization scenarios.
- Validate important API responses and database results where appropriate.
- Keep test data repeatable and avoid real customer information.

## 10. Performance and CI/CD

- Use JMeter to evaluate selected API workloads.
- Document test environment, workload, response times, error rates, and limitations.
- Run suitable automated tests through GitHub Actions.
- Store useful test reports and diagnostic artifacts without exposing secrets.

## 11. Future AI and MCP Extension

A later project phase may use Python and MCP to assist with test-case generation or test-failure analysis. AI-generated results must be reviewed and validated before use.

## 12. Acceptance Criteria

The implementation must demonstrate that:

1. Valid customers can register and duplicate emails are rejected.
2. Valid applications receive unique references.
3. Invalid application inputs are rejected.
4. Eligibility results follow documented configuration.
5. Only authorized officers can make loan decisions.
6. Disbursement cannot occur before approval.
7. EMI calculations match independently verified examples.
8. Duplicate repayments are rejected.
9. Outstanding balances and loan closure are