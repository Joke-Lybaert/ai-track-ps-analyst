# AI Chat: Copilot, or Whatever Works for You

Most of today's exercises are a plain AI chat conversation: paste in source material, ask for
something, read the answer critically. No coding, no IDE required.

Use whichever AI chat tool you have and are comfortable with. You can also switch during the
day: running the same prompt in two tools and comparing the answers is a useful exercise in
itself, and a good thing to share at a retro.

## Your options

| Tool | Where to find it | Good to know |
|------|------------------|--------------|
| **Microsoft 365 Copilot Chat** | The Copilot app, the Copilot icon in Edge, or inside Teams/Outlook. Sign in with your work account | Most of you already have this. Fine for every exercise except the two listed below |
| **GitHub Copilot Chat** | github.com/copilot in the browser, or the Copilot panel in VS Code or a GitHub Codespace. Sign in with your GitHub account | The free tier is enough for today. The only option that can do agent mode (Block 2) |
| **Claude.ai** | claude.ai in the browser, free account | Needed for the MCP exercise (Block 3). Fine for everything else too |
| **Anything else you already use** (ChatGPT, Gemini, ...) | Your usual place | Fine for the plain chat exercises |

Meridian Energy is a fictional client, so any of these is fine today. On a real engagement,
use only the tools your client and Cegeka allow for that client's data.

## Two exercises need a specific tool

- **Block 2, Pair BD (agent mode):** the agent has to read and edit several files at once.
  Use GitHub Copilot in agent mode, inside the Meridian Codespace (or VS Code if you have it).
  M365 Copilot and browser chats can't do this. The setup steps are in
  `block2-prompt-ladders.md`.
- **Block 3, Pair AD (MCP grounding):** the AI has to connect to our hosted MCP server. Use
  Claude.ai with a custom connector (or GitHub Copilot in VS Code/Codespace). M365 Copilot
  Chat can't connect to it. The setup steps are in `block3-prompt-ladders.md`.

Everything else works in any of the tools above.

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

In a plain chat, the AI only knows what you give it. Practical habits:

- Paste in the actual source text (the brief, an email, a requirements document) rather than
  summarising it yourself first. Let the AI work from the primary source.
- **If pasting fails or the text gets cut off**, attach the file instead (most tools have a
  paperclip or **+** button). The full Meridian brief is long, and some tools limit how much
  you can paste into one message. Afterwards, ask the AI to list the six documents it received,
  so you know it has all of them.
- If you're working across several documents, tell it explicitly: "I'm giving you six source
  documents. Read all of them before answering, and tell me if any of them contradict each
  other."
- Ask it to quote or reference which part of the source material it's drawing from. This makes
  it much easier for you to verify.

## Switching tools

Switching is fine, but the new tool knows nothing about your previous conversation. Start a
new chat, paste the source material again, and paste in whatever your team has built so far
(backlog, glossary, open questions). Never assume it "remembers" a decision you made elsewhere.

## Where to keep your work

The exercises refer to files like `backlog.md`, `decisions.md` and `open-questions.md`. If
you're working in the Meridian Codespace, they're already there. If you're not, a shared Word
document or OneNote page per file works just as well. What matters is that your team keeps one
shared version, not four copies in four chat windows.

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
material disagree about something, don't assume the AI noticed. Ask it directly: "did the source
material contain any contradictions? What were they, and how did you resolve them?"

## If you get stuck

If your tool stalls or stops responding, don't spend more than a couple of minutes fighting it:
switch to another tool from the table above, or ask your coach.
