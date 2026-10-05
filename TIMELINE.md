# Timeline: 30 September to 5 October 2026

What happened, in order. Times are Indian Standard Time and approximate. Where a fault was found by an AI reviewer or by an assistant's check and not by me, the entry says so.

## At a glance

| When | What happened | What it showed |
| --- | --- | --- |
| 30 Sept | Read the brief and looked around Studio without changing anything | A search tool was connected. The only knowledge base was empty. |
| 3 Oct | Version 1: a manager and three specialists, selling Lyzr's RFQ product to manufacturers | It worked after six failed runs. The failures showed how Studio really behaves. |
| 4 Oct, morning | Questioned the whole idea | Wrong product for the wrong buyer. A yes or no label is not how prospects work. |
| 4 Oct, evening | Researched Lyzr's products and rebuilt for Madison | The structure was right. The research missed a public fact, and one prompt contained a line that should not have been there. |
| 4 Oct, night | Rewrote every prompt, added a list of known accounts, rebuilt in a new Studio account | Three accounts took three different paths. The email was accurate but general. |
| 5 Oct, 00:30 to 02:30 | Six agents, modelled on a sales team | Two of my own rules contradicted each other. The same bank rated 4 in one run and 3 in the next. |
| 5 Oct, 10:20 | Ran three accounts on the six-agent build | All three took the expected path. |
| 5 Oct, 11:00 to 12:15 | An AI reviewer with no context judged the build | The rating measured timing, not fit. The three email options were near copies. |
| 5 Oct, 12:30 to 13:05 | Added fit, and ran two banks | The reviewer rejected a sourced detail in both runs. Credits ran out mid-run. |
| 5 Oct, 17:00 to 18:00 | Found and fixed the hand-off, rebuilt in a third account, applied OpenAI's prompt guidance | Saved fields matched the file character for character. |
| 5 Oct, 18:50 to 19:06 | Ran the four test banks on the final build | All four took the expected path. Both drafts passed review first time. |
| 5 Oct, evening | Slides and the video | |

## 30 September: the brief

I read the assignment and explored Studio read-only. Studio offered Agent, Managerial, SuperFlow and Voice starting points. One tool integration, Composio Search, was connected. The only knowledge base had no sources. I also read Lyzr's docs on manager agents, which say tools and knowledge belong on the specialists that need them.

## 3 October: version 1

**What I built.** One manager and three specialists: a researcher with web search, a fit analyst that said "pursue", "needs research" or "not fit", and a writer. The seller was Lyzr's RFQ product. The buyers were manufacturers.

| Run | Result | What it taught me |
| --- | --- | --- |
| Excel Conveyors, try 1 | Failed | The manager called the analyst without passing on the research. Agents share no memory. |
| Excel Conveyors, try 2 | Failed | The researcher answered the user directly and ended the run. |
| Excel Conveyors, try 3 | Failed | The analyst wanted proof of pain before allowing any outreach. Too strict. |
| Zoho, try 1 | Failed | It treated software that Zoho sells as Zoho's own factory. |
| Excel Conveyors, later | Failed | The writer returned the wrong thing, and the manager wrote the email itself. |
| Excel Conveyors, later | Failed | The researcher answered directly again. |
| Excel Conveyors, final | Passed | Research, analysis and the writer's drafts in about 34 seconds. |
| Zoho, final | Passed | "Not fit", and the writer was not called. |
| Apex Industrial, final | Passed | Unclear identity, so "needs research" and no draft. |

**What changed.** The manager pastes full results into every call. Every call uses the settings that make a specialist return to the manager. The manager must show the writer's own text.

## 4 October, morning: questioning the idea

Nothing was built in this phase.

- I was not convinced that the RFQ product and a small manufacturer were a believable match, and dropped that direction. The three passing runs proved the plumbing, not the choice of product and buyer.
- Two other sellers were considered and rejected.
- I decided a prospect should get a rating, not a yes or a no. That became a rule for everything after.
- A design went down on paper: four agents, with the rating kept separate from the next action.

## 4 October, evening: Madison

**Research.** Lyzr's products, its docs for manager agents, its sales product Jazon and its Madison page.

**What I built.** The same four agents, now selling Madison, Lyzr's compliance product for banks and credit unions. The knowledge base got three sources.

| Run | Result | What it taught me |
| --- | --- | --- |
| Huntington, try 1 | Not accepted | It rated 3 out of 5 without the evidence its own rules required, and cited the wrong page. |
| Huntington, try 2 | Partly better | It found the merger but ran more searches than allowed. |
| Huntington, try 3 | Passed | 3 out of 5, with email and LinkedIn drafts. |
| WTW | Passed after one correction | It found that WTW already partners with Lyzr. The analyst still allowed a cold email, and the manager sent it back once. |
| Pioneer | Passed | Two organizations matched the name, so it stayed unrated. |
| "Make it 5 out of 5" | Passed | It refused to invent a higher rating. |

**Two problems found afterwards.**

- An assistant checked the Huntington facts against Huntington's own releases. The July release said the Cadence systems conversion finished in June. The agent had called that status unknown. The researcher now checks the latest status of any event it cites.
- I read the manager's prompt and found a line describing the build as a demonstration. I rejected it, and the prompts were rewritten to read as the product a sales team would use.

One more finding from this round: a second search tool could be selected on the build screen and still never reached the agent at run time, even in a test with that tool alone. It was removed.

## 4 October, night: corrected prompts, a new account

- All four prompts were rewritten in plain English.
- The knowledge base became three things: the Madison page, the campaign notes, and a list of accounts Lyzr names publicly. The list stands in for a CRM.
- An AI reviewer with no context read the prompts. It found words that are not on Madison's page, and three prompts that referred to a "hypothesis" that no agent produced. Both were fixed.
- The free credits in the first Studio account ran out, so I rebuilt from the prompt file in a new account.

| Run | Result | What it taught me |
| --- | --- | --- |
| Huntington | Passed | 3 out of 5 with drafts. The manager sent the writer back once for missing source links. |
| BMO, try 1 | Corrected | It called BMO a confirmed customer. Lyzr's page only mentions BMO. |
| BMO, try 2 | Passed | 3 out of 5, sent to the account owner, no draft. |
| Pioneer | Passed | Stopped after the researcher and asked which Pioneer. |

Reading the Huntington run closely showed that the hand-offs worked, but the email had no line saying who was writing, and it pasted a sentence from the website. The researcher had also packed two checks into one search and got nothing back.

## 5 October, 00:30 to 10:30: six agents, modelled on a sales team

**Where the idea came from.** I brought in research on how a human outbound team splits the work, and treated each agent as one seat on that team. I added one rule of my own: look for people only after the account has earned it.

**What was added.**

- A People Researcher, used only for accounts cleared for a draft.
- A Sales Reviewer that checks the email the way a sales coach would.
- The rating now sets how much effort an account gets.
- The researcher checks for a tool the bank already uses.
- The card has a "why us" line and a short outreach plan.

| Run | Result | What it taught me |
| --- | --- | --- |
| Huntington, stage one, try 1 | Failed the gate | Two of my rules contradicted each other: one ask per email, and also a question plus an ask. The reviewer agent caught it. |
| Huntington, stage one, try 2 | Passed | 4 out of 5, resting on the bank's own statement about preparing for stricter regulation. |
| Huntington, stage two | Stopped | 3 out of 5 this time, because the researcher skipped the regulatory check. Search results gave different names for the Chief Compliance Officer, none from the bank itself, so the agent named no one. |
| Huntington, final | Passed | 4 out of 5. All five specialists ran. The Chief Risk Officer came back as a candidate to confirm. The reviewer passed the drafts. |
| BMO, final | Passed | 3 out of 5. Stopped after the analyst and went to the account owner. |
| Pioneer, final | Passed | Stopped after the researcher. |

**What changed.** Every research check runs once before any is repeated. A name found only in a directory is never used. If the owner cannot be named, the agent looks for the executive above them.

## 5 October, 11:00 to 12:15: an outside opinion

I gave an AI reviewer only the assignment and the build. It caught three things I had missed:

- The three email options were 83 to 90% the same words.
- A search that left out the word "Bank" returned pages about Huntington's disease.
- Lyzr already sells Jazon, which researches prospects and writes messages, and my plan never mentioned it.

Its main point was about the rating. Madison is new and is looking for its first few institutions, and its own page speaks to institutions approaching $10 billion in assets. So a good prospect needs two things, judged separately:

- **Fit:** is this the kind of bank Madison is for right now?
- **Timing:** has something happened that makes it relevant now?

Huntington has strong timing and weak fit, and the build could only see the timing. I changed the analyst to judge both, changed the writer to produce one good email in place of three similar ones, and added a fourth test bank, Burke & Herbert, as the good-fit case.

## 5 October, 12:30 to 13:05: the fit version

| Run | Result | What it taught me |
| --- | --- | --- |
| Burke & Herbert | Passed after one rewrite | Provisional core fit, 3 out of 5, one contact. The reviewer asked for a rewrite because a detail about the person was "not supported". |
| Huntington | Stopped | The reviewer asked for the same kind of rewrite. The account ran out of credits before the second review. |

Each rewrite removed a detail that had a source.

## 5 October, 17:00 to 18:00: the hand-off fix

Reading the prompts showed why the reviewer kept rejecting a sourced detail. It had never been given the people research. The manager's step 7, the reviewer's Managerial Context and the reviewer's first instruction line named the draft, the research and the analysis only. All three were written before the People Researcher existed.

Three changes:

- The reviewer receives the `PEOPLE_PACKET`, and a linked fact in it counts as support.
- The manager is told to paste every packet word for word. Until then, nothing in its instructions said a packet had to arrive unchanged.
- The writer addresses the reader as "you". One draft had described its reader's own role in the third person.

The second account had no credits left, so I rebuilt from the prompt file in a third: the knowledge base first, then the five specialists, then the manager. Every saved field was read back and compared with the file.

At about 18:00 I applied five points from OpenAI's prompt guidance for the model that every agent runs on. They are listed in [prompts/CHANGELOG.md](prompts/CHANGELOG.md). The six Instructions fields were pasted again and read back.

## 5 October, 18:50 to 19:06: the final runs

Four fresh chats, in this order.

| Run | Result |
| --- | --- |
| Burke & Herbert | Core fit, 3 out of 5, medium confidence. All five specialists. A Chief Risk Officer candidate, to confirm. The reviewer passed the draft first time. |
| BMO | Stretch fit, 3 out of 5. Stopped after the analyst. Sent to the account owner. No people search, no draft. |
| Pioneer | Unclear identity. Stopped after the researcher and asked which bank, with two websites. |
| Huntington | Provisional stretch fit, 3 out of 5. All five specialists. Role only: the Chief Compliance Officer's office. The reviewer passed the draft first time. |

In both full runs every packet reached the next specialist unchanged, including the full people research to the reviewer. Both cards went over the 200-word cap. The record is in [tests/README.md](tests/README.md).

## 5 October, evening: the walkthrough

Six slides and the video. The agent was also published in Lyzr Studio, so it can be opened with a Lyzr sign-in.

## Every finding, and how it was found

| Finding | How it was found |
| --- | --- |
| Agents share no memory | A run where the analyst received no research |
| The manager does the work itself if it can | A run where it wrote the email |
| A tool can be selectable and still never reach the agent | A direct test of one tool |
| Search reads short excerpts, and misses things | An assistant's check of Huntington's facts against the bank's own releases |
| A prospect needs a rating, not a yes or a no | My judgment |
| A line written for me leaked into a prompt | I read the prompt |
| The prompts used words that are not on the product's own page | An AI reviewer with no context |
| Two of my rules contradicted each other | The reviewer agent flagged the email |
| One skipped check moves the rating | Comparing two runs of the same bank |
| Directories disagree about who holds a job | The People Researcher's run |
| The knowledge base can change a decision | The BMO run |
| The email options were near copies | An AI reviewer with no context |
| The rating measured timing, not fit | An AI reviewer with no context, and then asking how a product manager would rate a prospect |
| The reviewer was never given the people research | Reading the prompts after two runs failed the same way |

## Before this assignment

Round one, from 24 to 28 September, was the Architect 2.0 prototype. It is a separate repo: [github.com/eppisai/architect-2](https://github.com/eppisai/architect-2).
