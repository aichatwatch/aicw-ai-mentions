---
title: Quickstart
description: Save an API key, run a scan, and open the report.
---

This page shows the fastest way to get a report. You need Node.js 18 or newer and an OpenRouter API key. See [API keys](/api-keys) if you do not have a key.

<Steps>
  <Step title="Save your API key">
    Run this command. It asks for your OpenRouter API key and stores it in a local, encrypted file.

    ```sh
    npx aicw-ai-mentions@latest setup-api-key
    ```
  </Step>
  <Step title="Run a scan">
    Run this command. It asks every question of the default template to the AI models. Replace `Y Combinator` with your own subject.

    ```sh
    npx aicw-ai-mentions@latest scan "Y Combinator"
    ```

    A scan can take several minutes.
  </Step>
  <Step title="Open the report">
    Run this command. It starts a local web server and tries to open your browser.

    ```sh
    npx aicw-ai-mentions@latest serve
    ```

    If the browser does not open, copy the address that the command prints. It starts with `http://localhost:`.
  </Step>
</Steps>

<Note>
A scan sends your questions to AI models and uses your API key. The provider can charge you for this. See [Local data and privacy](/local-data-and-privacy) for what is sent.
</Note>

## Next steps

- Change the questions: [Question templates](/question-templates).
- Understand the tables: [Reading the report](/reading-the-report).
- Run the tool often: [Install](/install) it with npm.
