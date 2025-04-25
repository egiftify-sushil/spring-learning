# 🔧 Project Build & Deployment Guide

## 📦 Root Project Overview
This repository hosts a **multi-module Java application** structured with Gradle.  
It follows a modular architecture to promote reusability, separation of concerns, and ease of maintainability.  
Each module in this project is responsible for a distinct functionality, with shared code encapsulated in reusable libraries.

### 📌 Project Version
The current version is maintained in the root project and applied consistently across all submodules.

## 🧩 Subprojects
## 📦 Modules Explained

### 🔹 `lib/`
Contains reusable **library modules** that are decoupled from business logic.

- These modules are shared across different services.
- Good place for common utilities, models, helpers, and core logic.
- Example: `lib:platform` holds platform-wide tools, constants, or adapters.

### 🔹 `app/`
Contains **service-level application modules**.

- These are the actual services or deployable units (e.g., WARs or JARs).
- They depend on one or more libraries from the `lib/` folder.
- Example: `app:customer` uses logic defined in `lib:platform`.

Each module under `app/` or `lib/` has its own `build.gradle` (or `.kts`) file to declare **module-specific dependencies**.

---

## 📁 Root Project

The **root project** provides the central configuration for the entire Gradle build.

- It defines plugin versions, repositories, dependency versions, and common tasks.
- Any global settings such as Java version, compiler options, and shared plugins are configured here.
- Acts as the single source of truth for versioning through `gradle.properties`.

---

## 🔧 Gradle Build Commands

### Clean all build outputs
```bash
./gradlew clean
