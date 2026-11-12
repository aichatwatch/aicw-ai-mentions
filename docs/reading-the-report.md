---
title: Reading the report
description: What the Mentions, Links, and Link Domains tabs show, and how to filter and export them.
---

After a scan, run `aicw-ai-mentions serve` and open the address it prints. The report has three tabs. They are in this order: Mentions, Links, Link Domains.

## Mentions

The Mentions tab lists the people, organizations, products, and brands that the AI models name in their answers.

<Frame>
  <img src="/imgs/mentions.png" alt="The Mentions tab. A table of names with columns for voice, position, mentions, and AI models." />
</Frame>

## Links

The Links tab lists each URL that the AI models cite.

<Frame>
  <img src="/imgs/links.png" alt="The Links tab. A table of cited URLs with columns for voice, position, citations, and AI models." />
</Frame>

## Link Domains

The Link Domains tab groups the cited URLs by website. Use it to see which websites the AI models trust most for your subject.

<Frame>
  <img src="/imgs/link-domains.png" alt="The Link Domains tab. A table of websites with columns for voice, position, citations, and AI models." />
</Frame>

## The columns

| Column | Meaning |
| --- | --- |
| Mention, Link, or Domain | The item that the AI models named or cited. |
| Voice | The share of voice of the item. A higher value means the item is more visible across the models. |
| Position | Where the item appears in the answers. Position 1 is the first place. |
| Mentions or Citations | How many times the models named or cited the item. |
| AI | The models that named or cited the item. |

Share of voice combines two things. The first is how many models name the item. Models with more users count more. The second is how early the item appears in the answers. An item that most models name near the top has the highest voice.

## Filter, search, and export

- Use the model list to show only one AI model.
- Use the **Search table** box to find an item.
- Click **Export CSV** to save the table as a CSV file.

## Open an old report

Reports stay in your [data folder](/local-data-and-privacy#where-the-files-are). To see them again, run `aicw-ai-mentions serve`. To make a report again from saved data, with no AI calls, use `rebuild-report-only`. See [Commands](/commands#rebuild-report-only).

## See a full example

Open the [live demo report](https://aichatwatch.com/demo/aicw-ai-mentions/) for the subject "Y Combinator".
