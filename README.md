# 🔍 Cloud Storage Forensics  
### A Client-Side Forensic Analysis of pCloud, MEGA, OneDrive & Google Drive

This project investigates how much forensic evidence can be recovered from a user’s computer when different cloud storage services are used. Since cloud servers cannot be accessed by investigators, client-side forensics becomes crucial for identifying user activity, file traces, logs, and metadata.

This research focuses on analyzing four major cloud service providers: **pCloud, MEGA, Microsoft OneDrive, and Google Drive**.

---

## 🧭 Project Overview

Cloud storage forensics is complex due to legal restrictions, distributed servers, and end-to-end encryption.  
This project demonstrates how artifacts can be extracted from:

- **RAM (volatile memory)**
- **Local disk & databases**
- **Browser artifacts**
- **Network behavior**
- **Client-side sync logs**

Using forensic tools like Autopsy, FTK Imager, Hindsight, and Hex Editor, the project reconstructs user actions such as:

- File upload  
- Download  
- Delete  
- Sync  
- Login activity  
- Encrypted folder usage  

---

## 🎯 Objectives

- Identify which client devices preserve the most forensic artifacts  
- Compare different cloud storage services  
- Extract evidence from RAM and disk  
- Analyze browser logs and cached data  
- Examine forensic challenges in modern cloud environments  
- Provide actionable methodology for future investigations  

---

## 🏗 Architecture & Methodology

### 1️⃣ Create controlled environment  
- VMware Workstation  
- Clean Windows OS image  

### 2️⃣ Install cloud applications  
- pCloud  
- MEGA Sync  
- Microsoft OneDrive  
- Google Drive (DriveFS)

### 3️⃣ Perform controlled activities  
- Upload files  
- Download files  
- Delete files  
- Share files  
- Sync across devices  

### 4️⃣ Acquire evidence  
- RAM Dump → FTK Imager  
- Disk Image → Autopsy  
- Browser History → Hindsight  
- Network Capture → Wireshark  
- DB/Log Inspection → Hex Editor Neo  

### 5️⃣ Analyze & document artifacts  
- Timestamps  
- User identities  
- Local DB entries  
- Encrypted handshake packets  
- Deleted file remnants  
- Local sync folder structure  
- Login/session details  

---

## 🛠 Tools Used

| Tool | Purpose |
|------|---------|
| **Autopsy** | Disk forensics, DB analysis, browser artifacts |
| **FTK Imager** | RAM dump acquisition, memory inspection |
| **Hex Editor Neo** | Binary artifact and DB inspection |
| **Hindsight** | Browser history reconstruction |
| **Wireshark** | Network capture & encrypted handshake study |
| **VMware** | Virtualized test environment |

---

## 📂 Forensic Findings (Highlights)

### 🟦 **pCloud**
- Email & **Crypto folder password found in RAM**
- Local SQLite DB reveals upload & delete logs  
- Browser cache shows encrypted Crypto folder previews  
- Version and login artifacts stored locally  

### 🟥 **MEGA**
- Email found in RAM but **password never stored**  
- Strong encryption, minimal recoverable data  
- Logs stored as text files  
- Sync database entries encrypted  
- Recovery key located in disk artifacts  

### 🟩 **OneDrive**
- Most detailed logs: **SyncDiagnostics.log**  
- User name, file path, timestamps found in RAM  
- Deleted file references + .lnk shortcuts  
- Extensive DB artifacts (OCSI.db)  
- Personal Vault setup info retrievable  

### 🟨 **Google Drive**
- Multiple DriveFS database files found  
- Sync DB entries show upload/download timestamps  
- Email and sync paths found in RAM  
- Browser autofill + session storage stores login behavior  

---

## 📌 Final Conclusions

- **Client-side forensics can recover large amounts of cloud evidence.**
- Even after deleting files, metadata and logs remain locally.  
- Each cloud provider leaves a *different amount* of traces:  

| Cloud Service | Forensic Evidence Availability |
|---------------|-------------------------------|
| **OneDrive** | ⭐⭐⭐⭐⭐ (Most Evidence) |
| **Google Drive** | ⭐⭐⭐⭐ |
| **pCloud** | ⭐⭐⭐ (Password leaked in RAM!) |
| **MEGA** | ⭐ (High security, minimal artifacts) |

- RAM artifacts are extremely valuable but disappear after reboot.  
- End-to-end encryption (MEGA/pCloud) reduces evidence but not fully.  
- Browser logs + local DBs give strong timeline reconstruction.  

---

## 🚧 Challenges

- Encrypted databases  
- Fast sync operations overwriting evidence  
- Cross-jurisdiction legal limitations  
- Volatile RAM data loss  
- Cloud apps storing logs in non-standard locations  

---

## 📎 Repository Contents

