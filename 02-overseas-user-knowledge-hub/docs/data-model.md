# Data model (simplified)

## Entities

| Entity | Key fields |
|---|---|
| **Post** | post_id, date, source (user / official), author (hashed), model, model_confidence, intent, sentiment, purchase_stage, topic_tags[], summary, text_original, text_translated, likes, comments |
| **Order** | order_id, date, customer_ref (hashed), model, quantity, country, channel |
| **Ticket** | ticket_id, date, customer_ref, model, category, resolution |
| **Join form** | form_id, date, user_ref, devices, main needs, wanted improvements, beta-test interest |
| **Match** | post_id ↔ order_id, method (username / email / manual), confidence |

## Label scheme

- **Intent (10):** pre-sales inquiry, usage help, after-sales issue, complaint, share experience, suggestion, shipping, beta application, community chat, official announcement.
- **Topic tags (14):** battery & range, fold & carry, power & terrain, braking & safety, comfort & ergonomics, quality & defects, setup & usage, after-sales & service, shipping & packaging, price & value, compliance & certification, use-case needs, competitor comparison, accessories.
- **Sentiment:** positive, neutral, negative, mixed.
- **Purchase stage:** purchased, not purchased, unsure.
- **Model confidence:** high, medium, low (“inferred” models are flagged in the UI).

## Matching rules

1. Exact username match → candidate.
2. Same-name collisions → manual review.
3. When email is available, match on email and upgrade the confidence.
4. Every match stores its method so the UI can show where it came from.

## Sample

[`../sample-data/posts_sample.csv`](../sample-data/posts_sample.csv) contains 31 **synthetic** posts that follow this schema.
