# Loja Social IPCA – Integrated Social Support System

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Kotlin](https://img.shields.io/badge/Kotlin-Jetpack%20Compose-7F52FF?logo=kotlin)](app)
[![React](https://img.shields.io/badge/React-Vite%20%2B%20TS-61DAFB?logo=react)](web)
[![Firebase](https://img.shields.io/badge/Firebase-Firestore%20%7C%20Auth%20%7C%20Functions-FFCA28?logo=firebase)](functions)

A complete digital system to modernize and streamline the management of IPCA's Social Store, replacing manual processes with a centralized solution that promotes transparency and mutual support within the academic community.

The project is a **monorepo** with three components:

| Folder | Description | Stack |
|---|---|---|
| [`app/`](app) | Android mobile app — used by beneficiaries and SAS staff | Kotlin, Jetpack Compose, MVVM + Clean Architecture, Hilt |
| [`web/`](web) | Public website for outreach and transparency (campaigns, donations, stock status) | React, Vite, TypeScript, Tailwind, shadcn/ui |
| [`functions/`](functions) | Cloud Functions — email and push notification delivery | Node.js, Firebase Functions v2, Nodemailer |

---

## Main Features

### Beneficiary Management
* **Digital Registration:** Sequential flow for collecting personal and academic data and submitting required documents (GDPR).
* **Applications (Requests):** Submission and tracking of support request status (Submitted, Under Review, Missing Info, Approved, or Rejected).
* **Self-Service Profile:** Beneficiaries can view their support history and edit their personal data.

### Inventory Management (Goods)
* **Stock Control:** Distinction between the product catalog (typology) and physical stock (quantities and batches).
* **Categorization:** Organized by goods type: Food, Personal Hygiene, and Cleaning.
* **Expiry Management:** Expiry date monitoring with automatic notifications to prevent waste.

### Delivery Management
* **Flexible Scheduling:** Monthly pickup scheduling with optional automatic recurrence.
* **Notifications:** Push alerts and emails to remind beneficiaries of delivery dates.
* **Operational Validation:** Immediate delivery status logging (Delivered/Not Delivered) by SAS staff.

### Campaigns and Community
* **Campaign Tracking:** Lifecycle management of internal and external collection initiatives.
* **Public Website:** Web page with information on campaigns, donations, and stock transparency.

---

## Tech Stack

**Android App**
* **Language:** Kotlin
* **UI:** Jetpack Compose + Compose Navigation
* **Architecture:** MVVM (Model-View-ViewModel) + Clean Architecture
* **Dependency Injection:** Hilt

**Web**
* **Framework:** React + Vite + TypeScript
* **UI:** Tailwind CSS + shadcn/ui (Radix primitives)

**Backend (Firebase, shared by App and Web)**
* **Firestore:** NoSQL data storage
* **Authentication:** User authentication
* **Storage:** Image storage (products/campaigns)
* **Cloud Functions:** Email delivery (Nodemailer) and push notifications (FCM)

---

## Code Organization

The Android app follows **Clean Architecture** principles, split into:

1. **Domain:** Pure business logic (Use Cases and Domain Models).
2. **Data:** Repositories and Data Sources (Firebase integration).
3. **Presentation:** UI layer organized by screens (`Screens`), reusable components (`Components`), and state management (`ViewModels`).

---

## Setup and Running

### 1. Clone the Repository

```bash
git clone https://github.com/Gusta11M/loja-social-ipca.git
cd loja-social-ipca
```

### 2. Android App (`app/`)

1. Create a project in the [Firebase Console](https://console.firebase.google.com/).
2. Add an Android app with the package `pt.ipca.lojasocial`.
3. Download `google-services.json` and place it in `app/`.
4. Open the project in **Android Studio**, sync Gradle, and run on an emulator/device with API 24+.

### 3. Web (`web/`)

```bash
cd web
cp .env.example .env   # fill in with your Firebase project credentials
npm install
npm run dev
```

### 4. Cloud Functions (`functions/`)

```bash
cd functions
cp .env.example .env   # SMTP credentials (Gmail App Password), never commit
npm install
firebase deploy --only functions
```

> **Security note:** all credentials (`google-services.json`, `.env`, signing keys) are excluded via `.gitignore` and must never be committed. Always use the `.env.example` files as reference.

---

## License

Distributed under the MIT license. See [LICENSE](LICENSE) for details.

---

## Team (Applied Project & Mobile Device Programming)
* 27962 Gustavo Daniel Loureiro Marques
* 29852 Gustavo da Costa Pereira
* 23010 Hugo Tiago Mendes Cruz
* 27977 Igor Miguel Torres da Costa
* 23016 Dani Carvalho da Cruz
* **Supervision:** Prof. Patrícia Isabel Sousa Trindade Silva Leite & Prof. Lourenço Miguel Araújo Gomes

---
**School of Technology – IPCA**
Bachelor's Degree in Computer Systems Engineering
