# Womanista 🌸

**A Flutter mobile application bringing together several women-focused services.**

Womanista is a final-year Bachelor of Software Engineering capstone (PUCIT, 2023), built by a **five-person team**. It consolidates services that women in Pakistan often access through separate, fragmented channels into a single mobile app, using Flutter on the front end and Firebase as the backend.

---

## 📘 About

This was a **team capstone (5 members)**, scoped as a **mobile application (Android and iOS)**. It was built as a working prototype to demonstrate modular software engineering across several service domains on a shared Firebase backend, not as a production system. (The repository contains default `web/` and `windows/` Flutter scaffolding, but those targets were not a focus and were not tested.)

---

## 🚀 Services

| Module | What it does |
| --- | --- |
| 🏥 **Doctor**        | Doctor listing and profiles, a doctor application form, a patient-request list, and email-based appointment initiation |
| 🛒 **E-Commerce**    | Product catalog, cart, checkout, orders, and an admin panel |
| 🚖 **Ride Booking**  | Ride request lifecycle, live map tracking, distance calculation, and rider/driver chat |
| 🛡️ **Self-Defense**  | Legal-awareness content, laws listing, and embedded educational videos |

---

## 👥 Team & My Contribution

Womanista was built by a team of five, with work divided by module and function.

**My role (Alishba Siddique):**
- **Project documentation lead** — proposal, planning and requirements, and design deliverables across the capstone lifecycle.
- **Doctor module** — designed and implemented the module described below.

Module ownership was split across the team; authentication and the shared app shell were built collaboratively.

---

## 🏥 Doctor Module (my module)

Files: `DoctorList.Dart`, `DoctorProfile.dart`, `BookAppointment.dart`, `DoctorRequests.dart`, `DoctorModuleApplicationForm.dart`, `Doctor_Provider.dart`, `DoctorRequestProvider.dart`, `Manu.dart`.

What it implements:
- **Doctor listing and profiles.** A predefined doctor dataset is written to a Firestore `Doctors` collection and read back to render the list and individual profile screens (`flutter_rating_bar` for ratings, `cached_network_image` for profile images).
- **Doctor application form.** A multi-field form screen (`DoctorModuleApplicationForm.dart`) for a doctor to submit registration details.
- **Patient request list.** Incoming patient queries are stored in and read from a Firestore `DoctorRequests` collection (`DoctorRequests.dart`).
- **Appointment initiation.** From a doctor's profile, the user starts an appointment by launching a pre-filled email to the doctor via `url_launcher` (`mailto:`).

**Honest scope note.** This module is a prototype. The doctor and request data are seeded from predefined sample data rather than entered by real users, appointment booking is handled through email rather than an in-app scheduling/approval system, and the screens manage state locally with `setState` and direct Firestore reads/writes rather than through the app-level Provider state used elsewhere. These are exactly the areas I would rebuild (see *Limitations*).

---

## 🧩 Other Modules (built by teammates)

- **E-Commerce** (`cart_provider.dart`, admin panel under `ECommerce/adminSide/`) — catalog, cart, checkout, order tracking, product management.
- **Ride Booking** (`rides_provider.dart`, `map_provider.dart`, `chat_provider.dart`, `place_service.dart`, `distance_work.dart`) — ride lifecycle, Google Maps tracking, distance calculation, in-app chat, separate driver flow.
- **Self-Defense** (`Laws_Provider.dart`, `Youtube.dart`) — laws list and descriptions, embedded YouTube educational content.

---

## 🛠️ Tech Stack

| Layer | Technology |
| --- | --- |
| Framework | Flutter (Dart, SDK 2.16+) |
| Targets | Android, iOS |
| State management | Provider (app-level), `setState` (Doctor module) |
| Auth | Firebase Authentication, Google Sign-In |
| Data | Cloud Firestore |
| Storage | Firebase Storage |
| Maps & location | `google_maps_flutter`, `location`, `permission_handler` |
| Media | `youtube_player_flutter`, `cached_network_image` |
| Other | `url_launcher`, `email_launcher`, `image_picker`, `flutter_rating_bar`, `uuid`, `google_fonts` |

---

## 🏗️ Architecture

A Flutter-first modular structure with Firebase as a backend-as-a-service:

```
            Firebase (Auth · Firestore · Storage)
                          ↑
            -----------------------------
            |      Flutter App Shell     |
            -----------------------------
             |        |        |        |
          Doctor   E-Com    Ride    Self-Defense
          Module   Module   Module      Module
```

App-level state (cart, rides, chat, requests, products, map, locations) is provided via `MultiProvider` in `main.dart`. Authentication state decides whether the app opens on `Home` or `Login`.

---

## 📂 Project Structure

```
lib/
 ├── main.dart                 # Firebase init + MultiProvider + auth gate
 ├── firebase_options.dart
 ├── variables/variables.dart
 └── screens/
      ├── Home.dart, login.dart, Signup.dart, forgotpassword.dart, settings.dart, AppDrawer.dart
      ├── Admin/                # admin home + driver registration requests
      └── modules/
           ├── DoctorModule/    # owned by Alishba Siddique
           ├── ECommerce/
           ├── RideBooking/
           └── selfeDefence/
```

---

## ⚙️ Getting Started

```bash
git clone https://github.com/Alishba-Siddique/Womanista.git
cd Womanista
flutter pub get
flutter run
```

**Prerequisites:** Flutter SDK, Dart, and a configured Firebase project (`firebase_options.dart`, `google-services.json`, `GoogleService-Info.plist`). A Google Maps API key is required for the Ride Booking module.

---

## 📄 Capstone Documentation

Formal deliverables I authored as documentation lead:

- 📌 [Proposal Guidelines](https://github.com/user-attachments/files/17608558/Proposal.Guidelines.docx)
- 📌 [Deliverable 1: Planning & Requirements](https://github.com/user-attachments/files/17608554/deliverable.1.planning.requirement.docx)
- 📌 [Deliverable 2: Development](https://github.com/user-attachments/files/17608555/Second.Deliverable.Development.1.1.docx)

---

## 🎥 Demo

- ▶️ [Watch the application demo](https://github.com/user-attachments/assets/bb50ad38-f0bb-4b68-b513-41b6e8db04fb)

---

## 🧠 System Design

Domain model class diagram (core entities and relationships across the modules):

<img width="1221" height="1600" alt="Domain Model Class Diagram" src="https://github.com/user-attachments/assets/85f2bd11-5076-472b-8bf1-dd46752a87ac" />

---

## 🎯 What I Took From This Project

- As documentation lead, I learned that in a five-person team the requirements and design documents are what keep everyone building the same system; they are not overhead.
- Building the Doctor module against Firestore taught me to work within a backend-as-a-service and to wire UI to a live data store.
- Reviewing my own module honestly taught me the difference between a working prototype and a production feature: seed data vs. real user data, an email hand-off vs. an actual booking workflow, and local `setState` vs. shared state management.

---

## 🚧 Limitations & Future Work

- Prototype-level: several modules (including parts of mine) use seeded sample data rather than live user-generated data.
- Doctor module: appointments are initiated by email rather than an in-app scheduling and approval workflow; this is the first thing I would rebuild, backed by Firestore with proper request states.
- No dedicated backend server (fully Firebase-dependent), which limits scalability and complex queries.
- Mobile only; web and desktop targets were not developed or tested.
- Inconsistent state-management approach across modules (Provider vs. local `setState`).

**Planned improvements:** a real appointment workflow with status states, a dedicated backend with role-based access control, consistent state management, and performance testing at scale.

---

## 👩‍💻 Team

A five-member BSc Software Engineering capstone team (PUCIT, 2023).
Repository maintained by **Alishba Siddique** — documentation lead and Doctor module.
