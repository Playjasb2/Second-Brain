---
date: 2023-10-21
tags:
  - webdev
---
Nx Docs: https://nx.dev/nx-cloud/recipes/other/ci-deployment

If we want [[Nx]] to generate a package.json for each app for deployment, do the following:

Do either:

1. Define a default in `nx.json`:

```json
{
  "targetDefaults": {
    "build": {
      "executor": "@nx/webpack:webpack",
      "options": {
        "generatePackageJson": true
      },
      // ...
    },
    // ...
  },
  // ...
}
```

2. Define a project-specific setting in `project.json`:

```json
{
  "targets": {
    "build": {
      "executor": "@nx/webpack:webpack",
      "options": {
        "generatePackageJson": true
      },
      //...
    },
    // ...
  }
  // ...
}
```

3. Define a project-specific setting in `package.json`:

```json
{
  "name": "...",
  "scripts": {
    // ...
  },
  "nx": {
    "targets": {
      "build": {
        "executor": "@nx/webpack:webpack",
        "options": {
          "generatePackageJson": true
        },
      },
      // ...
    },
    // ...
  },
  // ...
}
```

Source: https://stackoverflow.com/questions/57616136/generate-package-json-on-nx-build-deployment