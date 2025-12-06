<div align="center">
  <picture>
    <img alt="MehguViewer Logo" src="/thumbnail.png" width="400">
  </picture>
</div>

# <picture><img alt="MehguViewer Logo" src="/logo-light.png" height="32"></picture> MehguViewer <picture><img alt="MehguViewer Logo" src="/logo-dark.png" height="32"></picture>

> **The High-Performance Federated Media Protocol.**

[![License: AGPL v3](https://img.shields.io/badge/License-AGPL%20v3-zinc.svg)](https://www.gnu.org/licenses/agpl-3.0)
[![Protocol](https://img.shields.io/badge/Spec-OpenAPI%203.1-zinc?style=flat-square&logo=openapiinitiatives)](https://github.com/MehguViewer/MehguViewer.Proto)
[![Stack](https://img.shields.io/badge/.NET-Native%20AOT-512BD4?style=flat-square&logo=dotnet)](https://github.com/MehguViewer/MehguViewer.Core)

---

### **Manifesto**

**MehguViewer** is a distributed, specification-first ecosystem for hosting and consuming media. It decouples **Identity** (Auth) from **Content** (Core) to allow for a truly federated network where users own their data, and servers maximize performance.

*   **Stateless:** Core nodes do not hold user tables. Logic is driven by signed OIDC Claims.
*   **Native AOT:** Backends are compiled to native code for instant startup and minimal memory usage.
*   **Strict Types:** Communication requires strictly validated URNs and RFC 7807 error handling.

---

### **The Architecture**

The ecosystem is split into three strict architectural pillars.

```mermaid
graph TD
    User((User)) -->|Interface| Web[MehguViewer.Web]
    
    subgraph Federation
    Web -->|Get Token| Auth[MehguViewer.Auth]
    Web -->|Fetch Content| Core[MehguViewer.Core]
    end
    
    Core -.->|Verify Signatures via JWKS| Auth
    
    style Web fill:#18181b,stroke:#52525b,color:#fff
    style Auth fill:#3f3f46,stroke:#a1a1aa,color:#fff
    style Core fill:#3f3f46,stroke:#a1a1aa,color:#fff
    style User fill:#000,stroke:#fff,color:#fff
```

### **Repository Directory**

| Repository | Role | Tech Stack | Status |
| :--- | :--- | :--- | :--- |
| 📐 **[MehguViewer.Proto](https://github.com/MehguViewer/MehguViewer.Proto)** | **The Source of Truth.** Documentation, OpenAPI Specs, and Design Guidelines. **Start here.** | `Fumadocs` `OpenAPI` | 🟢 **Active** |
| 🏗️ **[MehguViewer.Core](https://github.com/MehguViewer/MehguViewer.Core)** | **The Content Node.** Hosts images, handles comments, validates tokens. | `.NET 9` `Native AOT` | 🟡 **WIP** |
| 🔐 **[MehguViewer.Auth](https://github.com/MehguViewer/MehguViewer.Auth)** | **The Identity Provider.** Handles OIDC Logins and global blocklists. | `Node.js` `OIDC` | 🟡 **WIP** |
| 👁️ **[MehguViewer.Web](https://github.com/MehguViewer/MehguViewer.Web)** | **The Lens.** The universal client for any Auth+Core combination. | `Next.js` `React` | 🟡 **WIP** |

---

<div align="center">
  <sub>MehguViewer Organization &copy; 2025</sub>
</div>
