
# 🔧 Project Build & Deployment Guide

## 📦 Root Project Overview

This is a multi-module Gradle project that includes several subprojects for modular functionality.  
The root project also handles global configurations and versioning.

### 📌 Project Version
The current version is maintained in the root project and applied consistently across all submodules.


### 🔧 `libs/` — Shared Libraries

These modules contain reusable components that are used across different services:

- **`freedompay/`**:  
  Integration utility for handling FreedomPay transactions or protocols.

- **`valutec/`**:  
  Integration utility for managing Valutec gift card operations or services.

- **`objects/`**:  
  Central repository for all shared **POJOs**, DTOs, and domain objects used across modules.

- **`platform/`**:  
  Wrapper over platform-level services such as:
  - Hibernate utility layer  
  - Email sending functionality  
  - Common service hooks and handlers

- **`common/`**:  
  Shared DAOs and utility classes that are not tied to a single domain.  
  Includes helpers, constants, and reusable low-level services.

- **`scheduler_base/`**:  
  Core scheduler logic that contains the **`Main`** class for running scheduled jobs.  
  This module is used by `scheduler_daemon` to initiate and manage job execution.

---

### 🧩 `app/` — Services and Daemon Modules

These modules represent deployable units or services with APIs or background processes.

#### 🔹 API Services

Each of the following modules exposes REST APIs and uses libraries under `libs/`:

- **`merchant/`**:  
  Handles all merchant-specific functionality and APIs.

- **`customer/`**:  
  Provides APIs for customer interactions and operations.

- **`portal/`**:  
  The **primary module for new API development**.  
  This acts as the central API gateway or unified backend moving forward.

- **`lifeline/`**:  
  Contains APIs and logic related to the "lifeline" feature or service, possibly for business continuity or user assistance.

#### 🔹 Scheduler Modules

- **`scheduler/`**:  
  Contains supporting services and logic for scheduled tasks.  
  These are consumed and triggered by the scheduler daemon.

- **`scheduler_daemon/`**:  
  A **non-API module** that runs as a background daemon.  
  Responsible for executing time-based tasks using the logic in `scheduler` and `scheduler_base`.

  > ✅ This is the entry point for all scheduled/background jobs.  
  > Designed to run on a timer or using cron-like mechanisms.

---

## 🔧 Build & Dependency Management

Each module:

- Has its own `build.gradle` file for declaring module-specific dependencies.
- Can reference other modules using Gradle's project dependency syntax (`project(':libs:common')`, etc.).

The **root project** provides the central configuration for the entire Gradle build.
- It defines plugin versions, repositories, dependency versions, and common tasks.
- Any global settings such as Java version, compiler options, and shared plugins are configured here.
- Acts as the single source of truth for versioning of subprojects.
- ext.tomcatWebapps = System.getenv('TOMCAT_WEBAPPS') Add tomcatwebapp for development

## 🔨 Useful Gradle Commands

```bash
./gradlew clean                       # Clean all build artifacts
./gradlew build                       # Build entire project
./gradlew :lib:platform:build         # Build a specific module
./gradlew build --rerun-tasks         # Force all tasks to re-run
./gradlew build --refresh-dependencies # Refresh all remote dependencies
./gradlew :app:customer:dependencies  # View dependency tree of a module
