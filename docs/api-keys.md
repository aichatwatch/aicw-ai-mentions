---
title: API keys
description: Get an OpenRouter API key and give it to the tool.
---

The tool asks AI models through the OpenRouter service. One OpenRouter key gives access to many AI models. All four bundled [model presets](/model-presets) use OpenRouter.

## Get a key

1. Sign up at [openrouter.ai](https://openrouter.ai/auth/signup).
2. Create a key on the [keys page](https://openrouter.ai/keys).

OpenRouter and the model providers can charge for requests. Check the prices in your OpenRouter account before you run a large scan.

## Give the key to the tool

Use one of these methods.

### Method 1: the setup command

Run this command. It asks for the key and stores it in an encrypted file in your [data folder](/local-data-and-privacy#where-the-files-are).

```sh
aicw-ai-mentions setup-api-key
```

The command checks the key format. An OpenRouter key must start with `sk-` and have at least 40 characters. If a key is already saved, press Enter to keep it.

### Method 2: an environment variable

If you prefer a variable, set `OPENROUTER_API_KEY` in your shell.

```sh
export OPENROUTER_API_KEY=sk-or-...
```

### Method 3: an env file

Put `OPENROUTER_API_KEY` in a `.env.local` or `.env` file. The tool reads these files from the folder where you run the command.

## Which key wins

If you set a variable in the shell, it has priority over the saved key. The tool uses the saved key only when the variable is not set.

## Other key names

The tool also accepts these names:

| Name | Provider |
| --- | --- |
| `OPENAI_API_KEY` | OpenAI |
| `ANTHROPIC_API_KEY` | Anthropic |
| `PERPLEXITY_API_KEY` | Perplexity |

No bundled preset uses these keys. The bundled model list has a few models that call OpenAI directly. Before a scan, the tool checks that at least one of the four keys is set.

<Warning>
Use an API key from the provider. Do not use a chat subscription login in a third-party tool. Do not paste a key into a chat message or into a public file.
</Warning>
