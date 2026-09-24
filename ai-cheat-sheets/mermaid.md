# Mermaid: Diagrams Written as Text

Mermaid is a way to create diagrams by describing them in plain text, rather than dragging
boxes and arrows around in a drawing tool. It comes up repeatedly today, and it's genuinely
useful for requirements work beyond the workshop, so it's worth understanding properly.

## Why this matters for you

As an analyst, you'll often need to represent a process or flow: how a complaint moves from
submission to resolution, what happens on each decision branch, who's involved at each step.
Drawing this by hand in a tool like Visio or draw.io works, but it's slow to update and awkward
to hand to an AI tool for help.

Mermaid flips this: the diagram is just text, which means:

- You (or an AI) can generate a full diagram from a plain description in seconds.
- Changing the diagram is just editing text, no dragging boxes around.
- It's easy to version, share, and paste directly into a chat with an AI tool for review or
  correction.

## Seeing it in action, with zero setup

Go to [mermaid.live](https://mermaid.live) in your browser. No account needed. Paste this in
the editor panel on the left:

```
flowchart TD
    A[Complaint received] --> B{Ombudsman mentioned?}
    B -- Yes --> C[Reclassify as regulatory]
    B -- No --> D[Standard handler workflow]
    C --> E[Escalate to Compliance within 2 days]
```

You'll see a flowchart render on the right immediately. That's the entire workflow: text in,
picture out.

## Basic syntax you'll actually use

**Flowcharts** (`flowchart TD` for top-down, `flowchart LR` for left-right):

```
flowchart TD
    A[Start] --> B[Do something]
    B --> C{A decision?}
    C -- Yes --> D[One outcome]
    C -- No --> E[Another outcome]
```

Square brackets `[...]` are a normal step. Curly braces `{...}` are a decision/branch point.
Arrows (`-->`) connect them, with an optional label (`-- Yes -->`).

**Sequence diagrams**, useful for showing who talks to whom and in what order:

```
sequenceDiagram
    Customer->>System: Submit complaint
    System->>Handler: Assign complaint
    Handler->>Customer: Send acknowledgement
```

You won't need much more syntax than this for most requirements work. Mermaid supports far
more (class diagrams, state diagrams, Gantt charts), but flowcharts and sequence diagrams cover
the majority of analyst use cases.

## Using AI to generate one for you

You rarely need to write Mermaid syntax by hand. Describe what you want and ask your AI chat
tool to generate the diagram:

> "Generate a Mermaid flowchart showing the complaint handling process: a complaint is
> received, acknowledged within 2 working days, assigned to a handler, resolved or escalated if
> the customer mentions the ombudsman, and closed. Use decision points where the process
> branches."

Paste the result into mermaid.live to check it renders correctly and matches what you meant.

## Fixing errors

Mermaid's syntax is strict about small things (a missing bracket, an unescaped character), and
both AI-generated and hand-written diagrams sometimes fail to render. If mermaid.live shows an
error instead of a diagram, don't debug the syntax yourself first: paste the broken code and the
error message back to your AI chat tool and ask it to fix it. This is usually faster and more
reliable than fixing it by hand.

## What Mermaid can and can't draw

AI will happily claim it has produced "a BPMN diagram in Mermaid". It hasn't: Mermaid has no
BPMN. Know what the tool supports before you ask for it.

| You want | In Mermaid? | What to do instead |
|----------|-------------|--------------------|
| Process flow with decisions | Yes: `flowchart` | Use `subgraph` blocks to fake swimlanes per role |
| Who talks to whom, in order | Yes: `sequenceDiagram` | |
| Domain model | Yes: `classDiagram` or `erDiagram` | |
| Lifecycle of one thing (e.g. complaint statuses) | Yes: `stateDiagram-v2` | |
| System context / containers (C4) | Partly: C4 support is experimental | PlantUML C4 or Structurizr if it needs to be exact |
| BPMN | No | Call your flowchart a process flow, not BPMN. For real BPMN use a modelling tool such as bpmn.io |
| UML use case diagram | No | PlantUML has one; AI writes PlantUML as easily as Mermaid |
| Decision table (DMN) | No | Ask AI for a plain table: conditions as columns, one rule per row |
| ArchiMate | No | A dedicated tool such as Archi |

The rule of thumb: if the notation has a strict standard behind it (BPMN, DMN, ArchiMate), a
text diagram will only ever approximate it. That's often fine for thinking and discussing,
but say so when you share it.

## Where you'll use this today

Diagrams come up when your team builds a domain model or represents a process flow from the
source material. The habit to build is the same one that applies to everything else today:
generate a first draft with AI, then check it against the actual source material rather than
accepting it because it looks plausible. A confident-looking diagram with the wrong branch
logic is just as misleading as confident-looking prose.

## If your network blocks mermaid.live

Some corporate networks block unfamiliar domains. If mermaid.live doesn't load, the Mermaid
extension for VS Code (if you have VS Code available) renders diagrams locally instead. Ask
your coach if you're stuck.
