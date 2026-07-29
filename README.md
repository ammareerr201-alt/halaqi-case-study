<p align="center">
  <img src="assets/banner/halaqi-case-study-banner.svg" alt="Halaqi case study banner" width="100%">
</p>

# Halaqi | حلاقي Case Study

Engineering case study for Halaqi, a production-grade Flutter and Firebase barber booking platform for the Iraqi market.

This repository is a public portfolio artifact. It contains no production source code, secrets, Firebase configuration, customer data, signing material, private URLs, or deployment credentials.

## Table Of Contents

- [Product Overview](#product-overview)
- [Problem](#problem)
- [Target Users](#target-users)
- [Features](#features)
- [Architecture](#architecture)
- [User Journeys](#user-journeys)
- [Booking Flow](#booking-flow)
- [Authentication](#authentication)
- [Notifications](#notifications)
- [Analytics](#analytics)
- [QR Attribution](#qr-attribution)
- [CI/CD](#cicd)
- [Security](#security)
- [Scalability](#scalability)
- [Monitoring](#monitoring)
- [Engineering Decisions](#engineering-decisions)
- [Lessons Learned](#lessons-learned)
- [Roadmap](#roadmap)
- [Store Links](#store-links)
- [Screenshots](#screenshots)

## Product Overview

Halaqi helps customers discover barbers, review services, choose available times, book appointments, receive notifications, and rate service quality.

For barbers, Halaqi supports onboarding, profile management, service management, availability, booking operations, notifications, wallet workflows, and portfolio presentation.

Halaqi also includes a separately maintained Flutter Web administration dashboard for operations, support, analytics, broadcasts, marketing campaigns, QR acquisition, system settings, monitoring, and release review.

## Problem

Many local barber workflows still depend on phone calls, messages, waiting in person, or guessing availability. That creates unclear wait times, missed appointments, overlapping bookings, limited service visibility, and difficult operational tracking for barbers.

## Target Users

| User | Need |
| --- | --- |
| Customers | Find barbers, compare services, book appointments, receive updates, and rate the experience. |
| Barbers | Manage services, availability, booking decisions, customer communication, wallet state, and profile presentation. |
| Admin operators | Monitor activity, support users, manage barbers, review analytics, run campaigns, and control system settings. |

## Features

| Area | Verified capabilities |
| --- | --- |
| Customer app | Authentication, location-aware discovery, barber profiles, services, booking, notifications, history, ratings, support |
| Barber app | Onboarding, profile, services, availability, booking queue, session actions, wallet, notifications, portfolio |
| Admin dashboard | Separately maintained Flutter Web dashboard for staff access, support workflows, broadcasts, marketing, analytics, and settings |
| Backend | Cloud Functions, scheduled jobs, trusted booking operations, retry handling, QR attribution |
| Reliability | Crashlytics, performance monitoring, structured logs, CI/CD release checks |

## Architecture

Halaqi uses Flutter for customer and barber mobile experiences, Firebase for core cloud services, Cloud Functions for trusted server-side operations, Firebase Hosting for public links and QR redirects, and monitoring/analytics services for production feedback.

Rendered architecture diagrams are available in [docs/architecture-diagrams.md](docs/architecture-diagrams.md).

## Technology Stack

| Layer | Stack |
| --- | --- |
| Mobile | Flutter, Dart, Android, iOS |
| Web operations | Separately maintained Flutter Web administration dashboard |
| Architecture | Feature-based modules, Cubit/BLoC, Provider, GoRouter |
| Backend | Firebase, Cloud Functions, TypeScript, Node.js, Firebase Admin SDK |
| Data | Firestore, Firebase Storage, BigQuery integration |
| Messaging | Firebase Cloud Messaging, local notifications |
| Observability | Crashlytics, Performance Monitoring, Analytics, structured logs |
| Product ops | Remote Config, App Check, QR attribution, Firebase Hosting |
| CI/CD | Codemagic, GitHub Actions |

## User Journeys

### Customer Journey

1. Sign in.
2. Discover nearby barbers.
3. Review profile, services, availability, and ratings.
4. Book a service and time.
5. Receive booking updates.
6. Attend the appointment.
7. Rate the experience.

### Barber Journey

1. Create or update barber profile.
2. Add services, portfolio, and availability.
3. Receive booking requests.
4. Accept, reject, or propose updates.
5. Manage active sessions and history.
6. Review wallet and operational state.

## Booking Flow

Booking operations are coordinated between the mobile app, Firestore, Cloud Functions, and notifications. Server-side operations are used for trusted state transitions and follow-up notifications.

See the rendered booking diagram in [docs/architecture-diagrams.md#booking-flow](docs/architecture-diagrams.md#booking-flow).

## Authentication

Authentication uses Firebase Authentication, role/profile loading from Firestore, and role-aware routing into customer, barber, or operational experiences.

See [docs/architecture-diagrams.md#authentication-flow](docs/architecture-diagrams.md#authentication-flow).

## Notifications

Notifications are driven by booking, support, and operational events. Delivery uses Firebase Cloud Messaging, notification records, retry state, and role-aware routing.

See [docs/architecture-diagrams.md#notification-flow](docs/architecture-diagrams.md#notification-flow).

## Analytics

The app uses privacy-aware analytics helpers, Firebase Analytics, operational aggregates, BigQuery integration, and admin-facing dashboards for product and reliability insight.

See [docs/architecture-diagrams.md#analytics-flow](docs/architecture-diagrams.md#analytics-flow).

## QR Attribution

QR acquisition uses public hosted links, redirect handling, source attribution, app/store routing, and acquisition analytics without exposing private campaign internals.

See [docs/architecture-diagrams.md#qr-attribution-flow](docs/architecture-diagrams.md#qr-attribution-flow).

## CI/CD

Halaqi uses Codemagic for signed Android and iOS release workflows and GitHub Actions for manual mobile build validation. Release checks include dependency installation, environment preparation, Firebase configuration presence checks, notification entitlement checks, Android build output, iOS build output, and artifact upload.

## Security

- Production source code remains private.
- Firebase configuration files are excluded from this public repository.
- Signing files and release credentials are excluded.
- User data, appointment data, phone numbers, location data, admin records, and analytics records are excluded.
- Public diagrams are intentionally high level and do not expose sensitive database rules or infrastructure details.
- Server-side operations are used for trusted booking and notification workflows.

More detail: [docs/security-and-privacy.md](docs/security-and-privacy.md).

## Scalability

- Firestore supports role-aware app state and real-time booking updates.
- Cloud Functions handle server-side validation, automation, scheduled work, and delivery workflows.
- Notification delivery uses retry state and normalized message types.
- Admin analytics are separated from customer-facing flows.
- CI/CD checks reduce release mistakes before store deployment.

## Monitoring

The production app uses Firebase Crashlytics, Performance Monitoring, Analytics, structured server logs, and admin-facing crash/analytics workflows to support debugging and product operations.

## Engineering Decisions

| Decision | Reason |
| --- | --- |
| Flutter | One production mobile codebase across Android and iOS. |
| Firebase | Fast path to authentication, database, storage, messaging, analytics, and monitoring. |
| Cloud Functions | Server-side authority for booking, notifications, automation, and admin operations. |
| Firestore | Realtime data model suited to booking and operational state. |
| Codemagic | Mobile-focused release automation. |
| GitHub Actions | Repeatable manual validation and build workflows. |

## Lessons Learned

- Product engineering is workflow design, not only feature delivery.
- Booking systems need trusted server-side decisions.
- Notifications require state, retries, audience rules, and observability.
- Admin tools should be described accurately without exposing private implementation.
- Analytics should be designed with privacy limits from the start.
- CI/CD and crash monitoring are part of shipping.

## Roadmap

- Add sanitized screenshots with demo data.
- Publish a deeper architecture walkthrough.
- Add a public product demo video when sensitive data can be removed.
- Document QR attribution and analytics decisions in more detail.
- Add AI-assisted analytics experiments after data review.

## Store Links

| Link | URL |
| --- | --- |
| Website | https://halaqi-links.web.app |
| App Store | https://apps.apple.com/ch/app/halaqi-%D8%AD%D9%84%D8%A7%D9%82%D9%8A/id6773111286 |
| Google Play | https://play.google.com/store/apps/details?id=com.haliqni.haliqni |

Privacy policy and support page links are not included because no verified public URLs were available for this repository.

## Screenshots

No production screenshots are included yet. A safe capture plan is available in [screenshots/README.md](screenshots/README.md).

## Repository Structure

| Path | Purpose |
| --- | --- |
| `.github/` | Issue and pull request templates for safe documentation feedback. |
| `CONTRIBUTING.md` | Contribution rules for documentation-only changes. |
| `LICENSE.md` | Portfolio content notice; does not license production source code. |
| `SECURITY.md` | Public security and sensitive-data reporting policy. |
| `assets/` | Public brand and preview assets. |
| `screenshots/` | Placeholder and privacy checklist for future sanitized screenshots. |
| `architecture/` | Architecture overview. |
| `diagrams/` | Mermaid source files for high-level diagrams. |
| `docs/` | Supporting case-study documentation. |
