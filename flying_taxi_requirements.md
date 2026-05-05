# 🚁 Flying Taxi Booking System

## 🧾 User Story

As a user, I want to book a flying taxi so that I can travel quickly between locations without traffic delays.

---

## ✅ Acceptance Criteria

### AC1: Search Availability

* User should be able to search flying taxis by entering pickup and drop locations
* System should display available taxis
* If no taxis available, show message: "No taxis available for selected route"

### AC2: Booking

* User should be able to select a taxi and confirm booking
* Booking should generate a unique booking ID
* Confirmation message should be shown after successful booking

### AC3: Payment

* User should be able to pay using card or wallet
* Payment failure should show message: "Payment failed. Please try again"
* Successful payment should confirm booking

### AC4: Cancellation

* User should be able to cancel booking before ride starts
* Cancellation confirmation message should be shown
* Refund should be processed within 5 minutes

---

## 📏 Business Rules

* BR1: Booking ID must be unique
* BR2: Payment must be completed before ride confirmation
* BR3: Cancellation not allowed after ride start
* BR4: Refund must be processed within 5 minutes

---

## ⚙️ Non-Functional Requirements (NFRs)

* NFR1: System should respond within 2 seconds
* NFR2: System should handle 1000 concurrent users
* NFR3: Payment data must be encrypted
* NFR4: UI should be mobile responsive

---

## 🧪 Existing Test Cases (Sample)

* Verify user can search taxis
* Verify booking is successful
* Verify payment success scenario
* Verify cancellation works

---

## 📌 Notes

* Assume valid locations unless specified
* System integrates with payment gateway
* System supports web and mobile
