---
layout: default
---

<link rel="stylesheet" href="/assets/css/custom.css">

# Enhancement Three: Databases

This narrative explains my enhancement to the CS-465 Full Stack Application through a database and authentication architecture migration to Google Firebase.

## Overview

The selected artifact for the databases category is the Travlr Full Stack Application, originally created in CS-465 Full Stack Development and later enhanced in CS-499 through a React/TypeScript rewrite of the administration site. At the start of this database enhancement, the artifact already had a modern React admin interface, but it was still backed by the existing Express API, MongoDB/Mongoose data models, Passport authentication, and custom JSON Web Tokens. For this milestone, I further enhanced the artifact by migrating the application's database and authentication architecture to Google Firebase, specifically Cloud Firestore for trip and user data and Firebase Authentication for account identity.

<a href="https://github.com/stacey-marchand-snhu/cs-499-artifact-one-cs-465-full-stack-app" target="_blank"><img src="/assets/images/mark-github-24.svg" alt="GitHub" style="filter: invert(1); height: 24px; margin-right: 6px; vertical-align: middle;"> Original Artifact (Main Branch)</a>

<a href="https://github.com/stacey-marchand-snhu/cs-499-artifact-one-cs-465-full-stack-app/tree/enhancement-three-firebase" target="_blank"><img src="/assets/images/mark-github-24.svg" alt="GitHub" style="filter: invert(1); height: 24px; margin-right: 6px; vertical-align: middle;"> Enhancement Three (Firebase + Firestore)</a>

## Justification & Improvement

This artifact was selected because it provided a strong opportunity to demonstrate database architecture in a realistic full-stack context. The Travlr application already included a public travel site, an administrative portal, a REST API, and persistent trip data, so the database layer was central to the application's purpose. Improving this artifact enabled demonstrating more than just basic CRUD functionality; it offered a chance to rethink how data is stored, how users are authenticated, how administrative permissions are enforced, and how the application can move from a local database model toward a modern cloud-based architecture.

The major improvement was replacing the MongoDB/Mongoose backend with a Firestore-backed API. In the previous React-enhanced version, trip data was modeled through Mongoose schemas and stored in MongoDB. In the enhanced version, trips are stored as documents in a Firestore trips collection, while user profile data is stored separately in a users collection. The backend was also converted from JavaScript to TypeScript, with typed trip and user models, a Firebase Admin SDK configuration file, and controller logic that works directly with Firestore collections. This made the database layer more explicit, more strongly typed, and better aligned with the TypeScript structure already used in the React admin application.

Authentication was also significantly improved. The earlier version used Passport, locally stored password hashes, salts, and custom JWT generation. The enhanced version moves identity management to Firebase Authentication, eliminating the need for the application to hash, store, or validate passwords manually. Registration now creates a Firebase Auth account, sets a custom role claim ("admin" or "user"), and writes a Firestore user profile document. The React admin app signs in through the Firebase client SDK, listens for authentication state changes, and automatically attaches fresh Firebase ID tokens to API requests. This creates a cleaner separation of responsibilities: Firebase manages identity, while the Express API verifies tokens and enforces application-specific access rules.

The enhancement also added robust authorization and validation. Protected API routes now verify Firebase bearer tokens and require an admin role before allowing trip creation, updates, or deletion. Public read routes remain available for viewing trips, while administrative write operations are restricted. The backend now also uses Zod validation schemas for trip and user registration data, meaning the API no longer relies solely on front-end validation or database schema behavior to reject invalid input. This was an important improvement because it made the database-facing layer more defensive and consistent. Finally, as a last line of defense, the Firestore database was programmed with role authorization rules to reinforce admin role requirements for write behavior, should a malicious party modify the codebase to attempt to gain destructive access to the persistence store:

![Firestore Authorization Rules](/assets/images/firestore-auth-code.png)

Several supporting improvements made the artifact more professional and easier to review. The project now includes updated root and admin README files that explain the Firebase-backed architecture, environment variables, authentication flow, API routes, and local setup process. The backend includes a Firestore seed script that clears and repopulates the trips collection from the existing JSON seed data. I also added a documented Postman collection that covers user registration, Firebase login, viewing trips, adding trips, and updating trips. This is a meaningful addition because it gives another developer or reviewer a practical way to test the API without having to walk through the UI first, and to access features unavailable through the interface.

## Course Outcomes

This enhancement met the course outcomes I planned to address in Module One.

**Outcome 1: <span class="gold">Employ strategies for building collaborative environments that enable diverse audiences to support organizational decision-making.</span>** This enhancement supports this outcome by creating an enterprise-accessible, cloud-hosted source of trip data that supports both the public site and the administrative portal. This shared data layer enables teams to collaborate on trip management and provides a reliable source of truth for organizational decision making about travel offerings.

**Outcome 2: <span class="gold">Design, develop, and deliver professional-quality oral, written, and visual communications that are coherent, technically sound, and appropriately adapted to specific audiences and contexts.</span>** This enhancement supports this outcome through updated, comprehensive, and refined documentation, comments, README files, and a Postman collection, all of which explain the revised database and authentication workflow to a technical audience. These communications are tailored to help other engineers understand and work with the Firebase-backed architecture.

**Outcome 3: <span class="gold">Design and evaluate computing solutions that solve a given problem using algorithmic principles and computer science practices and standards appropriate to its solution, while managing the trade-offs involved in design choices.</span>** This enhancement supports this outcome because I had to evaluate trade-offs between MongoDB/Mongoose and Firestore, between local credential handling and managed authentication, and between simple route protection and role-based authorization. Each decision involved concrete trade-offs between complexity, maintainability, security, and cloud service costs.

**Outcome 4: <span class="gold">Demonstrate an ability to use well-founded and innovative techniques, skills, and tools in computing practices for the purpose of implementing computer solutions that deliver value and accomplish industry-specific goals.</span>** This enhancement supports this outcome by using Firebase Authentication, Cloud Firestore, TypeScript, Zod validation, a service-oriented API structure, and state-of-the-art development tooling. These modern tools and practices represent industry-standard approaches to cloud-based application development and authentication.

**Outcome 5: <span class="gold">Develop a security mindset that anticipates adversarial exploits in software architecture and designs to expose potential vulnerabilities, mitigate design flaws, and ensure privacy and enhanced security of data and resources.</span>** This enhancement strongly supports this outcome by removing local password storage, verifying Firebase ID tokens before allowing any administrative operations, enforcing admin-only write operations, improving input validation before data reaches the database through Zod schemas, and implementing Firestore security rules as a final layer of defense. The enhancement eliminated all detected vulnerabilities identified during an NPM security audit.

## Enhancement Process

The process of enhancing this artifact taught me that database migration is really an architecture redesign, not just a change in storage technology. I had to carefully think through what belonged in Firebase Authentication, what belonged in Firestore, and what still belonged in the Express API. One challenge was preserving the existing application behavior while changing the foundation underneath it. The admin portal still needed to manage trips through familiar API calls, and the public site still needed to display trip data, but the way that data was retrieved, validated, and protected changed substantially.

Another challenge was keeping the migration scope and understanding clear. The goal was to improve the database and authentication architecture in a way that made sense for the artifact and demonstrated clear proficiency with a state-of-the-art persistence and authentication framework. By the end of the enhancement, the artifact had moved from a local MongoDB and custom user validation approach to a cloud-backed Firestore and Firebase Authentication model with strong typing, clear documentation, role-aware access control, and better API testing support. This makes the enhanced version a much stronger ePortfolio artifact because it shows that I can modernize an existing application's data architecture while preserving its purpose and improving its reliability, maintainability, and security.

[← Back to Portfolio](/)


