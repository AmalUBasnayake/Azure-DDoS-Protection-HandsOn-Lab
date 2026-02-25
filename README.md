# 🚀 Azure DDoS Network Protection Lab  
### 🔐 Attack Simulation & Automatic Mitigation (AZ-500 Aligned)

<p align="center">
  <img src="screenshots/azure-ddos-architecture.png" width="85%">
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Azure-Security-blue?style=for-the-badge&logo=microsoftazure">
  <img src="https://img.shields.io/badge/AZ--500-Ready-green?style=for-the-badge">
  <img src="https://img.shields.io/badge/DDoS-Network%20Protection-red?style=for-the-badge">
</p>

---

## 📌 Project Summary

This project demonstrates how **Azure DDoS Network Protection (Network Tier)** detects and mitigates a simulated volumetric attack against a public-facing Virtual Machine.

✔ Built secure Azure environment  
✔ Simulated real attack traffic  
✔ Observed automated mitigation  
✔ Validated protection using Azure Monitor  

---

# 🏗️ Architecture Overview

<details>
<summary>🔎 Click to Expand Architecture Details</summary>

### Core Components

- **Virtual Network:** `vnet-northeurope`
- **Virtual Machine:** `Victim-VM`
- **Public IP Address**
- **DDoS Protection Plan:** `AZ500-Lab-DDoS`
- **Azure Monitor Metrics**
- **Azure Cloud Shell (Attack Simulation)**

### Protection Flow

1. Incoming malicious traffic detected  
2. Azure baseline traffic comparison  
3. Automatic mitigation triggered  
4. Malicious packets dropped at edge  

</details>

---

# 🛠️ Implementation Walkthrough

---

## 🛡️ Step 1 — Create DDoS Protection Plan

<details>
<summary>View Configuration</summary>

Created dedicated DDoS Protection Plan:

```
AZ500-Lab-DDoS
```

Enabled **Network Protection Tier**.

📸 Screenshot:

![DDoS Plan Creation](screenshots/1-ddos-plan-create.png)

</details>

---

## 🌐 Step 2 — Enable Protection on VNet

<details>
<summary>View Configuration</summary>

Linked protection plan to:

```
vnet-northeurope
```

All public IPs inside the VNet now protected.

📸 Screenshot:

![VNet DDoS Enabled](screenshots/2-vnet-ddos-enable.png)

</details>

---

## 💣 Step 3 — Simulate DDoS Attack

<details>
<summary>View Attack Script</summary>

Used Azure Cloud Shell (PowerShell):

```powershell
while($true) {
    Invoke-WebRequest -Uri "http://<Victim-Public-IP>" -UseBasicParsing
}
```

Launched multiple background jobs to increase traffic.

📸 Screenshot:

![Attack Simulation](screenshots/3-attack-simulation.png)

</details>

---

# 📊 Monitoring & Detection

<details>
<summary>View Azure Monitor Metrics</summary>

**Metrics Configuration:**

- Scope → Victim-VM Public IP  
- Metric → Under DDoS attack or not  
- Aggregation → Max  

📸 Screenshot:

![DDoS Metrics](screenshots/4-ddos-metrics.png)

### Observations:

- Traffic spike detected  
- Attack flag enabled  
- Automatic mitigation triggered  

</details>

---

# ✅ Proof of Mitigation

<details>
<summary>View Mitigation Evidence</summary>

During attack simulation:

```
Connection timed out
```

This indicates Azure dropped malicious packets before reaching VM.

📸 Screenshot:

![Connection Timeouts](screenshots/5-timeouts.png)

</details>

---

# 🧹 Cleanup

<details>
<summary>Click to Expand Cleanup Commands</summary>

Stop attack jobs:

```powershell
Get-Job | Stop-Job
```

Delete Resource Group:

```powershell
Remove-AzResourceGroup -Name "AZ500-Lab-RG"
```

</details>

---

# 🎯 Skills Demonstrated

- Azure Network Security
- DDoS Threat Simulation
- Azure Monitor Metrics Analysis
- Incident Validation
- Cost-Control Cleanup
- AZ-500 Practical Readiness

---

# 📚 Certification Alignment

✔ AZ-500: Secure Network Infrastructure  
✔ Platform Protection Implementation  
✔ Monitor & Respond to Security Threats  

---

## 👨💻 Author

**Amal U. Basnayake**  
Cloud Security Engineer | Azure | AZ-500 Focused  

🔗 GitHub: https://github.com/AmalUBasnayake  
🔗 LinkedIn: https://www.linkedin.com/in/amal-udayanga-basnayake/  

---

<p align="center">
⭐ If you found this project useful, consider giving it a star!
</p>
