hunarsetu – Location-Based Skilled Worker Service Platform

Hunarsetu is a full-stack web application that connects clients with nearby skilled workers, such as electricians, plumbers, carpenters, painters, masons, and general laborers. The platform helps clients find workers based on their location, compare service rates, check availability, and send job requests online.

Workers can create professional profiles, manage their availability, receive job requests, and accept or decline work through their dashboard.

## 🚀 Key Features

### 1. User Authentication
- Separate registration for Clients and Workers.
- Secure email and password authentication.
- Role-based dashboards and access control.
- Protected routes for authenticated users.

### 2. Worker Registration and Profiles
- Full name and profile picture.
- Trade category selection.
- Phone number and address.
- City, postal code, and location coordinates.
- Hourly or daily service rates.
- Availability status: Available for Work or Busy.
- Profile management and updates.

### 3. Client Dashboard
- Search workers by service category.
- Find workers using city or postal code.
- View worker profiles, service rates, and availability.
- Display nearby workers based on location.
- Send job requests with a job description and contact details.

### 4. Job Request Management
- Store job requests in the database.
- Link every request to the relevant worker and client.
- Allow workers to accept or decline requests.
- Reveal client contact details to the worker after acceptance.
- Notify clients when their requests are accepted.
- Track request statuses such as Pending, Accepted, and Declined.

### 5. Real-Time Notifications
- In-app notifications for new job requests.
- Notification history for workers.
- Instant updates using Supabase Realtime.
- Acceptance and request-status notifications for clients.

### 6. Responsive User Interface
- Modern and user-friendly dashboard.
- Mobile, tablet, and desktop support.
- Worker cards with rates and availability indicators.
- Easy navigation and search functionality.

## 🧰 Technology Stack

| Component | Technology |
|---|---|
| Frontend | React.js / Next.js |
| Styling | Tailwind CSS |
| Backend | Next.js server-side functions / API routes |
| Database | Supabase PostgreSQL |
| Authentication | Supabase Auth |
| Real-Time Updates | Supabase Realtime |
| Image Storage | Supabase Storage |
| Location Search | City, postal code, and GPS coordinates |
| Version Control | Git and GitHub |

## 🏗️ System Architecture

The application follows a full-stack architecture:

1. **Frontend:** Provides registration, login, dashboards, worker search, and job request forms.
2. **Backend:** Validates user actions, handles requests, and enforces role-based access.
3. **Database:** Stores users, worker profiles, job requests, and notifications.
4. **Authentication:** Manages user sessions and account security.
5. **Real-Time Service:** Delivers notifications and request-status updates.
6. **Storage:** Stores worker profile pictures.

## 🗄️ Database Design

The application can use the following PostgreSQL tables:

### `profiles`
Stores common user information.

- `id` – User ID linked to authentication.
- `full_name` – User's full name.
- `role` – Client or Worker.
- `phone` – Contact number.
- `created_at` – Account creation timestamp.

### `worker_profiles`
Stores worker-specific information.

- `id` – Unique profile ID.
- `user_id` – Linked user ID.
- `trade_category` – Type of skilled work.
- `profile_picture` – Profile image URL.
- `city` – Work location.
- `pincode` – Postal code.
- `latitude` and `longitude` – Optional location coordinates.
- `hourly_rate` – Hourly service rate.
- `daily_rate` – Daily service rate.
- `is_available` – Current availability status.

### `job_requests`
Stores client requests for workers.

- `id` – Unique request ID.
- `client_id` – Client who created the request.
- `worker_id` – Worker receiving the request.
- `job_description` – Details of the required work.
- `contact_phone` – Client contact information.
- `status` – Pending, Accepted, or Declined.
- `created_at` – Request creation timestamp.

### `notifications`
Stores in-app notifications.

- `id` – Unique notification ID.
- `user_id` – Notification recipient.
- `job_request_id` – Related job request.
- `message` – Notification message.
- `is_read` – Read/unread status.
- `created_at` – Notification timestamp.

**Security note:** Configure PostgreSQL Row Level Security (RLS) policies so users can access only the records they are authorized to see. Client contact details should be revealed to the assigned worker only after the request has been accepted.

## ⚙️ Installation and Setup

### Prerequisites

Install the following tools:

- Node.js and npm
- Git
- A GitHub account
- A Supabase account

### Step 1: Clone the Repository

```bash
git clone https://github.com/YOUR-USERNAME/localpro.git
cd localpro
```

Replace `YOUR-USERNAME` with your GitHub username and `localpro` with your repository name if different.

### Step 2: Install Dependencies

For a Next.js project:

```bash
npm install
```

### Step 3: Configure Supabase

1. Create a project at https://supabase.com.
2. Open your Supabase project settings.
3. Copy your project URL and publishable key.
4. Create a `.env.local` file in the project root.

Add the following configuration:

```env
NEXT_PUBLIC_SUPABASE_URL=your_supabase_project_url
NEXT_PUBLIC_SUPABASE_ANON_KEY=your_supabase_publishable_key
```

Use the key name expected by your installed Supabase SDK. Never expose your Supabase secret or service-role key in frontend code.

### Step 4: Set Up the Database

Create the required tables in the Supabase SQL Editor. Configure foreign keys, validation constraints, indexes, and Row Level Security policies before using the application with real users.

### Step 5: Run the Application

```bash
npm run dev
```

Open http://localhost:3000 in your browser.

> These commands assume the repository is configured as a Next.js application with the corresponding scripts. A React/Vite project may use different commands.

## 🔄 How It Works

1. A user registers as a Client or Worker.
2. A Worker completes their profile and sets their service rates and availability.
3. A Client searches for a suitable worker by category and location.
4. The Client submits a job request with a description and contact details.
5. The system stores the request and notifies the selected Worker.
6. The Worker accepts or declines the request.
7. If accepted, the authorized Worker can access the Client's contact details.
8. The Client receives a notification about the request status.

## 🔐 Security Considerations

- Use Supabase Auth for account authentication.
- Apply Row Level Security to all user-related tables.
- Validate job requests on the server.
- Keep secret API keys out of public repositories.
- Restrict contact information to authorized users.
- Validate uploaded images and limit file sizes.
- Apply appropriate rate limits to sensitive operations.

## 🌟 Future Enhancements

- GPS-based worker discovery and distance calculation.
- Maps integration for location visualization.
- Online payments and invoices.
- Ratings and reviews for completed jobs.
- Worker verification and document uploads.
- Job completion tracking.
- SMS or WhatsApp notifications.
- Advanced search filters and service recommendations.
- Admin dashboard for managing users and reports.

## 🎯 Project Objective

The primary goal of LocalPro is to make finding reliable skilled workers easier, faster, and more convenient. It provides workers with an opportunity to showcase their skills and connect with potential clients while helping households and businesses find suitable local services.

## 🤝 Contributing

Contributions and suggestions are welcome.

1. Fork the repository.
2. Create a feature branch.
3. Commit your changes.
4. Push your branch to GitHub.
5. Open a Pull Request.

## 📄 License

This project can be distributed under the MIT License. Add a `LICENSE` file to the repository if you choose to release it under that license.

---

**Built with React/Next.js, Tailwind CSS, Supabase, and PostgreSQL.**

*Connecting local skills with local needs.*
