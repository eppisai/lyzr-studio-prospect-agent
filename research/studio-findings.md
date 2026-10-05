# What I learned about Lyzr Studio while building this

Each point below came from something that happened in a run. The last column is what I would want the product to do about it.

## How a manager and its specialists really behave

| What I saw | How it showed up | What I did | What the product could do |
| --- | --- | --- | --- |
| Sub-agents share no context. | The first run: the manager called the analyst and passed no research. | Every call carries the full packets, pasted in under labels. | Shared, typed state that every agent in a run can read. |
| A specialist can answer the user directly and end the run. | The researcher replied to the user twice in early runs. | Every call sets `respond_directly=false`, `handoff=false` and `internal_call=true`. | Make "return to the manager" the default for an attached specialist. |
| A manager will do a specialist's work if it can. | It wrote the email itself when the writer returned the wrong thing. | The manager is told not to write copy, and to show the writer's text exactly. | Let a builder mark a step as "must come from this specialist". |
| A hand-off is described in three separate fields. | The manager's instructions, the specialist's Managerial Context and the specialist's own instructions each say what is passed. When the People Researcher was added, the three that describe the reviewer's input were not updated, and the reviewer went two runs without the people research. No error appeared. | I fixed the three lines and compared every packet character for character. | Define each hand-off once, and warn when an agent expects an input that nothing sends. |

## Tools and knowledge

| What I saw | How it showed up | What I did | What the product could do |
| --- | --- | --- | --- |
| A tool can be selected and still not reach the running agent. | A second search tool was selected on the build screen and was never available at run time, even in a test with that tool alone. | Removed it and used the DuckDuckGo action only. | Show on the build screen what the agent can actually call. |
| Search returns excerpts, not pages. | The agent called an event's status unknown when the bank's own release had settled it. | Every fact is marked as a search excerpt. The researcher checks the latest status of any event it cites. | A fetch-the-page step for a link the agent wants to rely on. |
| Search and word budgets are only instructions. | An early researcher ran more searches than its prompt allowed. The final cards ran over their 200-word cap. | Recorded as known misses. | Runtime limits per agent: a maximum number of tool calls, a maximum output length. |
| A small knowledge base returns fewer chunks than asked for. | Ten chunks were requested and five came back, because the three sources make only five chunks. | Checked retrieval on its own before attaching it. | Show the chunk count next to the retrieval setting. |
| The knowledge base can change a decision. | Web search found no link between BMO and Lyzr. The knowledge base did, and the run stopped before any outreach. | Kept the seller's knowledge on the analyst only. | This is the pattern I would lead with when showing a knowledge base to a customer. |

## Testing and looking back at a run

| What I saw | How it showed up | What I did | What the product could do |
| --- | --- | --- | --- |
| The same input can give a different answer. | Huntington rated 4 in one run and 3 in the next. One skipped research check moved the rating. | Every check runs once before any is repeated. The card always shows its evidence. | A stability check: run the same input twice and show where the runs differ. |
| There is no saved test set. | After each prompt change I reran the test banks by hand in new chats. | Kept the inputs and expected paths in a file. | A test set per build, with the expected path for each input and a pass or fail after every change. |
| A reopened chat loses its step-by-step activity. | The Activity panel said "No activity yet" when a finished chat was reopened. Traces did persist, with names cut short in the timeline. | Captured the activity while each run was open. | Keep the activity with the chat. An agent that works from evidence has to be auditable later. |
| Source links can turn into attachments. | In one answer, three cited links were shown as PDF chips and their labels dropped out of the sentences. | Noted beside that output. | Keep a cited link inline. |
| What is saved can differ from what was pasted. | Before one round, two saved fields held duplicated text. | After every paste, each saved field was read back and compared with the file. | Version the fields, and show a diff between versions. |

## Why this matters for Architect

Architect builds agents from a prompt. In a build with more than one agent, the parts I spent the most time on were not the prompts for each agent. They were the hand-offs between agents, the test set, and being able to see what a finished run actually did. Those are the parts I would want Architect to generate and check for the builder.

## Lyzr pages I read for this

- [Agent Studio](https://docs.lyzr.ai/enterprise/agent-studio/agents/studio): build, playground, versions and deployment.
- [Manager agents](https://docs.lyzr.ai/enterprise/agent-studio/manageragent/studio): delegation, and keeping tools and knowledge on the specialists that need them.
- [Knowledge bases](https://docs.lyzr.ai/enterprise/agent-studio/knowledgebase/studiokb): adding sources and checking what is retrieved.
- [Madison](https://www.madison.lyzr.ai/), [Jazon](https://www.lyzr.ai/jazon/) and the [Prospect Research Agent blueprint](https://www.lyzr.ai/blueprints/sales/prospect-research-agent/).
