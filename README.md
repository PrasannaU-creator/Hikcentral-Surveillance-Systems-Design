# Enterprise CCTV System Design — HikCentral Professional (500 × 4MP)

A complete, end-to-end **system design reference** for a large-scale IP video surveillance
deployment built on **Hikvision HikCentral Professional** — covering both the **network
architecture** and the **storage / RAID architecture** for **500 × 4 MP cameras**.

This repository documents the kind of planning that goes into a real enterprise CCTV project:
topology, device selection, VLAN and fibre design, storage capacity calculation and RAID
configuration.

---

## 📂 Documents

| Document | Description |
|----------|-------------|
| 📶 [**Network Architecture**](docs/HikCentral_Network_Architecture.pdf) | Topology, device models, VLAN & fibre backbone design |
| 💾 [**Storage & RAID Architecture**](docs/HikCentral_Storage_RAID_Architecture.pdf) | Capacity calculation, HDD configuration & retention planning |

---

## 📶 Network Architecture

![Network Architecture cover](assets/network-cover.png)

**What's covered**
- **End-to-end topology** — cameras → access → distribution → redundant core → server farm → operator clients
- **Device models & specifications** — Cisco Catalyst 9000 switches + Hikvision VMS servers and Hybrid SAN storage
- **VLAN segmentation & IP plan** — isolated management/server zone, per-zone camera subnets
- **Fibre backbone** — 10G access, 25G aggregation/core, OS2 single-mode & OM4 multimode with matching optics

![Network topology](assets/network-topology.png)

---

## 💾 Storage & RAID Architecture

![Storage Architecture cover](assets/storage-cover.png)

**What's covered**
- **Bitrate & capacity calculation** — H.265 @ 4 Mbps, 24/7 continuous (per camera, per server, whole system)
- **Per-server HDD build** — 5 × Hybrid SAN units, 100 cameras each
- **RAID design** — RAID-5 / RAID-6 with hot spares, parity trade-offs explained
- **Retention planning** — drive-size → retention table (≈35 to ≈105 days)
- **Storage stack** — physical disks → RAID arrays → storage pool → LUNs → record volumes

![Storage stack](assets/storage-stack.png)

---

## 🧱 System at a Glance

| Parameter | Value |
|-----------|-------|
| Cameras | ~500 × 4 MP (H.265) |
| Recording | 24 / 7 continuous |
| Access switches | 6 × Cisco Catalyst C9300-48P |
| Distribution | 3 × Cisco Catalyst C9300X-24Y |
| Core | 2 × Cisco Catalyst C9500-24Y4C (StackWise Virtual) |
| Server-farm switch | 1 × Cisco Catalyst C9500-48Y4C |
| Backbone | 10G access · 25G core · 100G inter-core |
| VMS | HikCentral Professional (mgmt + recording + streaming servers) |
| Storage | 5 × Hikvision Hybrid SAN DS-A81024S (24 × 8 TB, RAID-5) |
| Workstations | 10 × Intel Core i7 control clients |

---

## 🛠️ Technologies

`HikCentral Professional` · `Hikvision Hybrid SAN (DS-A81024S)` · `Cisco Catalyst 9000`
· `H.265 / HEVC` · `iSCSI` · `RAID-5 / RAID-6` · `VLAN segmentation` · `OS2 / OM4 fibre`

---

## 👤 Author

**Prasanna U**
🔗 LinkedIn: [linkedin.com/in/prasanna-udaikumar](https://www.linkedin.com/in/prasanna-udaikumar/)
✉️ Email: Prasanna.udhay@outlook.com

---

## 📄 License

Released under the [MIT License](LICENSE). These documents are shared as a **design reference**.
Product model numbers are **suggested, suitable components** for the design — verify exact part
numbers, bitrates and retention against project-specific requirements before procurement.
