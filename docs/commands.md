---
title: Commands
description: Reference for every command, flag, and environment variable of the aicw-ai-mentions CLI.
---

The command is `aicw-ai-mentions`. If you do not install it, put `npx aicw-ai-mentions@latest` in front of each command.

If you run the command with no arguments, it opens an interactive menu. Add `--advanced` to the menu command to show the advanced items.

```sh
aicw-ai-mentions --advanced
```

## Main commands

### scan

Creates a scan for a subject, asks the AI models, and builds the report. `new` is another name for `scan`.

```sh
aicw-ai-mentions scan "Y Combinator"
```

The scan saves a project in your [data folder](/local-data-and-privacy#where-the-files-are). The project name comes from the subject. If a project with that name exists, the tool adds `_1`, `_2`, and so on. A scan needs an API key. See [API keys](/api-keys).

| Flag | Meaning |
| --- | --- |
| `--template <path>` or `-t <path>` | Use a question template file. |
| `--template-text <text>` or `--template-inline <text>` | Use questions from a string. Write `\n` between questions. |
| `--questions <N>` or `-q <N>` | Run only the first N questions. |
| `--date <date>` | Use a date for the run. See [Dates](#dates). |

See [Question templates](/question-templates) for the details.

### serve

Starts a local web server for your reports and tries to open your browser.

```sh
aicw-ai-mentions serve
```

The server uses port 8080. If that port is busy, it tries the next ports, up to 9 more. To start at a different port, set the `PORT` environment variable. The command prints the final address.

### mcp

Starts the MCP server. See [MCP server](/mcp-server) for the flags `--http`, `--stdio`, `--port`, `--host`, and `--path`.

```sh
aicw-ai-mentions mcp
```

### setup-api-key

Asks for your API key and saves it in an encrypted file. See [API keys](/api-keys).

```sh
aicw-ai-mentions setup-api-key
```

### show-user-data-location

Prints the data folder of the tool.

```sh
aicw-ai-mentions show-user-data-location
```

## Commands for a saved project

These commands take the name of a saved project. Use the name that the scan created. If the name has spaces, put it in quotes.

### build

Asks the AI models, analyzes the answers, and builds the report. The `scan` command runs this step for you. It needs an API key.

### rebuild

Analyzes the saved answers again and builds the report. It does not ask the models the questions again. It calls an AI model to extract the names, so it needs an API key. This command analyzes the saved answers of the project "Y Combinator" again.

```sh
aicw-ai-mentions rebuild "Y Combinator"
```

### rebuild-report-only

Builds the report from saved answers and citations. It does not call any AI model and needs no API key. This command builds the report of the project "Y Combinator" again.

```sh
aicw-ai-mentions rebuild-report-only "Y Combinator"
```

### Advanced commands

These commands are shown in the menu only with `--advanced`. You can run them from the command line at any time.

| Command | What it does |
| --- | --- |
| `transform-answers <project>` | Makes the `answer.md` files again from the `answer.json` files. |
| `verify-links <project>` | Removes links that are not valid. See [Link checks](#link-checks). |
| `fetch-answers-ai <project>` | Fetches the AI answers only. Needs an API key. |

## Other commands

| Command | What it does |
| --- | --- |
| `check-models` | Sends a test message to every model in the model list. Needs API keys. |
| `version` | Shows the version. `--version` and `-v` do the same. |
| `update` | Checks for a newer version and prints how to install it. `u` does the same. |
| `license` | Shows the license text. |
| `help` | Shows the documentation. `--help` and `-h` do the same. |

## Dates

The `--date` flag sets the date of the data to use. Write it as `YYYY-MM-DD`. The date must be one that has complete answers in the project. If it does not, the command stops with an error. You can also set the `AICW_TARGET_DATE` environment variable. The MCP tool `aicw_rebuild_report` takes the same date.

## Link checks

Link checks are off by default. The `scan`, `build`, and `rebuild` commands do not run them. Run `verify-links` when you want them.

The command removes links with a wrong format, links with a domain that does not resolve, and links that return a 404 or 410 status. By default it also opens each link on the web. To check only the format and skip the web requests, set `AICW_VERIFY_LINKS` to `false`.

## Environment variables

| Variable | Meaning | Default |
| --- | --- | --- |
| `OPENROUTER_API_KEY` | OpenRouter key. | not set |
| `OPENAI_API_KEY` | OpenAI key. | not set |
| `ANTHROPIC_API_KEY` | Anthropic key. | not set |
| `PERPLEXITY_API_KEY` | Perplexity key. | not set |
| `AICW_DATA_FOLDER` | A folder to use instead of the default [data folder](/local-data-and-privacy#where-the-files-are). The folder must exist. | not set |
| `AICW_VERIFY_LINKS` | If `false`, `verify-links` checks only the link format. | not set |
| `AICW_SKIP_UPDATE_CHECK` | If `true`, the tool skips the background update check. | not set |
| `AICW_CONCURRENT_REQUESTS` | How many AI requests run at the same time. | 2 |
| `AICW_REQUEST_DELAY_MS` | The pause between requests, in milliseconds. | 300 |
| `AICW_AI_CACHE_TTL_SECONDS` | How long the tool keeps saved AI responses. `0` turns the cache off. | 94608000 (3 years) |
| `AICW_TARGET_DATE` | The date to use, like `--date`. | not set |
| `AICW_DEBUG` | If `true`, shows technical details when an error occurs. | not set |
| `PORT` | The first port for `serve`. | 8080 |

To set a variable for one command on macOS or Linux, put it before the command.

```sh
AICW_CONCURRENT_REQUESTS=1 aicw-ai-mentions scan "Y Combinator"
```

If AI requests fail often, use a lower `AICW_CONCURRENT_REQUESTS` value or a higher `AICW_REQUEST_DELAY_MS` value.
