# SiamSera Database Design

## 1. Design Goals

The SiamSera database is designed to support the core MVP marketplace workflow:

1. Manage student accounts and university affiliations.
2. Track student verification status.
3. Store second-hand product listings.
4. Support product categories and photos.
5. Support university-based marketplace discovery.
6. Store buyer-seller conversations and messages.
7. Preserve data integrity and enforce ownership relationships.

## 2. Design Assumptions

- A user has one primary university for the MVP.
- A user can create multiple listings.
- Each listing belongs to one seller.
- Each listing belongs to one category.
- Each listing can have multiple photos.
- A conversation is associated with one listing and one buyer/seller pair.
- Messages belong to exactly one conversation.
- Verification status is stored on the user account.
- Payment and delivery entities are intentionally excluded from the MVP.

## 3. Entity Relationship Diagram

```text
                    ┌──────────────────┐
                    │   UNIVERSITIES    │
                    ├──────────────────┤
                    │ PK university_id  │
                    │    name           │
                    └────────┬─────────┘
                             │ 1
                             │
                             │ N
                    ┌────────▼─────────┐
                    │      USERS       │
                    ├──────────────────┤
                    │ PK user_id       │
                    │ FK university_id │
                    │    name          │
                    │    email         │
                    │    password_hash  │
                    │    verify_status  │
                    └───────┬──────────┘
                            │ 1
                            │
                            │ N
                    ┌───────▼──────────┐
                    │     LISTINGS     │
                    ├──────────────────┤
                    │ PK listing_id    │
                    │ FK seller_id     │
                    │ FK category_id   │
                    │    name          │
                    │    price         │
                    │    condition     │
                    │    description   │
                    │    location      │
                    │    status        │
                    └───────┬──────────┘
                            │ 1
                            │
                            │ N
                    ┌───────▼──────────┐
                    │ LISTING_PHOTOS   │
                    ├──────────────────┤
                    │ PK photo_id      │
                    │ FK listing_id    │
                    │    photo_url     │
                    │    sort_order    │
                    └──────────────────┘

        ┌──────────────────┐
        │    CATEGORIES    │
        ├──────────────────┤
        │ PK category_id   │
        │    name          │
        └────────┬─────────┘
                 │ 1
                 │
                 │ N
              LISTINGS

        USERS (buyer) ──────┐
                            │
                            ▼
                    ┌──────────────────┐
                    │  CONVERSATIONS   │
                    ├──────────────────┤
                    │ PK conversation_id│
                    │ FK listing_id    │
                    │ FK buyer_id      │
                    │ FK seller_id     │
                    │    created_at    │
                    └────────┬─────────┘
                             │ 1
                             │
                             │ N
                    ┌────────▼─────────┐
                    │     MESSAGES     │
                    ├──────────────────┤
                    │ PK message_id    │
                    │ FK conversation_id│
                    │ FK sender_id     │
                    │    message_text  │
                    │    sent_at       │
                    └──────────────────┘

              USERS (seller) ────────┘
```

## 4. Entity Definitions

### 4.1 Universities

Stores the universities supported by SiamSera.

### 4.2 Users

Stores student accounts, their selected university, and verification status.

### 4.3 Categories

Stores marketplace product categories such as Electronics, Textbooks, Furniture, Clothing, and Dormitory Items.

### 4.4 Listings

Stores products offered for sale by students.

### 4.5 Listing Photos

Stores references to images associated with marketplace listings.

### 4.6 Conversations

Represents a private buyer-seller conversation associated with a listing.

### 4.7 Messages

Stores individual text messages sent inside a conversation.

## 5. Table Specifications

### 5.1 Universities

| Field | Data Type | Key | Null | Description |
|---|---|---|---|---|
| university_id | INT | PK | NO | Unique university identifier |
| name | VARCHAR(150) | UNIQUE | NO | University name |
| created_at | DATETIME | | NO | Record creation timestamp |

### 5.2 Users

| Field | Data Type | Key | Null | Description |
|---|---|---|---|---|
| user_id | INT | PK | NO | Unique user identifier |
| university_id | INT | FK | NO | User's selected university |
| name | VARCHAR(100) | | NO | Display name |
| email | VARCHAR(255) | UNIQUE | NO | Login/contact identifier |
| password_hash | VARCHAR(255) | | NO | Secure password hash |
| verification_status | VARCHAR(20) | | NO | Pending/Verified/Rejected |
| created_at | DATETIME | | NO | Account creation time |
| updated_at | DATETIME | | NO | Last profile update |

### 5.3 Categories

| Field | Data Type | Key | Null | Description |
|---|---|---|---|---|
| category_id | INT | PK | NO | Unique category identifier |
| name | VARCHAR(100) | UNIQUE | NO | Category name |
| description | VARCHAR(255) | | YES | Optional category description |

### 5.4 Listings

| Field | Data Type | Key | Null | Description |
|---|---|---|---|---|
| listing_id | INT | PK | NO | Unique listing identifier |
| seller_id | INT | FK | NO | User who owns the listing |
| category_id | INT | FK | NO | Listing category |
| name | VARCHAR(150) | | NO | Product name |
| price | DECIMAL(10,2) | | NO | Selling price |
| condition | VARCHAR(50) | | NO | Product condition |
| description | TEXT | | NO | Product description |
| location | VARCHAR(255) | | NO | Exchange/meeting location |
| status | VARCHAR(20) | | NO | Available/Sold/Unavailable |
| created_at | DATETIME | | NO | Creation timestamp |
| updated_at | DATETIME | | NO | Last update timestamp |

### 5.5 Listing_Photos

| Field | Data Type | Key | Null | Description |
|---|---|---|---|---|
| photo_id | INT | PK | NO | Unique photo identifier |
| listing_id | INT | FK | NO | Related listing |
| photo_url | VARCHAR(500) | | NO | Image storage reference |
| sort_order | INT | | NO | Photo display order |

### 5.6 Conversations

| Field | Data Type | Key | Null | Description |
|---|---|---|---|---|
| conversation_id | INT | PK | NO | Unique conversation identifier |
| listing_id | INT | FK | NO | Listing being discussed |
| buyer_id | INT | FK | NO | Buyer/user |
| seller_id | INT | FK | NO | Seller/user |
| created_at | DATETIME | | NO | Conversation creation time |
| updated_at | DATETIME | | NO | Last conversation update |

### 5.7 Messages

| Field | Data Type | Key | Null | Description |
|---|---|---|---|---|
| message_id | INT | PK | NO | Unique message identifier |
| conversation_id | INT | FK | NO | Related conversation |
| sender_id | INT | FK | NO | User who sent message |
| message_text | TEXT | | NO | Message content |
| sent_at | DATETIME | | NO | Message timestamp |

## 6. Relationships and Cardinality

| Relationship | Cardinality | Description |
|---|---|---|
| University → Users | 1:N | One university can have many users |
| User → Listings | 1:N | One user can create many listings |
| Category → Listings | 1:N | One category can contain many listings |
| Listing → Listing Photos | 1:N | One listing can contain multiple photos |
| Listing → Conversations | 1:N | A listing can have conversations from interested buyers |
| User → Conversations as buyer | 1:N | A user can initiate conversations |
| User → Conversations as seller | 1:N | A seller can receive conversations |
| Conversation → Messages | 1:N | A conversation contains many messages |
| User → Messages | 1:N | A user can send many messages |

## 7. Integrity Constraints

### Primary Keys
Every table shall have a unique primary key.

### Foreign Keys
- `Users.university_id` references `Universities.university_id`.
- `Listings.seller_id` references `Users.user_id`.
- `Listings.category_id` references `Categories.category_id`.
- `Listing_Photos.listing_id` references `Listings.listing_id`.
- `Conversations.listing_id` references `Listings.listing_id`.
- `Conversations.buyer_id` references `Users.user_id`.
- `Conversations.seller_id` references `Users.user_id`.
- `Messages.conversation_id` references `Conversations.conversation_id`.
- `Messages.sender_id` references `Users.user_id`.

### Validation Rules
- User email must be unique.
- University name must be unique.
- Category name must be unique.
- Listing price must be greater than or equal to zero.
- Listing status must use an allowed status value.
- Verification status must use an allowed status value.
- Required fields must not be NULL.
- A seller must be a valid registered user.
- A message sender must be a participant in the related conversation.

## 8. Ownership and Authorization Rules

1. A user can update only their own profile information.
2. A seller can update or change the status of only their own listings.
3. A buyer cannot modify the seller's listing.
4. Only conversation participants can read or send messages in a private conversation.
5. Administrative operations require appropriate administrator authorization.

## 9. Indexing Strategy

The following indexes are recommended for common marketplace queries:

| Table | Index | Reason |
|---|---|---|
| Users | `university_id` | University-based marketplace queries |
| Listings | `seller_id` | Seller's own listings |
| Listings | `category_id` | Category filtering |
| Listings | `price` | Price-range filtering |
| Listings | `condition` | Condition filtering |
| Listings | `location` | Location filtering |
| Listings | `created_at` | Recent listing sorting |
| Listings | `status` | Available listing queries |
| Conversations | `listing_id` | Conversations by listing |
| Conversations | `buyer_id` | Buyer's conversations |
| Conversations | `seller_id` | Seller's conversations |
| Messages | `conversation_id` | Conversation history retrieval |
| Messages | `sent_at` | Chronological message ordering |

## 10. Data Security and Privacy

- Passwords shall be stored as secure hashes.
- Verification information shall be protected and minimized.
- The database should not store unnecessary sensitive verification documents.
- Access to private conversations shall be authorized.
- User-generated text should be validated before storage/display.
- Uploaded images should be validated for supported file type and reasonable size.
- Database credentials must not be committed to a public source-code repository.

## 11. Data Lifecycle

### Listing lifecycle

```text
Draft/Creation
     ↓
Available
     ↓
Sold / Unavailable
```

### Verification lifecycle

```text
Pending
  ├──→ Verified
  └──→ Rejected
```

### Conversation lifecycle

```text
Created
   ↓
Active messaging
   ↓
No longer active / retained as history
```

## 12. MVP Exclusions

The following database entities are intentionally not required for the initial MVP:

- Payments
- Orders/checkout
- Delivery/shipping
- Auctions
- Seller business accounts
- Advanced recommendation engine

These can be added later without changing the core user/listing/chat model significantly.
