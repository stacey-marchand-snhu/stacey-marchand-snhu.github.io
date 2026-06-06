---
layout: default
---

<link rel="stylesheet" href="/assets/css/custom.css">

# Enhancement Three
# Databases

This narrative explains my enhancement to the CS-465 Full Stack Application through a database and authentication architecture migration to Google Firebase.

## Overview

The selected artifact for the databases category is the Travlr Full Stack Application, originally created in CS-465 Full Stack Development and later enhanced in CS-499 through a React/TypeScript rewrite of the administration site. At the start of this database enhancement, the artifact already had a modern React admin interface, but it was still backed by the existing Express API, MongoDB/Mongoose data models, Passport authentication, and custom JSON Web Tokens. For this milestone, I further enhanced the artifact by migrating the application's database and authentication architecture to Google Firebase, specifically Cloud Firestore for trip and user data and Firebase Authentication for account identity.

## Justification & Improvement

This artifact was selected because it provided a strong opportunity to demonstrate database architecture in a realistic full-stack context. The Travlr application already included a public travel site, an administrative portal, a REST API, and persistent trip data, so the database layer was central to the application's purpose. Improving this artifact enabled demonstrating more than just basic CRUD functionality; it offered a chance to rethink how data is stored, how users are authenticated, how administrative permissions are enforced, and how the application can move from a local database model toward a modern cloud-based architecture.

The major improvement was replacing the MongoDB/Mongoose backend with a Firestore-backed API. In the previous React-enhanced version, trip data was modeled through Mongoose schemas and stored in MongoDB. In the enhanced version, trips are stored as documents in a Firestore trips collection, while user profile data is stored separately in a users collection. The backend was also converted from JavaScript to TypeScript, with typed trip and user models, a Firebase Admin SDK configuration file, and controller logic that works directly with Firestore collections. This made the database layer more explicit, more strongly typed, and better aligned with the TypeScript structure already used in the React admin application.

Authentication was also significantly improved. The earlier version used Passport, locally stored password hashes, salts, and custom JWT generation. The enhanced version moves identity management to Firebase Authentication, eliminating the need for the application to hash, store, or validate passwords manually. Registration now creates a Firebase Auth account, sets a custom role claim ("admin" or "user"), and writes a Firestore user profile document. The React admin app signs in through the Firebase client SDK, listens for authentication state changes, and automatically attaches fresh Firebase ID tokens to API requests. This creates a cleaner separation of responsibilities: Firebase manages identity, while the Express API verifies tokens and enforces application-specific access rules.

The enhancement also added robust authorization and validation. Protected API routes now verify Firebase bearer tokens and require an admin role before allowing trip creation, updates, or deletion. Public read routes remain available for viewing trips, while administrative write operations are restricted. The backend now also uses Zod validation schemas for trip and user registration data, meaning the API no longer relies solely on front-end validation or database schema behavior to reject invalid input. This was an important improvement because it made the database-facing layer more defensive and consistent. Finally, as a last line of defense, the Firestore database was programmed with role authorization rules to reinforce admin role requirements for write behavior, should a malicious party modify the codebase to attempt to gain destructive access to the persistence store:

![Firestore Authorization Rules](/assets/images/firestore-auth-code.png)

Several supporting improvements made the artifact more professional and easier to review. The project now includes updated root and admin README files that explain the Firebase-backed architecture, environment variables, authentication flow, API routes, and local setup process. The backend includes a Firestore seed script that clears and repopulates the trips collection from the existing JSON seed data. I also added a documented Postman collection that covers user registration, Firebase login, viewing trips, adding trips, and updating trips. This is a meaningful addition because it gives another developer or reviewer a practical way to test the API without having to walk through the UI first, and to access features unavailable through the interface.

## Course Outcomes

This enhancement met the course outcomes I planned to address in Module One. It supports Outcome 1 by creating an enterprise-accessible, cloud-hosted source of trip data that supports both the public site and the administrative portal. It supports Outcome 2 through updated, comprehensive, and refined documentation, comments, README files, and a Postman collection, all of which explain the revised database and authentication workflow to a technical audience. It supports Outcome 3 because I had to evaluate trade-offs between MongoDB/Mongoose and Firestore, between local credential handling and managed authentication, and between simple route protection and role-based authorization. It supports Outcome 4 by using Firebase Authentication, Cloud Firestore, TypeScript, Zod validation, a service-oriented API structure, and the very latest development tooling. Finally, it supports Outcome 5 by removing local password storage, verifying Firebase ID tokens, enforcing admin-only write operations, improving input validation before data reaches the database, and eliminating all detected vulnerabilities identified during an NPM security audit.

The overall outcome-coverage plan needs no alteration, but I would describe the final implementation more precisely. The enhancement does include Firebase Authentication, Cloud Firestore, separate trips and users collections, typed TypeScript models, role metadata, Zod validation, and a Firestore seed process. However, the submitted implementation enforces most access control through the Express API layer by verifying Firebase ID tokens and checking custom role claims, rather than through a separate Firestore security rules file. This still supports the planned security outcome because administrative trip create, update, and delete operations are protected by token verification and role-based middleware. At the same time, I would note that the registration route is currently simplified for the milestone and would need additional hardening in a production version, such as restricting who can create administrative accounts.

## Enhancement Process

The process of enhancing this artifact taught me that database migration is really an architecture redesign, not just a change in storage technology. I had to carefully think through what belonged in Firebase Authentication, what belonged in Firestore, and what still belonged in the Express API. One challenge was preserving the existing application behavior while changing the foundation underneath it. The admin portal still needed to manage trips through familiar API calls, and the public site still needed to display trip data, but the way that data was retrieved, validated, and protected changed substantially.

Another challenge was keeping the migration scope and understanding clear. The goal was to improve the database and authentication architecture in a way that made sense for the artifact and demonstrated clear proficiency with a state-of-the-art persistence and authentication framework. By the end of the enhancement, the artifact had moved from a local MongoDB and custom user validation approach to a cloud-backed Firestore and Firebase Authentication model with strong typing, clear documentation, role-aware access control, and better API testing support. This makes the enhanced version a much stronger ePortfolio artifact because it shows that I can modernize an existing application's data architecture while preserving its purpose and improving its reliability, maintainability, and security.

---

[← Back to Portfolio](/)


