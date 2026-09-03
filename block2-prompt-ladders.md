# Block 2 Prompt Ladders
**11:15-12:45 · Pair AC and Pair BD work in parallel**

Pairs have rotated. You are now working with someone you haven't paired with today yet.
Before you write a single prompt: spend 5 minutes reading what your teammates produced in
Block 1. You will be building on it, and possibly fixing it.

---

## Pair AC: Business rules catalogue & exception coverage

Your job: formalise every business rule buried in the source material, especially the
contradictory ones, into an explicit, defensible rules catalogue, then expand the backlog
to cover the exceptions most teams miss.

---

### Before you start: read the backlog

Open Pair AB's backlog and acceptance criteria from Block 1. Do not rewrite anything yet.
Just read it, and check it against `open-questions.md`.

Ask yourselves: for every business rule stated in the source material, is there a story that
enforces it? If not, that's your first task: not a prompt task, a reading task.

---

### Prompt 1: Extract the business rules

```
Here is the full source material for a Complaint Management System requirements engagement:

[paste all six documents]

Extract every business rule stated or implied in this material. A business rule is a
constraint the system must enforce: a timeframe, an eligibility condition, a mandatory
step, a prohibition.

For each rule:
1. State it precisely, in one sentence
2. Quote the source
3. Flag if it conflicts with any other rule you've extracted, and name the conflicting rule

Do not resolve conflicts. Just surface them. That is the point of this exercise.
```

**What to do with the output:**
- Go rule by rule. The two big ones to check: the auto-close conflict (Sarah vs Marc/Priya),
  and the resolution timeframe conflict (5 days internal vs 8 weeks regulatory vs "extensions
  ~30% of the time")
- For each conflict, decide: is this something your team resolves with a documented assumption,
  or something that must go to the open-questions log as a blocker? The auto-close conflict
  should go to the log. It's a genuine policy conflict, not something an FA should decide alone.

---

### Prompt 2: Correct the flawed acceptance criteria

You've been handed three acceptance criteria drafted by a previous session that do not
correctly reflect the source material. Find them in `flawed-acceptance-criteria.md`
(ask your coach for this file if you don't have it).

```
Here are three acceptance criteria drafted for this Complaint Management System project.
Here is the actual source material they should be based on.

[paste the three flawed criteria]
[paste the relevant source material excerpts]

Each of these three criteria has a factual error relative to the source material: not a
style issue, an actual mismatch with what a stakeholder said. Find each error, explain what
is wrong, and rewrite the criterion correctly. Cite the source material for the correction.
```

**What to do with the output:**
- Do not just apply the fix: read the explanation. Each one should teach you something about
  reading source material precisely rather than trusting a plausible-sounding requirement
- Confirm all three corrected criteria are internally consistent with your Block 1 backlog

---

### Prompt 3: Expand coverage: the missed categories

```
The user story backlog so far covers: billing complaints, supply interruptions, contract
disputes, and general service complaints. The source material also describes a fourth
category, regulatory complaints, and a business customer segment that may or may not be
in scope.

For regulatory complaints:
Write user stories and acceptance criteria for the escalation flow Priya described: 2-working-day
escalation to compliance, different handling, different ownership.

For business customers:
Do not write stories yet. Sarah says this may be out of scope, but Priya says excluding it
creates a costly retrofit risk. Instead, write this up as a structured open question: what
decision is needed, who needs to make it, and what happens to the requirements package if
the answer is "in scope" versus "out of scope."
```

**What to do with the output:**
- Check the regulatory complaint stories against Priya's exact words: escalation "within two
  working days of receipt," not five
- The business customer write-up should NOT resolve the question: if AI tries to just pick
  an answer, push back and ask it to write the open question instead

---

### Prompt 4: Exception flow: extension and escalation

```
Write user stories and full acceptance criteria for:
1. The extension-approval flow: a handler requests more time before the resolution target,
   with a reason, approved by the team leader
2. The missed-deadline escalation flow: what happens when a complaint passes its resolution
   target without an approved extension

For each, be explicit about what triggers the flow, who is notified, and what the system
must record for audit purposes (remember the five-year retention requirement).
```

**What to do with the output:**
- Check: does the missed-deadline escalation distinguish "missed the 5-day internal target
  with no extension" from "missed the 8-week regulatory obligation"? These require different
  responses: the regulatory miss requires a letter to the customer about the ombudsman, per Priya.

---

## Pair BD: Agent-mode backlog restructure

Your job: use your AI tool's agent mode to restructure the entire requirements backlog
in a single coordinated operation. You may not edit individual files manually.
Everything goes through the agent.

This block will teach you more about AI agents than any tutorial.

---

### Before you start: understand what you're doing

Agent mode (available in Copilot Chat via "Agent" mode, or equivalent in your AI tool) can
read and edit multiple files in a single operation. It is not magic. It operates on the files
you have in your workspace, makes a plan, and executes changes step by step.

> **No IDE, and can't install one?** Expect this to be the normal case for most of today, not
> an exception. Open the Meridian requirements workspace in a free **GitHub Codespace** instead
> (Code → Codespaces → Create codespace, on the repo's GitHub page; ask your coach for the
> link), a full VS Code running in your browser, nothing to install. Enable **GitHub Copilot
> Free** (no credit card needed) for agent mode: capped at 50 requests a month, plenty for one
> block. Everything below works the same once you're in; `backlog.md`, `glossary.md`,
> `decisions.md`, and `open-questions.md` are already there waiting from Block 1.

Your job: give it a good enough instruction that the changes are correct and consistent.
Your constraint: **do not touch any file manually**. If the agent makes a mistake, fix it
with another agent prompt, not by editing directly. This is how you learn where agents fail.

---

### The restructure brief

The requirements backlog produced so far has the following problems (many of these will be
genuine issues from what Block 1 produced):

1. **Inconsistent story format**: some stories follow "As a... I want... so that...", some don't
2. **Missing traceability**: some stories have no note on which source document they came from
3. **Terminology drift**: some stories use terms that don't match the glossary Pair CD built
4. **Untestable acceptance criteria**: some criteria use vague language that can't be verified
5. **Orphaned diagram references**: if any story references a flow that isn't in a diagram yet, or vice versa

---

### Prompt 1: Plan before acting

Before letting the agent touch any files:

```
I have a requirements backlog for a Complaint Management System that needs restructuring.
Before making any changes, analyse the backlog and produce a restructuring plan.

For each of these problems, list every story or section that needs to change:
1. Inconsistent story format (not following As a/I want/so that)
2. Missing traceability notes (no source document cited)
3. Terminology that doesn't match our glossary: [paste glossary]
4. Untestable acceptance criteria (vague, non-verifiable language)
5. References to diagrams or flows that don't exist yet

Do not make any changes yet. Just list what needs to change and why.
```

**What to do with the output:**
- Read the plan carefully. Does it match what you can see in the backlog?
- Are there things it missed? Things it flagged that aren't actually problems?
- Only proceed to Prompt 2 once you agree with the plan.

---

### Prompt 2: Execute the restructure

```
Now execute the restructuring plan. Apply all five categories of changes across the entire backlog.

Constraints:
- Do not change the actual content or meaning of any acceptance criterion: only its clarity
  and testability
- Do not remove any story without flagging it to me first
- Do not invent new source document citations: if a story genuinely has no traceable source,
  flag it, don't fabricate one
- After each category of changes, pause and list what you changed before moving to the next

Start with terminology, then story format, then traceability, then testability of criteria,
then diagram cross-references.
```

**What to do with the output:**
- Watch what the agent does between categories: this is the observable "reasoning" of an agent
- If it tries to fabricate a source citation for an untraceable story: stop it and tell it why
  that's worse than leaving it flagged
- Keep a running note: what did the agent change that you didn't expect?

---

### Prompt 3: Verify nothing broke

```
The restructuring is complete. Now verify the backlog is still correct:

1. Does every story still say what it originally said, just more clearly?
2. Are there any stories now missing that existed before?
3. Do all traceability notes point to real source material, not fabricated ones?
4. Is terminology now consistent with the glossary throughout?

List every issue you find. Do not fix anything yet, just list.
```

Then, after reviewing the list:

```
Fix all the issues you identified. Apply the fixes now.
```

---

### Prompt 4: Reflect on the agent

This is not an AI prompt. This is a discussion prompt for your pair.

Talk through these questions and write your answers in `decisions.md`:

1. What did the agent do that surprised you?
2. At what point, if any, did you not trust what it was doing?
3. If you were doing this on a real client's requirements repository, what guardrails would
   you want in place?
4. What would have happened if you had let it run without checking the plan first?

---

## End of Block 2 checklist

Before lunch at 12:45, your team should be able to answer yes to:

**Pair AC:**
- [ ] Business rules catalogue exists with every conflict explicitly flagged
- [ ] The auto-close conflict and resolution timeframe conflict are both in `open-questions.md`,
      not silently resolved
- [ ] Regulatory complaint stories exist and match Priya's exact escalation timeframe
- [ ] Business customer question is written up as an open question, not a decision
- [ ] Extension and escalation flows have full acceptance criteria

**Pair BD:**
- [ ] Agent restructure completed: all five categories addressed
- [ ] No fabricated source citations exist in the backlog
- [ ] `decisions.md` updated with agent reflection answers

**Both pairs together:**
- [ ] Backlog merged into one shared document
- [ ] You have something to say at Retro 2 about what the agent did unexpectedly
