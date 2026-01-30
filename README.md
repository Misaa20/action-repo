# action-repo

This repository is a **dummy GitHub repository** used to generate GitHub events for the Developer Assessment task.

It is connected to a webhook endpoint hosted in the `webhook-repo` using **GitHub Webhooks**. Any activity performed in this repository triggers webhook events that are captured, processed, and stored by the backend service.

---

## Purpose

The sole purpose of this repository is to **emit GitHub events** such as:

- Push
- Pull Request
- Merge (detected via merged pull requests)

These events are sent to a registered webhook endpoint and later displayed in the UI as part of the assignment.

---

## Events Generated

The following GitHub actions are used to trigger webhook calls:

### 1. Push Event
Triggered when code is pushed to any branch.

Example:
```bash
git push origin main
