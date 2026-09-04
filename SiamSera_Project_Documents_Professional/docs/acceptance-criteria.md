# SiamSera Acceptance Criteria

## 1. Acceptance Approach

Acceptance criteria define observable conditions that must be satisfied for the SiamSera MVP to be accepted.

Each scenario follows the **Given / When / Then** format:

- **Given** describes the initial state.
- **When** describes the user's action.
- **Then** describes the expected system result.

## 2. Account and Student Verification

### AC-01 — Student Registration

**Given** a student has valid registration information  
**When** the student submits the registration form  
**Then** SiamSera shall create the account and confirm successful registration.

### AC-02 — Student Login

**Given** a registered student has valid login credentials  
**When** the student submits the login form  
**Then** SiamSera shall authenticate the student and provide access to the marketplace.

### AC-03 — Invalid Login

**Given** a student enters incorrect login credentials  
**When** the student attempts to sign in  
**Then** the system shall reject the login and display an appropriate error message without revealing sensitive authentication information.

### AC-04 — Select University

**Given** a registered student is completing or editing their profile  
**When** the student selects a university  
**Then** the system shall save the selected university to the student's profile.

### AC-05 — Student Verification

**Given** a student provides the information required by the verification workflow  
**When** the verification process is successfully completed  
**Then** the system shall set the student's verification status to Verified.

### AC-06 — Verification Status Display

**Given** a student's account has Verified status  
**When** another user views an applicable profile or listing  
**Then** SiamSera shall display an appropriate verified-student indicator without exposing unnecessary verification information.

## 3. Listing Creation and Management

### AC-07 — Create Complete Listing

**Given** an authenticated student is creating a listing  
**When** the student provides a product name, price, condition, description, category, location, and photo  
**Then** the system shall create the listing and make it available in the marketplace.

### AC-08 — Required Listing Validation

**Given** a student is creating a listing  
**When** one or more required fields are missing or invalid  
**Then** the system shall display validation feedback and shall not create the incomplete listing.

### AC-09 — Invalid Price

**Given** a student is creating or editing a listing  
**When** the student enters an invalid price such as a negative value or invalid format  
**Then** the system shall reject the value and request a valid price.

### AC-10 — Edit Own Listing

**Given** a student owns an existing listing  
**When** the student changes valid listing information and saves  
**Then** the system shall update the listing and display the updated information.

### AC-11 — Prevent Unauthorized Listing Edit

**Given** a student does not own a listing  
**When** the student attempts to edit that listing  
**Then** the system shall deny the operation.

### AC-12 — Mark Listing as Sold

**Given** a student owns an available listing  
**When** the student marks the item as Sold  
**Then** the listing status shall change to Sold and it shall no longer be treated as normally available inventory.

### AC-13 — Listing Photo

**Given** a student is creating a listing  
**When** the student uploads a supported product image  
**Then** the system shall associate the image with the listing and make it available on the listing detail page.

## 4. Marketplace Discovery

### AC-14 — Browse Listings

**Given** available listings exist  
**When** a student opens the marketplace  
**Then** the system shall display available listings with basic product information.

### AC-15 — Keyword Search

**Given** listings exist containing searchable product information  
**When** a student enters a keyword and performs a search  
**Then** the system shall display relevant matching listings.

### AC-16 — Category Filter

**Given** listings exist in multiple categories  
**When** a student selects a category filter  
**Then** the system shall display listings matching the selected category.

### AC-17 — Price Filter

**Given** listings have different prices  
**When** a student selects a valid minimum and/or maximum price  
**Then** the system shall display listings whose prices fall within the selected range.

### AC-18 — Condition Filter

**Given** listings have different product conditions  
**When** a student selects a condition  
**Then** the system shall display listings matching the selected condition.

### AC-19 — Location Filter

**Given** listings have different locations  
**When** a student selects a location filter  
**Then** the system shall display listings matching the selected location.

### AC-20 — Combined Filters

**Given** multiple filters are available  
**When** a student applies more than one compatible filter  
**Then** the system shall return listings satisfying the combined criteria.

### AC-21 — No Search Results

**Given** no listings match the selected search or filter criteria  
**When** the search is performed  
**Then** the system shall clearly indicate that no matching items were found.

## 5. University-Based Marketplace

### AC-22 — Same-University Priority

**Given** a student has selected a university  
**When** the student opens the marketplace  
**Then** listings from the selected university shall be prioritized or primarily displayed.

### AC-23 — University Context

**Given** a student is browsing the marketplace  
**When** the marketplace page is displayed  
**Then** the student shall be able to understand which university context is being used for the marketplace results.

### AC-24 — Broader Marketplace Access

**Given** broader marketplace browsing is enabled  
**When** a student chooses to view listings outside their university  
**Then** the system shall allow access to those listings without changing the student's selected university.

## 6. Listing Details

### AC-25 — View Listing Details

**Given** a student sees an available listing  
**When** the student opens the listing  
**Then** the system shall display the product photos, name, price, condition, description, category, location, and relevant seller/university information.

### AC-26 — Contact Seller

**Given** a student is viewing another student's listing  
**When** the student chooses to contact the seller  
**Then** the system shall open or create a conversation associated with the listing.

## 7. Buyer-Seller Chat

### AC-27 — Start Conversation

**Given** a buyer is viewing a listing owned by another student  
**When** the buyer selects the chat/contact option  
**Then** SiamSera shall create or open the relevant buyer-seller conversation.

### AC-28 — Send Message

**Given** two users have a valid conversation  
**When** one participant sends a non-empty text message  
**Then** the message shall be stored with the sender and timestamp and become visible in the conversation.

### AC-29 — Conversation History

**Given** a conversation contains previous messages  
**When** a participant opens the conversation  
**Then** the system shall display the relevant message history.

### AC-30 — Meeting Arrangement

**Given** a buyer and seller are communicating about an item  
**When** they exchange suitable meeting information through chat  
**Then** the system shall allow the conversation to continue normally.

### AC-31 — Conversation Authorization

**Given** a user is not a participant in a private conversation  
**When** the user attempts to access that conversation  
**Then** the system shall deny access.

## 8. Overall MVP Acceptance

The SiamSera MVP is ready for release when:

1. All Must Have requirements are implemented.
2. At least 90% of acceptance scenarios pass.
3. No critical defect prevents a student from completing the core buy/sell workflow.
4. Unauthorized listing modification is prevented.
5. Student verification status is handled correctly.
6. Search and filtering return appropriate results.
7. University-based marketplace prioritization works.
8. Listing details and photos display correctly.
9. Buyer-seller chat works for the core messaging workflow.
10. No unresolved critical security or data-loss defect remains.

## 9. Release Decision

| Result | Decision |
|---|---|
| All critical scenarios pass and no critical defects remain | Accept |
| Minor non-blocking defects remain | Accept with documented follow-up |
| Any critical workflow is unusable | Reject until corrected |
| Critical security/data-loss defect remains | Reject until corrected |
