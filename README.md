# Angular 16 CRUD App — Azure DevOps CI/CD Deployment

## Overview

Deployed a full **Angular 16 CRUD application** to **Azure App Service** using a fully automated **CI/CD pipeline** built in **Azure DevOps**. This project covers cloud infrastructure provisioning, build automation, and release management — following professional DevOps practices used in enterprise environments.

---

## What Was Done

**1. Provisioned Azure App Service**
Created a Web App (`Angular123456`) on Azure App Service with Node.js 22 LTS runtime on Windows, hosted in the Korea South region under resource group `Angular`.

**2. Stored Source Code in Azure Repos**
Pushed the Angular 16 CRUD project to Azure Repos (`AngularFe` repository), including all config files: `angular.json`, `tsconfig.json`, `package.json`, and the full `src/` directory.

**3. Built the CI Pipeline**
Created `AngularFe-CI` pipeline in Azure DevOps with three automated tasks:
- `npm install` — restores all project dependencies
- `npm run ng build` — compiles the Angular app into a production build
- `Publish Artifact: drop` — packages the `/dist/angular-16-crud` output as a deployable artifact

✅ Build #123 completed successfully in 1 minute 52 seconds.

**4. Configured the CD Release Pipeline**
Set up a Release Pipeline (`New release pipeline`) with a single deployment stage:
- Connection type: **Azure Resource Manager**
- Task: **Azure App Service Deploy** targeting `Angular123456`
- Package source: `$(System.DefaultWorkingDirectory)/_Angualr-CI(3)/drop/angular-16-crud`
- Trigger: **Automated after release creation**

✅ Release-1 deployed successfully — triggered automatically by the CI build.

**5. Verified the Live Application**
Confirmed the app was live and functional at the Azure-generated domain, with the **Tutorials List** CRUD interface loading correctly.

---

## Skills Demonstrated

| Area | Detail |
|---|---|
| Frontend | Angular 16, TypeScript, npm |
| Cloud | Microsoft Azure, Azure App Service |
| DevOps | Azure Pipelines (CI), Azure Releases (CD) |
| Infrastructure | Azure Resource Manager, App Service Plan |
| Automation | Build triggers, artifact publishing, auto-release |

---

## Project Structure

```
AngularFe/
├── src/              # Angular app source code
├── angular.json      # Angular CLI configuration
├── tsconfig.json     # TypeScript configuration
├── package.json      # Dependencies and build scripts
└── README.md
```

---

**Author:** Abdullah Mohammed
**Tech Stack:** Angular 16 · Azure App Service · Azure DevOps · Node.js · TypeScript
