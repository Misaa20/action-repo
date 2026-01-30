# action-repo-

This repository acts as the **event source** for the Developer Assessment Task.  
It is responsible for triggering GitHub webhook events on specific repository actions.

These events are sent to a registered webhook endpoint (`webhook-repo`) where they are processed and stored in MongoDB.

---

## Purpose-

The goal of this repository is to generate GitHub events with **minimal and relevant data** that can be consumed by an external webhook receiver.

This repository itself does not contain any backend or UI logic.

---

## Supported GitHub Events-

The following GitHub events are enabled for this repository:

- **Push**
- **Pull Request**
- **Merge** (via merged pull requests)

Each action triggers a webhook payload sent by GitHub.

---

## Event Semantics-

The webhook payloads generated from this repository are later transformed into human-readable logs such as:

### Push Event

{author} pushed to {to_branch} on {timestamp}


### Merge Event

{author} merged branch {from_branch} to {to_branch} on {timestamp}


---

## Webhook Configuration

GitHub Webhooks for this repository are configured with:

- **Payload URL**: Webhook endpoint from `webhook-repo`
- **Content Type**: `application/json`
- **Events**:
  - Push events
  - Pull request events

GitHub automatically sends HTTP `POST` requests to the webhook endpoint whenever one of the above actions occurs.

---

## How It Works

1. A developer performs an action on this repository
2. GitHub emits a webhook event
3. The event is sent to the Flask webhook receiver
4. The receiver extracts required fields and stores them in MongoDB
5. The UI polls MongoDB every 15 seconds to display updates

---

## Related Repository

- **webhook-repo**  
  Contains the Flask-based webhook receiver that:
  - Handles incoming GitHub webhook events
  - Stores processed data in MongoDB
  - Serves data for UI polling

---

## Notes

- No application code is required in this repository
- This repository exists solely to emit GitHub events
- All business logic lives in the webhook receiver

---

## Era

Developer Assessment Submission

