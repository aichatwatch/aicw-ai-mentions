---
title: Troubleshooting
description: Fix common problems and find answers to common questions.
---

## Problems

### Node.js is too old

The tool needs Node.js 18 or newer. If your version is older, the tool prints a message and stops. Install a newer version from [nodejs.org](https://nodejs.org/).

### No API keys were set

If the tool says that no API keys were set, run `aicw-ai-mentions setup-api-key`. You can also set `OPENROUTER_API_KEY`. See [API keys](/api-keys).

### The saved credentials cannot be decrypted

If you copied the data folder from another computer, the saved keys can fail to decrypt. Run `setup-api-key` again to replace the file.

### AICW_DATA_FOLDER does not exist

If you set `AICW_DATA_FOLDER` to a path that does not exist, the tool stops with an error. Create the folder or change the variable.

### Some answers failed

Some AI requests can fail because of rate limits or key problems. Run the command again. The tool saves the answers that it already has. If the problem stays, lower `AICW_CONCURRENT_REQUESTS` or raise `AICW_REQUEST_DELAY_MS`. See [Commands](/commands#environment-variables).

### A model does not work

If a model returns an error, run `aicw-ai-mentions check-models` to test the models. Providers can rename or remove models. Free models change often. See [Model presets](/model-presets).

### The question count is rejected

The `--questions` value must be a whole number from 1 to the number of questions in the template. See [Question templates](/question-templates).

### The template is rejected

You cannot use `--template` and `--template-text` in the same command. A template must have at least one question line.

### The port is busy

`serve` uses port 8080. If it is busy, the tool uses the next free port, up to 9 ports higher. The command prints the address that it uses.

### The browser does not open

Copy the address that `serve` prints and paste it in your browser.

### The report is empty or old

Run `aicw-ai-mentions rebuild-report-only "<project>"` to build the report again from saved data. If the answers are missing, run a new scan.

### The command stops with a vague error

Set `AICW_DEBUG` to `true` and run the command again. The tool then shows technical details. Errors are also written to `error.log` in the data folder.

## Questions

### Which AI models does the tool ask?

The default preset asks Perplexity, Claude, ChatGPT, Gemini, and Grok through OpenRouter. See [Model presets](/model-presets).

### How long does a scan take?

A full scan can take several minutes. The time depends on the number of questions and the speed of the models.

### Does a scan cost money?

The tool is free. The AI providers can charge for the requests that you send with your API key. Check the prices in your OpenRouter account.

### Can I scan the same subject again?

Yes. A new scan creates a new project with a name such as `Y Combinator_1`. To compare data over time, see the `--date` flag in [Commands](/commands#dates).

### Is my data sent to AICW?

No. The tool has no AICW server. See [Local data and privacy](/local-data-and-privacy).

### How do I update the tool?

Run `aicw-ai-mentions update`. It prints the command to run. See [Install](/install#update).

## Get help

To report a bug or ask a question, open an issue on [GitHub](https://github.com/aichatwatch/aicw-ai-mentions/issues). For other contact, use the [AICW contact page](https://aichatwatch.com/quote).
