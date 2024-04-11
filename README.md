# Project Documentation

## Overview
This project involves the creation and deployment of a simple WebApp, a web application built using the ASP.NET Core Razor Pages framework. The deployment process is automated using Packer, a tool for creating identical machine images for multiple platforms from a single source configuration. This documentation provides an overview of the 'razorWebApp', the Packer configuration files used for automating the virtual machine setup, and the GitHub repository management practices, including security and code quality measures.

## 1. razorWebApp Documentation

### Introduction
- The razorWebApp is an ASP.NET Core Razor Pages application. Razor Pages is a page-based programming model that makes building web UI easier and more productive. The application is designed to run on a Windows environment, specifically tailored for Windows 11, as indicated by the deployment scripts.

### Development Environment
- **Visual Studio:** Recommended IDE for development, with support for Razor syntax highlighting, IntelliSense, and debugging.
- **.NET Core SDK:** Requires the .NET Core SDK for development and runtime environments.

## 2. Packer Files Documentation

### Key Components
- **VirtualBox-ISO Builder:** Configures a VirtualBox VM, specifying the Windows 11 ISO, hardware specifications, and WinRM for remote communication.
- **Provisioners:** PowerShell scripts automate the environment setup, including setting execution policies, installing .NET Core, and deploying the razorWebApp.

### Usage
- To use the Packer configuration, ensure Packer and VirtualBox are installed. Run `packer build` with the JSON file as an argument to create the VM image.

## 3. GitHub Repository Documentation

### Dependabot
- Dependabot is configured to ensure all dependencies are up-to-date, reducing the risk of security vulnerabilities. It automatically creates pull requests to update dependencies to the latest versions, helping to maintain the security and reliability of the application.

### Branch Policy
- A strict branch policy is enforced to maintain code quality and stability. The repository is organized with separate branches for different activities to streamline development and deployment processes:
  - **Development Branch:** Serves as the primary branch for ongoing development, where new features and bug fixes are merged before being deployed to production.
  - **Pipelines Branch:** Used specifically for testing and refining CI/CD pipelines, ensuring that automation processes are robust and efficient.
  - **Packer Branch:** Dedicated to maintaining and updating Packer configurations, allowing for isolated testing and development of VM image creation scripts.
  - **Main Branch:** The production branch where the stable version of the application resides. All changes merged into this branch are considered ready for deployment.
  - **README Branch:** Dedicated to create documentation for the project with general guidelines regarding to installation and useness.
  - This branching strategy ensures that changes are properly isolated and tested in their respective contexts before being integrated into the main codebase.

### CodeQL
- CodeQL is used for automated code scanning, identifying potential security issues and coding errors. It runs on every pull request and periodically on the main branch, ensuring that the codebase remains secure against known vulnerabilities and adheres to best coding practices.

### Pull Requests
- Pull requests are required for all changes, ensuring code review and automated checks (e.g., CodeQL, unit tests) pass before merging. This practice enhances code quality and team collaboration by facilitating thorough review and discussion of proposed changes.

### .gitignore File
- A Visual Studio `.gitignore` file is used to exclude system files, build outputs, and other non-source files from the repository, keeping it clean and focused on source code. This helps prevent accidental inclusion of unnecessary files that can clutter the repository and complicate version control.

### Branch Protection and Rulesets
- Branch protection rules are applied to the main branch, including required status checks, required reviews, and restrictions on who can merge changes. These rules ensure that the main branch remains stable and secure. Additional protection rules can be configured for other critical branches (e.g., development, pipelines, packer) to ensure that all changes meet the project's quality and security standards before being merged.

## Conclusion
This project leverages modern development practices and tools to ensure the efficient deployment and maintenance of the razorWebApp. By utilizing Packer for VM image creation, adhering to strict GitHub repository management practices with a structured branching strategy, and ensuring code quality and security through automated tools like CodeQL and Dependabot, the project sets a solid foundation for scalable and secure web application development.
