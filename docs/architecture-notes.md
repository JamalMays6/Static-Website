# 🏗️ Rise Up Bank – Architecture Notes

This document provides a deeper architectural explanation behind the Rise Up Bank static website migration, CI/CD pipeline, and Azure implementation.

---

## 1. High-Level Architecture Diagram

```mermaid
flowchart LR
    subgraph Dev["Developer Laptop (VS Code)"]
      A[Edit static website\nHTML/CSS/Images]
      B[git push]
    end

    subgraph GitHub["GitHub Repository"]
      C[website/ folder\nsource code]
      D[GitHub Actions\nCI/CD pipeline]
    end

    subgraph Azure["Azure"]
      E[Storage Account\nriseupstaticweb]
      F["$web container\nStatic Website Hosting"]
    end

    subgraph User["End-User Browser"]
      G[Visits public endpoint\nstatic website]
    end

    A --> B --> C
    C --> D
    D -->|Upload via Azure CLI| F
    E --> F
    F --> G
