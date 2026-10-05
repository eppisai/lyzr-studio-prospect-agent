# The prompts

Six agents, exactly as they are saved in Lyzr Studio. Each file has the Role, the Goal, the Instructions and, for the five specialists, the Managerial Context that the manager reads when deciding who to call.

| # | Agent | Its one question | File |
| --- | --- | --- | --- |
| 1 | Enterprise Prospect & Outreach Manager | Who does what next, and is each hand-off complete? | [1-manager.md](1-manager.md) |
| 2 | Account Evidence Researcher | What changed at this account, and do they already have this covered? | [2-account-evidence-researcher.md](2-account-evidence-researcher.md) |
| 3 | Opportunity Analyst | Is it relevant, why us, what next, and how much effort? | [3-opportunity-analyst.md](3-opportunity-analyst.md) |
| 4 | People Researcher | Who would we approach? | [4-people-researcher.md](4-people-researcher.md) |
| 5 | Outreach Writer | What do we say, and in what order? | [5-outreach-writer.md](5-outreach-writer.md) |
| 6 | Sales Reviewer | Would our best rep send this? | [6-sales-reviewer.md](6-sales-reviewer.md) |

What changed between versions, and why, is in [CHANGELOG.md](CHANGELOG.md).

## The flow

```
Salesperson gives one account
        |
     MANAGER                 team lead: routes, checks, assembles
        |
  1  ACCOUNT RESEARCHER      web search        What changed, and do they already have this covered?
        |   unclear name  ->  stop and ask for a website
  2  OPPORTUNITY ANALYST     knowledge base    Is it relevant, why us, what next, how much effort?
        |   not a draft   ->  stop: account owner / hold / outside the offer / research more
  3  PEOPLE RESEARCHER       web search        Who would we approach?   1 person at rating 3, up to 3 at rating 4 or 5
  4  OUTREACH WRITER         nothing           What do we say, and in what order?
  5  SALES REVIEWER          nothing           Would our best rep send this?   one rewrite at most
        |
  Account card for the salesperson to review. Nothing is sent.
```

Four decisions depend on what was found, which is why this is a manager and not a fixed chain:

1. **Identity.** An unclear name stops the run after the researcher.
2. **Action.** An existing relationship, a salesperson's note, an account outside the offer or a rating below 3 stops the run after the analyst.
3. **Effort.** A rating of 3, or a stretch fit at any rating, earns one candidate and one message. A core fit rated 4 or 5 earns up to three candidates, one message and an angle for each other role.
4. **Review.** A draft that fails the review is rewritten once. If it fails again it is shown as unfinished.

Each agent has one question, one resource and one output. The two researchers see the outside world. The analyst sees what the seller knows. The writer and the reviewer see only what they are handed.

## What each agent judges

The analyst returns four separate judgments, because one number cannot carry all of them.

| Judgment | Values | What it answers |
| --- | --- | --- |
| Fit | core, stretch, outside | Is this the kind of bank Madison is for right now? |
| Rating | 1 to 5, or unrated | How strong is the reason to talk now? |
| Relationship | published_existing, public_reference_unverified, unknown | Does Lyzr already know this account? |
| Evidence confidence | low, medium, high | Where did the facts come from, and how fresh are they? |

The next action is the first of these that applies:

1. `route_existing_owner`: Lyzr already has, or publicly mentions, a relationship. The account goes to its owner.
2. `hold_per_notes`: the salesperson's notes say not to contact, or to wait.
3. `outside_offer`: not a bank or credit union, or no credible conversation.
4. `research_more`: the rating is below 3, or a hook, a hypothesis, a discovery question or a quoted Madison capability is missing.
5. `exploratory_draft`: the rating is 3 or higher and all four exist.

Effort is set only with `exploratory_draft`: `one_contact` for a rating of 3 or a stretch fit, `buying_group` for a core fit rated 4 or 5.

## Setup in Studio

| Agent | Model | Tools and knowledge | Memory |
| --- | --- | --- | --- |
| Enterprise Prospect & Outreach Manager | `gpt-6-sol` | None. The five agents below are attached to it. | Off |
| Account Evidence Researcher | `gpt-6-sol` | Composio Search: DuckDuckGo search action only | Off |
| Opportunity Analyst | `gpt-6-sol` | Knowledge base `madison_seller_evidence`, Basic retrieval | Off |
| People Researcher | `gpt-6-sol` | Composio Search: DuckDuckGo search action only | Off |
| Outreach Writer | `gpt-6-sol` | None | Off |
| Sales Reviewer | `gpt-6-sol` | None | Off |

The knowledge base is described in [../knowledge-base](../knowledge-base).

## Building it in a new account

1. Create the knowledge base and add its three sources. Check that a search for "BMO" returns the BMO entry and a search for "core fit" returns the who-fits-best section.
2. Create the five specialists with the Role, Goal and Instructions in these files. Add the search tool to the two researchers and the knowledge base to the analyst.
3. Create the manager, attach the five specialists and paste each one's Managerial Context.
4. Read each saved field back against these files, then run the four test inputs in [../tests](../tests).

I did this three times, in three accounts. The last build is the one that was tested and published.

## How a call is made

Sub-agents in Studio share no context. The manager's instructions therefore say three things about every call:

- Paste every packet word for word, under its label. Never refer to "the research above".
- Begin each message with one line saying what is needed. A person may read these messages in the run's trace.
- Use `respond_directly=false`, `handoff=false` and `internal_call=true`, so the specialist returns to the manager and does not answer the salesperson itself.

The manager also checks each packet before moving on. If one is incomplete or contradicts itself, it makes one correction call and says exactly what is wrong. That check is separate from the Sales Reviewer's review of the email.

## What this does not do

It does not look up contact details, send anything, track replies or write to a CRM. A salesperson confirms the recipient and sends. Studio lists Gmail, Instantly, HubSpot and Salesforce among its pre-built tools, so that route exists. None of them was tested here.
