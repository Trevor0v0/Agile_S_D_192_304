# SiamSera Project Charter

## 1. Project Overview

| Item | Details |
|---|---|
| Project name | SiamSera |
| Product concept | University-focused second-hand marketplace for students |
| Primary users | University students |
| Document status | Initial project charter |
| Version | 1.0 |
| Date | 5 September 2026 |

SiamSera is intended to provide a convenient marketplace where university students can buy and sell second-hand items. The platform focuses on student-to-student transactions, university-based discovery, student verification, and direct communication between buyers and sellers.

## 2. Problem Statement

Students often have unused textbooks, electronics, furniture, clothing, dormitory supplies, and other items that could be useful to other students. General-purpose marketplaces can make it difficult to find nearby students or items relevant to a particular university.

SiamSera addresses this problem by creating a student-focused marketplace where users can list used items, search and filter products, prioritize listings from their university, verify their student identity, and communicate directly with buyers or sellers.

## 3. Vision and Objectives

### Vision

Make buying and selling second-hand items among university students simple, convenient, and trustworthy.

### Objectives

1. Allow students to create detailed second-hand product listings with photos.
2. Help students find suitable products through keyword search and filters.
3. Prioritize marketplace listings from the user's selected university.
4. Provide student verification to increase trust between marketplace users.
5. Provide direct buyer-seller chat for questions and meeting arrangements.
6. Deliver a simple, responsive experience suitable for everyday student use.

## 4. Scope

### In scope for the initial release

- Student registration, sign-in, and profile management.
- University selection and student verification.
- Creating second-hand item listings.
- Uploading product photos.
- Listing information including product name, price, condition, category, description, and location.
- Browsing available listings.
- Keyword search.
- Filtering by category, price, condition, and location.
- University-based marketplace discovery.
- Listing detail pages.
- Buyer-seller chat.
- Listing management by sellers, including editing and marking items as sold/unavailable.

### Out of scope for the initial release

- Integrated online payment processing.
- Delivery and shipping management.
- Auction functionality.
- Automated price negotiation.
- Business/vendor accounts.
- Advanced AI product recommendations.
- Full transaction escrow or payment protection.
- University-wide administrative systems integration unless separately approved.

## 5. Stakeholders and Responsibilities

| Stakeholder | Interest or responsibility |
|---|---|
| Student users | Buy and sell second-hand products |
| Sellers | Create accurate listings and communicate with buyers |
| Buyers | Search for products, review details, and communicate with sellers |
| Project team | Analyze, design, develop, test, and document SiamSera |
| Project supervisor/instructor | Review requirements, quality, and project deliverables |
| Marketplace administrator | Manage categories, moderation, and platform-level content where required |
| Universities | Provide the context for student identity and university affiliation |

The team should assign ownership for each major feature and nominate a reviewer for significant changes.

## 6. Major Deliverables

1. Approved project charter and requirements specification.
2. User flows/wireframes for authentication, marketplace browsing, listing creation, and chat.
3. Implemented student account and university-selection flow.
4. Implemented student verification flow.
5. Implemented listing creation and management.
6. Implemented search and filtering.
7. Implemented university-based marketplace discovery.
8. Implemented buyer-seller chat.
9. Database schema and development seed data.
10. Acceptance test evidence and defect list.
11. Demonstrable release candidate and project documentation.

## 7. Milestones

| Milestone | Exit condition |
|---|---|
| Discovery and scope | Charter, target users, assumptions, and MVP scope approved |
| Requirements and design | Requirements, acceptance criteria, database design, and core user flows reviewed |
| Foundation | Application structure, database, and authentication foundation available |
| Core marketplace build | Listing, search/filter, university, verification, and chat features implemented |
| Validation | Acceptance scenarios executed and critical defects resolved |
| Release and handover | Demonstration completed and documentation finalized |

Exact dates should be assigned according to the course schedule and team availability.

## 8. Success Measures

- At least 90% of defined acceptance scenarios pass before release.
- A verified student can create a complete listing without assistance.
- A student can find relevant products using search and filters.
- Same-university listings are clearly prioritized for users who have selected a university.
- Buyers and sellers can successfully start and continue a chat.
- No unresolved critical security or data-loss defects remain at release.
- Core marketplace pages remain usable on common desktop and mobile browsers.

## 9. Risks and Mitigations

| Risk | Impact | Mitigation |
|---|---|---|
| Fake or inaccurate listings | Reduced trust | Require authenticated users and validate required listing data |
| Fraud or unsafe meeting arrangements | User safety concern | Encourage users to arrange exchanges carefully and avoid unnecessary personal information |
| Inappropriate listing content | Platform quality issue | Provide moderation/reporting mechanisms where feasible |
| Fake student identity | Reduced trust | Use a defined verification workflow and display verification status |
| Scope expansion | Schedule overrun | Keep payment, delivery, auctions, and advanced recommendations out of MVP |
| Privacy issues | High | Minimize stored personal/verification information and restrict access |
| Development delays | High | Prioritize Must Have MVP features |
| Poor search performance | Reduced usability | Add appropriate database indexes and test common queries |

## 10. Assumptions and Constraints

- The initial audience is university students.
- Users have access to a modern web browser and internet connection.
- Users are responsible for the accuracy of information in their listings.
- The MVP focuses on connecting buyers and sellers rather than processing payments.
- Meeting arrangements are coordinated by users through chat.
- Student verification requirements may vary by university and should be finalized during implementation.
- The project has limited time and team capacity, so optional features should not delay the MVP.

## 11. Approval Criteria

The charter is ready for approval when the team and supervisor agree on:

- The initial-release scope and exclusions.
- The target student user group.
- The listing and marketplace workflow.
- The university verification approach.
- The buyer-seller communication workflow.
- The success measures and acceptance approach.
- The assumptions requiring validation during development.
