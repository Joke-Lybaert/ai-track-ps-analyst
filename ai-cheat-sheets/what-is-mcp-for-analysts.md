# What Is MCP?

You'll hear the term "MCP" in exercise 3. You don't need to understand it deeply to use it, but
knowing roughly what it is will help the exercise make sense, and it's a concept that comes up
well beyond this workshop.

## The problem, in plain terms

An AI chat tool only knows two things: what it learned during training (which doesn't include
your company's specific documents) and whatever you type into the conversation. Left to itself,
if you ask it something about, say, a regulatory requirement, it will answer based on general
patterns it's seen elsewhere, which might be right, might be close, or might be entirely
invented. It will sound equally confident either way. That's the core risk this workshop keeps
coming back to.

The fix is to give the AI direct access to the actual document, so it can check rather than
guess.

## What MCP is, without the technical detail

MCP (Model Context Protocol) is just the underlying standard that makes this possible: it lets
an AI tool connect to a specific source of documents and read from it directly, on demand,
during a conversation. You don't need to know how it works internally. What matters is what it
enables: an AI tool that answers from a real document instead of from memory.

In exercise 3, when you set up the "custom connector" in Claude.ai (see
`claude-ai-custom-connectors.md`), what you're actually doing is connecting Claude to a small
MCP server your coach has set up, which has access to one specific document: the regulatory
standards for this exercise. That's the whole mechanism. The connector is just the
Claude.ai-specific name for "speaking MCP to that server."

## Why this matters for the exercise

The whole point of exercise 3 is to compare an AI's answer with and without that connection:

- **Without grounding:** ask a question about a regulatory requirement with no connector
  enabled, and the AI will answer from general knowledge. It may sound entirely plausible and
  still be wrong, or it may invent a specific-sounding detail (a made-up article number, for
  example) that doesn't exist.
- **With grounding:** the same question, connector enabled, and the AI actually reads the real
  document before answering. The specifics should now match the document exactly, because it's
  no longer guessing.

Being able to tell these two apart, and knowing to check, is the actual skill exercise 3 is
teaching. The mechanism (MCP) is just the plumbing that makes the "with grounding" case
possible.

## Why this matters beyond today

This same idea applies directly to tools you already use. Copilot connecting to a document
source, or Rovo answering a question by actually searching your Jira and Confluence content
rather than guessing, are the same underlying pattern: an AI tool with access to real,
specific information versus one working from general knowledge alone. The habit worth keeping
is not about MCP specifically, it's asking, whenever an AI gives you an answer: is this
grounded in something real I can check, or is this a plausible-sounding guess?

## The one-sentence version

MCP is what lets an AI tool read your actual documents on demand instead of guessing, and
knowing whether it's doing that is more useful than knowing how it works.
