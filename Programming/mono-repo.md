Getting started:

npx create-nx-workspace --name queue --workspaceType integrated --useGithub --ci github --formatter none

Select None in terminal result:
```bash
 NX   Let's create a new workspace [https://nx.dev/getting-started/intro]

√ Which stack do you want to use? · none
```

Cd into generated folder
```bash
cd queue
```

Install generator and initialize the repo:
```bash
npm add -D @nx-dotnet/core
nx g @nx-dotnet/core:init

```

Update `nx.json` by adding the `generators` defaults:
```json
"generators": {
    "@nx-dotnet/core": {
        "application": {
            "language": "C#",
            "testTemplate": "xunit",
            "skipTests": false,
            "solutionFile": true,
            "useOpenApiGenerator": false,
            "skipSwaggerLib": true,
            "pathScheme": "dotnet"
        },
        "library": {
            "language": "C#",
            "testTemplate": "xunit",
            "skipTests": false,
            "solutionFile": true,
            "useOpenApiGenerator": false,
            "skipSwaggerLib": true,
            "pathScheme": "dotnet"
        }
    }
}
```

Force a reset of the cache:
```bash
nx reset
```

After adding this config you can use the generators:
Here are 2 options:
```bash
nx g @nx-dotnet/core:app [ProjectAppName] --directory=apps 
```
```bash
nx g @nx-dotnet/core:lib [ProjectLibName] --directory=libs
```

After generating a lib you can link it to a project using the following command
```bash
nx generate @nx-dotnet/core:project-reference --project=[ProjectAppName] --reference=[ProjectLibName]
```
