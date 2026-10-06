# Micro Installation Guide

## Option 1: Install from VSIX (quickest)
1. Open Visual Studio Code.
2. Press `Ctrl+Shift+P` and run **Extensions: Install from VSIX...**
3. Select the `vscode-aem-sync-1.0.5.vsix` file.
4. Reload VS Code when prompted.

## Option 2: Build and install locally (for development)
1. Install dependencies:
   ```bash
   npm install
   ```
2. Package the extension:
   ```bash
   npx vsce package
   ```
3. In VS Code, run **Extensions: Install from VSIX...** and choose the generated `.vsix` file.

## Auto-rollout script example
Use this PowerShell script to package and install (or update) the extension automatically:

```powershell
$ErrorActionPreference = "Stop"

# 1) Build VSIX
npm install
npx vsce package

# 2) Get the newest VSIX in the current folder
$vsix = Get-ChildItem -Filter "*.vsix" |
  Sort-Object LastWriteTime -Descending |
  Select-Object -First 1

if (-not $vsix) {
  throw "No VSIX file found."
}

# 3) Install/update in VS Code
code --install-extension $vsix.FullName --force

Write-Host "Installed: $($vsix.Name)"
```
