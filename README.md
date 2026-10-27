# Care-Flow

A workforce scheduling and communication platform designed for nursing managers and healthcare staff.

> **Portfolio Showcase** — The production source repository is private. This public repository documents the project's architecture, product design, engineering decisions, and technologies without exposing application secrets or private data.

## Overview

Care-Flow was created to simplify scheduling and day-to-day workforce communication for healthcare teams. Managers can organize employees and schedules, while staff can manage availability and communicate scheduling needs through a centralized web application.

## Key Features

- Employee onboarding and workforce management
- Role-based access for managers and healthcare staff
- Employee profiles with contact and employment information
- Staff availability submission
- Schedule creation and management
- Sick-leave communication workflows
- Authentication and protected application data
- Responsive web-based interface

## Roles

**Manager** — manages employees, schedules, onboarding, and workforce information.

**LPN / HCL** — accesses staff-facing functionality such as availability, scheduling information, and profile management.

## Technology

| Area | Technology |
| --- | --- |
| Application | Modern web application |
| Database & Auth | Supabase / PostgreSQL |
| Hosting | Vercel |
| DNS / Edge | Cloudflare |
| Source Control | GitHub |
| CI/CD | GitHub Actions |
| Runtime | Node.js |

## Architecture

```text
                    Internet
                       |
                  Cloudflare
                       |
                     Vercel
                       |
                 Web Application
                    /       \
                   /         \
          Authentication    Application API
                 |                |
                 +------ Supabase-+
                         |
                    PostgreSQL
```

The project separates application delivery from managed authentication and data services. Deployment workflows are maintained through GitHub and CI/CD automation.

## Engineering Highlights

### Database design
Care-Flow uses a relational data model for employees, roles, scheduling information, and application relationships. Database changes are managed through migrations rather than manual production changes.

### Authentication & authorization
The application separates manager and employee capabilities using application roles. Authorization is designed so users only access functionality appropriate to their role.

### CI/CD
Source changes are version-controlled in GitHub and deployed through an automated workflow, with environment-specific configuration stored outside the repository.

### Security
Secrets and environment-specific credentials are not committed to source control. Personally identifiable employee information and production configuration are intentionally excluded from this showcase.

## What This Project Demonstrates

- Full-stack SaaS architecture
- PostgreSQL relational data modelling
- Authentication and role-based access
- Database migration workflows
- CI/CD and deployment automation
- Cloud-hosted application operations
- DNS and edge configuration
- Designing software around real operational workflows

## Project Status

Care-Flow is an independently developed project. This repository serves as a technical portfolio overview; the production source remains private.

## Screenshots

Product screenshots and additional architecture visuals can be added here as the application evolves.

---

Built as a practical exploration of SaaS engineering, cloud deployment, and workflow automation.
