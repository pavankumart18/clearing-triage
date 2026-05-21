# Clearing Triage

An interactive demo of an AI triage agent that shadows UK university clearing teams on A-level Results Day.

**Live demo:** https://pavankumart18.github.io/clearing-triage/

## What this is

UK universities run "clearing" for two weeks every August. On Results Day (the third Thursday of August), tens of thousands of 18-year-olds either find out they got into their firm choice, missed it, or exceeded it. Universities spin up call centres that take hundreds of thousands of phone calls in a single day. The conversation is highly emotional, the stakes are high, and the volumes are unmanageable.

This demo shows what an AI triage agent could look like working alongside the human team — not replacing it. The pitch is shadow mode: the agent handles the same calls in parallel, produces a retrospective at end of day, and the human team stays in control of every confirmed offer.

## Three views

### Live triage
The agent in flight. The queue on the left holds seven student scenarios across the emotional spectrum at 8am on Results Day — devastated, frantic, numb, elated, pressured, strategic, confused. Click any one to play back the conversation with typing indicators, reasoning trace, and matched UCAS vacancies populating in real time.

There is also a **Live conversation** entry at the top of the queue. This is a free-form chat where you type as the student. The agent responds via a state machine that parses grades, subject area, emotional cues, UCAS Personal IDs, and university names — and pulls real vacancy matches from the same index used by the scripted scenarios. Try:

- *"I just got BBB, missed Bristol Biomedical, I'm in pieces"*
- *"My mum's here, she says I should call Manchester but every line is engaged"*
- *"I got A*AA, can I trade up from Lancaster to LSE Economics?"*
- *"I don't see the point anymore"* (fires the wellbeing protocol)

### UCAS vacancy explorer
A live-feed mirror of publicly published UCAS clearing vacancies. Forty courses across Russell Group, mid-tier, and post-92 institutions, each with realistic entry-requirement language: A-level grade strings, UCAS Tariff points, BTEC equivalents, subject prerequisites, GCSE floors, contextual offers, foundation routes. Filter by grades, subject, region, or contextual eligibility.

### End-of-day retrospective
The artefact handed back to the partner university at the end of the day. 314 interactions shadowed in parallel: where the agent agreed with the human team, where it would have escalated, where it would have been faster, where it would have got it wrong. Includes six sampled cases with their reasoning trace.

## What's real, what's mocked

**Real:** the structure of UCAS vacancy data, the conventions of entry-requirement language, the order in which clearing teams ask questions, the emotional cues clearing teams hear at 8am, the questions that need answering. The vacancy index is drawn from courses that historically had clearing places at institutions that historically accept through clearing.

**Mocked:** student-side only. Names, exact grades, conversation flow. No real applicant data is used.

## Agent system prompt

The full production-grade system prompt for the agent — including empathy rules, information-collection order, vacancy-matching algorithm, wellbeing protocol, and special flows for adjustment, international, and mature applicants — is in [`prompt.md`](./prompt.md). It is written to be pasted directly as the `system` message of a Claude API call.

## Running locally

It is a single self-contained HTML file with no build step. Either:

```bash
# Open directly
start index.html      # Windows
open index.html       # macOS
xdg-open index.html   # Linux
```

…or serve it:

```bash
python -m http.server 8000
# then visit http://localhost:8000
```

## Stack

Vanilla HTML, CSS, and JavaScript. One file, no dependencies, no build step. The fonts are loaded from Google Fonts; everything else is local.

## Licence

For demonstration purposes. Get in touch before reusing the agent prompt or visual design in production.
