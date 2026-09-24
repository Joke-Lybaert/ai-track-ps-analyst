# Block 3 Prompt Ladders
**13:45-15:15 · Pair AD and Pair BC work in parallel**

Final pair rotation. This block goes deeper than anything you've done today.
The goal is not to finish everything. It's to experience what these tools actually feel like
and where they genuinely change the way you work.

---

## Pair AD: MCP grounding: regulation you can trust

You are going to connect to a hosted MCP server and use it to give your AI tool real,
grounded context from Meridian's actual regulatory framework document. This is the foundation
of how serious AI-assisted requirements work should be done: not relying on the model's
training data about "typical" energy sector regulation, but feeding it the actual source of truth.

---

### What is MCP and why does it matter here?

MCP (Model Context Protocol) is a standard that lets AI tools connect to external data sources
and tools as first-class capabilities. Instead of copy-pasting a document into a chat window
every time, you give the AI a live connection to the information it needs.

Today you'll connect to a hosted MCP server that serves Meridian's actual regulatory standards
extract, then use it to audit your team's requirements backlog. When you ask a question, the AI
can call that server to read the real document and ground its answer in it, rather than making
things up from training data, which matters enormously in regulated domains. An AI that has
memorised "typical" energy sector complaint-handling regulation from its training data will
produce plausible-sounding requirements that may not match what actually applies to Meridian.
This is exactly the kind of failure mode Module 1 covered: confident, fluent, wrong.

---

### Setup (do this before prompting)

No local install either way: this is a hosted server, not a local one. Most FAs won't have a
code editor installed, so start with the first option below unless you already have one.

**No IDE (the common case), free Claude.ai account, browser only:**
1. Create a free account at [claude.ai](https://claude.ai) if you don't have one.
2. Go to **Customize → Connectors → Add custom connector**.
3. Paste in the hosted MCP server URL (https://ai-track-ps-production.up.railway.app) and click **Add**. No authentication step
   needed: the server is open, nothing to log into.
4. In a new chat, click **+** → **Connectors**, and toggle `ai-track-standards` on for that
   conversation.

Free accounts are limited to one custom connector: that's exactly what this needs, so no paid
plan required. Wherever a prompt below says "call read_document," Claude will use the connector.

**If you do have VS Code or another Copilot-enabled editor:** open `.vscode/mcp.json` in your
project (or run **MCP: Add Server** from the Command Palette) and add:
```json
{
  "servers": {
    "ai-track-standards": {
      "type": "http",
      "url": "<hosted MCP server URL, ask your coach>"
    }
  }
}
```
Requires VS Code 1.101 or later. Verify by opening Copilot Chat in agent mode. You should see
`ai-track-standards` listed as an available tool, exposing `list_documents` and `read_document`.

---

### Prompt 1: Verify the connection

```
Using the ai-track-standards MCP server, call read_document with id "meridian-regulatory" to
read the regulatory standards document, and give me a summary of the five obligations most
likely to be missed or watered down when requirements are written under time pressure.
```

**What to do with the output:**
- If your AI tool reads from the actual file: the MCP connection works. The answer will
  reference specific clauses from the Meridian regulatory standards document.
- If it produces generic energy-sector regulatory advice instead: the MCP connection is not
  working. Check the setup steps before continuing.

The difference matters. This is the difference between grounded AI and hallucinated AI.

---

### Prompt 2: Audit the backlog against the regulation

```
Using the ai-track-standards MCP server's read_document tool (id "meridian-regulatory") to
read the regulatory standards, audit our requirements backlog for violations or gaps.

[paste your team's backlog and acceptance criteria]

For each violation or gap:
- Name the story or section
- Quote the relevant clause from the regulatory standards that is violated or unaddressed
- Explain why it matters
- Suggest the correct requirement language

Sort findings by severity: Critical → Major → Minor.
```

**What to do with the output:**
- Check: are the quoted clauses actually in the Meridian regulatory standards document, or did
  the AI invent them? This is easy to verify: open the document and check.
- This is a live demonstration of grounded vs. ungrounded output. Note down any invented clause
  references for Retro 3.

---

### Prompt 3: Fix the critical findings

```
From the audit, take all Critical findings and fix them in the backlog now.
For each fix:
- Apply the change to the relevant story or acceptance criterion
- Add a note explaining what was wrong and what was fixed, with the regulatory clause cited
```

---

### Prompt 4: Expand the use of grounding

Now that you've seen MCP working with a hosted server, think about what else this could
connect to on a real engagement. This is a discussion + research prompt:

```
What other MCP servers or grounding approaches would be useful for a functional analyst
working on a requirements engagement at a client site: think about connecting to a client's
actual policy documents, a regulatory database, a wiki, or a ticketing system.

Search for and list what's realistically available today, with:
- What they connect to
- What you could do with them in a requirements workflow
- Any confidentiality or security considerations for using them with client data
```

**What to do with the output:**
- Verify anything listed actually exists: don't take the AI's word for it
- Note: this is a good test of hallucination risk. Grounding tools for non-code domains are
  newer and less standardised than code-focused ones, so the model's training data may be
  incomplete or outdated.
- Write your findings in `decisions.md` under a "grounding exploration" section

---

## Pair BC: AI-assisted structured review: the quality gate

Your job: use AI to produce a structured review of the entire requirements package: the kind
of review a senior FA would do before presenting to a client steering committee.
This teaches you to use AI as a reviewer, not just a generator.

The interesting challenge: AI will find real issues AND invent fake ones.
Your job is to tell the difference.

---

### The review mandate

You are acting as the engagement's senior FA. Before the requirements package goes in front
of Meridian's steering committee, you need to produce:

1. A **traceability review**: can every story be traced to a specific stakeholder statement?
2. A **testability review**: can every acceptance criterion actually be verified?
3. A **completeness review**: are all business rules from the brief actually reflected?
4. A **diagram review**: do the process diagrams cover exceptions, not just the happy path?
5. A **pre-mortem**: if this package were built exactly as written, how could the project fail?

---

### Prompt 1: Traceability review

```
Review this user story backlog for traceability.

[paste the full backlog]

Here is the source material it should be traceable to:

[paste all six source documents]

For each story:
1. State whether you can trace it to a specific statement in the source material
2. If yes: quote the exact source
3. If no: flag it as potentially invented and explain what makes you suspicious

Be exhaustive. Check every single story.
```

**What to do with the output:**
- This is the most important review of the day. Cross-reference every finding against the
  actual source material yourself.
- Pay special attention to stories about the satisfaction survey and dashboards. Sarah mentions
  these almost as an aside. Has the backlog inflated them into full features nobody actually
  scoped?

---

### Prompt 2: Testability review

```
Review the acceptance criteria in this backlog for testability.

[paste the full backlog with acceptance criteria]

For each acceptance criterion:
1. Write, in one sentence, exactly how a tester would verify it
2. If you cannot write that sentence, flag the criterion as not testable and rewrite it so
   that it is

Be strict. "The system should handle this appropriately" style language always fails this test.
```

**What to do with the output:**
- Fix every criterion flagged as untestable: these are real problems, not nitpicks
- Note how many criteria failed on the first pass. This is useful data for the showcase.

---

### Prompt 3: Completeness review against business rules

```
Here are the business rules extracted from the source material:

[paste Pair AC's business rules catalogue]

Here is our requirements backlog:

[paste the full backlog]

For each business rule:
1. State whether it is reflected in a story or acceptance criterion
2. If yes: quote the exact story/criterion that covers it
3. If no: state that it is missing and what would happen if a development team built from
   this backlog without it
4. If partially: describe what's missing

Be exhaustive. Check every single rule, including the ones marked as conflicts.
```

**What to do with the output:**
- Cross-reference every finding. Pay special attention to the auto-close conflict and the
  resolution timeframe distinction: has the backlog actually kept these as open questions,
  or did it quietly resolve them somewhere along the way?
- If the AI says a rule is covered but you can't find it: ask it to quote the specific story.
  If it can't, it was hallucinating.

---

### Prompt 4: Diagram exception review

```
Here is our main process diagram (Mermaid) and any exception flow diagrams we've produced:

[paste diagrams]

Walk through the main flow and identify every point where reality would branch away from
the happy path but the diagram doesn't show it. Specifically check for:
1. What happens when a handler is on leave and a deadline is approaching
2. What happens to a complaint received outside business hours
3. What happens when a customer submits two complaints about the same issue
4. What happens when a standard complaint becomes a regulatory complaint mid-investigation
   (customer mentions the ombudsman partway through)

For each gap, describe what should be added.
```

**What to do with the output:**
- Update your diagrams with at least one of these exception paths before the showcase
- Note which ones the AI itself thought of unprompted versus only found because you asked
  directly: this is useful data for Retro 3

---

### Prompt 5: Pre-mortem: how could this fail?

```
Act as a red team reviewing this requirements package before it goes to the client.

[paste the full backlog with acceptance criteria, and open-questions.md]

Here is the source material the package is based on:

[paste all six source documents]

Imagine it is one year from now. The system was built exactly from this package, and the
project is considered a failure. Give me 10 distinct scenarios that explain why. Cover at
least:
- technical failures (integration, data, performance)
- organisational failures (ownership, adoption, process)
- legal and regulatory failures

For each scenario:
1. Describe what went wrong in two sentences
2. Point to the specific story, acceptance criterion, or missing requirement that caused it
3. Quote the source material that shows this risk is already knowable today, or say
   explicitly that the scenario is speculation
```

**What to do with the output:**
- Sort the 10 scenarios into three piles: backed by the source material, plausible but
  speculative, and invented. Expect all three.
- Did the red team find anything your four structured reviews missed? Tom's email (Salesforce
  integration, the portal being replaced) is a common blind spot. If it found something new,
  that's worth sharing at Retro 3.
- Backed scenarios go into the Critical or Major sections of the review document in the next
  prompt. Speculative ones can go into the risks register, labelled as speculation.

---

### Prompt 6: Compile the review document

```
Based on the reviews we've done (traceability, testability, completeness, diagram
exceptions, pre-mortem), produce a single structured review document suitable to send ahead of a
steering committee checkpoint.

Format:
# Meridian CMS Requirements: Pre-Steering-Committee Review
## Executive Summary (3-4 sentences)
## Critical Issues (must resolve before the checkpoint)
## Major Issues (should resolve before the checkpoint)
## Minor Issues / Recommendations
## What's done well (at least 3 things)
## Open questions requiring a client decision (list all of them, not just the big ones)
## Readiness status: NOT READY / READY WITH CAVEATS / READY

Be honest. If there are real problems, flag them as blocking.
```

**What to do with the output:**
- Save this as your showcase artifact for Retro 3
- Note the readiness status, and whether you agree with it

---

## Finished early? Stretch: wireframe the customer view

For either pair, only once your own ladder is done. This is not a design exercise: a
wireframe is a quick way to find requirements you haven't written yet.

```
Sarah wants customers to be able to see where their complaint is. Here are our user stories
and acceptance criteria for customer-facing complaint tracking:

[paste the relevant stories and acceptance criteria]

Create a low-fidelity wireframe of the customer's complaint status page as a single HTML
file I can open in a browser. Grey boxes and plain text only: no branding, no colours, no
images. Focus on what information is shown, in what order, and what the customer can do on
this page.

Below the wireframe, list every piece of information or behaviour on the page that is NOT
covered by the stories and acceptance criteria I gave you.
```

Save the HTML output as a file (for example `status-page.html`) and open it in your browser.

**What to do with the output:**
- Go through the "not covered" list. Each item is either a missing story or criterion, or
  something the AI invented. Which is which?
- Check it against Tom's email: where did the AI assume this page lives? The current portal
  is being replaced in about 14 months, so the requirement must not depend on it.
- Which statuses does the customer actually see? What do they see while the complaint is
  "awaiting customer info", after it has been escalated as a regulatory complaint, or once
  the 14-day closure letter has gone out?
- If you did this, bring it to the showcase: 2 minutes, the wireframe plus the gaps it exposed.

---

## End of Block 3 checklist

Before Retro 3 at 15:15:

**Pair AD:**
- [ ] MCP server is running and verified (Prompt 1 output references real clauses from the document)
- [ ] Audit completed and Critical findings fixed
- [ ] `decisions.md` updated with grounding exploration findings
- [ ] You can explain the difference between grounded and ungrounded AI output

**Pair BC:**
- [ ] All four reviews and the pre-mortem completed
- [ ] Pre-steering-committee review document exists and is saved
- [ ] You can name at least one finding that was a false positive and one that was real
- [ ] Readiness status determined and you can defend it

**Both pairs together:**
- [ ] Backlog and diagrams merged into one shared package
- [ ] You each have one concrete thing to share at Retro 3
