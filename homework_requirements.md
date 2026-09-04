# AI Support Classifier Requirements

## Overview
The AI assistant must analyze incoming support tickets and assign exactly one CATEGORY and one PRIORITY. 

## Categories
1. BUG: The system is not working as expected, throwing errors, or crashing.
2. BILLING: Issues related to payments, subscriptions, invoices, or refunds.
3. FEATURE: User requests new functionality, UI changes, or enhancements.
4. QUESTION: General inquiries, how-to questions, or asking for documentation.

## Priorities
1. CRITICAL: Complete system outage, data loss, security breaches, or users completely unable to pay.
2. HIGH: Core functionality is broken, but a workaround exists. Login issues for individual users.
3. LOW: Minor UI bugs, typos, general questions, and all feature requests.

## Rules
- If a ticket involves a BUG and BILLING, categorize it as BILLING but assign priority based on the severity of the bug.
- Sarcasm or emotional language should not artificially inflate the Priority. Evaluate the actual technical issue.
- Feature requests can never be higher than LOW priority, regardless of how angry the user is.
