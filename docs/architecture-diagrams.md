# Architecture Diagrams

These diagrams are intentionally high level. They describe public portfolio architecture without exposing production source code, security rules, secrets, customer records, internal dashboards, or deployment credentials.

## System Overview

```mermaid
flowchart LR
  A["Customer mobile app"] --> B["Firebase Authentication"]
  C["Barber mobile app"] --> B
  D["Flutter Web admin dashboard"] --> B
  A --> E["Cloud Firestore"]
  C --> E
  D --> E
  A --> F["Firebase Storage"]
  C --> F
  E --> G["Cloud Functions"]
  G --> E
  G --> H["Firebase Cloud Messaging"]
  G --> I["Analytics and BigQuery"]
  J["Firebase Hosting links"] --> G
  K["Crashlytics and Performance"] --> L["Production monitoring"]
```

## Booking Flow

```mermaid
flowchart TD
  A["Customer selects barber and service"] --> B["Mobile app creates booking request"]
  B --> C["Firestore stores booking state"]
  C --> D["Cloud Functions validate trusted actions"]
  D --> E["Barber receives notification"]
  E --> F["Barber accepts, rejects, or proposes update"]
  F --> G["Firestore updates booking state"]
  G --> H["Customer receives follow-up notification"]
```

## Notification Flow

```mermaid
flowchart LR
  A["Booking or support event"] --> B["Notification record"]
  B --> C["Cloud Function delivery worker"]
  C --> D["Firebase Cloud Messaging"]
  D --> E["Customer or barber device"]
  C --> F["Retry and delivery status"]
```

## QR Attribution Flow

```mermaid
flowchart LR
  A["QR code scan"] --> B["Firebase Hosting link"]
  B --> C["Redirect handler"]
  C --> D["Campaign source attribution"]
  D --> E["App or store destination"]
  D --> F["Acquisition analytics"]
```

## Authentication Flow

```mermaid
flowchart TD
  A["User starts sign in"] --> B["Firebase Authentication"]
  B --> C["Authenticated session"]
  C --> D["Firestore loads role and profile"]
  D --> E["Customer experience"]
  D --> F["Barber experience"]
  D --> G["Admin operations experience"]
```

## Analytics Flow

```mermaid
flowchart LR
  A["Mobile app events"] --> B["Privacy-aware analytics helpers"]
  B --> C["Firebase Analytics"]
  D["Cloud Functions"] --> E["Operational aggregates"]
  E --> F["Admin analytics dashboard"]
  E --> G["BigQuery integration"]
```
