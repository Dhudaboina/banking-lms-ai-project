# Loan Lifecycle and Business Workflow

**Project:** Banking Loan Management System  
**Document ID:** LMS-WF-001  
**Version:** 1.0  
**Status:** Draft

## 1. Purpose

This document defines the end-to-end loan lifecycle, application statuses, permitted transitions, business rules, and validation scenarios for the Banking Loan Management System.

## 2. End-to-End Workflow

1. Customer registers with valid information.
2. Customer submits a loan application.
3. The system validates the application fields.
4. The system evaluates configured eligibility rules.
5. The loan officer reviews the application.
6. The loan officer approves or rejects the application.
7. An approved application is converted into a loan record.
8. Disbursement is simulated.
9. The system generates the EMI repayment schedule.
10. Simulated repayments are recorded and balances are updated.
11. The loan is closed when all required repayments are completed.

## 3. Application and Loan Statuses

### Application statuses

- SUBMITTED: Application has been received.
- UNDER_REVIEW: Application is being reviewed.
- APPROVED: Application has been approved.
- REJECTED: Application has been rejected with a reason.

### Loan statuses

- DISBURSED: Disbursement has been simulated.
- ACTIVE: The loan has an ongoing repayment obligation.
- OVERDUE: At least one instalment is overdue.
- CLOSED: All required repayment obligations are completed.

## 4. Permitted Status Transitions

| Current Status | Next Status | Condition |
|---|---|---|
| SUBMITTED | UNDER_REVIEW | Application is valid |
| UNDER_REVIEW | APPROVED | Authorized officer approves |
| UNDER_REVIEW | REJECTED | Authorized officer rejects with reason |
| APPROVED | DISBURSED | Loan record is created and disbursement is simulated |
| DISBURSED | ACTIVE | Loan becomes active for repayment |
| ACTIVE | OVERDUE | An instalment becomes overdue |
| OVERDUE | ACTIVE | Overdue obligations are resolved and no instalment remains overdue |
| ACTIVE | CLOSED | All required repayments are completed |
| OVERDUE | CLOSED | All required repayment obligations, including applicable overdue amounts, are settled |

Any transition not listed above must be rejected unless an explicitly documented business rule permits it.

## 5. Core Business Rules

**WF-001:** Applications must have a unique application reference.

**WF-002:** Only authorized loan officers may approve or reject applications.

**WF-003:** Rejected applications must include a rejection reason.

**WF-004:** Rejected applications cannot proceed directly to disbursement.

**WF-005:** Disbursement can be simulated only for approved applications.

**WF-006:** Repayment records must reference an existing loan.

**WF-007:** Duplicate payment references must be rejected.

**WF-008:** A loan cannot be closed while required repayment obligations remain outstanding.

**WF-009:** Important status changes must be recorded in audit history.

## 6. Exception Scenarios

- Missing mandatory customer information.
- Invalid loan amount or tenure.
- Unauthorized approval attempt.
- Approval attempted for an already rejected application.
- Disbursement attempted before approval.
- Repayment submitted for a nonexistent loan.
- Duplicate payment reference.
- Loan closure attempted with an outstanding balance.

## 7. Initial Test Scenarios

**TC-LIFE-001:** Submit a valid loan application and verify SUBMITTED status.

**TC-LIFE-002:** Move a valid application to UNDER_REVIEW.

**TC-LIFE-003:** Approve an application as an authorized loan officer.

**TC-LIFE-004:** Reject an application without a reason and verify validation failure.

**TC-LIFE-005:** Attempt to disburse a rejected application and verify rejection of the operation.

**TC-LIFE-006:** Record a valid simulated repayment and verify the updated balance.

**TC-LIFE-007:** Submit a duplicate payment reference and verify that no duplicate repayment is recorded.

**TC-LIFE-008:** Attempt to close a loan with an outstanding balance and verify that closure is blocked.

## 8. Audit Requirements

Audit records should capture the entity, previous status, new status, timestamp, and authorized actor for important changes. Sensitive information must not be unnecessarily exposed in logs.

## 9. Scope Note

This workflow is an educational simulation. Actual bank workflows, regulatory controls, approval policies, and repayment rules vary by institution and must not be inferred from this project.
