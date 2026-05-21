# Summary

Total test cases: 25

Category-wise breakdown: Positive 4, Negative 4, Boundary 4, Security 2, Performance 2, UI/UX 1, Integration 1, Compatibility 1, Accessibility 1, Localization 1, Regression 1, Edge Cases 1, Data Validation 1, Compliance 1

Priority-wise breakdown: P1 10, P2 10, P3 4, P4 1

# Test Cases

| TC ID | Test Case Title | Category | Priority | Preconditions | Test Steps | Test Data | Expected Result | Actual Result | Status | Linked AC / BR |
|---|---|---|---|---|---|---|---|---|---|---|
| TC_001_001 | Search available flying taxis for a valid route | Positive | P1 | User is logged in and search service is available | 1. Open the flying taxi booking page. 2. Enter a valid pickup location. 3. Enter a valid drop location. 4. Click Search. | Pickup: Mumbai Airport; Drop: Pune Station | Available flying taxis are displayed with route details and pricing. | Not Executed | Not Executed | Not Executed | AC1 |
| TC_001_002 | Display route search results including taxi count and estimated fare | Positive | P2 | User is on booking screen; search service is available | 1. Enter pickup location. 2. Enter drop location. 3. Click Search. 4. Verify result cards. | Pickup: Bangalore HSR; Drop: Mysore City Center | Search results include taxi list, estimated fare, and route duration. | Not Executed | Not Executed | Not Executed | AC1 |
| TC_001_003 | Preserve search criteria after a successful availability lookup | Regression | P3 | User is on booking screen | 1. Enter pickup and drop locations. 2. Perform search. 3. Navigate back or refresh results area. | Pickup: Delhi Aero City; Drop: Gurugram Cyber City | Previously entered route values remain visible or recoverable after successful search. | Not Executed | Not Executed | Not Executed | AC1 |
| TC_001_004 | Warn user when pickup and drop locations are identical | Edge Cases | P2 | User is on booking screen | 1. Enter same value in pickup and drop fields. 2. Click Search. | Pickup: Mumbai Airport; Drop: Mumbai Airport | System blocks search and displays "Pickup and drop locations must be different". | Not Executed | Not Executed | Not Executed | AC1 |