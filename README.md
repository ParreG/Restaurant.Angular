# restaurant-angular

An Angular frontend for a restaurant booking system — a clean multi-step booking flow that communicates with the [Restaurant.API](https://github.com/ParreG/Restaurant.API) backend.

Built as the SPA layer of a three-part restaurant system, focused on giving guests a smooth booking experience with real-time table availability checks before confirming.

---

## Tech Stack

- **Angular 17+** — Component-based SPA with modern control flow syntax (`@switch`, `@for`, `@if`)
- **Reactive Forms** — Form validation across multiple steps
- **RxJS** — Async availability checks with `pipe`, `tap`, `map`, `catchError`, `finalize`
- **HttpClient** — API communication for table availability and booking creation

---

## Features

- **4-step booking flow** — Date/time selection, contact details, review and confirmation
- **Real-time availability check** — Queries the API for available tables before allowing the user to proceed
- **Shared booking state** — `BookingStoreService` keeps form data alive across all steps without prop-drilling
- **Smart confirmation** — Checks if a booking already exists before firing a new API call, prevents duplicates on back-navigation
- **Shared components** — Reusable `LoadingSpinnerComponent` and `ErrorMessageComponent` with retry support
- **Form validation** — Required fields, email format, min/max guests enforced with Reactive Forms

---

## Project Structure

```
src/app/
├── layout/
│   ├── navbar/
│   └── footer/
├── pages/
│   └── booking/
│       ├── booking.component          # Step controller and navigation logic
│       ├── select-datetime/           # Step 1 — date, time, guest count + availability check
│       ├── contact-details/           # Step 2 — name, email, phone
│       ├── review/                    # Step 3 — summary before confirming
│       └── confirmation/              # Step 4 — creates booking and shows result
├── services/
│   ├── booking-store.service          # Shared state across all steps
│   ├── booking-api.service            # POST booking to API
│   └── table-api.service              # GET available tables
├── models/                            # TypeScript interfaces
└── shared/
    ├── loading-spinner/
    └── error-message/
```

---

## Getting Started

### Prerequisites

- Node.js 18+
- Angular CLI (`npm install -g @angular/cli`)
- [Restaurant.API](https://github.com/ParreG/Restaurant.API) running locally

### Setup

1. Clone the repo

```bash
git clone https://github.com/ParreG/ResturangPG_Angular.git
cd ResturangPG_Angular
```

2. Install dependencies

```bash
npm install
```

3. Start the dev server

```bash
ng serve
```

The app runs on `http://localhost:4200` and expects the API at `https://localhost:7270`.

---

## Related Repos

| Repo | Role |
|------|------|
| [Restaurant.API](https://github.com/ParreG/Restaurant.API) | REST API — the backend |
| [Restaurant.MVC](https://github.com/ParreG/Restaurant.MVC) | MVC frontend — server-rendered views |
| [Restaurant.Angular](https://github.com/ParreG/Restaurant.Angular) | Angular frontend — SPA client |
