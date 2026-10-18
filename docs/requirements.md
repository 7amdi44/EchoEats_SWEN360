# EchoEats Requirements

Priorities use MoSCoW (Must / Should / Could / Won't).

## Functional Requirements

| ID | Requirement | MoSCoW |
| --- | --- | --- |
| F-01 | Users can sign up as either a vendor or a consumer with an email and password. An email that is already registered can't be used again. | Must |
| F-02 | Users can log in and log out. When the wrong password is entered, an error message is displayed and they are not allowed to enter. | Must |
| F-03 | A vendor adds a food listing by completing the name, photo, description, starting price, quantity, expiry time and dietary tags. If one is left out, it won't save. | Must |
| F-04 | Vendors can edit or delete their own listings, except once a customer has reserved the item. | Must |
| F-05 | Customers can look through all the listings, then filter by distance, dietary tags, or price. | Must |
| F-06 | A map view lets consumers see which nearby vendors have something listed right now. | Should |
| F-07 | The closer the date gets to the expiry date, the lower the price. Price(t) = BasePrice * DecayFunction(timeRemaining). Verify by calculating the formula manually at one point in time and comparing it with the price shown in the app. | Must |
| F-08 | The rate of price decline for each listing is chosen by the seller: linear, exponential or stepped. | Should |
| F-09 | The vendor enters the lowest price they will accept, and the price stops there no matter how close the item is to expiry. | Must |
| F-10 | Prices on screen update by themselves at least every 15 minutes, without reloading the page. | Must |
| F-11 | Listings that have expired or sold out are hidden from search. | Must |
| F-12 | A consumer can reserve an item. It is held for them for 15 minutes and taken out of the available quantity. | Must |
| F-13 | If the reservation isn't confirmed within 15 minutes, it is released automatically. | Must |
| F-14 | Two people can't end up with the last unit. If both press reserve at once, only one goes through and the other sees a message saying it's gone. | Must |
| F-15 | Before pickup, a consumer can cancel their reservation, which puts the quantity back. | Should |
| F-16 | Payment is only simulated. The price the consumer paid is saved with the order, so a later price drop doesn't change it. | Must |
| F-17 | Every confirmed order gets a pickup code. The vendor types it in to mark the order as collected. | Should |
| F-18 | Users get a notification when a saved item drops in price, and again 1 hour before an item expires. | Could |
| F-19 | Consumers can see how many meals they have saved and an estimate of the CO2 this prevented. | Could |
| F-20 | Vendors get a dashboard with items listed, sold and unsold, plus total revenue. | Should |
| F-21 | Machine learning price prediction. | Won't |
| F-22 | A/B testing of pricing strategies. | Won't |
| F-23 | Route optimization for pickups from several vendors. | Won't |
| F-24 | Image verification of food quality at pickup. | Won't |
| F-25 | Real payment gateway and vendor payouts. | Won't |
| F-26 | Community leaderboards and monthly impact reports. | Won't |

## Non-Functional Requirements

| ID | Requirement | MoSCoW |
| --- | --- | --- |
| NFR-01 | 95% of searches finish within 2 seconds with 100 listings and 50 simulated users. | Must |
| NFR-02 | When a new price is calculated, users should see it within 30 seconds. | Should |
| NFR-03 | The number of confirmed reservations for a listing must never exceed its quantity, even when requests arrive at the same time. | Must |
| NFR-04 | Passwords are stored hashed, never as plain text. | Must |
| NFR-05 | A vendor can't change another vendor's listings, and users can't see anyone else's orders. | Must |
| NFR-06 | Only collect the data actually needed for ordering. | Should |
| NFR-07 | A first-time user can search, reserve and confirm in under 5 minutes without help (tested with at least 3 people). | Should |
| NFR-08 | It is possible to search and reserve using just the keyboard. | Could |
| NFR-09 | Nothing is lost when the page is refreshed or the browser is closed and reopened, because data is saved in local storage. | Must |
| NFR-10 | Bad input gets a clear error message instead of crashing the app. | Must |
| NFR-11 | The app runs on the newest Chrome, Edge and Firefox, and on a phone screen. | Should |
| NFR-12 | Interface, pricing logic and storage are kept in separate modules, with unit tests for the pricing functions. | Should |
