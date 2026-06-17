Demo Service Activation API

This repo holds the Demo Service Activation API and the automation that onboards it into Postman.

It is part of a set of demo services (customer, billing, and service activation) used to show how a single workflow can create a fully structured Postman workspace from an OpenAPI spec.

What's in here


open-api-specs/demo-service-activation-api-openapi.yaml is the OpenAPI spec, the single source of truth for this service.
.github/workflows/onboard.yml is the workflow that reads the spec and provisions everything in Postman.


What the workflow does

When it runs, the workflow creates a complete Postman workspace for this service:


The spec, uploaded to Postman Spec Hub
Three test collections: baseline (every endpoint), smoke (a quick health check), and contract (verifies the live API still matches the spec)
Two environments, prod and staging, holding the runtime URLs
A weekly monitor that runs the contract tests on a schedule to catch spec drift


It also registers the service in the Postman API Catalog and commits the generated assets back into this repo.

How it runs

The workflow runs in two ways:


Automatically, whenever the spec under open-api-specs/ changes on the main branch.
Manually, from the Actions tab using the Run workflow button.


Per-service configuration

Onboarding a new service only requires changing five values in the workflow file: the project name, the domain, the domain code, the spec path, and the environment runtime URLs. Everything else stays the same.

Required secrets

Three secrets must be set in the repo (Settings > Secrets and variables > Actions):


POSTMAN_API_KEY for Postman operations
POSTMAN_ACCESS_TOKEN for governance and workspace linking
GH_FALLBACK_TOKEN for committing generated assets back to the repo


Note

This is a demonstration service. The runtime URLs are placeholders and do not point at a live API.
ShareProject contentCSECreated by youcontext-transfer.md194 linesmdContentREADME (2).mdmdREADME (1).mdmdopenapi: 3.0.3
info:
  title: Payment Processing API - Refund Service
  description: |
    Comprehensive API for managing payment refunds in a financial services platform.
    This API handles refund creation, status tracking, cancellation, and reporting for
    payment transactions processed througpasted# Payment Refund API — Postman Onboarding

This repo contains the automated Postman onboarding workflow for FinServCo's 
Payment Refund API service.

---

## What This Does

Triggering this workflow automatically creates a fully structured Postman 
workspace for the Payment Refund API, including:

-pasted# Postman GitLab Spec Sync Starter

This is a sanitized starting point for a GitLab customer who wants to bring a large OpenAPI estate into Postman from GitLab CI. It intentionally uses placeholder names, placeholder CI variables, and generic paths so it can be shared without customer-specific workspasted---
title: Authenticate with OAuth 2.0 authentication in Postman
approved: 2025-10-31T00:00:00.000Z
max-toc-depth: 2
ux: v12
topictype: multiple
---

With OAuth 2.0, you first retrieve an access token for the API, then use that token to authenticate future requests. Access tokens are typically shortpastedPostman GitLab Spec Sync Starter
This is a sanitized starting point for a GitLab customer who wants to bring a large OpenAPI estate into Postman from GitLab CI. It intentionally uses placeholder names, placeholder CI variables, and generic paths so it can be shared without customer-specific workspacpastedAutomated OAS Ingestion for Postman via AWS API Gateway
Automated workflow to sync OpenAPI specifications from AWS API Gateway to Postman Spec Hub, generating collections and environments for API testing and documentation.

Quick Start
Prerequisites
Node.js v18+ installed
AWS CLI configured with valpasted[0:00 to 0:15] Intro
Hi guys, this is Josh from the Customer Success Engineering team here at Postman. Today I'm going to demo a workflow some of our more mature customers have started to adopt to automate deploying a best-in-class Postman workspace.
[0:15 to 0:35] The problem
Most customers we workpasted
