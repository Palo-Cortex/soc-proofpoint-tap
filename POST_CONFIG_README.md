# SOC-Proofpoint-TAP Content Pack for Cortex XSIAM

This repository contains the **SOC-Proofpoint-TAP** content pack for Palo Alto Networks Cortex XSIAM. It enables effective incident handling and visibility for Proofpoint TAP v2 alerts by providing layout customizations and detection rule guidance.

---

## 📦 What's Included

- Incident Layouts:
  - `Proofpoint - Message Delivered`
  - `Proofpoint - Click Permitted`
- Layout Rules to dynamically assign layouts based on alert metadata
- Sample Data Model Rules syntax for use in XSIAM
- Supporting configurations to route and visualize Proofpoint TAP v2 alerts

---

## ✅ Prerequisites

- Cortex XSIAM tenant
- Ingested and parsed data from **Proofpoint TAP v2** (via Broker VM, API, or other integrations)

---

## 🛠️ Installation Steps

### 1. Install the Content Pack

1. Install the Demisto SDK
2. Configure .env file for tenant
3. Git Clone this project: `SOC-Proofpoint-TAP`
4. Upload the pack to the tenant with the sdk: demisto-sdk upload -x -z -i ../Packs/soc-proofpoint-tap

---

### 2. Create Layout Rules

In **Settings > Layouts > Layout Rules**, create the following two layout rules:

#### 📩 Rule: Proofpoint - Message Delivered

- **Condition:**
  ```text
  tags = Proofpoint, DS:Proofpoint TAP v2 AND alert type = Proofpoint TAP - Message Delivered

- **Layout:** `Proofpoint - Message Delivered`

#### 🔗 Rule: Proofpoint - Click Permitted

- **Condition:**

alert type = Proofpoint TAP - Click Permitted AND original tags = DS:Proofpoint TAP v2
- **Layout:** `Proofpoint - Click Permitted`

> Example layout rules shown below:  
> ![Layout Rules Screenshot](https://github.com/Palo-Cortex/soc-proofpoint-tap/blob/main/images/layout-rule.jpg)

---

### 3. Configure Data Model Rules

> ⚠️ **Note:** Due to current limitations, the `demisto-sdk` does **not support uploading models**.

To apply the Data Model Rules:

1. Navigate to **Settings → Data Management → Data Model Rules**
2. Copy and paste the rule content from the following file in this repository:

AssetsModelingRules/proofpoint_tap_rule
