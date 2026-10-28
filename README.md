# Growth Audit — Photo Recovery

**Live:** https://melikesezer2019-cloud.github.io/photo-recovery-flow-rebuild/

Five ideas to unlock more revenue from the traffic Photo Recovery already has, plus a clickable prototype of the onboarding and paywall rebuilt in Photo Recovery's own design. Prepared by Adapty, based on the live iOS flow and the App Store listing.

## The five ideas

| # | Idea | What it changes | Potential outcome |
| :-- | :-- | :-- | :-- |
| 1 | Offer the free trial when they close | Closing the ₺2,499.99/year paywall opens one second chance: a 3-day free trial on the same yearly plan. | ARPU +10–15% |
| 2 | Ask what they lost, then name it | Two taps (what and when), then the paywall says “Recover Your Deleted Photos” instead of “Recover Deleted Data and Files”. | CR +15–20% |
| 3 | Ask for tracking first, one prompt at a time | Tracking is asked first, photo access second, and notifications move to after the paywall. | CR +5–10% |
| 4 | Put your 8M+ users next to the price | The rating and “8M+ users” move onto the paywall. | CR +10–15% |
| 5 | Show the scan working on their answer | A short scan that names their answer, then the time left in iPhone's 30-day Recently Deleted window. | CR +10–15% |

The prototype has English and Turkish, light and dark, a 30-second walkthrough, and jump chips to open any screen.

## Building idea 3 in Adapty

A flow can't show iOS system prompts itself, but a button's custom action can ask the app to. Give each permission card's button a custom action (`request_att`, `request_photos`, and `request_push` after the paywall), followed by Navigate next. The app shows the matching system prompt when it receives the ID. The order and the cards stay editable from the dashboard. Log the tracking answer as a user attribute to compare opt-in, not just purchases. See [Actions](https://adapty.io/docs/onboarding-actions.md) in the Adapty docs.

## Rebuild it as an Adapty flow

The prototype can be rebuilt as a real Adapty flow in your own account with Claude Code, the [adapty-skills](https://github.com/adaptyteam/adapty-skills) plugin and its `flow-generator` skill.

**Before you start**

- Install the plugin (`claude plugin marketplace add adaptyteam/adapty-skills`, then `claude plugin install adapty-skills@adapty`) and sign the Adapty CLI in to your account.
- Have your weekly and yearly subscriptions, and the 3-day free trial offer, in App Store Connect and connected to Adapty. Prices come from the store, not from the flow.

**Prompt to paste**

```text
Clone https://github.com/melikesezer2019-cloud/photo-recovery-flow-rebuild and open index.html in a browser.
Using the flow-generator skill, rebuild its Prototype view as an Adapty flow for my app <APP NAME>:
- Screens in order: setup, intro slides, what was lost, when, scan, ready, paywall, offer on close, notifications.
- English and Turkish, with the copy from the T table in index.html.
- The paywall headline and the days-left card follow the "what" and "when" answers (conditional text).
- Closing the paywall goes to the offer screen with the 3-day free trial on the yearly plan.
- Permission buttons fire custom actions request_att, request_photos and request_push, then go to the next screen.
- Upload the images in img/ and use my existing weekly and yearly products.
Show me a preview of every screen before publishing, then attach the flow to a new placement.
```

**What stays on your side**

- A handler in the app for `request_att`, `request_photos` and `request_push` that shows the iOS prompt.
- Custom fonts, which are uploaded in the Flow Builder by hand.
- A check of the scan animation on a device; the CLI preview shows one still frame.
- The overview page, side panel, walkthrough and QR code belong to the audit and are not part of the flow.

## Grounding

Impact ranges are Adapty's expected effect from teardowns and A/B tests across subscription apps — not measured lift for Photo Recovery. Every price, rating, quote and claim comes from Photo Recovery's own App Store listing, website and in-app screens.

## Run it locally

```bash
python3 -m http.server 8921
```

Then open http://localhost:8921.
