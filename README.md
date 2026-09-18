# Insurance Premium Billing & Collections Reconciliation

## Overview

A simulated insurance premium billing and collections reconciliation project, built to demonstrate the core day-to-day work of a Surety/Premium Collections Analyst: monitoring outstanding receivables, reconciling payments against invoices, and producing aging reports that identify which accounts need follow-up.

The dataset is fully simulated — 10 agencies, 50 policies, and three months of billing — with realistic payment behavior built in: some agencies pay reliably, some pay late, and some consistently pay short. The project reconciles every invoice against actual payments received and classifies outstanding balances by how many days past due they are.

## Business Problem

Insurance carriers and MGAs rely on agencies to remit premium payments on time and in full. When payments are late, short, or missing, outstanding receivables build up — and identifying which accounts are past due, by how much, and for how long is the core function of a collections/reconciliation team. This project builds that reconciliation and aging process from raw billing and payment data.

## Tools

Python | Pandas | NumPy | SQL | SQLite | Excel (PivotTables, XLOOKUP, Data Validation)

## Dataset

Simulated data generated in `notebook/data_generation.ipynb`:

- **10 agencies**, each assigned a payment behavior profile (reliable, slow, problem)
- **50 policies** across three lines of business: Commercial Auto, General Liability, Commercial Property
- **150 invoices** billed monthly from June–August 2026
- **Payments** simulated per invoice as on-time, late, or short, with probability driven by each agency's payment profile

## What I Built

### 1. Data Generation (`notebook/data_generation.ipynb`)
Built four related tables (agencies, policies, invoices, payments) with realistic billing and payment simulation logic, then reconciled billed vs. paid amounts to calculate outstanding balance, payment status (Paid / Current / Past Due), and aging bucket (1-30 / 31-60 / 60+ days past due) for every invoice.

### 2. SQL Analysis (`notebook/sql_analysis.ipynb`)
Used SQL (SQLite) to answer collections-focused business questions:
- Aging summary by bucket
- Top past-due agencies by outstanding balance
- Payment behavior by scenario (on-time, late, short)
- Status and line-of-business breakdowns

### 3. Python Analysis (`notebook/python_analysis.ipynb`)
Visualized the aging summary and top past-due agencies using Pandas and Seaborn.

### 4. Excel Reconciliation Workbook (`Excel/insurance_premium_reconciliation.xlsx`)
- **Reconciliation sheet** — full invoice-level data with calculated balance, status, and aging bucket
- **Agencies sheet** — lookup table joined via XLOOKUP to pull agency names into the reconciliation view
- **Aging Summary PivotTable** — balance and invoice count broken out by aging bucket and agency

## Key Findings

- **150 invoices** were reconciled: 108 Paid, 42 Past Due
- Outstanding balance by aging bucket: **1-30 Days: $40,205** (21 invoices) · **31-60 Days: $15,858** (11 invoices) · **60+ Days: $6,448** (10 invoices)
- **Commercial Auto and Commercial Property** together account for the large majority of past-due balance ($27,850 and $24,849 respectively), while General Liability accounts for far less ($9,813) despite having fewer invoices overall
- Agencies flagged with "problem" or "slow" payment profiles were, as designed, disproportionately represented in the past-due and aging totals — confirming the reconciliation logic correctly surfaces at-risk accounts


## Purpose

This project demonstrates practical skills directly relevant to premium billing, accounts receivable, and collections roles: building and validating a reconciliation process from raw billing/payment data, writing SQL to answer collections-specific business questions, and producing an aging report and Excel workbook of the kind used daily in real receivables management.
