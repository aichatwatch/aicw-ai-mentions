---
title: Install
description: Run AICW AI Mentions with npx or install it globally with npm.
---

AICW AI Mentions needs Node.js 18 or newer. If you use an older version, the tool prints a message and stops.

## Run without an install

If you want to try the tool, use npx. The `@latest` tag makes npx fetch the newest version.

```sh
npx aicw-ai-mentions@latest setup-api-key
```

```sh
npx aicw-ai-mentions@latest scan "Y Combinator"
```

```sh
npx aicw-ai-mentions@latest serve
```

## Install with npm

If you use the tool often, install it globally.

```sh
npm install -g aicw-ai-mentions
```

Then run the same commands without `npx`.

```sh
aicw-ai-mentions setup-api-key
```

```sh
aicw-ai-mentions scan "Y Combinator"
```

```sh
aicw-ai-mentions serve
```

The `serve` command prints the local report address. Open it in your browser.

## Check the version

To see the installed version, run this command.

```sh
aicw-ai-mentions version
```

## Update

To check for a newer version, run this command.

```sh
aicw-ai-mentions update
```

The command does not install anything. It prints the command that you must run yourself. For a global install, that command is `npm install -g aicw-ai-mentions@latest`. If you use npx, the `@latest` tag already fetches the newest version.

The tool also checks for a new version in the background. See [Local data and privacy](/local-data-and-privacy#update-checks).

## Run from a source checkout

To work on the code, see [Contributing](/contributing).
