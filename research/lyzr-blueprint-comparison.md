# How this build compares with Lyzr's own Prospect Research Agent

Lyzr publishes a [Prospect Research Agent blueprint](https://www.lyzr.ai/blueprints/sales/prospect-research-agent/) for sales development teams, and sells Jazon, which researches prospects and writes outbound messages. I read both before settling the scope. This page says plainly what my build covers and what it does not.

## Two halves of prospecting

Prospecting has two halves:

1. **Find prospects.** Start from filters such as industry, size and geography and produce a list.
2. **Judge one prospect.** Decide whether it is worth a salesperson's time, and if so who to approach and what to say.

For banks and credit unions, the first half is the easy one. Every US bank and credit union is on a public list. So I built the second half, in depth, for one account at a time. The workflow can be turned around to filter a list first and then judge each account. I kept it to one account so the reasoning stays visible.

## Side by side

| What Lyzr's blueprint describes | In this build |
| --- | --- |
| Finding prospects from filters such as industry, revenue and geography | Not built. The salesperson supplies one account. |
| Enriching records from data providers and the CRM | Web search only. Facts are search excerpts with links. |
| Scoring on fit | Built. Fit is core, stretch or outside, with a one-sentence reason. |
| Scoring on intent signals | Partly. Timing is rated from 1 to 5 from public events such as a merger or a stated program. No intent-data provider is used. |
| Scoring on engagement history | Stood in for by a text file of accounts Lyzr names publicly. No CRM history. |
| Naming key decision-makers and buying triggers | Built, with a limit. One to three candidates from the bank's own pages or filings, marked "to confirm". No data provider verifies a title. |
| Preparing personalised outreach | Built. One email, a LinkedIn note and a follow-up, checked by a separate reviewer agent. |
| Syncing with a CRM | Not built. |
| Processing thousands of records | Not built. One account per run, about three minutes for a full run. |

## What this build adds

Things the blueprint page does not describe, and that I think matter for an enterprise sales team:

- **It can say no.** Two of the four test banks did not get an email. One went to its account owner, and for one the agent asked which bank was meant.
- **The next action is separate from the score.** Three banks scored 3 out of 5 and got three different next steps.
- **Every fact carries its source and its strength.** The card shows the counterevidence and the biggest open question, and says what evidence would change the rating.
- **A reviewer checks the email against the evidence** before a salesperson sees it, and can send it back once.
- **Nothing is sent.** A person confirms the recipient and the facts.

## Where this would sit next to Jazon

Jazon is Lyzr's sales product for account prioritisation, research and outbound writing. This build is a narrower thing: for one account, it decides whether outreach has been earned at all, and what can honestly be said in the first message. I see it as a step before a sequence starts, not a replacement for one.

## What I did not measure

The blueprint page gives performance figures. I have none to set beside them. Nothing was sent to any prospect, so there are no reply rates, and I did not time a salesperson with and without the agent.
