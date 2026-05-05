# Summary

Total test cases: 20

Category-wise breakdown: Positive 3, Negative 4, Boundary 2, Security 1, Performance 2, UI/UX 1, Integration 2, Compatibility 1, Accessibility 1, Localization 1, Regression 1, Edge Cases 1, Data Validation 1, Compliance 1

Priority-wise breakdown: P1 11, P2 7, P3 2, P4 0

# Test Cases

| TC ID | Test Case Title | Category | Priority | Preconditions | Test Steps | Test Data | Expected Result | Actual Result | Status | Linked AC / BR |
|---|---|---|---|---|---|---|---|---|---|---|
| TC_001_001 | Search taxis for a valid route and display availability | Positive | P1 | User is on booking screen; search service is available | 1. Enter pickup location.
2. Enter drop location.
3. Click Search.
4. Observe results. | Pickup: Mumbai Airport; Drop: Pune Station | Available flying taxis are displayed with route details and pricing. | Not Executed | Not Executed | Not Executed | AC1 |
| TC_002_001 | Show message when no taxis are available for selected route | Negative | P1 | User is on booking screen | 1. Enter pickup location.
2. Enter a route with no service coverage.
3. Click Search. | Pickup: Remote Zone A; Drop: Remote Zone B | Message "No taxis available for selected route" is displayed. | Not Executed | Not Executed | Not Executed | AC1 |
| TC_003_001 | Validate pickup and drop locations at route search boundaries | Boundary | P2 | User is on booking screen | 1. Enter valid pickup location.
2. Leave drop location blank.
3. Click Search.
4. Repeat with pickup and drop locations identical. | Pickup: Mumbai Airport; Drop: blank / same as pickup | System blocks search and displays a validation error for missing or invalid route input. | Not Executed | Not Executed | Not Executed | AC1 |
| TC_004_001 | Search availability on mobile viewport | UI/UX | P3 | Mobile browser/device is available | 1. Open booking screen on a mobile viewport.
2. Enter locations.
3. Tap Search.
4. Verify result layout. | iPhone 13 viewport; Pickup: Mumbai Airport; Drop: Pune Station | Search controls and results remain readable and usable without horizontal scrolling. | Not Executed | Not Executed | Not Executed | NFR4 |
| TC_005_001 | Select taxi and confirm booking successfully | Positive | P1 | Search results are displayed; user is authenticated | 1. Select an available taxi.
2. Click Book/Confirm.
3. Review booking confirmation. | Taxi ID: TX-1001 | Booking is confirmed and a unique booking ID is generated and displayed. | Not Executed | Not Executed | Not Executed | AC2, BR1 |
| TC_006_001 | Prevent booking confirmation when no taxi is selected | Negative | P1 | Search results are displayed | 1. Do not select a taxi.
2. Click Confirm Booking. | No taxi selected | System prevents booking and displays "Please select a taxi to continue". | Not Executed | Not Executed | Not Executed | AC2 |
| TC_007_001 | Validate booking ID uniqueness across consecutive bookings | Data Validation | P1 | Two valid booking attempts can be made in sequence | 1. Complete booking for first taxi.
2. Complete second booking.
3. Compare booking IDs. | Booking 1 and Booking 2 | Each booking receives a unique booking ID; no duplicate ID is generated. | Not Executed | Not Executed | Not Executed | AC2, BR1 |
| TC_008_001 | Confirm booking with payment completion before ride confirmation | Integration | P1 | Selected taxi is available; payment gateway is reachable | 1. Select a taxi.
2. Proceed to payment.
3. Complete payment successfully.
4. Observe booking status. | Card payment success | Booking is confirmed only after payment succeeds. | Not Executed | Not Executed | Not Executed | AC3, BR2 |
| TC_009_001 | Reject booking confirmation when payment is not completed | Negative | P1 | Selected taxi is available | 1. Select a taxi.
2. Attempt to skip payment.
3. Try to finalize booking. | No payment method used | Booking is not confirmed until payment is completed. | Not Executed | Not Executed | Not Executed | AC3, BR2 |
| TC_010_001 | Display payment failure message for declined card or wallet transaction | Negative | P1 | Selected taxi is available; payment gateway is reachable | 1. Select a taxi.
2. Choose card or wallet.
3. Submit a failing payment attempt. | Declined card / insufficient wallet balance | Message "Payment failed. Please try again" is displayed and booking remains unconfirmed. | Not Executed | Not Executed | Not Executed | AC3 |
| TC_011_001 | Enforce payment amount and selected method at transaction boundary | Boundary | P2 | Selected taxi is available | 1. Enter zero or invalid payment amount if exposed.
2. Choose card and wallet separately.
3. Submit payment. | Amount: 0; Payment method: card/wallet | System rejects invalid payment input and does not proceed with confirmation. | Not Executed | Not Executed | Not Executed | AC3 |
| TC_012_001 | Verify payment data is encrypted during transaction | Security | P1 | User is on payment screen; network inspection is available | 1. Start payment flow.
2. Capture network/request payloads.
3. Validate sensitive payment fields. | Card number, CVV, wallet token | Sensitive payment data is encrypted and not exposed in plain text. | Not Executed | Not Executed | Not Executed | NFR3 |
| TC_013_001 | Complete booking and payment integration end to end | Integration | P1 | Search results are available; payment service is functional | 1. Search route.
2. Select taxi.
3. Pay using card.
4. Confirm booking.
5. Verify final status. | Route: Mumbai Airport to Pune Station; Card payment success | Booking confirmation, payment success, and booking ID generation complete without service mismatch. | Not Executed | Not Executed | Not Executed | AC1, AC2, AC3 |
| TC_014_001 | Cancel booking before ride start and receive confirmation | Positive | P1 | A confirmed booking exists; ride has not started | 1. Open booking details.
2. Click Cancel Booking.
3. Confirm cancellation.
4. Observe status. | Active booking ID | Cancellation confirmation is shown and booking status changes to cancelled. | Not Executed | Not Executed | Not Executed | AC4 |
| TC_015_001 | Block cancellation after ride start | Negative | P1 | A confirmed booking exists; ride has started | 1. Open booking details after ride start.
2. Attempt to cancel the booking. | Active in-progress booking | Cancellation is rejected and message "Cancellation not allowed after ride start" is displayed. | Not Executed | Not Executed | Not Executed | AC4, BR3 |
| TC_016_001 | Verify refund is processed within 5 minutes after cancellation | Performance | P2 | A confirmed booking is cancelled successfully; refund system is available | 1. Cancel a booking.
2. Monitor refund timestamp.
3. Verify refund completion time. | Cancelled booking ID | Refund is processed within 5 minutes of cancellation. | Not Executed | Not Executed | Not Executed | AC4, BR4, NFR2 |
| TC_017_001 | Handle 1000 concurrent search and booking users | Performance | P1 | Performance environment is available | 1. Simulate 1000 concurrent users.
2. Execute search and booking flows.
3. Measure response time and success rate. | 1000 virtual users | System maintains acceptable responsiveness and completes requests without critical failure. | Not Executed | Not Executed | Not Executed | NFR1, NFR2 |
| TC_018_001 | Ensure booking flow works on supported browsers and devices | Compatibility | P2 | Test devices/browsers are available | 1. Open booking flow on supported browsers/devices.
2. Perform search, select taxi, pay, and cancel checks. | Chrome, Firefox, Safari, Android browser | Core booking features work consistently across supported environments. | Not Executed | Not Executed | Not Executed | NFR4 |
| TC_019_001 | Verify booking screen is accessible by keyboard and screen reader | Accessibility | P2 | Accessibility tools are available | 1. Navigate booking screen using keyboard only.
2. Read controls with screen reader.
3. Perform search and booking actions. | Keyboard navigation; screen reader enabled | All interactive controls are reachable, labeled, and operable without mouse dependency. | Not Executed | Not Executed | Not Executed | NFR4 |
| TC_020_001 | Validate localized message text is shown correctly for payment failure and no availability states | Localization | P3 | Application language settings are available | 1. Switch language if supported.
2. Trigger no availability.
3. Trigger payment failure.
4. Observe message text. | Locale: en-IN | Localized messages are displayed correctly without truncation or translation errors. | Not Executed | Not Executed | Not Executed | AC1, AC3 |

# Traceability Matrix
- AC1 → TC_001_001, TC_002_001, TC_003_001, TC_004_001, TC_013_001, TC_020_001
- AC2 → TC_005_001, TC_006_001, TC_007_001, TC_013_001
- AC3 → TC_008_001, TC_009_001, TC_010_001, TC_011_001, TC_012_001, TC_013_001, TC_020_001
- AC4 → TC_014_001, TC_015_001, TC_016_001
- BR1 → TC_005_001, TC_007_001
- BR2 → TC_008_001, TC_009_001, TC_013_001
- BR3 → TC_015_001
- BR4 → TC_016_001
- NFR1 → TC_017_001
- NFR2 → TC_016_001, TC_017_001
- NFR3 → TC_012_001
- NFR4 → TC_004_001, TC_018_001, TC_019_001, TC_020_001

# Assumptions & Notes
- Jira ticket AD-231 contains complete story, ACs, BRs, and NFRs; no attachments or comments added additional requirements.
- AC1 route availability is validated using supported and unsupported routes.
- Payment failure error text must match exactly: "Payment failed. Please try again".
- Booking ID uniqueness is validated across separate confirmed bookings.
- Refund timing is measured from successful cancellation timestamp.
- Localization, compliance, accessibility, regression, and compatibility scenarios are represented through functional coverage only where explicit UI/device behavior was available in the ticket; no separate acceptance criteria were provided for locale/legal/regional rules.