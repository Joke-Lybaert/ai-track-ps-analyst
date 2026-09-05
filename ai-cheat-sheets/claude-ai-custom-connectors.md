# Claude.ai and Custom Connectors: Setup Guide

Exercise 3 uses Claude.ai, a browser-based AI chat tool, connected to a document source through
something called a "connector." This page walks through the setup from scratch. If you've never
used any AI chat tool before, this is written for you.

## What Claude.ai is

Claude.ai is a website where you can chat with an AI, similar in spirit to any AI chatbot you
may have used before. Nothing to install. You create a free account and use it entirely in your
browser.

## What a "connector" is

Normally, an AI chat tool only knows what you type into it and what it learned during training,
which does not include your company's internal documents. A connector is a way to give it
direct, live access to a specific, defined source, in our case, one specific document we have made available. 
Once connected, the AI can go read that document itself when it needs
to, rather than you having to copy and paste it in every time, and rather than it guessing.

This matters because it's the difference between an AI answering "here's what companies
typically do" (a guess) and an AI answering "here's what your document actually says" (a
grounded answer). Exercise 3 is built around noticing that difference. See
`what-is-mcp-for-analysts.md` for more on how this works underneath.

## Setting up your account

1. Go to [claude.ai](https://claude.ai) in your browser.
2. Sign up for a free account using your email address (or another sign-in option offered).
3. Verify your email if prompted.
4. You'll land in a chat interface once signed in, ready to use immediately.

The free plan is enough for today's exercise. You do not need a paid plan.

## Adding the workshop's connector

1. Click your account name or the settings icon (usually bottom-left or top-right, depending on
   the current layout).
2. Look for **Settings** → **Connectors** (it may be under an "Organization Settings" or
   "Customize" section depending on account type).
3. Click **Add custom connector**.
4. Paste the server URL your coach provides for today's workshop.
5. Give it a name if asked (for example, "Meridian regulatory standards").
6. Save. You should see it appear in your list of available connectors.

The free tier allows one custom connector, which is exactly what you need for today.

## Using it in a conversation

1. Start a new conversation in Claude.ai.
2. Look for an option to enable or attach the connector to the conversation (usually a small
   icon or toggle near the message box, sometimes under a "tools" or "connectors" menu).
3. Once enabled, ask a question that the connected document could answer, for example:
   > "According to the regulatory standards document, what's the required acknowledgement
   > timeframe for a complaint?"
4. Claude will retrieve the relevant part of the document and answer based on it, rather than
   guessing. You'll often see an indication that it looked something up.

## How to tell it's actually working

Ask it something specific enough that a guess would likely be wrong, then check the answer
against the actual document yourself. If the answer matches the document precisely (specific
numbers, specific terms), the connector is working. If the answer sounds generic or doesn't
match, double-check that the connector is enabled for that conversation.

## What this is not

This is separate from Claude Code, a different product mentioned elsewhere in these materials
for developers. Claude.ai is the browser-based chat product; nothing here requires installing
anything or writing code.

## If you get stuck

Some corporate networks are stricter about outbound connections than others, though Claude.ai
itself should be reachable from a normal browser without special configuration. If the
connector won't save or won't respond, ask your coach.
