# action-repo

This repository is created as part of the Developer Assessment task.  
Its sole purpose is to act as a **dummy GitHub repository** that generates GitHub events using **GitHub Webhooks**.

The events triggered in this repository are sent to a webhook endpoint implemented in the `webhook-repo`.

---

## Purpose of This Repository

This repository is used only to **generate GitHub events** such as:

- Push
- Pull Request
- Merge (via merged pull requests)

No backend or UI logic is implemented here.  
All processing, storage, and display of events is handled by the `webhook-repo`.

---

## GitHub Events Generated

### 1. Push Event
Triggered when code is pushed to any branch in this repository.

Example:
```bash
git push origin main
2. Pull Request Event
Triggered when a pull request is created or closed between branches.

Steps:

Create a new branch

Push changes

Open a pull request to another branch

3. Merge Event (Brownie Points)
Triggered when a pull request is merged.

Note: GitHub does not provide a separate merge webhook event.
A merge is identified using the pull_request webhook payload where:

pull_request.merged == true
Webhook Configuration
A GitHub webhook is configured for this repository with the following details:

Payload URL

<public-url>/webhook
Content Type

application/json
Subscribed Events

Pushes

Pull requests

The public URL is exposed using tools like ngrok during local development.

How This Repository Works in the Assignment Flow
Actions (push, pull request, merge) are performed in this repository.

GitHub sends webhook events to the configured endpoint.

The webhook endpoint (in webhook-repo) receives and stores the event data in MongoDB.

The UI polls the database every 15 seconds to display the latest repository activity.

Related Repository
webhook-repo
Contains the Flask webhook receiver, MongoDB integration, and UI for displaying the repository events.

Notes
This repository contains no application logic.

It exists only to trigger GitHub webhook events.

All core implementation is handled in the webhook-repo.
