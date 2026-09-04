# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Goal

Evaluate an AI Support Classifier using Promptfoo and corporate Amazon Bedrock Claude.

## Project Overview

This is a **Promptfoo evaluation project** that tests an AI support ticket classifier. The system uses Claude Haiku 4.5 (via AWS Bedrock) to analyze incoming support messages and classify them by category (BUG, BILLING, FEATURE, QUESTION) and priority (CRITICAL, HIGH, LOW).

## Source Files

- `homework_requirements.md` — **Source of truth** for business rules. Specifies category definitions, priority levels, and edge cases (e.g., sarcasm should not inflate priority, feature requests are always LOW priority).

- `tests.csv` — Test input and expected outputs. Format: `user_message, expected_category, expected_priority`

- `prompt.txt` — The prompt under test (the LLM prompt for the support classifier).

- `promptfooconfig.yaml` — Promptfoo configuration, Bedrock provider settings, and assertion configuration.

## Common Commands

**Run the evaluation:**
```bash
promptfoo eval
```

**View results in browser:**
```bash
promptfoo view
```

**Environment Setup:**
- AWS credentials must be configured (Bedrock access in us-east-1)
- `.env` or `.env.local` can be used for AWS configuration if needed (see `.gitignore`)

## GitHub Workflow

- **Before changing files:** explain the plan and list files to be changed.
- **Work on non-main branches:** create feature branches for all work.
- **Commit discipline:** use small, logical commits with Conventional Commit messages.
- **Before each commit:** run `git status` and `git diff` to review changes.
- **Never commit:** secrets, AWS credentials, tokens, `.env` files, or corporate configuration.
- **Never force-push:** preserve branch history.
- **Amending published commits:** requires explicit approval.
- **Push and PRs:** require explicit approval before proceeding.
- **After completing a task:** propose a commit message and wait for approval.
- **Root-cause first:** do not change expected CSV values merely to make an evaluation pass; analyze failures first.

## Bedrock Safety

- **No unprompted external calls:** do not run `promptfoo eval`, invoke Bedrock, or make paid external calls without explicit approval.
- **Show intent before eval:** before running an eval, display the intended command and expected number of model calls.
- **Credentials from environment only:** use AWS credentials only from the terminal environment or AWS profile, never from repository files.

## Validation

- **Static validation:** validate YAML/static configuration where possible before commits.
- **Post-eval analysis:** after an eval, record pass/fail results and analyze failures before modifying prompt or tests.
