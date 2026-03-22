# AGENTS.md - Paperclip Local Working Guide

This repository is the Paperclip platform monorepo. Treat it as the upstream or platform-core workspace for AI-agent-company infrastructure, not as the place for business-specific clutter that belongs in `retailAI`.

## Goal

- understand, run, and extend the Paperclip platform responsibly
- keep platform work distinct from company-specific implementations
- use this repo for core control-plane capabilities, not for every downstream customization

## Current Idea And Progress

- Product idea:
  a control plane for AI-agent companies
- Current state:
  active monorepo with server, CLI, packages, docs, Docker, and database workflows
- Local role:
  platform-core reference and extension point
- Current product maturity:
  significant implementation already exists; this is not a greenfield repo

## Read First

Before substantial work, read:

1. `doc/GOAL.md`
2. `doc/PRODUCT.md`
3. `doc/SPEC-implementation.md`
4. `doc/DEVELOPING.md`
5. `doc/DATABASE.md`

## Initial Setup Requirements

- Node.js 20+
- `pnpm`
- Docker
- local Postgres via Docker Compose
- recommended commands:
  `pnpm install`
  `docker compose up -d db`
  `pnpm dev`

## Environments

- local development:
  monorepo dev runner plus local database
- quickstart / dockerized local environment:
  use the provided compose files
- untrusted review / smoke flows:
  use the dedicated Docker assets where appropriate
- production:
  separate deployment concern, not something to improvise casually from the root

## Dependencies

- pnpm workspace packages
- Node / TypeScript toolchain
- Postgres
- Docker and compose-based local infrastructure
- platform docs in `doc/`

## Backend Need

- backend required:
  yes
- backend shape:
  server-side platform services backed by Postgres and supporting packages
- root-level truth:
  this repo is backend-meaningful; do not treat it as frontend-only

## Backend Development Plan

1. Preserve the documented platform architecture.
2. Keep schema and migration work disciplined.
3. Add or change services only with a clear product need and corresponding docs.
4. Keep platform concerns here and move company-specific policies to `retailAI`.
5. Prefer upstream-compatible or platform-wide improvements over bespoke hacks.

## How Development Should Progress

1. Use the root docs as the contract.
2. Keep the monorepo understandable and package boundaries clean.
3. Avoid embedding project-specific business logic that should live elsewhere.
4. Strengthen onboarding, observability, and deployment reliability before adding speculative features.
5. If your own company implementation diverges heavily, move that work into the dedicated companion repo.

## Relationship To retailAI

- `paperclip`:
  platform core
- `retailAI`:
  your business-specific company layer

Keep that separation explicit.

## End Goal

The end goal is a clean, operable Paperclip platform workspace that can either track upstream closely or support careful platform-level extension, while your own company-specific implementation lives beside it instead of inside it.
