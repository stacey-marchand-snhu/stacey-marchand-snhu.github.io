---
layout: default
---

<link rel="stylesheet" href="/assets/css/custom.css">

# Enhancement One
# Software Design & Engineering

This narrative explains my first enhancement to the CS-465 Full Stack Web Application: A complete rewrite using React and Tailwind CSS for a vastly improved user experience.

## Overview

This was originally created as part of SNHU's CS-465 Full Stack Development course activities. The application is a travel site with a public-facing Express/Handlebars website, a MongoDB-backed REST API, and an administrative interface for managing trip records. For this enhancement, I focused on the administration site. The original admin interface was built in Angular, while the enhanced version rewrites it as a React and TypeScript single-page application using Vite, React Router, Tailwind CSS, reusable components, and a vastly more modern structure and appearance.

## Justification & Improvement

This artifact was selected because it presents a strong opportunity to show growth beyond simply making an application work better. The original version already demonstrated full-stack development concepts, including routing, API calls, authentication, trip management, and MongoDB integration. However, the enhanced version better represents my current software engineering skills because it focuses on maintainability, user experience, component organization, and holistic security. This made it a good fit for the ePortfolio because it shows that I can revisit an existing project, evaluate its weaknesses, and improve it in a professional, purposeful, and polished manner.

The biggest improvement was the rewrite of the admin application from Angular components and services into a React/TypeScript structure. The enhanced version separates the interface into clearer pages, reusable components, shared models, API modules, utilities, and an authentication context. The application's code is now clean, thoroughly and succinctly commented, and more secure. Validation and sanitization have been added to all fields that users can interact with, protecting the data layer against corruption and undesirable interactions. From a maintainability standpoint, ESLint and Prettier have been added to reinforce consistent coding standards across the entire application.

The enhanced artifact also improves the administrative workflow by providing a more intuitive, responsive, and informative interface. The dashboard now includes clearer loading, empty, and error states, leveraging toast notifications to convey operation states after adding, saving, deleting, or logging in. Confirmation dialogs have also been implemented for destructive actions, such as deleting trips or navigating away after making changes to the trip form. Dynamic guidance has been added to the trip form to help users understand expected input values. Finally, the visual appearance uses a darker theme to reduce eye strain, with high-contrast controls that are easy to locate and possess color cues to naturally indicate their function.

Security and reliability were also significantly improved, though the greatest impact here will be in the next enhancement to this artifact when it is migrated to leverage Google Firebase. The application still uses the existing Express API and MongoDB backend. The changes in this milestone focused on the React/TypeScript rewrite and supporting improvements to the existing backend. The enhanced admin app stores the JWT in a cookie, uses an Axios instance to attach the bearer token to protected requests, redirects users on unauthorized responses, and guards administrative routes through a new protected route component. The backend was also adjusted to support the new React development server, improve CORS handling, add login rate limiting, correct the JWT middleware flow so protected routes only continue after verification succeeds, improve error handling in the trip and authentication controllers, and enforce unique trip codes. Lastly, 55 vulnerabilities (as of this writing) were addressed after thorough package upgrades and migrations; the enhanced version passes NPM audits with none remaining. Overall, this enhancement was a rigorous exercise in assessing and hardening the security and robustness of an existing application.

## Course Outcomes

This enhancement comprehensively meets the course outcomes I planned to address in Module One. It supports Outcome 1 by improving the administrative interface for users while also making the codebase easier for future developers to navigate and maintain. It supports Outcome 2 through clearer documentation via file headers, comments, and README updates that explain the new project structure and authentication flow. It supports Outcome 3 because the rewrite required evaluating design trade-offs, especially Angular versus React, local storage versus route-based navigation, local component logic versus shared, reusable components, and simpler implementation versus stronger validation and maintainability. It supports Outcome 4 by leveraging current professional tools and practices, including React, TypeScript, Vite, React Router, Axios, Tailwind CSS, ESLint, and Prettier. It also supports Outcome 5 through improvements to protected routes, authentication handling, token flow, validation, rate limiting, CORS behavior, and safer rendering of trip descriptions.

## Enhancement Process

The enhancement process taught me that rewriting an application is not just a translational swap. Moving from Angular to React required me to rethink how the application should be structured, how shared behavior should be separated, and how security should be integrated. This involved careful thought about state management, route protection, reusable form design, API abstraction, token handling, and user feedback. One challenge was keeping the rewrite appropriately scoped; it would have been easy to start adding the later Firebase work here, but that would have blurred the purpose of this milestone. Instead, I kept the focus on software design and engineering: improving the architecture, usability, maintainability, and reliability of the existing application. In the real world, this emulates the skill of limiting deliverables to the scope of their requirements.

Overall, this enhanced artifact is a stronger representation of my current abilities than the original CS-465 version. It shows that I can take an existing full-stack project, identify meaningful design weaknesses, modernize the front end, improve administrative workflows, strengthen validation and authentication, and document the results in a way that would help another developer understand the system they are walking into. For my ePortfolio, this artifact demonstrates not just that I can build software, but that I can improve software thoughtfully and explain the reasoning behind those improvements.

---

[← Back to Portfolio](/)

