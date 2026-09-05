# Copilot Chat

Today's default AI tool is Copilot Chat used as a plain conversation, no coding, no IDE
required. If you've never used any AI chat tool before, start here.

## What it is

Copilot Chat is a conversation window: you type a question or request in plain English, and it
responds in plain English (or whatever format you ask for: a list, a table, a draft document).
It's the same underlying idea as any AI chatbot you may have heard of, made available through
your company's GitHub Copilot license.

You do not need to know anything about programming to use it well. Today's exercises use it for
reading requirements, drafting user stories, building a glossary, and generating diagrams, none
of which involve writing code.

## Getting started

Where you access it depends on how your organization has it set up, ask your coach if you're
not sure, but common entry points are:

- A browser tab at github.com/copilot (sign in with your work GitHub account)
- A Copilot Chat panel inside Microsoft Teams or Office apps, if licensed that way
- A Copilot Chat extension inside a code editor, if you happen to have one installed (not
  required for today)

Once open, you'll see a text box. Type your question or request and press Enter.

## How to prompt it well

The quality of the answer depends heavily on how much context you give it. Compare:

> "Write user stories for this."

versus

> "Here is a client brief describing a complaint management system. Write user stories in the
> format 'As a [role], I want to [action], so that [benefit]', with acceptance criteria in
> Given/When/Then format. Flag anything you had to infer rather than something the brief stated
> directly."

The second version tells it the format you want, and, importantly, asks it to be honest about
what it made up versus what it found. That second instruction matters a lot: without it, AI
will often present an inference as if it were a stated fact.

## Working with source material

Because you're using plain chat (not the grounded MCP connection covered in Block 3), the AI
only knows what you tell it. Practical habits:

- Paste in the actual source text (the brief, an email, a requirements document) rather than
  summarizing it yourself first. Let the AI work from the primary source.
- If you're working across several documents, tell it explicitly: "I'm giving you six source
  documents. Read all of them before answering, and tell me if any of them contradict each
  other."
- Ask it to quote or reference which part of the source material it's drawing from. This makes
  it much easier for you to verify.

## Iterating

Your first result rarely needs to be your last. Common, useful follow-ups:

- "This story is too vague, break it into two."
- "You said X, but the brief also mentions Y. Did you consider that?"
- "Explain why you decided that, rather than the alternative."

Treat it like a fast, confident junior colleague: capable of a lot, but not infallible, and
worth double-checking on anything that matters.

## What to watch for

AI chat tools are fluent and confident even when they're wrong or when they've quietly resolved
a contradiction in your source material without telling you. If two stakeholders in your source
material disagree about something, don't assume the AI noticed, ask it directly: "did the source
material contain any contradictions? What were they, and how did you resolve them?"

## If you get stuck

See `../../ai-tooling-fallback.md` for what to do if Copilot Chat itself isn't accessible to
you, or ask your coach.
