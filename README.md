# Booking_System


# ✈️ Multi-Service Booking System
 
A unified travel booking platform that lets users search, compare, and book **flights, hotels, car rentals, and local activities/tours** — all in a single itinerary and checkout flow (OTA-style, similar to Booking.com / Expedia).
 
---
  
## Overview
 
Unlike a single-purpose booking system (e.g., flights only), this system is designed as a **multi-service OTA (Online Travel Agency)**, where independent service modules (Flight, Hotel, Car, Activities) share a common core: authentication, cart, payment, and — most importantly — a unified **Itinerary** that ties all booked services for a trip together.
 
## Actors
 
| Actor | Description |
|---|---|
| **Traveler / Customer** | End user searching and booking travel services |
| **Admin** | Manages the platform, suppliers, pricing, and reports |
| **Supplier Manager** | Manages data for a specific supplier (airline, hotel chain, car rental co.) |
| **External Suppliers / APIs** | Third-party providers (flight, hotel, car, activity data) |
| **Payment Gateway** | External payment processor |
 
---
 
## 📌 System Features
 
### A. Core / Shared Features
> Shared across all service modules.
 
- **User Account Management** — registration, login, profile, saved documents/payment methods
- **Unified Search** — single search entry point across all service types
- **Multi-Service Cart** — combine multiple service types in one cart
- **Unified Payment & Checkout** — single payment flow covering all cart items
- **Itinerary Management** — groups all bookings for a trip into one itinerary/timeline
- **Notifications System** — booking confirmations, reminders, and change alerts
- **Booking History & Management** — view/modify/cancel past and upcoming bookings
- **Reviews & Ratings** — per-service feedback
- **Customer Support** — chat/tickets, FAQs
- **Promotions & Loyalty Program** — discount codes, points, rewards
  
### B. Flight Booking
11. **Flight Search & Booking**
12. **Seat Selection**
13. **Online Check-in**

--

### C. Hotel Booking
14. **Hotel Search & Booking**
15. **Room Selection & Details**

--

### D. Car Rental
16. **Car Search & Booking**
17. **Insurance & Add-ons Selection**

--

### E. Local Trips & Activities
18. **Activity/Tour Search & Booking**

--

### F. Package / Bundle Booking
19. **Pre-built Packages** (Flight + Hotel + Trip bundles)
20. **Custom Package Builder**

--

### G. Admin & Management
21. **Admin Dashboard**
22. **Supplier / Inventory Management**
23. **Reports & Analytics**
24. **User & Access Management** (admin side)
    
--


## 📌 System functions

---

# A. Core / Shared Features

These features are shared across all booking modules (Flights, Hotels, Cars, Activities).

## 1. User Account Management

- Register (Sign Up)
- Login / Logout
- Forgot / Reset Password
- Email / Phone Verification (OTP)
- Update Profile Information
- Upload & Manage Travel Documents (Passport, ID)
- Manage Saved Payment Methods

---

## 2. Unified Search

- Select Service Type
  - Flight
  - Hotel
  - Car Rental
  - Activity / Tour
- Enter Search Criteria
  - Destination
  - Travel Dates
  - Number of Guests
- Auto-suggest Destinations
- Display Relevant Search Results

---

## 3. Multi-Service Cart

- Add Services to Cart
- Remove Services from Cart
- Update Booking Details
- View Cart Summary
  - Flight
  - Hotel
  - Car
  - Activities
- Validate Cart
  - Availability
  - Date Conflicts

---

## 4. Unified Payment & Checkout

- Select Payment Method
- Apply Promo Code
- Split Payment *(Optional)*
- Process Payment
- Generate Unified Invoice
- Handle Payment Failure & Retry

---

## 5. Itinerary Management

- Create Itinerary from Bookings
- Display Trip Timeline
- Detect Schedule Conflicts
- Modify Individual Booking
- Cancel Individual Booking
- Export Itinerary (PDF)

---

## 6. Notifications System

- Booking Confirmation
- Service Reminder
- Delay / Change Notifications
- Cancellation / Refund Notifications
- Manage Notification Preferences

---

## 7. Booking History & Management

- View Upcoming Bookings
- View Past Bookings
- Filter by Service Type
- Filter by Booking Status
- View Booking Details
- Modify Booking
- Cancel Booking

---

## 8. Reviews & Ratings

- Submit Review
- Rate Service (1–5 Stars)
- View Customer Reviews
- Report Inappropriate Reviews

---

## 9. Customer Support

- Create Support Ticket
- Live Chat
- Track Ticket Status
- Browse FAQs
- Search Help Articles

---

## 10. Promotions & Loyalty Program

- View Promotions
- Apply Discount Codes
- Earn Loyalty Points
- Redeem Points
- View Loyalty Tier & Status

---

# B. Flight Booking

## 11. Flight Search & Booking

- Search Flights
  - One-way
  - Round-trip
  - Multi-city
- Filter Results
  - Price
  - Stops
  - Airline
  - Departure Time
- Sort Results
- View Flight Details
- Enter Passenger Information
- Confirm Booking

---

## 12. Seat Selection

- View Seat Map
- Select Seat
- Choose Cabin Class
- Upgrade to Extra Legroom

---

## 13. Online Check-in

- Check-in Within Allowed Time
- Change Seat During Check-in
- Generate Boarding Pass (PDF / QR)

---

# C. Hotel Booking

## 14. Hotel Search & Booking

- Search Hotels
- Filter Hotels
  - Price
  - Star Rating
  - Amenities
- View Hotel Details
- View Hotel Photos
- Confirm Booking

---

## 15. Room Selection & Details

- View Available Rooms
- Select Room Type
- Select Number of Nights
- View Cancellation Policy
- Add Special Requests
  - Late Check-in
  - Extra Bed

---

# D. Car Rental

## 16. Car Search & Booking

- Search Rental Cars
- Filter Results
  - Car Type
  - Transmission
  - Rental Company
- View Car Details
- Confirm Booking

---

## 17. Insurance & Add-ons

- Select Insurance Package
- Add Driver Option
- Add Extras
  - GPS
  - Child Seat

---

# E. Local Trips & Activities

## 18. Activity / Tour Booking

- Search Activities
- Filter Results
  - Duration
  - Price
  - Language
- View Activity Details
- Book Private Tour
- Book Group Tour
- Confirm Booking

---

# F. Package / Bundle Booking

## 19. Pre-built Packages

- Browse Packages
- View Package Details
- View Pricing
- Book Package

---

## 20. Custom Package Builder

- Select Base Package
- Customize Individual Components
- Automatic Price Recalculation
- Confirm Package Booking

---

# G. Admin & Management

## 21. Admin Dashboard

- View System KPIs
- Access All Modules

---

## 22. Supplier & Inventory Management

- Add Supplier
- Edit Supplier
- Remove Supplier
- Manage API Keys
- Manage Supplier Connections
- Manage Inventory
  - Flights
  - Hotels
  - Cars
  - Activities
- Manage Pricing
- Manage Availability

---

## 23. Reports & Analytics

- Sales Reports
- Booking Reports
- Booking Trends
- Export Reports
  - Excel
  - PDF

---

## 24. User & Access Management

- View Users
- Search Users
- Activate Account
- Suspend Account
- Delete Account
- Assign Roles
- Manage Permissions

