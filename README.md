# Womanista 🌸

**A Multi-Platform Flutter Application for Women Empowerment**

---

## 📘 Capstone Project

**Womanista** was developed as a **final-year capstone project**, aimed at designing and implementing a **scalable, modular, multi-domain mobile application** using Flutter.

The project goes beyond a simple app by focusing on:

* System design & architecture
* Modular software engineering
* Cross-platform deployment
* Real-world feature integration

---

## 🚀 Overview

Womanista is a **multi-service platform** that integrates essential services into a single application:

* 🏥 Healthcare (Doctor Consultation & Booking)
* 🛒 E-Commerce (Shopping & Orders)
* 🚖 Ride Booking (Transport System)
* 🛡️ Self-Defense (Awareness & Legal Education)

The system is built using a **single Flutter codebase** targeting:

* Android
* iOS
* Web
* Windows

---

## 🏗️ Architecture

The application follows a **Flutter-first modular monolith architecture**:

```
             Firebase (Backend Services)
                      ↑
        ---------------------------------
        |       Flutter App Shell       |
        ---------------------------------
         |        |        |        |
      Doctor   E-Com    Ride    Self-Defense
      Module   Module   Module      Module
```

### Key Design Decisions

* Feature-based modularization
* Provider pattern for state management
* Firebase as Backend-as-a-Service
* Minimal native code (platform bootstrapping only)

---

## 📂 Project Structure

```
lib/
 ├── main.dart
 ├── firebase_options.dart
 ├── screens/
 │    ├── Home.dart
 │    ├── login.dart
 │    ├── Signup.dart
 │    ├── forgotpassword.dart
 │    ├── settings.dart
 │    ├── AppDrawer.dart
 │    └── modules/
 │         ├── DoctorModule/
 │         ├── ECommerce/
 │         ├── RideBooking/
 │         └── selfeDefence/
assets/
android/
ios/
web/
windows/
```

---

## 🔐 Authentication System

* User Signup & Login
* Password Recovery
* Session Handling
* Firebase Authentication integration

---

## 🧩 Core Modules

### 🏥 Doctor Module

* Doctor listing & profiles
* Appointment booking system
* Request & approval workflows
* Admin-side management
* Providers:

  * `Doctor_Provider.dart`
  * `DoctorRequestProvider.dart`

---

### 🛒 E-Commerce Module

* Product catalog & details
* Cart management
* Checkout flow
* Address & payment handling
* Order tracking
* Admin panel for product management
* Provider:

  * `cart_provider.dart`

---

### 🚖 Ride Booking Module

* Rider & Driver flows
* Ride request lifecycle
* Real-time ride tracking
* Distance calculation & map integration
* Chat between driver and rider

Key components:

* `rides_provider.dart`
* `ride_requests_provider.dart`
* `map_provider.dart`
* `chat_provider.dart`
* `place_service.dart`
* `distance_work.dart`

---

### 🛡️ Self-Defense Module

* Legal awareness content
* Laws listing & descriptions
* YouTube-based educational content
* Admin content control

Provider:

* `Laws_Provider.dart`

---

## 🔄 State Management

The application uses the **Provider pattern**:

* Centralized business logic in `*_Provider.dart` files
* Reactive UI updates
* Shared state across screens (cart, rides, appointments, etc.)

---

## 🔥 Backend Integration (Firebase)

Firebase is used as a **Backend-as-a-Service (BaaS)**:

* Authentication
* Cloud data storage (Firestore / Realtime DB)
* Configuration

### Configuration Files

* `firebase_options.dart`
* `android/app/google-services.json`
* `ios/Runner/GoogleService-Info.plist`

---

## 🎨 Assets & Media

* Stored in `/assets/`
* Includes UI images and resources
* Demo media included for presentation purposes

---

## 📄 Project Documentation

* 📌 [Proposal Guidelines](https://github.com/user-attachments/files/17608558/Proposal.Guidelines.docx)
* 📌 [Deliverable 1: Planning & Requirements](https://github.com/user-attachments/files/17608554/deliverable.1.planning.requirement.docx)
* 📌 [Deliverable 2: Development](https://github.com/user-attachments/files/17608555/Second.Deliverable.Development.1.1.docx)

---

## 🎥 Demo

* ▶️ [Watch Application Demo](https://github.com/user-attachments/assets/bb50ad38-f0bb-4b68-b513-41b6e8db04fb)

---

## 🧠 System Design

### Domain Model Class Diagram

This diagram illustrates the **core entities and relationships** across all modules.

<img width="1221" height="1600" alt="Domain Model Class Diagram" src="https://github.com/user-attachments/assets/85f2bd11-5076-472b-8bf1-dd46752a87ac" />

---

## ⚙️ Getting Started

### Prerequisites

* Flutter SDK
* Dart
* Firebase project setup

### Installation

```bash
git clone https://github.com/Alishba-Siddique/Womanista.git
cd Womanista
flutter pub get
```

### Run the App

```bash
flutter run
```

---

## 📱 Supported Platforms

| Platform | Support |
| -------- | ------- |
| Android  | ✅       |
| iOS      | ✅       |
| Web      | ✅       |
| Windows  | ✅       |

---

## 🎯 Learning Outcomes

Through this project:

* Applied **software architecture principles**
* Built a **multi-module scalable system**
* Implemented **cross-platform mobile development**
* Practiced **state management using Provider**
* Integrated **Firebase services in production-like setup**

---

## 🚧 Limitations & Future Work

* No dedicated backend server (fully Firebase-dependent)
* Limited real-time scalability testing
* UI/UX can be further refined

### Future Improvements

* Microservices-based backend
* Role-based access control
* Advanced analytics & AI integration
* Performance optimization for large-scale users

---

## 👩‍💻 Author

**Alishba Siddique**

---

## ⭐ Final Note

Womanista demonstrates how a **single Flutter application** can unify multiple service domains while maintaining **modularity, scalability, and clean architecture** — making it both a strong academic project and a practical system design implementation.
