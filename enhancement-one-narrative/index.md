---
layout: default
---

<link rel="stylesheet" href="/assets/css/custom.css">

# Enhancement One
# Software Design & Engineering

This narrative explains my first enhancement to the CS-465 Full Stack Web Application: A complete rewrite using React and Tailwind CSS for a vastly improved user experience.

## Overview

This was originally created as part of SNHU's CS-465 Full Stack Development course activities. The application is a travel site with a public-facing Express/Handlebars website, a MongoDB-backed REST API, and an administrative interface for managing trip records. For this enhancement, I focused on the administration site. The original admin interface was built in Angular, while the enhanced version rewrites it as a React and TypeScript single-page application using Vite, React Router, Tailwind CSS, reusable components, and a vastly more modern structure and appearance.

**Original Artifact:** https://github.com/stacey-marchand-snhu/cs-499-artifact-one-cs-465-full-stack-app

**Enhancement One Branch:** https://github.com/stacey-marchand-snhu/cs-499-artifact-one-cs-465-full-stack-app/tree/enhancement-one-react-tailwind

## Justification & Improvement

This artifact was selected because it presents a strong opportunity to show growth beyond simply making an application work better. The original version already demonstrated full-stack development concepts, including routing, API calls, authentication, trip management, and MongoDB integration. However, the enhanced version better represents my current software engineering skills because it focuses on maintainability, user experience, component organization, and holistic security. This made it a good fit for the ePortfolio because it shows that I can revisit an existing project, evaluate its weaknesses, and improve it in a professional, purposeful, and polished manner.

The biggest improvement was the rewrite of the admin application from Angular components and services into a React/TypeScript structure. The enhanced version separates the interface into clearer pages, reusable components, shared models, API modules, utilities, and an authentication context. The application's code is now clean, thoroughly and succinctly commented, and more secure. Validation and sanitization have been added to all fields that users can interact with, protecting the data layer against corruption and undesirable interactions. From a maintainability standpoint, ESLint and Prettier have been added to reinforce consistent coding standards across the entire application.

The enhanced artifact also improves the administrative workflow by providing a more intuitive, responsive, and informative interface. The dashboard now includes clearer loading, empty, and error states, leveraging toast notifications to convey operation states after adding, saving, deleting, or logging in. Confirmation dialogs have also been implemented for destructive actions, such as deleting trips or navigating away after making changes to the trip form. Dynamic guidance has been added to the trip form to help users understand expected input values. Finally, the visual appearance uses a darker theme to reduce eye strain, with high-contrast controls that are easy to locate and possess color cues to naturally indicate their function.

Security and reliability were also significantly improved, though the greatest impact here will be in the next enhancement to this artifact when it is migrated to leverage Google Firebase. The application still uses the existing Express API and MongoDB backend. The changes in this milestone focused on the React/TypeScript rewrite and supporting improvements to the existing backend. The enhanced admin app stores the JWT in a cookie, uses an Axios instance to attach the bearer token to protected requests, redirects users on unauthorized responses, and guards administrative routes through a new protected route component. The backend was also adjusted to support the new React development server, improve CORS handling, add login rate limiting, correct the JWT middleware flow so protected routes only continue after verification succeeds, improve error handling in the trip and authentication controllers, and enforce unique trip codes. Lastly, 55 vulnerabilities (as of this writing) were addressed after thorough package upgrades and migrations; the enhanced version passes NPM audits with none remaining. Overall, this enhancement was a rigorous exercise in assessing and hardening the security and robustness of an existing application.

## Course Outcomes

This enhancement comprehensively meets the course outcomes I planned to address in Module One.

**Outcome 1: <span class="gold">Employ strategies for building collaborative environments that enable diverse audiences to support organizational decision making.</span>** This enhancement supports this outcome by improving the administrative interface for users while also making the codebase easier for future developers to navigate and maintain. The improved structure, clear component organization, and comprehensive comments enable other developers to contribute to the project, and the better UI helps administrative users make informed decisions about trip management.

**Outcome 2: <span class="gold">Design, develop, and deliver professional-quality oral, written, and visual communications that are coherent, technically sound, and appropriately adapted to specific audiences and contexts.</span>** This enhancement supports this outcome through clearer documentation via file headers, comments, and README updates that explain the new project structure and authentication flow. The enhanced UI also communicates states and actions more clearly to administrative users through toast notifications, error messages, confirmation dialogs, and intuitive layout.

**Outcome 3: <span class="gold">Design and evaluate computing solutions that solve a given problem using algorithmic principles and computer science practices and standards appropriate to its solution, while managing the trade-offs involved in design choices.</span>** This enhancement supports this outcome because the rewrite required evaluating design trade-offs, especially Angular versus React, local storage versus route-based navigation, local component logic versus shared, reusable components, and simpler implementation versus stronger validation and maintainability. Each decision was deliberate and documented.

**Outcome 4: <span class="gold">Demonstrate an ability to use well-founded and innovative techniques, skills, and tools in computing practices for the purpose of implementing computer solutions that deliver value and accomplish industry-specific goals.</span>** This enhancement supports this outcome by leveraging current professional tools and practices, including React, TypeScript, Vite, React Router, Axios, Tailwind CSS, ESLint, and Prettier. These tools represent state-of-the-art practices in modern web development and are directly applicable to professional software engineering.

**Outcome 5: <span class="gold">Develop a security mindset that anticipates adversarial exploits in software architecture and designs to expose potential vulnerabilities, mitigate design flaws, and ensure privacy and enhanced security of data and resources.</span>** This enhancement supports this outcome through improvements to protected routes, authentication handling, token flow, validation, rate limiting, CORS behavior, and safer rendering of trip descriptions. The security improvements are detailed in the Justification & Improvement section above.

## Enhancement Process

The enhancement process taught me that rewriting an application is not just a translational swap. Moving from Angular to React required me to rethink how the application should be structured, how shared behavior should be separated, and how security should be integrated. This involved careful thought about state management, route protection, reusable form design, API abstraction, token handling, and user feedback. One challenge was keeping the rewrite appropriately scoped; it would have been easy to start adding the later Firebase work here, but that would have blurred the purpose of this milestone. Instead, I kept the focus on software design and engineering: improving the architecture, usability, maintainability, and reliability of the existing application. In the real world, this emulates the skill of limiting deliverables to the scope of their requirements.

Overall, this enhanced artifact is a stronger representation of my current abilities than the original CS-465 version. It shows that I can take an existing full-stack project, identify meaningful design weaknesses, modernize the front end, improve administrative workflows, strengthen validation and authentication, and document the results in a way that would help another developer understand the system they are walking into. For my ePortfolio, this artifact demonstrates not just that I can build software, but that I can improve software thoughtfully and explain the reasoning behind those improvements.

---

[← Back to Portfolio](/)

