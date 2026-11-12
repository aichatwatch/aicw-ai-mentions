---
title: Local data and privacy
description: Where the tool stores files, what it sends to which service, and how to control it.
---

The tool runs on your computer. It has no AICW server. Your projects, reports, logs, cache, and saved keys stay on your machine. The tool sends data to other services only in the cases on this page.

## Where the files are

The tool stores everything in one data folder. To print the exact path, run this command.

```sh
aicw-ai-mentions show-user-data-location
```

| System | Default data folder |
| --- | --- |
| macOS | `~/Library/Application Support/aicw/` |
| Windows | `%APPDATA%\aicw\` |
| Linux | `~/.config/aicw/` |

On Linux, if `XDG_CONFIG_HOME` is set, the folder is `$XDG_CONFIG_HOME/aicw`. To use another folder, set `AICW_DATA_FOLDER` to the path of an existing folder.

The data folder has these parts:

| Path | Content |
| --- | --- |
| `projects/` | One folder for each scan. It has `questions.md`, `project.json`, and the questions with their answers. |
| `reports/` | The HTML reports. Each scan has a folder here. |
| `cache/` | Saved AI responses and the result of the update check. |
| `logs/` | Log files. |
| `config/.credentials/credentials.json` | Your saved API keys, encrypted. |
| `error.log` | Errors from the command line. |

## What the tool sends

| When | What is sent | To whom |
| --- | --- | --- |
| `scan`, `build`, `fetch-answers-ai` | Your questions, with the subject filled in, and a short instruction to include source links. | OpenRouter, which passes them to the model provider |
| `scan`, `build`, `rebuild` | The text of the AI answers, so that a model can extract the names. | OpenRouter, which passes it to the model provider |
| `check-models` | A short test message. | The model providers |
| `verify-links` | A web request to each cited link. | The websites of those links |
| Background update check | A request for the package data of `aicw-ai-mentions`. | The npm registry |

Your API key goes only to the provider of the key. The key is not part of the questions.

The scan sends the subject and the question text. Do not put private or secret information in a subject or a template.

Reports are static HTML files. The report pages load their style sheets and scripts from the web, so your browser contacts those hosts when you open a report. The tool does not send your report data in these requests.

## Saved keys

`setup-api-key` saves keys in an encrypted file with permissions for your user only. A key that you set as an environment variable is not saved. If you copy the file to another computer, the tool may not be able to decrypt it. In that case, run `setup-api-key` again.

## Update checks

When you run a command in a terminal, the tool checks the npm registry in the background for a newer version. It shows a notice if one exists. It never installs anything.

The check runs at most one time every 24 hours. It does not run when the output is redirected, for example in a script. To turn it off, set `AICW_SKIP_UPDATE_CHECK` to `true`.

## Link checks

The tool does not open the cited links while it scans. Link verification is off by default. When you run `verify-links`, the tool sends a request to each link. See [Commands](/commands#link-checks).

## Remove your data

To remove your data, delete the data folder. To remove only one scan, delete its folder in `projects/` and in `reports/`.
