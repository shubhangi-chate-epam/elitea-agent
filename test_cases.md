# Summary

Total test cases: 16

Category-wise breakdown: Positive (4), Negative (4), Boundary (2), Security (1), Performance (1), UI/UX (1), Integration (1), Compatibility (1), Accessibility (1), Localization (0), Regression (0), Edge Cases (0), Data Validation (0), Compliance (0)

Priority-wise breakdown: P1 (6), P2 (7), P3 (3), P4 (0)

# Test Cases

| TC ID | Test Case Title | Category | Priority | Preconditions | Test Steps | Test Data | Expected Result | Actual Result | Status | Linked AC / BR |
|---|---|---|---|---|---|---|---|---|---|---|
| TC_XXX_001 | Search taxis for an available route | Positive | P1 | User is on booking page | 1. Enter pickup location. 2. Enter drop location. 3. Click Search. | Pickup: Downtown Helipad; Drop: Airport Helipad | Available taxis are displayed for the selected route. | Not Executed | Not Executed | AC1 |
| TC_XXX_002 | Search taxis when route has no availability | Negative | P1 | User is on booking page | 1. Enter pickup location. 2. Enter drop location with no service. 3. Click Search. | Pickup: Downtown Helipad; Drop: Remote Zone 9 | Message "No taxis available for selected route" is displayed. | Not Executed | Not Executed | AC1 |
| TC_XXX_003 | Search taxis with minimum valid route boundary | Boundary | P2 | User is on booking page | 1. Enter the nearest supported pickup location. 2. Enter the nearest supported drop location. 3. Click Search. | Pickup: Helipad A; Drop: Helipad B | System returns availability results without validation error. | Not Executed | Not Executed | AC1 |
| TC_XXX_004 | Confirm booking after selecting a taxi | Positive | P1 | User has searched and selected an available taxi | 1. Select a taxi. 2. Click Confirm Booking. | Taxi ID: TX-101 | Unique booking ID is generated and confirmation is shown. | Not Executed | Not Executed | AC2, BR1 |
| TC_XXX_005 | Attempt booking confirmation without selecting taxi | Negative | P1 | User is on results page with available taxis | 1. Do not select any taxi. 2. Click Confirm Booking. | No taxi selected | Booking is not created; user is prompted to select a taxi before continuing. | Not Executed | Not Executed | AC2 |
| TC_XXX_006 | Verify booking ID uniqueness across two bookings | Boundary | P1 | User can complete two separate bookings | 1. Complete booking 1. 2. Complete booking 2 for different ride. 3. Compare booking IDs. | Booking 1 and Booking 2 | Each booking receives a unique booking ID. | Not Executed | Not Executed | AC2, BR1 |
| TC_XXX_007 | Successful card payment completes booking | Positive | P1 | User has a selected taxi and booking is pending payment | 1. Choose card payment. 2. Enter valid card details. 3. Submit payment. | Card: Valid Visa test card | Payment succeeds and booking is confirmed. | Not Executed | Not Executed | AC3, BR2 |
| TC_XXX_008 | Payment failure shows exact error message | Negative | P1 | User has a selected taxi and booking is pending payment | 1. Choose card payment. 2. Enter declined card details. 3. Submit payment. | Card: Declined test card | Message "Payment failed. Please try again" is displayed and booking remains unconfirmed. | Not Executed | Not Executed | AC3 |
| TC_XXX_009 | Pay using wallet successfully | Positive | P2 | User has a selected taxi and booking is pending payment | 1. Choose wallet payment. 2. Confirm wallet authorization. | Wallet: Valid wallet account | Payment succeeds and booking is confirmed. | Not Executed | Not Executed | AC3, BR2 |
| TC_XXX_010 | Prevent ride confirmation before payment completion | Negative | P1 | Booking selected but payment not completed | 1. Select taxi. 2. Skip payment. 3. Attempt to confirm ride. | No payment | System blocks ride confirmation until payment is completed. | Not Executed | Not Executed | AC3, BR2 |
| TC_XXX_011 | Cancel booking before ride start | Positive | P1 | Booking is confirmed and ride has not started | 1. Open confirmed booking. 2. Click Cancel Booking. 3. Confirm cancellation. | Confirmed booking ID | Cancellation confirmation is shown and refund is initiated. | Not Executed | Not Executed | AC4, BR4 |
| TC_XXX_012 | Reject cancellation after ride has started | Negative | P1 | Ride has started for a confirmed booking | 1. Open active ride booking. 2. Click Cancel Booking. | Active ride booking ID | Cancellation is not allowed after ride start. | Not Executed | Not Executed | AC4, BR3 |
| TC_XXX_013 | Refund is processed within five minutes after cancellation | Performance | P2 | Booking is cancelled successfully | 1. Cancel booking. 2. Monitor refund timestamp. | Cancelled booking ID | Refund is completed within 5 minutes of cancellation. | Not Executed | Not Executed | AC4, BR4 |
| TC_XXX_014 | Payment data transmission is encrypted | Security | P1 | User is on payment screen | 1. Enter payment details. 2. Submit payment. 3. Verify transport/security behavior. | Card details or wallet token | Payment data is protected through encryption during transmission/storage. | Not Executed | Not Executed | NFR3 |
| TC_XXX_015 | System response time remains within two seconds for booking search | Performance | P2 | Environment is stable with normal test load | 1. Enter pickup and drop locations. 2. Click Search. 3. Measure response time. | Standard route search | Search results are returned within 2 seconds. | Not Executed | Not Executed | NFR1 |
| TC_XXX_016 | Mobile responsive UI on small-screen device | UI/UX | P2 | User accesses app on mobile device | 1. Open booking page on mobile screen. 2. Navigate search, selection, and payment controls. | Device: 390x844 viewport | UI elements render correctly without overlap and remain usable on mobile. | Not Executed | Not Executed | NFR4 |

# Traceability Matrix

AC1 -> TC_XXX_001, TC_XXX_002, TC_XXX_003
AC2 -> TC_XXX_004, TC_XXX_005, TC_XXX_006
AC3 -> TC_XXX_007, TC_XXX_008, TC_XXX_009, TC_XXX_010
AC4 -> TC_XXX_011, TC_XXX_012, TC_XXX_013
BR1 -> TC_XXX_004, TC_XXX_006
BR2 -> TC_XXX_007, TC_XXX_009, TC_XXX_010
BR3 -> TC_XXX_012
BR4 -> TC_XXX_011, TC_XXX_013
NFR1 -> TC_XXX_015
NFR3 -> TC_XXX_014
NFR4 -> TC_XXX_016

# Assumptions & Notes

- Jira ticket AD-231 contains complete story, ACs, BRs, and NFRs; no attachments or comments added additional requirements.
- AC1 route availability is validated using supported and unsupported routes.
- Payment failure error text must match exactly: "Payment failed. Please try again".
- Booking ID uniqueness is validated across separate confirmed bookings.
- Refund timing is measured from successful cancellation timestamp.
- Localization, compliance, accessibility, regression, and compatibility scenarios are represented through functional coverage only where explicit UI/device behavior was available in the ticket; no separate acceptance criteria were provided for locale/legal/regional rules.