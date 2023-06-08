# UpdateAssemblyInfoSlim

A custom task extension for Azure DevOps, that edits the
`Properties/AssemblyInfo.cs` file inside a `.NET Framework` project.

> This is a new patch, originaly made from [UpdateAssemblyInfo](https://github.com/BoolBySigma/UpdateAssemblyInfo).

## Prerequisites

- [VisualStudio](https://visualstudio.microsoft.com/downloads/)

- [Node.js](https://nodejs.org/en/download)

- Once having Node, then install `tfx-cli` with:
  ```
  npm i -g tfx-cli
  ```

## Build

- Build the `Bool.PowerShell.sln` project with VisualStudio.

- After you build the project, you must place the newly built
  `Bool.PowerShell.UpdateAssemblyInfo.dll` in
  `Extension/update-assembly-info-task/Bool.PowerShell.UpdateAssemblyInfo.dll`.

- Navigate to the `Extension` directory with:
  ```
  cd Extension
  ```

- Build the `.vsix` executable:
  ```
  tfx extension create --manifest-globs vss-extension.json
  ```

> ### NOTE:
> Before every build:
> - You must manually update the `version` in [`Extension/vss-extension.json`](/Extension/vss-extension.json) to a new version.
> - You must manually update the `version` in [`task.json`](/Extension/update-assembly-info-task/task.json) to a new version.
>
> If you don't do this, then when you upload the new built extension to Azure DevOps, it won't recognize the new build.
