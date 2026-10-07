# ShowTime Central · Event Ticketing

A console app in core Java for discovering and booking events, inspired by BookMyShow. Customers browse, book and manage tickets; organizers publish and manage their events; an administrator approves organizers and oversees everything.

**Portfolio:** [utkarash-thakur.vercel.app](https://utkarash-thakur.vercel.app)

## Highlights

- Three separate flows (administrator, event organizer, customer), each with its own menu.
- Layered design: service interfaces (`EventServices`, `BookingServices`, `CustomerService`) with separate implementations.
- Custom exceptions for login, bookings, duplicates and invalid input, so bad input never crashes the app.
- Data saved to disk with Java object serialization (`Event.ser`, `Bookings.ser`, `Customer.ser`, `Organizer.ser`), so it survives restarts without a database.
- Customer wallet: add funds and pay for tickets; if an organizer deletes an event, customers who booked it are refunded.

## Features

**Administrator**
- Log in with the default account (`admin` / `admin`).
- Approve or reject organizer registrations.
- View and manage organizers and their events.
- See all customers and their bookings.

**Event organizer**
- Register, then log in once approved.
- Add events with type, venue, date and time, ticket count and price.
- Update or delete events by event ID.
- View bookings for their events.

**Customer**
- Sign up with a unique email and log in.
- Browse events and book by event ID.
- Add money to a wallet and pay from it.
- View profile and booking history; delete the account.

## Tech stack

Java · OOP · Collections · Java Serialization (no database)

## Project structure

```
Event Ticketing/src/com/masai
├── Main.java            menus for the three roles
├── admin/               Administrator
├── organizer/           EventOrganizer, OrganizerImpl
├── event/               Event, EventType, EventServices(+Impl)
├── booking/             Booking, BookingServices, BookingServiceImpl
├── customer/            Customer, CustomerService(+Impl)
├── exceptions/          Authentication, Booking, DuplicateData, Event, InvalidChoice, InvalidDetails
├── FileExists.java      loads and creates the .ser data files
└── IDGeneration.java    unique IDs
```

## Run it locally

1. Install a JDK (Java 8 or newer).
2. Open the `Event Ticketing` folder as a Java project in Eclipse or IntelliJ, and run `com.masai.Main`.
   Or compile and run from a terminal:
   ```bash
   cd "Event Ticketing"
   javac -d bin $(find src -name "*.java")
   java -cp bin com.masai.Main
   ```
3. Data files (`*.ser`) are created in the working folder on first run.

## Author

**Utkarash Thakur**, Backend Engineer · [Portfolio](https://utkarash-thakur.vercel.app) · [LinkedIn](https://www.linkedin.com/in/utkarash-thakur/)
