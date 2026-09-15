# rasa-chatbot

A conversational triage and store-request assistant built for pet/livestock owners, developed for **Codictive 2.0**, the state-level Idea Hackathon organized by Bansal Institute of Science & Technology (Bhopal) in collaboration with Coding Thinker — April 2024.

## What it does

The bot handles four flows for an animal owner:

- **Contact doctors/officials** — routes the user toward a human vet or relevant official rather than attempting any diagnosis itself.
- **Request products** — accessories, food, or medicine, collecting the specific details needed to fulfill the request. This is the store layer that came out of early user research: vets were willing to review reports at low cost, but that left no margin for the team, so the store became the actual monetization path.
- **Updates** — lets a user ask for further information.
- **Feedback** — collects open-ended messages from the user.

## Scope, honestly stated

This repository is the conversational/dialogue layer only. The original hackathon concept included an ML model to classify animal symptoms and suggest a diagnosis before handoff to a vet — that model was scoped but not built in the hackathon timeframe. What's implemented here is intake and routing: get the user to the right flow (a human vet, a product request, an update, or feedback), not automated diagnosis. Any vet involved always has final say.

## Stack

- **Rasa Open Source 3.1** — NLU + dialogue management
- Custom actions (Python) — `action_contact_doctors`, `action_store_product_details`, `action_store_update_details`, `action_store_feedback`
- Button-driven dialogue flow defined in `domain.yml`, training data in `data/`

## Structure

```
├── actions/          # custom action implementations
├── data/             # NLU training data, stories, rules
├── config.yml         # Rasa pipeline/policy configuration
├── domain.yml          # intents, responses, slots, custom actions
├── credentials.yml      # channel credentials (placeholder)
└── endpoints.yml         # action server endpoint config
```

## Running it

```bash
pip install rasa
rasa train
rasa run actions      # in one terminal
rasa shell             # in another, to chat with the bot
```

## Status

Built and demoed within a 36-hour hackathon window. Archived as a snapshot of that build — not maintained.
