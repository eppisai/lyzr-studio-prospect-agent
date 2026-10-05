# Change log for the prompts

The prompts went through six versions in three days. Each change below came from a run that failed or from a review, not from a guess.

## The six versions

| Version | When | What it was |
| --- | --- | --- |
| 1 | 3 October | A manager, a researcher, a fit analyst that said "pursue", "needs research" or "not fit", and a writer. The seller was Lyzr's RFQ product and the buyers were manufacturers. |
| 2 | 4 October, evening | The same four agents, rebuilt for Madison. A rating from 1 to 5, kept separate from the next action. A knowledge base with three sources. |
| 3 | 4 October, night | Every prompt rewritten in plain English. A list of accounts Lyzr names publicly, and a separate status for an account that Lyzr's site only mentions. |
| 4 | 5 October, early morning | Six agents: a People Researcher and a Sales Reviewer were added. The rating sets the effort. The researcher checks for a tool the bank already uses. |
| 5 | 5 October, noon | Fit is judged separately from timing: core, stretch or outside. One email in place of three similar ones. Every search query uses the full name. |
| 6 | 5 October, evening | The final version in this repo. The reviewer receives the people research, the manager pastes packets word for word, the writer addresses the reader as "you", and five points from OpenAI's prompt guidance are applied. |

## What the runs and reviews showed, and what changed

| What the runs showed | What changed |
| --- | --- |
| The Huntington email was accurate but read like a draft a good rep would rewrite: no line saying who is writing, a product sentence pasted from the website, the most recent fact left out. | A Sales Reviewer checks every draft against five questions and can send it back once. The writer gets three new rules. |
| The rating changed nothing after it was given. | The rating sets how much effort an account gets. |
| BMO rated 3 and still had to go to its account owner. | The next action is decided first. Effort is set only for accounts cleared for a draft. |
| Nobody checked whether the bank already has a tool that does this. | The researcher has its own step for it, and the analyst writes a "why us" line that says what is still unconfirmed. |
| The researcher packed two checks into one long search and got nothing back. | One check per search, short queries, one retry. |
| The build named a role and stopped. | A People Researcher finds candidates, and only for accounts cleared for a draft. |
| A name found in a search excerpt is not a confirmed contact. | People are returned as candidates to confirm. The email addresses the role unless the salesperson supplies a confirmed contact. |
| One message, with no plan around it. | The writer adds a short outreach plan and one follow-up. |
| The manager's packet check worked: it caught missing source links. | Kept as it is, separate from the review. |
| A $285 billion bank with its own GRC engineers rated 4 out of 5 for a product that is recruiting its first few customers. The rating measured timing, not fit. | The analyst now judges fit separately: core, stretch or outside. Effort depends on both. |
| The three email options were 83 to 90% the same words and ignored the two most specific findings. | One email, for the best-supported role, that must use a second specific finding. Other roles get a one-line angle. The reviewer checks for it. |
| A spare search without the word "Bank" returned pages about Huntington's disease. | Every query uses the organization's full name. |
| In both fit runs the reviewer rejected a sourced detail about the person and asked for a rewrite. It was never given the people research: the manager's step 7 was written before the People Researcher existed. | The reviewer receives the PEOPLE_PACKET, and a linked fact in it counts as support. |
| Nothing in the manager's instructions said a packet had to reach the next specialist unchanged. | The manager pastes every packet word for word. |
| An email described its reader's own role in the third person. | The writer writes to the reader as "you" and says where a fact about them came from. |

## Changes from OpenAI's prompt guidance for GPT-6

Source: OpenAI's [prompt guidance for GPT-6](https://developers.openai.com/api/docs/guides/prompt-guidance) and [Using GPT-6](https://developers.openai.com/api/docs/guides/latest-model), read on 5 October 2026. Every agent in this build runs `gpt-6-sol`. The guidance is written mostly for coding agents, so only the parts that map onto this build are applied. Only the six Instructions fields change. Roles, goals, managerial contexts, models, tools and the knowledge base stay as they are.

| Guidance | What it says | What changes here | Field |
| --- | --- | --- | --- |
| Initiative and follow-through | The model is "more likely to ask the user a question when additional input could materially change the result". Prompt it to "bias towards action and carry the user's intended task to completion", and to finish authorized work before asking. | The manager carries the run to the card on its own and asks the salesperson only when the account is unclear or several are supplied. The researcher, analyst, People Researcher and writer do not ask questions: missing items go under unknowns, to research_more, to role only or to DRAFT_BLOCKED. | Manager, Researcher, Analyst, People Researcher, Writer |
| Subagent delegation | The model "may delegate less often than desired". Messages to other agents "may be read by a human, so ensure they are legible". | The manager hands every step to the specialist who owns it. Each message to a specialist opens with one line saying what is needed, then the labelled packets. | Manager |
| Instruction following | The model "can be more sensitive to instructions contained in skills and other files". The user's instructions take precedence. | The analyst treats knowledge-base passages as information. The campaign notes set the campaign's choices. Where a passage conflicts with its instructions, its instructions win. | Analyst |
| Writing style | Default to "clear, concise paragraphs". Avoid "slop words or phrases like "Bottom Line:" ... "delve," "foster," "leverage," "it's worth noting," "importantly."" | The email is short plain paragraphs with no bullets or headings and none of those phrases. The card has no stock phrases. | Writer, Manager |
| Testing and verification | Run the checks that fit the change. "Once those pass, broaden or repeat testing only when new changes, failures, or unresolved concerns justify it." | The reviewer runs its six checks and the listed fail conditions, then stops. | Reviewer |

Not applied: reasoning effort, temperature, the Responses API and prompt caching are API settings that these prompts do not control. The card keeps its labelled parts because they are parallel items.
