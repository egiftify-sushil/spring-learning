# 🔧 Project Build & Deployment Guide

## 📦 Root Project Overview
This repository hosts a **multi-module Java application** structured with Gradle.  
It follows a modular architecture to promote reusability, separation of concerns, and ease of maintainability.  
Each module in this project is responsible for a distinct functionality, with shared code encapsulated in reusable libraries.

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
