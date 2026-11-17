# Design Patterns Mapped to Features – Sprint 2

**Kanban card:** SCRUM-17 – Design patterns
**Owner:** Saud Aldoseri
**Related:** [decision-matrix.md](decision-matrix.md), UML class diagram (SCRUM-19)

| Pattern | Where it is used | Feature / requirement | Why |
|---|---|---|---|
| **Strategy** | `PricingStrategy` interface, implemented by `LinearPricing`, `ExponentialPricing` and `SteppedPricing`. The vendor picks one on the Post Food screen. | F-08, F-09, US03 | A new price curve can be added without changing `FoodListing`. The vendor's minimum price (F-09) is applied after the curve, and each curve can be unit tested alone. |
| **Observer** | The Pricing Engine is the subject. Consumer views and the Notification Module subscribe to it. | F-10, F-18, US03, US12 | When the scheduler recalculates a price, open screens update without a reload and price-drop alerts are sent. |
| **Repository** | `UserRepository`, `ListingRepository`, `ReservationRepository`, `OrderRepository` | NFR-09, NFR-12 | Hides how data is stored. Browser local storage today, a database later, with no change to the application layer. |

## How they fit the architecture

- Strategy and Observer live in the **application layer** (pricing engine and scheduler).
- Repository forms the **data layer**.
- Views and controllers (MVC) in the **presentation layer** only talk to the application layer, never to the repositories directly.
