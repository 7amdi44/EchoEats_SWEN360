# Architecture Decision Matrix – Sprint 2

**Kanban card:** SCRUM-16 – Decision matrix and architecture choice
**Owner:** Saud Aldoseri
**Builds on:** SCRUM-15 (architecture drivers and style comparison, Abdullah Al-Kuwari)

## Styles compared

- Layered (three-tier) client-server
- MVC (Model-View-Controller)
- Microservices

## Weights

Each style is scored from 1 (poor) to 5 (excellent).

| Criterion | Weight | Reason for the weight |
|---|---|---|
| Scalability | 20% | Target load is small: 100 listings and 50 simulated users (NFR-01) |
| Security | 25% | Hashed passwords and vendor-only access to own listings (NFR-04, NFR-05) |
| Maintainability | 25% | Interface, pricing and storage must be separate modules (NFR-12) |
| Team fit | 30% | Five students, fixed four-week sprint |

## Matrix

| Criterion | Weight | Layered client-server | MVC | Microservices |
|---|---|---|---|---|
| Scalability | 20% | 3 | 3 | 5 |
| Security | 25% | 4 | 3 | 2 |
| Maintainability | 25% | 5 | 4 | 3 |
| Team fit | 30% | 5 | 4 | 1 |
| **Weighted score (out of 5)** | 100% | **4.35** | **3.55** | **2.55** |

Calculation, layered: 0.20×3 + 0.25×4 + 0.25×5 + 0.30×5 = 4.35

## Decision

**Three-tier client-server architecture, with MVC inside the presentation layer.**

- MVC alone scored lower because it only organises the user interface. It has no place for the background scheduler, the pricing curves or the repositories, so it is used for the views and controllers only.
- **Pricing (F-07 to F-09, US03):** the pricing engine sits in the application layer, so `Price(t) = max(MinPrice, BasePrice × Decay(timeRemaining))` can be unit tested without the UI (NFR-12).
- **Reservations (F-12 to F-14, US04, US08):** one reservation module updates stock atomically, so two users cannot book the last unit (NFR-03). The scheduler releases unpaid holds after 15 minutes.
- **Security (NFR-04, NFR-05):** authentication and vendor permission checks live in one application-layer entry point.
- **Team:** members can work on views, application modules and repositories in parallel.
- **Growth:** simulated payment (F-16) and local storage (NFR-09) can later be replaced without changing the views.

Microservices scored lowest: it scales best, but the extra endpoints, service-to-service authentication and deployment setup are too heavy for a five-person, four-week sprint.
