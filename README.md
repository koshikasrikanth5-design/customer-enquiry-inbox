# Customer Enquiry Inbox

A cloud-based Customer Enquiry Inbox system built for the National College of Ireland - Doing Business on the Cloud (H9BOC) module.

## Project Overview

This project implements a mini SaaS customer enquiry management system with four modular single-file HTML pages that connect to a shared Firebase Firestore database. The system is designed for deployment on GitHub Pages and demonstrates real-time cloud-based business operations.

## System Architecture

The application follows a modular architecture where each HTML file operates independently while sharing the same Firebase backend:

- **index.html** - Landing page with navigation to all modules
- **public.html** - Public-facing enquiry submission form
- **staff.html** - Staff dashboard with authentication for managing enquiries
- **insights.html** - Real-time operational metrics and statistics dashboard

## Technology Stack

| Technology | Purpose |
|------------|---------|
| HTML5 | Page structure |
| CSS3 | Styling |
| JavaScript (ES6+) | Application logic |
| Bootstrap 5 | UI framework (via CDN) |
| Font Awesome 6 | Icons (via CDN) |
| Firebase Web SDK v9+ | Backend services (via CDN) |
| Firebase Firestore | NoSQL database |
| Firebase Authentication | User authentication (Email/Password) |

## Firebase Configuration

**Project ID:** customer-enquiry-inbox-52174

### Firestore Collection: `enquiries`

| Field | Type | Description |
|-------|------|-------------|
| name | string | Customer name |
| email | string | Customer email address |
| message | string | Enquiry message |
| status | string | "New", "In Progress", or "Resolved" |
| createdAt | timestamp | Creation timestamp |
| updatedAt | timestamp | Last update timestamp |
| internalNotes | string | Staff internal notes |

## Features

### 1. Public Form (public.html)
- Form validation for name, email, and message fields
- Submits enquiry to Firestore with status "New"
- Success/error message display
- No authentication required

### 2. Staff Dashboard (staff.html)
- Firebase Email/Password authentication
- Login and registration modals
- Real-time enquiry listing with onSnapshot listener
- Status update (New, In Progress, Resolved)
- Internal notes editing
- Status filter functionality

### 3. Insights Dashboard (insights.html)
- Real-time statistics with onSnapshot listener
- Total enquiries count
- Count by status (New, In Progress, Resolved)
- Last 24 hours activity tracking
- Resolution rate percentage
- Status distribution progress bar

## Staff Login Credentials

| Field | Value |
|-------|-------|
| Email | staff@enquiry.com |
| Password | staff123 |

## GitHub Pages Deployment

1. Create a new GitHub repository
2. Upload all HTML files (index.html, public.html, staff.html, insights.html)
3. Go to repository Settings > Pages
4. Set Source to "Deploy from a branch" and select "main" branch
5. Your site will be available at: `https://koshikasrikanth5-design.github.io/customer-enquiry-inbox/`

## Firebase Security Rules

Configure these rules in Firebase Console:

```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /enquiries/{enquiryId} {
      allow create, read, update, delete: if true;
    }
  }
}
```

**Note:** For production environments, implement proper authentication-based security rules.

## Real-Time Integration

The system demonstrates real-time integration where:
- Records created in the Public module appear in the Staff module without page refresh
- Staff updates are reflected in the Insights module instantly
- All modules use Firestore `onSnapshot` listeners for live updates

## Project Structure

```
customer-enquiry-inbox/
|-- index.html          # Landing page
|-- public.html         # Public enquiry form
|-- staff.html          # Staff dashboard (protected)
|-- insights.html       # Operational metrics dashboard
|-- README.md           # Project documentation
```

## License

This project was developed for academic purposes as part of the National College of Ireland coursework.

## Author

Developed for the Doing Business on the Cloud (H9BOC) module at National College of Ireland, 2025.
