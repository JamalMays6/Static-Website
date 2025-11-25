# 🌐 Rise Up Bank Website Migration: Azure Static Web Hosting

## ✅ Project Objectives

| Task                        | Status |
|-----------------------------|--------|
| Create Azure Storage Account | ✅     |
| Enable Static Website Hosting | ✅     |
| Upload index.html and images | ✅     |
| Test public accessibility    | ✅     |
| Fix broken icons             | ✅     |

## 🔎 Case Study: Rise Up Bank Migrates to Azure Blob Storage
### Description
This guide walks you through setting up a static website using Azure Blob Storage. You’ll create a Storage Account via the Azure Portal, enable static website hosting, and upload an index.html file to the special $web container. No coding knowledge is required, as the necessary HTML and CSS files are provided. Finally, you’ll verify the website’s accessibility using the Azure Blob Storage endpoint in a private or incognito browser.

### Background

Rise Up Bank, a fintech startup, relies heavily on its website to attract, inform, and onboard clients. The company previously hosted its site on on-premises infrastructure, but growing maintenance costs and poor scalability led to operational inefficiencies.

## 🏗️ Architecture Overview

```mermaid
flowchart LR
    subgraph Dev["Developer Laptop (VS Code)"]
      A[Edit HTML/CSS\nStatic site files]
      B[git commit & push]
    end

    subgraph GitHub["GitHub Repo\n(JamalMays6/Static-Website)"]
      C[Source code\nwebsite/ folder]
      D[GitHub Actions\nCI/CD Workflow]
    end

    subgraph Azure["Azure"]
      E[Storage Account\nriseupstaticweb]
      F["$web container\nStatic Website Hosting"]
    end

    subgraph User["End User Browser"]
      G[Customer visits\nriseupstaticweb.z20.web.core.windows.net]
    end

    A --> B --> C
    C --> D
    D -->|Deploy static files| F
    F --> G

---

#### What is Azure Blob Storage? 
Azure Blob Storage is Microsoft's object storage solution for the cloud. It’s optimized for storing massive amounts of unstructured data, like text or binary data. You can use it to store files, backups, logs, and host static websites, similar to AWS S3.

<img width="281" height="281" alt="2e13e292-be37-40f4-9516-cb74f555c81c" src="https://github.com/user-attachments/assets/6669e857-2eeb-411d-9af8-d7dfe8ee97b7" />

---
#### Challenge ⚠️
Currently, Rise Up Bank’s website is hosted on traditional on-prem servers. Every week, the IT team found themselves bogged down by patches, maintenance, and emergency restarts. Whenever customer traffic spiked, especially during promotions, the site slowed down or crashed. Instead of focusing on new features or improving user experience, the team spent most of their time just trying to keep the lights on.

#### Solution ✅
To break free from the limitations of on-prem hosting, Rise Up Bank made the move to Azure. Instead of managing hardware and patching servers, they turned on Static Website Hosting in Azure Blob Storage. Suddenly, traffic surges were no longer a problem—Azure scaled with them automatically. By connecting to Azure CDN, users across the country saw faster load times. And with built-in encryption and role-based access, the site stayed locked down and secure.

<img width="350" height="350" alt="a8608a63-183c-482a-bb53-4a17a21b23be" src="https://github.com/user-attachments/assets/2618b36f-4927-42a5-b042-996f0b3823df" />

#### Outcome 🏁 
After switching to Azure Blob Storage, Rise Up Bank finally found stability. The website loaded faster, scaled effortlessly during traffic spikes, and stayed online around the clock. Customers noticed the difference, and so did the IT team. With infrastructure worries out of the way, they could now focus on what really mattered, building better features and delivering smarter, safer banking.

---

## 🪜 Step-by-Step Guide

### 🔹 Step 1: Log in to Azure
- Go to [https://portal.azure.com](https://portal.azure.com)
- Use a **least privileged identity** instead of a Global Admin for daily tasks.

---

### 🔹 Step 2: Create a Storage Account
1. Search for **"Storage accounts"** in the Azure Portal and click **+ Create**.
2. Fill in:
   - Subscription: Select your active one
   - Resource group: Create or select an existing one
   - Name: A unique name (e.g., `riseupstaticweb`)
   - Region: Closest to your users
   - Performance: **Standard**
   - Redundancy: **Locally-redundant storage (LRS)**
     
<img width="682" height="507" alt="8eede9c2-6bcc-47f8-8028-a2530215e249" src="https://github.com/user-attachments/assets/a4e2f12b-61f2-4357-8d6e-333eec6a0767" />

  
3. Click **Review + Create** → **Create**

---

### 🔹 Step 3: Enable Static Website Hosting
1. Navigate to the new Storage Account
2. Under **Data Management**, click **Static Website**
3. Set:
   - Static website: **Enabled**
   - Index document: `index.html`
   - Error document path: `404.html`
4. Click **Save**


<img width="1881" height="513" alt="2026de75-6b67-44b0-9fea-9a0f31d7242f" src="https://github.com/user-attachments/assets/a411d73e-0226-47d4-8b93-6b788383b91d" />

---

### 🔹 Step 4: Upload Your Web Files
1. In the left menu, go to **Containers** → select **$web**
2. Click **Upload** → Add `index.html`, CSS, and images

---

### 🔹 Step 5: Test Your Site
1. Return to the **Static Website** blade
2. Copy the **Primary endpoint**
3. Paste it in an **incognito browser tab**

Your website should now be live.

---

## 🧠 Troubleshooting

| Issue                        | Solution                                  |
|-----------------------------|-------------------------------------------|
| Broken icons/images         | Ensure image files are uploaded to `$web` |
| 404 error on page load      | Confirm `index.html` is uploaded correctly |
| Changes not appearing       | Wait for blob sync or clear browser cache |

---

## 🔐 Security & Optimization Notes

- No server maintenance required
- RBAC and container-level access control for better security
- Can integrate Azure CDN or Front Door for faster global delivery

---

## 📌 Future Enhancements

- 🔗 Bind custom domain via Azure DNS  
- 🔄 Automate updates with GitHub Actions  
- 🛡️ Add Azure WAF + Front Door

---

## 📋 Summary Table

| Feature             | Tool                  | Business Value                          |
|---------------------|------------------------|------------------------------------------|
| Web hosting         | Azure Blob Static Site | Cost-effective and scalable              |
| Uptime & durability | Azure LRS              | Ensures availability for all visitors    |
| Visual design       | Branded assets         | Improves credibility and UX              |
| Global performance  | (Optional) CDN         | Reduces latency for international users  |

---
> 🚀 **Project Type**: Cloud Engineer Project  
> 🧰 **Tech Stack**: Azure Storage Account, Static Website Hosting, HTML/CSS  
> 🏦 **Use Case**: Financial Startup Website Migration  
> 📍 **Live Demo**: [https://riseupstaticweb.z20.web.core.windows.net](https://riseupstaticweb.z20.web.core.windows.net)
## 🗓️ Project Completion Date

August 07, 2025
