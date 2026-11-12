---
title: Contributing
description: Set up a source checkout, build the tool, and run the tests.
---

The source code is on [GitHub](https://github.com/aichatwatch/aicw-ai-mentions). The tool uses the MIT license. To report a bug or ask a question, open a [GitHub issue](https://github.com/aichatwatch/aicw-ai-mentions/issues).

## Set up

Clone the repository and install the packages. You need Node.js 18 or newer.

```sh
git clone https://github.com/aichatwatch/aicw-ai-mentions.git
```

```sh
cd aicw-ai-mentions
```

```sh
npm install
```

## Build and test

The tool is written in TypeScript. The build step compiles it to the `dist` folder.

```sh
npm run build
```

To build and run the tests, use this command. The tests use temporary data folders and test keys. They do not need a real API key.

```sh
npm test
```

## Useful scripts

| Script | What it does |
| --- | --- |
| `npm run build` | Compiles the code and copies the config files. |
| `npm run dev` | Compiles again when a file changes. |
| `npm test` | Builds, then runs the test files in `tests/`. |
| `npm run test:local` | Builds, then runs the `help` command. |
| `npm run link:local` | Builds and links the command to your computer. |
| `npm run unlink:local` | Removes that link. |
| `npm run package:dry` | Shows what the npm package would contain. |
| `npm run demo:build` | Maintainer helper. It writes demo output to `.demo-data/`. |
| `npm run clean` | Removes `dist/`, `.last-build`, `*.tgz`, and `.tmp/`. |

To run the built tool from the checkout, use this command.

```sh
node bin/aicw-ai-mentions.js help
```

## Send a change

Open a pull request on GitHub. Run `npm test` before you send it.
