# Project Architecture

**Project:** Banking Loan Management System  
**Document ID:** LMS-ARCH-004  
**Version:** 1.0  
**Status:** Draft

## 1. Overview

The Banking Loan Management System is an educational application that simulates the mortgage lending lifecycle. It separates the user interface, backend business logic, database, and QA automation framework.

## 2. Architecture Components

### 2.1 Frontend

The frontend provides screens for:

- Customer registration and login
- Mortgage application submission
- Document status tracking
- Loan application status
- Repayment schedule and loan balance

The frontend communicates with the backend through HTTP APIs.

### 2.2 Backend

**Technology:** Java and Spring Boot

The backend is responsible for:

- Request validation
- Customer and application management
- Eligibility evaluation
- Role-based authorization
- Loan approval and rejection
- EMI and repayment calculations
- Simulated disbursement
- Audit history

Business rules must be enforced on the server, not only in the frontend.

### 2.3 Database

**Technology:** PostgreSQL

Planned data entities include:

- Customers
- Users and roles
- Loan applications
- Documents and document statuses
- Loans
- Repayment schedules
- Repayment transactions
- Audit records

Monetary values must use suitable decimal types. Database constraints should protect data integrity.

### 2.4 QA Automation Framework

**Technology:** TypeScript and Playwright

The framework will support:

- UI automation
- API testing
- Positive and negative scenarios
- Boundary-value validation
- Authorization testing
- Test data management
- Reusable fixtures and utilities
- HTML test reports and failure diagnostics

### 2.5 Performance Testing

**Technology:** Apache JMeter

JMeter will exercise selected backend APIs under a documented workload. Results will include response times, throughput, error rates, and test limitations.

### 2.6 CI/CD and Version Control

**Technologies:** Git, GitHub, and GitHub Actions

GitHub will store source code, documentation, and test assets. GitHub Actions will run suitable automated checks and publish useful test reports.

### 2.7 Future AI Extension

Python and MCP may later support AI-assisted test-case generation and test-failure analysis. Generated suggestions must be reviewed before being used.

## 3. High-Level Data Flow

1. A customer interacts with the frontend.
2. The frontend sends an HTTP request to the Spring Boot backend.
3. The backend validates the request and enforces authorization.
4. The backend applies business rules and reads or updates PostgreSQL.
5. The backend returns an appropriate response.
6. Playwright verifies the UI and API behavior.
7. SQL checks validate selected persisted results.
8. GitHub Actions executes automated checks during CI.

## 4. Quality and Security Principles

- Validate inputs on the server.
- Enforce authorization on protected operations.
- Never store passwords in plain text.
- Do not expose secrets or sensitive information in logs.
- Keep tests repeatable and use fictional test data.
- Verify financial calculations with independent examples.
- Record important status changes in audit history.
- Prevent duplicate repayment references.

## 5. Architecture Scope

This architecture is a planned design for an educational project. Components will be implemented incrementally, and this document will be updated when implementation decisions change.

Real payment processing, credit bureau integrations, and production banking services are out of scope.