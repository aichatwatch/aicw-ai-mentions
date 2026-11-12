---
title: AICW AI Mentions
description: A free command line tool that asks several AI models the same questions and builds a local report of the names and links they give.
---

AICW AI Mentions is an open-source tool from AI Chat Watch (AICW). It shows how AI assistants talk about a company, a product, a person, or a topic. Use it to see which names and websites the AI models give when people ask about your subject.

The tool runs on your computer. It asks several AI models the same questions. It finds the names and the links in the answers. Then it builds an HTML report that you open in your browser.

## What you get

The report has three tabs:

- **Mentions** lists the people, organizations, and products that the AI models name.
- **Links** lists the web pages that the AI models cite.
- **Link Domains** groups the cited links by website.

You can filter by model, search the tables, and export each table as a CSV file.

<Frame>
  <img src="/imgs/mentions.png" alt="The Mentions tab of an AICW AI Mentions report. It shows names ranked by share of voice." />
</Frame>

You can see a finished report in the [live demo](https://aichatwatch.com/demo/aicw-ai-mentions/).

## Where to start

<CardGroup cols={2}>
  <Card title="Quickstart" href="/quickstart">
    Run your first scan in a few minutes.
  </Card>
  <Card title="Install" href="/install">
    Run the tool with npx or install it with npm.
  </Card>
  <Card title="Read the report" href="/reading-the-report">
    Learn what each column in the report means.
  </Card>
  <Card title="Use it from an AI agent" href="/mcp-server">
    Start the MCP server for Claude, Codex, or ChatGPT.
  </Card>
</CardGroup>

## What you need

- Node.js 18 or newer.
- An OpenRouter API key. See [API keys](/api-keys).

## License and source

The tool uses the MIT license. The npm package is `aicw-ai-mentions`. The source code is on [GitHub](https://github.com/aichatwatch/aicw-ai-mentions). To report a bug or ask a question, open a GitHub issue. For other contact, use the [AICW contact page](https://aichatwatch.com/quote).
