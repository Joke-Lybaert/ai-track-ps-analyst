# Flawed Acceptance Criteria: Block 2, Pair AC, Prompt 2

**Facilitator note:** hand this file to Pair AC only when they reach Prompt 2 of Block 2.
It plays the same role the three failing tests play in the developer day: a known-bad
artifact from "a previous session" that the pair must diagnose and correct using AI,
by checking it against the actual source material rather than trusting it at face value.

Do not explain what's wrong with them. Let the prompt and the source material do the work.

---

## AC-014: Resolution timeframe

**Story:** As a complaints handler, I want the system to flag a complaint as overdue if it
has not been resolved within the target time, so that I can prioritise my work.

**Acceptance criteria (as drafted):**
```
Given a complaint has been open for more than 5 working days
When a handler views the complaint
Then the system displays an "overdue" warning
And the complaint automatically escalates to the team leader
```

**What's wrong:** This conflates the 5-day internal target with the 8-week regulatory
obligation, and invents automatic escalation that no stakeholder described. Marc explicitly
said extensions are common (~30% of cases) and require team leader approval with a reason.
Missing the 5-day target is not itself an automatic escalation trigger if an extension has
been approved. The regulatory consequence (a customer letter) only applies at 8 weeks, not 5 days.

---

## AC-027: Customer non-response

**Story:** As a complaints handler, I want complaints to close automatically if the customer
stops responding, so that I don't have to chase unresponsive customers indefinitely.

**Acceptance criteria (as drafted):**
```
Given a customer has not responded to an information request for 7 days
When the 7-day period elapses
Then the complaint status changes to "closed"
And the customer receives a closure notification
```

**What's wrong:** This is the auto-close story exactly as Sarah described it in her email,
and exactly what Marc and Priya both explicitly rejected, citing a prior regulatory fine.
This should not be a story with acceptance criteria at all in its current form; it should be
an open question, or at minimum implement the actual required procedure (two reminders, a
14-day formal notice, then manual sign-off, never automatic).

---

## AC-041: Business customer complaints

**Story:** As a business customer, I want to submit complaints through the same system as
residential customers, so that my complaint is tracked consistently.

**Acceptance criteria (as drafted):**
```
Given a business customer submits a complaint
When the complaint is received
Then it follows the standard residential complaint workflow
And is assigned to a complaints handler in the standard queue
```

**What's wrong:** Sarah called this "probably out of scope" and Priya said excluding it
entirely creates retrofit risk. Neither position supports silently routing business
customers through the standard flow as if the question were settled. This criterion invents
a decision nobody made. It should be flagged as an open question pending input from the
commercial team on the account-manager-first process and the contract value threshold.
