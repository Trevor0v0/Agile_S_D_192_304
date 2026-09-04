# SiamSera Requirements Specification

## 1. Document Control

| Field | Value |
|---|---|
| Product | SiamSera |
| Version | 1.0 initial specification |
| Audience | Project team, supervisor, testers, and future implementers |
| Primary users | University students |
| Related documents | Project Charter, Acceptance Criteria, Database Design |

## 2. Product Description

SiamSera is a university-focused second-hand marketplace web application. Students can create listings for used items, discover products through search and filters, primarily browse items associated with their university, verify their student status, and communicate directly with buyers or sellers.

The MVP is intended to support the core discovery and communication workflow without implementing online payments or delivery services.

## 3. User Roles

| Role | Description | Permissions |
|---|---|---|
| Student | Main marketplace user | Manage own profile, browse listings, search/filter, create/manage own listings, chat |
| Verified Student | Student whose university identity has been verified | All Student permissions plus verified status display |
| Administrator | Maintains platform-level data and moderation | Manage categories, moderate listings/users, manage supported universities where applicable |

## 4. User Stories

- As a student, I want to create an account so I can use the marketplace.
- As a student, I want to select my university so I can see relevant listings.
- As a student, I want to verify my university identity so other users can trust that I am a student.
- As a student, I want to create a listing with photos and product details so I can sell an item.
- As a seller, I want to edit or mark my listing as sold so its information stays accurate.
- As a student, I want to search for products by keyword so I can find items quickly.
- As a student, I want to filter products by category, price, condition, and location so I can narrow the results.
- As a student, I want to prioritize listings from my university so I can find convenient student-to-student exchanges.
- As a buyer, I want to view complete listing details so I can decide whether an item is suitable.
- As a buyer, I want to chat with a seller so I can ask questions and arrange a meeting.
- As a seller, I want to receive buyer messages so I can answer questions about my item.

## 5. Functional Requirements

### FR-01 — Account Registration and Authentication
- The system shall allow a student to register an account.
- The system shall validate required registration fields.
- The system shall prevent duplicate accounts using the same unique email/identifier.
- The system shall allow registered users to sign in and sign out.
- Passwords shall be stored securely using password hashing.

### FR-02 — Student Profile and University
- The system shall allow a student to select a university.
- The system shall store the selected university against the user's profile.
- The system shall allow users to view and update appropriate profile information.

### FR-03 — Student Verification
- The system shall provide a university identity verification process.
- The system shall store a verification status such as Pending, Verified, or Rejected.
- The system shall display a verified indicator to other users when appropriate.
- Sensitive verification information shall not be publicly exposed.

### FR-04 — Create Listing
- An authenticated student shall be able to create a listing.
- A listing shall include product name, price, condition, description, category, location, and at least one photo.
- The system shall validate required fields.
- The system shall associate the listing with its seller and university context.

### FR-05 — Listing Management
- A seller shall be able to view their own listings.
- A seller shall be able to edit their own listing.
- A seller shall be able to mark a listing as Sold or Unavailable.
- A seller shall not be able to edit another user's listing.

### FR-06 — Browse Marketplace
- Users shall be able to browse available listings.
- Listing cards shall provide enough information to identify the product, including name and price.
- Users shall be able to open a listing detail page.

### FR-07 — Search
- Users shall be able to search listings using keywords.
- Search shall consider relevant listing fields such as product name and description.
- The system shall clearly show when no matching results are found.

### FR-08 — Filtering
Users shall be able to filter marketplace results by:
- Category
- Minimum and maximum price
- Condition
- Location

The system shall allow users to combine applicable filters.

### FR-09 — University-Based Marketplace
- The system shall use the user's selected university as marketplace context.
- Listings from the selected university shall be prioritized or primarily displayed.
- The system shall clearly communicate the university context to the user.
- If broader marketplace browsing is supported, users shall be able to discover listings outside their university.

### FR-10 — Listing Details
- The listing detail page shall display product photos.
- It shall display product name, price, condition, description, category, location, and relevant seller/university information.
- It shall provide an option to contact the seller.

### FR-11 — Buyer-Seller Chat
- A user shall be able to start a conversation about a listing.
- The conversation shall identify the buyer, seller, and related listing.
- Participants shall be able to send text messages.
- Messages shall be stored with sender and timestamp information.
- Participants shall be able to view relevant conversation history.

### FR-12 — Listing Status
- Listings shall have a status such as Available, Sold, or Unavailable.
- Sold/unavailable listings shall not be treated as normally available marketplace inventory.
- The seller shall be able to update the status of their own listing.

## 6. Non-Functional Requirements

### NFR-01 — Usability
The interface shall use clear labels, understandable navigation, and consistent controls. Core tasks should be achievable without specialized technical knowledge.

### NFR-02 — Performance
Common operations such as browsing, searching, filtering, and opening a listing should respond within an acceptable time under normal project usage.

### NFR-03 — Security
- Passwords shall never be stored as plain text.
- Authentication shall protect user-specific operations.
- Authorization shall prevent users from modifying other users' listings.
- Sensitive verification information shall be restricted.
- User input shall be validated and sanitized.

### NFR-04 — Reliability
The system should handle invalid inputs and expected errors without crashing or corrupting data.

### NFR-05 — Maintainability
Code and database structures should use clear naming, modular organization, and consistent conventions.

### NFR-06 — Compatibility
The web application should support commonly used modern desktop and mobile browsers.

### NFR-07 — Privacy
The system should collect only information required for the marketplace workflow and should avoid exposing private user information unnecessarily.

## 7. Data Requirements

The system shall maintain data for:
- Users
- Universities
- Categories
- Listings
- Listing photos
- Conversations
- Messages
- Student verification status

## 8. Business Rules

1. Every listing must have exactly one seller.
2. A seller must be a registered user.
3. A listing must reference a valid category.
4. A listing must contain a valid non-negative price.
5. Required listing information must not be empty.
6. Only the listing owner may modify or change the status of a listing.
7. A conversation must reference valid participating users and a relevant listing.
8. A message must belong to a valid conversation and sender.
9. A user may have only one active profile associated with their account.
10. Verification status must be controlled by the defined verification workflow.

## 9. Requirement Priority

| Requirement | Priority |
|---|---|
| Registration and authentication | Must Have |
| Student verification | Must Have |
| Create listing | Must Have |
| Listing management | Must Have |
| Browse listings | Must Have |
| Search | Must Have |
| Filtering | Must Have |
| University-based marketplace | Must Have |
| Listing details | Must Have |
| Buyer-seller chat | Must Have |
| Online payments | Out of MVP |
| Delivery/shipping | Out of MVP |
| Auctions | Out of MVP |
| AI recommendations | Out of MVP |

## 10. Traceability

| Feature | Requirements | Acceptance Criteria |
|---|---|---|
| Registration/login | FR-01 | AC-01–AC-02 |
| University/profile | FR-02 | AC-03 |
| Verification | FR-03 | AC-04–AC-05 |
| Create/manage listing | FR-04–FR-05 | AC-06–AC-09 |
| Browse/search/filter | FR-06–FR-08 | AC-10–AC-14 |
| University marketplace | FR-09 | AC-15–AC-16 |
| Listing details | FR-10 | AC-17 |
| Chat | FR-11 | AC-18–AC-20 |
| Listing status | FR-12 | AC-21 |
