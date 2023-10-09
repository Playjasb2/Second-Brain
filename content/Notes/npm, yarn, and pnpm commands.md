---
date: 2023-10-08
tags:
  - webdev
---
| npm Command                           | yarn Equivalent                     | pnpm Equivalent                     |
|---------------------------------------|-------------------------------------|-------------------------------------|
| `npm install`                         | `yarn` or `yarn install`            | `pnpm install`                      |
| `npm install <package>`               | `yarn add <package>`                | `pnpm add <package>`                |
| `npm install <package> -g`            | `yarn global add <package>`         | `pnpm add <package> --global`       |
| `npm update <package>`                | `yarn upgrade <package>`            | `pnpm update <package>`             |
| `npm uninstall <package>`             | `yarn remove <package>`             | `pnpm uninstall <package>`          |
| `npm install --no-package-lock`       | `yarn install --no-lockfile`        | N/A                                 |
| `npm ci`                              | `yarn install --frozen-lockfile`    | `pnpm install --frozen-lockfile`    |
| `npm install <package> --save-dev`    | `yarn add <package> --dev`          | `pnpm add <package> --save-dev`     |
| `npm install <package> --save-optional`| `yarn add <package> --optional`     | `pnpm add <package> --save-optional`|
| `npm install <package> --save-peer`   | `yarn add <package> --peer`         | `pnpm add <package> --save-peer`    |
| N/A                                   | `yarn upgrade-interactive`          | `pnpm update --interactive`         |
| `npm cache clean`                     | `yarn cache clean`                  | N/A                                 |
| `npm run <script>`                    | `yarn run <script>`                 | `pnpm run <script>` or `pnpm <script>`|
| `npm list`                            | `yarn list`                         | `pnpm list`                         |
| `npm audit`                           | `yarn audit`                        | `pnpm audit`                        |

| npx Command               | yarn Equivalent       | pnpm Equivalent       |
|---------------------------|-----------------------|-----------------------|
| `npx <command>`           | `yarn dlx <command>` (Yarn 2) | `pnpm exec <command>` |
| `npx create-react-app my-app` | `yarn dlx create-react-app my-app` (Yarn 2) | `pnpm dlx create-react-app my-app` |

