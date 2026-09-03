# Block 1 Prompt Ladders
**09:30. 11:00 · Pair AB and Pair CD work in parallel**

These are structured prompts, not free-form suggestions. Work through them in order.
The goal of this block is not to finish as much as possible. it is to build prompting habits
that will make the rest of the day faster and safer.

After each prompt: read the output critically before using it. If something feels off, it probably is.

> **No IDE, and can't install one?** Start here, not at Block 2. open the Meridian
> requirements workspace in a free **GitHub Codespace** now (Code → Codespaces → Create
> codespace, on the repo's GitHub page. ask your coach for the link). It's a full VS Code in
> your browser, nothing to install, and `backlog.md` / `glossary.md` / `decisions.md` /
> `open-questions.md` are already there for you to fill in as you go, so Block 2's agent-mode
> exercise has real files to work with later. See `block2-prompt-ladders.md` for the AI-tool
> side of this same setup (GitHub Copilot Free).

---

## Pair AB. Backlog foundation: domain understanding & user stories

You are building the core user story backlog for the Meridian complaint management system.

---

### Prompt 1. Understand before you build

Open your AI chat tool. Paste the full contents of the Meridian brief (all six source documents) and send this prompt:

```
I'm an FA joining a requirements engagement for a Complaint Management System.
Here is all the source material we've gathered so far:

[paste all six documents here]

Explain the domain to me as if I'm a new analyst joining the team.
Then identify every ambiguity, gap, or contradiction you find across these documents.
Be specific. quote the conflicting statements directly, don't just say "there are some gaps."
```

**What to do with the output:**
- Go through every ambiguity or contradiction the AI identified. Are they real? Did it miss any?
- Discuss with your pair: for each one, is this something you can decide yourselves, or something
  that must go to the open-questions log?
- Start `decisions.md` and `open-questions.md` in a shared file. These are your team's record.
  you'll refer back to them all day.

> **Watch for:** AI may confidently resolve a contradiction for you without flagging it as one.
> That's the risk. The auto-close instruction from Sarah versus the compliance position from
> Marc and Priya is the clearest example. check whether AI treats it as settled or as open.

---

### Prompt 2. User story backlog proposal

```
Based on this source material, propose a complete user story backlog for the Complaint
Management System. Organise it into epics. For each story, use the format:

As a [role], I want to [action], so that [benefit].

For each story, also note:
- Which source document(s) it is traceable to
- Whether it is directly stated, or an inference you made (be explicit about which)

Do not invent functionality that is not supported by the source material. If you think
something is missing, list it separately as a "gap". not as a story.
```

**What to do with the output:**
- Count the stories. If it's 25+, be suspicious. read them critically rather than treating
  volume as progress.
- Pick five stories at random and trace each one back to the specific source document sentence
  it came from. Any you cannot trace are candidates for removal.
- Check: does the backlog include a story for regulatory complaints (the fourth category, from
  Marc's interview)? Does it include anything for business customers?

---

### Prompt 3. Acceptance criteria

Once you've agreed on the story list:

```
Write full acceptance criteria for these user stories: [paste your agreed story list]

Requirements:
- Use Given/When/Then format
- Every acceptance criterion must be independently testable. a tester should be able to read
  it and know exactly how to verify it
- Do not use vague language like "the system should provide a clear and intuitive experience".
  if a criterion cannot be objectively verified, do not write it
- Reference specific numbers, timeframes, and rules from the source material where they apply
  (e.g. the 2-working-day acknowledgement, not "promptly")

Provide acceptance criteria for each story in full. No placeholders.
```

**What to do with the output:**
- Read every criterion and ask: "how would a tester verify this?" If you can't answer in one
  sentence, it needs to be rewritten
- Check the resolution timeframe stories specifically. does the AI distinguish the 5-day
  internal target from the 8-week regulatory obligation, or has it collapsed them into one number?
- Verify the package declarations of your terminology are consistent with your glossary (see Pair CD)

---

### Prompt 4. Process flow narrative

```
Write a narrative walkthrough of the core complaint handling flow, from submission to
resolution, based on these user stories and the current-state process description
(Document 6 in the source material).

Then do the same for the extension-approval exception flow: what happens when a handler
cannot meet the resolution target and needs more time.

For each flow, list every decision point. every place where the process branches based
on a condition.
```

**What to do with the output:**
- These narratives are what Pair CD will turn into Mermaid diagrams next block. make sure
  they are accurate before handing them over
- Check: does the extension-approval narrative match what Marc actually described (team leader
  approves, with a reason, roughly 30% of cases)?

---

### Prompt 5. Interrogate the output

This is the most important prompt of the block. Do not skip it.

```
Review the user story backlog and acceptance criteria you just generated against these
specific facts from the source material. For each one, tell me:
1. Whether it is currently reflected in a story or acceptance criterion
2. Where exactly (which story)
3. What a development team would build wrong if this were missing

Facts to check:
- The acknowledgement must happen within 2 working days and is a regulatory requirement, not
  a nice-to-have
- Resolution has both a 5-day internal target and an 8-week regulatory obligation. these are
  not the same thing
- Regulatory complaints (customer has mentioned the ombudsman) must escalate to compliance
  within 2 working days, not follow the standard flow
- All complaint records, including every communication and status change, must be retained
  for five years
- Auto-closing a complaint due to customer non-response is explicitly rejected by both the
  complaints handler and the compliance officer
```

**What to do with the output:**
- This is your quality gate. Anything missing needs to be added before the block ends.
- Note down which facts the AI says are covered but you cannot actually find in a story.
  those need to be added, not assumed.

---

## Pair CD. Glossary, domain model & requirements scaffold

You are building the supporting structure: a glossary that resolves inconsistent terminology,
a domain/data model diagram, and the traceability scaffold the whole team will use all day.

---

### Prompt 1. Audit the terminology

```
Here is source material for a Complaint Management System requirements engagement:

[paste all six documents]

Audit the terminology used across these documents. Specifically:
1. Where do different stakeholders use different words for the same concept?
2. Where does the same word seem to mean different things to different stakeholders?
3. What terms are used without ever being defined (e.g. "complaint categories",
   "escalation", "regulatory complaint")?

List every inconsistency you find, with the exact quotes and who said what.
```

**What to do with the output:**
- This becomes the seed for your glossary. resolve each inconsistency with a single
  agreed definition
- Note especially: "escalation" is used by Sarah (missed-deadline escalation) and by Priya
  (regulatory-complaint escalation) to mean two different workflows. Does your glossary
  distinguish them?

---

### Prompt 2. Build the glossary

```
Based on the terminology audit, produce a glossary of domain terms for this Complaint
Management System. For each term:
- A single, precise definition
- The source document(s) that informed the definition
- Any conflicting usage you resolved, and how

Include at minimum: complaint, complaint category, handler, team leader, acknowledgement,
resolution, escalation, extension, regulatory complaint, business customer.
```

**What to do with the output:**
- Check every definition against the source material yourself. don't assume the AI resolved
  the conflict correctly
- Share this glossary with Pair AB as soon as it's stable. their acceptance criteria should
  use these exact terms

---

### Prompt 3. Domain model diagram

```
Based on this source material and glossary, propose a domain model for the Complaint
Management System as a Mermaid class diagram (or entity-relationship diagram. your choice,
explain why).

Include: Complaint, Complaint Category, Handler, Team Leader, Customer, Escalation,
Extension Request, and any other entities you think the domain requires.

For each entity, list its key attributes and its relationships to other entities,
with cardinality (one-to-many, many-to-many, etc.).
```

**What to do with the output:**
- Paste the Mermaid output into mermaid.live. Does it render without errors? AI-generated
  Mermaid often has subtle syntax issues. fix them before moving on
- Check: does the model distinguish a regulatory complaint from a standard complaint, or does
  it treat "category" as a flat, undifferentiated field?
- Does the model account for the 5-year retention requirement. is there any entity or field
  that looks like it would make old records deletable?

---

### Prompt 4. Stakeholder & RACI map

```
Based on the source material, produce a RACI matrix for the Complaint Management System
requirements engagement itself. not the software, the project.

Rows: the key decisions and deliverables (e.g. "resolve the auto-close contradiction",
"confirm the business customer threshold", "approve final acceptance criteria").
Columns: Sarah Belmans, Marc Devos, Priya Nair, Tom Geerts, the commercial team, your FA team.

For each row, assign Responsible / Accountable / Consulted / Informed.
```

**What to do with the output:**
- This is useful scaffolding for the open-questions log. anything where "Responsible" is
  unclear or missing from the source material is itself an open question
- Note where the source material never actually named who is accountable for something
  (business customer threshold is a strong candidate. Priya says "check with the commercial
  team" but no one on the commercial team has been interviewed)

---

### Prompt 5. Requirements package scaffold

```
Produce a template structure for the final requirements package deliverable, with section
headers only (no content yet): user story backlog by epic, process diagrams, glossary,
open questions log, assumptions log, gaps and risks register.

For each section, write one sentence describing what "good" looks like in that section.
what would make a development team trust it.
```

**What to do with the output:**
- This becomes the shared document shell the whole team assembles into throughout the day
- Share it with the room before Retro 1 so everyone is filling in the same structure

---

## End of Block 1 checklist

Before Retro 1 at 11:00, your team should be able to answer yes to:

**Pair AB:**
- [ ] `decisions.md` and `open-questions.md` exist and have real entries
- [ ] A first-draft user story backlog exists, organised by epic
- [ ] Acceptance criteria exist for the core submission and acknowledgement flow
- [ ] You've run Prompt 5 and know which facts from the source material are not yet reflected

**Pair CD:**
- [ ] Glossary exists with at least the 10 core terms defined
- [ ] Domain model diagram exists and renders in mermaid.live without errors
- [ ] RACI map exists
- [ ] Requirements package scaffold exists and has been shared with Pair AB

**Both pairs together:**
- [ ] Glossary terms and backlog terminology are consistent (deal with mismatches now)
- [ ] Everyone has seen the shared requirements package scaffold
