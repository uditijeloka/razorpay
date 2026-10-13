# AI build log

## 1. AI tools and models used

| Tool | Model | Used for |
| --- | --- | --- |
| Claude (Anthropic), in the Claude app | Claude Opus 5.5 | Web research, fact-checking against Razorpay's docs, consolidating my thinking into the product note, building the prototype, the repo docs, and adding animations to my recorded video |
| Gemini (Google) | Gemini research mode | An independent research report on merchant tasks that are hard to do in the Razorpay app |

Other tools, no AI: GitHub, Vercel, macOS screen recording.

I used AI to speed up research and to consolidate and structure my own thinking. The core idea, the product decisions and the demo recording are mine.

## 2. Workflow

**Finding the gap (multi-source research and triangulation)**
I set up the research myself: compare what sellers can do on the Razorpay website versus the app, then look for where merchants struggle. I ran it as two independent passes:
- Claude searched Razorpay's docs, Play Store and App Store reviews, Trustpilot and competitor apps.
- I had Claude write a structured research prompt and ran it in Gemini as a second model.

I then triangulated the two outputs against primary sources (Razorpay's own docs and the review pages). Anything that couldn't be traced to a source was dropped.

**Picking the problem**
Claude shortlisted five merchant tasks. I scored them against filters I defined such as use away from a desk, frequency of use, whether it can be done in 2 minutes and a clear workaround today. Disputes passed all. I dropped Settle Now (a convenience, not a loss) and held payments (the outcome depends on Razorpay's own review). I chose to make "collect proof when the order ships" angle the core of the solution. 

**Product note**
I used Claude to consolidate my research and decisions into a one-page note. I directed several rounds of revisions: removing an AI-suggested persona in favour of a merchant segment, rewriting, applying better designs, adding a "How I found this problem" section, and adding risks and why the idea matters to Razorpay.

**Prototype (spec first, then build)**
I wrote the requirements and had Claude generate the code: a single static HTML, CSS and JavaScript file with no backend. Before each major change I asked for a written plan, reviewed it, then approved the build. I grounded the design in two references I supplied: Razorpay's disputes documentation for the logic, and App Store screenshots of the Razorpay app for the look.

**Demo video**
I recorded the demo myself, with my own clicks and voice. Afterwards I used Claude only to add an animated opening, an ending and one confetti moment, keeping my recording, audio and timing unchanged.

## 3. Key prompts

| Prompt (paraphrased) | Effect |
| --- | --- |
| "Here are Gemini's exact sources for these figures" | Forced a re-check against the primary source (section 4) |
| "See how disputes work in Razorpay's docs. It should have statuses. Make the theme match the Razorpay app. Before building, list every change you will make." | Prototype grounded in Razorpay's real dispute model and UI, with a plan reviewed before any code |
| "Keep the timer outside the app" | Demo instrumentation separated from the product UI |
| "The final decision isn't visible on Home. Research whether Razorpay shows these statuses today, and if not, add them." | Found a real product gap and designed for it |
| "Go through every file. Flag anything that might not be factually correct." | A review pass to remove hallucinations |

## 4. AI outputs I corrected

**Main example: the ₹3,000 "penalty"**

- **What the AI said:** Gemini reported that sellers face "penalties up to ₹3,000 or $675" for missing the dispute deadline. When I asked Claude to verify, it said the figures had no source.
- **What I did:** I went back to Gemini for its exact citations and asked Claude to check them against the primary source.
- **What was true:** Razorpay's Chargeback Fees and Penalties page confirmed the 3 working-day window and the automatic loss. The ₹3,000 and $675 figures exist, but they are arbitration fees, charged only if a dispute escalates to its final stage. There is no fee at the first stage.
- **Why it mattered:** one model misattributed a real number and the other wrongly dismissed it. Using either output unchecked would have put a false claim in my submission. I kept "3 working days, or automatic loss" as the core problem and never call ₹3,000 a penalty for missing the deadline. I also dropped Gemini's competitor comparison table, since none of its cells could be traced to a competitor source.

**Other corrections**

| AI output | Problem | What I changed |
| --- | --- | --- |
| A "Disputed" status on payments in the prototype | Razorpay payments only have Created, Authorized, Captured, Refunded or Failed. The status was invented. | The payment keeps its real status, with a separate dispute line underneath |
| "₹1,400 taken back from your balance" | Razorpay's docs disagree on when the amount is deducted | Changed to "on hold", which is accurate either way |
| Auto-detecting shipping by reading courier SMS or WhatsApp messages | Phone platforms restrict apps from reading these | Reframed as reading the tracking number from the courier slip photo |
| Track 1 explanation said the brief requires "one person" and "don't touch the rest of the app" | Neither line was in the brief | Checked the brief's actual wording before designing |
| A persona ("Priya") in the product note | Felt invented and generic | Replaced with a merchant segment |
| Video suggestions: louder voice, cropped browser, auto-zooms | Didn't fit how I wanted the demo to feel | Kept my recording as is and only added the opening, ending and confetti |

## 5. What AI did versus what I did

- **AI:** gathered and summarised sources, generated the prototype code from my specs, drafted documents from my notes, and ran automated checks.
- **Me:** chose the problem and the core idea, set the research method and filters, verified every claim, defined the flow and product decisions, directed every revision, and recorded the demo.

## 6. AI-related limitations, risks and verification

**Limitations**
- **Hallucination and misattribution:** both models produced at least one wrong or misframed claim (section 4). Nothing went into the submission without a primary source.
- **Source coverage:** AI web search returned only a sample of app store reviews and could not read X or LinkedIn posts, so the review evidence is partial and leans towards unhappy users. It is not a substitute for talking to sellers, which is my first next step.
- **Conflicting docs:** where Razorpay's own pages disagree, AI can't resolve which is current. I used wording that holds under both.
- **Prototype code:** AI-generated, single-file and demo-grade, with no tests, backend or production security. It shows the flow and is not a starting codebase.

**Risks**
- **Generic output:** AI tends to give similar names, phrasing and layouts to everyone. I ran a dedicated review pass to replace the AI-suggested product name, sample business and stock phrases.
- **Over-trust:** a confident AI answer can feel verified when it isn't. I treated every number and claim as unverified until I matched it to a source.

**Verification steps**
- **Cross-model triangulation:** compared Claude and Gemini outputs and resolved disagreements against Razorpay's docs.
- **Primary-source grounding:** every number in the product note traces to a Razorpay doc page or a public review.
- **Automated checks:** after each prototype change, Claude ran headless-browser click-throughs and screenshots to catch errors and layout regressions.
- **Manual testing:** I clicked through every path (contest, accept, won, lost) on laptop and phone, and checked the public links in an incognito window.
- **Data hygiene:** all data in the prototype is made up. No API keys, credentials, real customer data or Razorpay logos are in the repo.
