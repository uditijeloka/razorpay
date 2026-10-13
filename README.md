# Proof Ready

Contest a payment dispute from your phone in under 2 minutes.

A concept prototype for the Razorpay x ISB Build Challenge, Track 1: Razorpay in Your Pocket.

- **Live prototype:** ADD_VERCEL_LINK
- **Demo video:** ADD_VIDEO_LINK
- **Product note:** ADD_PDF_LINK
- **How it works under the hood:** [ARCHITECTURE.md](ARCHITECTURE.md)

## The problem

When a customer disputes a card payment, the disputed amount is held from the seller's balance. The seller is told by email and has 3 working days to respond, or they lose automatically. Today disputes can only be handled on the Razorpay Dashboard, but small sellers run their business from their phone, and that is where the courier slip, parcel photo and customer chat live.

## Who it is for

Small online sellers who take card payments through Razorpay payment links: Instagram and WhatsApp sellers, home businesses and small D2C brands.

## The flow

1. **When shipping (about 5 seconds):** for card payments above an amount the seller sets, the app asks "Shipped? Add proof." The seller snaps the courier slip and parcel, or shares the customer chat. It is saved against that payment.
2. **When a dispute is raised:** a phone alert says how much is on hold and the respond-by date. Tapping it opens the dispute.
3. **Dispute screen:** status, amount, a live countdown, a status tracker (Open, Under review, Won or Lost) and the customer's reason in plain words.
4. **Contest:** a checklist of the proof that wins this type of dispute. Saved proof is already filled in; missing items are flagged. The seller can contest the full amount or part of it.
5. **Partial disputes:** the seller ticks which photos show the disputed item (here, ₹1,400 of a ₹4,200 order).
6. **Explanation, review, submit.** The status moves to Under review. Or **Accept dispute** if the customer is right.
7. **Final decision:** when the bank decides, the seller gets an alert, Home shows "Won" or "Lost" until they tap "Got it", and the payment keeps a "Final" dispute line.
8. **Disputes tab** under Payments groups every dispute into Needs a response, Under review and Final decision.

## Key decisions

- **Live inside the app sellers already use.** Disputes sit as a third tab under Payments, next to Transactions and Settlements, plus an alert on Home. The rest of the app is unchanged.
- **Collect proof at shipping, not after the dispute.** It is easiest to get then, and the 3-day deadline leaves no time to hunt for it.
- **A checklist per dispute type, not an empty upload box.** Banks ask for different proof for different reasons.
- **Show the dispute's status on the payment and on Home.** Today a payment only shows Captured, Failed and so on, and the dispute's outcome sits in a separate Disputes section that most small sellers never open.
- **Warn about WhatsApp proof.** For some dispute types, banks prefer email or invoice records, so the app suggests adding the invoice.
- **Make Accept dispute an equal option.** Fighting a fair claim wastes time and can add fees if it escalates.
- **Stay close to Razorpay's existing dispute rules** (statuses, evidence types, partial contest, explanation limit), so the feature builds on what already exists.

**Not built on purpose:** later dispute stages (pre-arbitration and arbitration), fraud disputes, bulk handling for large merchants, auto-written explanations, Settle Now.

## Next version

Read the tracking number from the courier slip photo and pull delivery status from the courier automatically, so sellers who skip the shipping prompt are still covered.

## Try it

Open the live link. On a laptop you see the phone next to a demo guide with a timer and buttons to play the bank's decision. On a phone the app fills the screen. All data is synthetic.

## How it was built

Built with Claude (Anthropic) from my product note, flow and Razorpay app screenshots, then reviewed and edited by me. See the AI build log submitted with the challenge.

Not an official Razorpay product.
