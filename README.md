# Disputes on mobile: a concept for the Razorpay app

A concept prototype that lets small sellers respond to card payment disputes from the Razorpay app.

Built for the Razorpay x ISB Build Challenge, Track 1: Razorpay in Your Pocket.

- **Demo video:** ADD_VIDEO_LINK
- **Technical notes:** [ARCHITECTURE.md](ARCHITECTURE.md)

## The problem

When a customer disputes a card payment, Razorpay holds the disputed amount from the seller's balance. The seller is told by email and has 3 working days to respond, or the dispute is lost automatically. Disputes can only be handled on the Razorpay website. Small sellers run their business from their phone, and the courier slip, parcel photos and customer chats are all on that phone.

## Who it is for

Small online sellers who take card payments through Razorpay payment links: Instagram sellers, home businesses and small D2C brands. The demo uses Hook & Yarn, a made-up crochet business.

## The flow

1. **When the order ships (about 5 seconds):** for card payments above an amount the seller chooses, the app asks "Shipped? Add proof." The seller photographs the courier slip and parcel, or shares the customer chat. The files are saved against that payment.
2. **When a dispute is raised:** an alert shows the amount on hold and the respond-by date. Tapping it opens the dispute.
3. **Dispute screen:** the status, amount, a countdown, a status tracker (Open, Under review, Won or Lost) and the customer's reason in plain words.
4. **Contest:** a checklist of the proof needed for this type of dispute. Saved files are already filled in and missing items are flagged. The seller can contest the full amount or part of it.
5. **Partial disputes:** the seller picks the photos that show the disputed item (in the demo, ₹1,400 of a ₹4,200 order).
6. **Explanation, review and submit.** The status moves to Under review. If the customer is right, the seller can accept the dispute instead.
7. **Final decision:** when the bank decides, the seller gets an alert. Home shows Won or Lost until the seller taps "Got it", and the payment keeps a "Final" line.
8. **Disputes tab:** under Payments, every dispute is grouped into Needs a response, Under review and Final decision.

## Key decisions

- **Collect proof at shipping.** It is easiest to get then, and 3 working days is a short window.
- **Keep it in the existing app.** Disputes sit as a third tab under Payments, next to Transactions and Settlements, with an alert on Home. Nothing else in the app changes.
- **Use a checklist for each dispute type.** Banks ask for different proof for different reasons.
- **Show the outcome on the payment and on Home.** Today a payment only shows Captured or Failed, and the result of a dispute sits in a separate section.
- **Flag weak proof.** For some dispute types banks prefer email or invoice records over WhatsApp chats, so the app suggests adding the invoice.
- **Make accepting as easy as contesting.** Fighting a fair claim takes time and can add fees.
- **Follow Razorpay's existing dispute rules** for statuses, evidence types, partial contest and the explanation field.

**Left out on purpose:** later dispute stages (pre-arbitration and arbitration), fraud disputes, bulk handling for large merchants, auto-written explanations and Settle Now.

## Next steps

Talk to 5 to 10 sellers about missed disputes and whether the shipping prompt helps. Later, read the tracking number from the courier slip photo and fetch delivery status automatically.

## Trying the prototype

On a laptop, the phone sits next to a demo guide with a timer and buttons for the bank's decision. On a phone, the app fills the screen. All data is made up.

## How it was built

I built this with Claude (Anthropic), working from my product note, my flow and screenshots of the Razorpay app, and then reviewed and edited it myself. More detail is in the AI build log submitted with the challenge.

This is not an official Razorpay product.
