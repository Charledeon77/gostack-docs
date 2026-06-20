---
title: Getting Started
has_children: true
layout: default
nav_order: 2
---

# INSTALLATION

In this section, you will install the GoStack framework, the essential foundation for building and scaling robust applications. By following this guide, you will set up both the environment and the CLI tools required to streamline your development workflow.

## The GoStack CLI (Gost)
Gost serves as the foundational command-line interface for the GoStack framework, acting as the primary engine for scaffolding project structures, managing database migrations, and automating routine code generation tasks. By centralizing these core development workflows, Gost enables developers to rapidly initialize consistent, production-ready environments, ensuring that all necessary dependencies and configuration files are correctly provisioned from the very first command.

## Installation by Platform

Ensure you have Go installed on your system before proceeding. Select your operating system to view the specific installation steps:

- [Windows](#1-installing-gostack-on-windows)
- [Linux](#2-installing-gostack-on-linux)
- [MacOS](#3-installing-gostack-on-macos)

### 1. Installing GoStack on: Windows
1. Ensure Go is installed and added to your system PATH.
2. Open PowerShell or Command Prompt.
3. Run the following command to install the Gost CLI globally:
   go install github.com/Charledeon77/gostack/cmd/gost@latest

### 2. Installing GoStack on: Linux
1. Ensure Go is installed and your GOPATH is configured.
2. Open your terminal.
3. Run the following command to install the Gost CLI globally:
   go install github.com/Charledeon77/gostack/cmd/gost@latest

### 3. Installing GoStack on: MacOS
1. Ensure Go is installed (via Homebrew or the official installer).
2. Open your terminal.
3. Run the following command to install the Gost CLI globally:
   go install github.com/Charledeon77/gostack/cmd/gost@latest

---

## POST-INSTALLATION SETUP

Once the installation is complete, these universal steps will finalize your configuration and prepare you to begin development:

1. Verify Installation:
   gost --version
   (Confirm the version number is displayed to ensure the CLI is accessible.)

2. Create Your First Project:
   gost new myapp
   (This generates a 'myapp' directory with a complete GoStack project structure.)

3. Initialize:
   cd myapp
   (Navigate into your new project directory.)

4. Review Environment Defaults:
   Check the generated '.env' file, which includes your automatically generated 'APP_KEY' and default application settings.

5. Launch the Development Server:
   go run cmd/gostack/main.go
   (Your application will start and be accessible locally at http://localhost:8080.)

## What you get
The 'gost new' command provides a production-ready starting point including:
- A modular project structure.
- A functional main.go file.
- An auto-configured .env file.
- A pre-initialized go.mod file with all required dependencies.
