# Product Walkthrough

This document summarizes the major Care-Flow workflows represented in the application walkthrough. The public showcase intentionally excludes screenshots containing identifiable demonstration data.

## 1. Login & Verification

Managers and workers share the same entry point. A user enters a registered phone number, receives a six-digit OTP, verifies it, and is automatically routed to the correct portal based on role.

## 2. Manager Dashboard

The manager landing page centralizes operational communication:

- On-call manager information
- Pinned high-priority announcements
- Full announcement feed
- Announcement search
- Rich-text announcement composer

Managers can publish new messages immediately and pin important communication.

## 3. Employee Management

The employee directory groups active employees by role and provides access to detailed profiles.

Managers can review and edit workforce information including contact information, role, casual status, certifications, shift preferences, maximum hours, and emergency-contact information.

Vacation ranges can also be added and maintained for individual employees.

## 4. Onboarding

Managers invite new workers using an onboarding form. Invitations can be delivered by SMS, and the onboarding tracker shows progress.

After phone verification and completion, the worker becomes part of the employee directory.

## 5. Scheduling

Managers can work with scheduling periods and availability requests.

A new period defines:

1. Start date
2. End date
3. Availability-response deadline
4. Required dates
5. Shift type
6. Required role

Configured availability requests are then sent to eligible workers.

## 6. Shift Creation

Care-Flow supports standard day, evening, and night shift patterns. Managers can select multiple dates and apply shift requirements in bulk before sending the availability request.

## 7. Schedule Detail & Direct Assignment

The detailed schedule presents the period as a shift grid.

Open shifts can be selected to display workers who are available or unavailable. A manager can directly assign a worker and see the grid update immediately.

The view also surfaces overtime/hour-limit warnings and distinguishes agency shifts.

## 8. Notifications & Coverage

Sick-day notifications identify the affected worker and shift. Unacknowledged notifications remain highlighted.

Managers can view workers who volunteered to cover the shift, connecting absence notification directly to replacement staffing.

## 9. Manager Profile

Managers can view and edit their own profile information, including contact information, address, emergency contact, and notes.

## 10. Worker Home

The worker home page combines scheduling and communication.

A monthly calendar highlights assigned shifts. Workers can open a scheduled day for shift details, while management announcements remain visible on the page.

## 11. Sick-Day Workflow

For eligible future shifts, a worker can submit a sick-day request and optionally provide a reason.

After submission:

```text
Worker Shift
    |
Submit Sick Day
    |
Shift marked as requested
    |
Manager notified
    |
Coverage / volunteers reviewed
```

## 12. Worker Availability

The availability area separates current requests from historical submissions.

Workers open a current request to begin the response workflow.

## 13. Batch Availability Response

All requested shifts in the scheduling period are presented by date. The worker answers **Yes** or **No** for each shift.

The final submission becomes available only after the required responses are completed. Submitted availability is then available to management during scheduling.

## 14. Worker Profile

Workers can maintain personal and employment-related information such as contact details, address, shift preferences, certifications, maximum hours, and emergency-contact information.

## End-to-End Scheduling Flow

```text
Manager
  |
  +-- Create Period
  |      |
  |      +-- Select Dates
  |      +-- Define Shifts
  |      +-- Select Roles
  |
  +-- Send Availability Request
            |
            v
          Worker
            |
            +-- Review Requested Shifts
            +-- Answer Yes / No
            +-- Submit Availability
            |
            v
          Manager
            |
            +-- Review Availability
            +-- Assign Workers
            +-- Direct Assign if needed
            |
            v
        Worker Calendar
```

## Portfolio Note

The full application walkthrough contains demonstration employee records and contact information. Those materials are retained privately rather than copied verbatim into this public repository.
