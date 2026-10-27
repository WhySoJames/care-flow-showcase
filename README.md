# Care-Flow

**Healthcare workforce scheduling, availability, onboarding, and shift-coverage platform.**

Care-Flow is a web application designed around the day-to-day workflow between nursing managers and healthcare workers. It provides separate Manager and Worker portals for scheduling, availability collection, employee onboarding, announcements, notifications, sick-day requests, and profile management.

> **Portfolio Showcase** — The production source repository is private. This public repository documents the product, workflows, architecture, and engineering work without exposing application secrets, production data, or private source code.

## Product at a Glance

| Manager Portal | Worker Portal |
| --- | --- |
| Dashboard & announcements | Shift calendar |
| Employee directory & profile editing | Assigned shifts |
| Vacation management | Management announcements |
| SMS employee onboarding | Sick-day requests |
| Scheduling periods | Availability requests |
| Shift creation & direct assignment | Batch availability responses |
| Overtime & agency-shift visibility | Personal profile management |
| Sick-day notifications & volunteer coverage | Shift preferences & certifications |

## Authentication & Role Routing

Care-Flow uses a shared phone-based authentication flow for managers and workers.

1. The user enters their registered phone number.
2. A six-digit OTP verification code is sent to the phone.
3. The user verifies the code.
4. Care-Flow automatically routes the authenticated user to the appropriate Manager or Worker portal.

This provides a simple login experience while keeping role-specific workflows separated.

## Manager Portal

### Dashboard & Announcements

The Manager Dashboard acts as the operational hub. Managers can view the announcement feed, keep high-priority messages pinned, identify the current on-call manager, search announcements, and publish rich-text announcements.

### Employee Management

Managers can browse active employees by role and open detailed employee profiles. Profile information includes contact details, role, casual status, certifications, shift preferences, maximum hours, emergency contact information, and other workforce data.

Employee records can be switched into edit mode and updated directly from the portal.

Managers can also maintain employee vacation date ranges.

### Employee Onboarding

New workers can be invited directly from Care-Flow.

The onboarding workflow captures information such as:

- Phone number
- First and last name
- Role
- Casual status
- Seniority / hire date
- Maximum hours per scheduling period

Care-Flow can send an SMS invitation containing the secure onboarding/login path. Managers can track onboarding status and workers join the employee directory after completing verification.

### Scheduling & Availability Collection

Managers create scheduling periods by defining a start date, end date, and worker response deadline.

They can then select calendar dates and create required shifts by role. Supported shift patterns include day, evening, and night shifts.

Once configured, an availability request is sent to eligible workers.

### Schedule Detail & Direct Assignment

The schedule-detail view presents a full-period shift grid with assigned employees.

Managers can:

- See open and assigned shift slots
- Directly assign employees to open shifts
- See available and unavailable workers during assignment
- Identify workers approaching overtime/hour limits
- Distinguish agency shifts
- Update the schedule immediately after assignment

### Notifications & Shift Coverage

When a worker submits a sick-day request, managers receive a notification tied to the affected shift.

Unacknowledged requests are highlighted, and managers can view workers who have volunteered to cover the open shift. This connects absence reporting with the coverage workflow instead of treating them as separate processes.

## Worker Portal

### Home

The Worker Home screen provides a monthly calendar showing assigned shifts. Selecting a scheduled day opens the shift details.

Management announcements remain visible beneath the calendar so operational communication and scheduling are available from the same screen.

### Sick-Day Requests

For eligible future shifts, workers can open the shift and submit a sick-day request with an optional reason.

The shift is marked as requested and management is notified.

### Availability

Workers can see:

- **Current requests** — scheduling periods awaiting a response
- **Past requests** — previously completed availability submissions

Opening a request starts a batch-response workflow. Every requested shift is grouped by date and the worker answers **Yes** or **No** for each one. Once every shift has a response, the batch can be submitted to management for scheduling.

### Worker Profile

Workers can view and maintain their personal information, including contact details, address, shift preferences, certifications, maximum hours, and emergency contact information.

## Core Workflow

```text
                         CARE-FLOW

                +-----------------------+
                | Phone + OTP Login     |
                +-----------+-----------+
                            |
                    Role-based routing
                     /             \
                    /               \
           MANAGER PORTAL       WORKER PORTAL
                 |                    |
       Create scheduling period       |
                 |                    |
         Define required shifts       |
                 |                    |
         Send availability request -->|
                                      |
                              Yes / No responses
                                      |
       Availability returned <---------+
                 |
          Build schedule
                 |
       Assign / Direct Assign
                 |
          Published shifts ----------> Worker Calendar
                 |
                 |<---------- Sick-day request
                 |
        Coverage notification
                 |
         View volunteers
                 |
          Fill open shift
```

## Technology

| Area | Technology |
| --- | --- |
| Database & Auth | Supabase / PostgreSQL |
| Hosting | Vercel |
| DNS / Edge | Cloudflare |
| Source Control | GitHub |
| CI/CD | GitHub Actions |
| Runtime | Node.js |

## Application Architecture

```text
                     Internet
                        |
                   Cloudflare
                        |
                      Vercel
                        |
                  Web Application
                  /             \
          Manager Portal     Worker Portal
                  \             /
                   Application Layer
                     /        \
                    /          \
             Authentication   Data Access
                    \          /
                     Supabase
                        |
                   PostgreSQL
```

## Engineering Highlights

**Role-aware application design** — A shared authentication entry point routes users into distinct manager and worker experiences.

**Relational workforce data** — Employees, roles, availability, scheduling periods, shifts, vacation ranges, notifications, and related records are represented as structured application data.

**Workflow-oriented scheduling** — Scheduling is modelled as a process: define a period, request availability, collect responses, assign workers, and manage exceptions.

**Operational exception handling** — Sick days, volunteer coverage, overtime warnings, open shifts, and agency shifts are surfaced directly in scheduling workflows.

**Database migrations** — Database changes are managed through migrations rather than relying on manual production changes.

**CI/CD** — Application changes are version-controlled in GitHub and deployed through automated workflows.

**Security-conscious portfolio design** — Production credentials, environment secrets, private employee information, and the private application source are intentionally excluded from this repository.

## What This Project Demonstrates

- Full-stack SaaS product development
- Healthcare workforce workflow modelling
- PostgreSQL relational data design
- OTP authentication and role-based application flows
- Scheduling and availability systems
- Employee onboarding workflows
- Notification and shift-coverage workflows
- CI/CD and cloud deployment
- Managed backend services
- DNS / edge configuration
- Product and UI design around real operational processes

## Repository Structure

```text
care-flow-showcase/
├── README.md
└── docs/
    ├── ARCHITECTURE.md
    └── PRODUCT-WALKTHROUGH.md
```

## Privacy

The screenshots used during development contain demonstration/test data. This public showcase intentionally avoids publishing identifiable phone numbers, addresses, emergency contacts, credentials, or production records.

## Project Status

Care-Flow is an independently developed project. Development continues in a private repository; this repository is maintained as a technical and product portfolio case study.

---

**Private source · Public engineering showcase**
