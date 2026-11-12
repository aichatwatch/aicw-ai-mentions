---
title: Question templates
description: Change the questions that a scan asks to the AI models.
---

A scan asks a list of questions to every AI model. A question template is a text file or a text string that holds this list. If you give no template, the tool uses the built-in default template.

## The default template

The default template has three questions. They ask:

1. What the subject is known for, and which organizations, products, people, publications, communities, or websites are linked to it.
2. Which alternatives, competitors, partners, or other players are named with the subject.
3. Which sources a model would cite to check claims about the subject.

Each question asks the model to give direct source links.

## Template rules

- Each non-empty line is one question.
- A line that starts with `#` is a comment. The tool ignores it.
- A line can start with `-`, `*`, or a number such as `1.` or `1)`. The tool removes this prefix.
- Write `{{SUBJECT}}` where the subject must appear. The tool replaces it with the subject you give to `scan`.

Example template file:

```md
# My questions
Which sources cite {{SUBJECT}} most often?
Which competitors or alternatives are named near {{SUBJECT}}?
```

## Use a template file

To use your own file, give its path with `--template`. You can also use `-t`.

```sh
aicw-ai-mentions scan "Y Combinator" --template ./questions.md
```

## Use a template string

To give the questions on the command line, use `--template-text`. Write `\n` between the questions. The tool changes each `\n` to a new line.

```sh
aicw-ai-mentions scan "Y Combinator" --template-text "Who mentions {{SUBJECT}}?\nWhich links cite {{SUBJECT}}?"
```

`--template-inline` is another name for `--template-text`.

<Warning>
You cannot use `--template` and `--template-text` together. The scan stops with an error. If the template has no questions, the scan also stops.
</Warning>

## Run only the first questions

By default, the scan runs every question in the template. To run only the first few, use `--questions` (or `-q`) with a number.

```sh
aicw-ai-mentions scan "Y Combinator" --questions 2
```

The number must be a whole number from 1 to the number of questions in the template. Other values cause an error.

## Questions from an AI agent

The MCP tool `aicw_scan` takes the same options. See [MCP server](/mcp-server).
