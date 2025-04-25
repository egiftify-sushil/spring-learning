# 🔧 Project Build & Deployment Guide

## 📦 Root Project Overview
This repository hosts a **multi-module Java application** structured with Gradle.  
It follows a modular architecture to promote reusability, separation of concerns, and ease of maintainability.  
Each module in this project is responsible for a distinct functionality, with shared code encapsulated in reusable libraries.

├── build.gradle.kts / build.gradle # Root build configuration ├── settings.gradle # Declares all subprojects ├── gradle.properties # Centralized versioning and properties ├── tomcatwebapps/ # Deployment directory for WAR files ├── lib/ # Library modules (pure logic/utilities) │ └── platform/ # Example: platform utilities │ └── build.gradle # Module-specific dependencies/config ├── app/ # Application modules (services) │ └── customer/ # Example: customer service app │ └── build.gradle # Module-specific dependencies/config └──


### 📌 Project Version
The current version is maintained in the root project and applied consistently across all submodules.

---

## 🧩 Subprojects

Below are the key modules/subprojects included in this project:

- `:lib:platform` – Shared platform logic and utility classes.
- `:app:customer` – Core application module for customer-related operations.
- *(Add more modules here as needed)*

---

## 🛠️ Common Gradle Commands

### 🔄 Clean Project
```bash
./gradlew clean
