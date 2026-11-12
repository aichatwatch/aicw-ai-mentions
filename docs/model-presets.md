---
title: Model presets
description: The four bundled sets of AI models, and which one a scan uses.
---

A model preset is a named set of AI models. A preset lists the models that answer the questions. It also names the model that reads the answers and extracts the names.

## The default preset

Every scan uses the preset `ai_chats_with_search`. The tool writes this name into the `project.json` file of the scan.

| Part | Models |
| --- | --- |
| Models that answer | Perplexity Sonar Pro Search, Anthropic Claude Sonnet (latest), OpenAI ChatGPT (latest), Google Gemini Flash (latest), xAI Grok (latest) |
| Model that extracts names | OpenAI GPT-4o mini |

These models can search the web. The tool calls all of them through OpenRouter.

## All bundled presets

| Preset name | Models that answer |
| --- | --- |
| `ai_chats_with_search` | Perplexity Sonar Pro Search, Claude Sonnet, ChatGPT, Gemini Flash, Grok |
| `foundation_models` | Llama 3.3 70B, Qwen QwQ 32B, DeepSeek Chat V3 |
| `foundation_models_lgd` | Llama 3.3 70B, Gemini 2.0 Flash Exp, DeepSeek Chat V3 |
| `foundation_models_lgdq` | Llama 3.3 70B, Qwen QwQ 32B, DeepSeek Chat V3, Gemini 2.0 Flash Exp |

All presets use OpenAI GPT-4o mini to extract the names. All presets use OpenRouter, so one `OPENROUTER_API_KEY` is enough.

<Note>
The three `foundation_models` presets use models that OpenRouter has marked as free. Providers can change or remove free models. If a model stops working, run `aicw-ai-mentions check-models`.
</Note>

## Change the preset of a scan

The `project.json` file of a scan has an `ai_preset` field. To use another preset, put one of the preset names from the table in this field. See [Local data and privacy](/local-data-and-privacy#where-the-files-are) for the file location.

If the name is not a bundled preset, the tool stops and lists the names that it knows.

## Check that models still work

To send a short test message to every model in the model list, run this command.

```sh
aicw-ai-mentions check-models
```

This command calls the AI providers with your API keys. Each call can cost money.
