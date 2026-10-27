# Business Requirements Document (BRD)

**Project:** Banking Loan Management System  
**Document ID:** LMS-BRD-001  
**Version:** 1.0  
**Status:** Draft

## 1. Purpose

The purpose of this project is to develop an educational Banking Loan Management System that simulates the loan lifecycle, including customer registration, loan applications, eligibility validation, loan decisions, EMI calculations, and repayment tracking.

## 2. Business Problem

Managing loan applications requires accurate customer information, consistent eligibility checks, controlled approval workflows, repayment calculations, and traceable records.

This project will simulate these activities in one application to demonstrate banking domain knowledge and software engineering practices.

## 3. Project Objectives

- Develop a loan application workflow.
- Validate customer and loan information.
- Implement configurable eligibility rules.
- Support loan approval and rejection.
- Calculate monthly EMIs and repayment schedules.
- Record simulated repayments and outstanding balances.
- Maintain audit history for important operations.
- Validate application quality through functional, API, UI, and performance testing.

## 4. User Roles

### Customer
- Register and maintain permitted customer information.
- Submit a loan application.
- View application status and repayment details.

### Loan Officer
- Review submitted applications.
- Review eligibility results.
- Approve or reject applications with appropriate authorization.
- View loan and repayment information.

### Administrator
- Manage permitted user access and configurable system rules.
- Review audit history and system records.

## 5. Functional Requirements

**FR-001: Customer Registration**  
The system shall validate required customer information and create a unique customer record.

**FR-002: Loan Application**  
The system shall accept valid loan applications and assign a unique application reference.

**FR-003: Eligibility Validation**  
The system shall evaluate applications using documented, configurable educational rules.

**FR-004: Loan Decision**  
Authorized loan officers shall be able to approve or reject applications. Rejections shall include a reason.

**FR-005: EMI Calculation**  
The system shall calculate monthly instalments using the principal, annual interest rate, and loan tenure.

**FR-006: Repayment Management**  
The system shall maintain repayment schedules and record simulated payments without processing real money.

**FR-007: Status Tracking**  
The system shall display the current application or loan status to authorized users.

**FR-008: Audit History**  
The system shall record important changes, including loan decisions and repayment updates.

## 6. Non-Functional Requirements

- Validate inputs on the server.
- Enforce appropriate role-based access.
- Protect passwords and sensitive configuration.
- Store monetary values using appropriate decimal types.
- Prevent duplicate repayment references.
- Support repeatable functional and performance testing.
- Maintain documentation and version history.

## 7. Project Scope

**Included:** Loan applications, eligibility rules, approvals, EMI calculations, simulated repayments, audit history, testing, Jira defect management, JMeter performance testing, CI/CD, and planned AI/MCP integration.

**Excluded:** Real payment processing, live credit bureau integration, actual lending decisions, and production banking integrations.

## 8. Acceptance Criteria

The initial system will be considered functionally ready when valid applications can be submitted, invalid inputs are rejected, authorized users can make loan decisions, EMI calculations are verified, simulated repayments update balances correctly, and documented automated tests pass.

## 9. Assumptions

The project uses fictional customers, configurable educational business rules, and simulated financial transactions. Performance targets will be established and evaluated through documented tests.

## 10. Risks

- Incorrect financial calculations.
- Invalid status transitions.
- Unauthorized access.
- Duplicate repayments.
- Inadequate test coverage.
- Performance degradation under concurrent requests.

These risks will be addressed through design reviews, automated testing, access controls, and performance analysis.
