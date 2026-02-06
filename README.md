# Attendance Manager - Bank Teller System

A comprehensive PWA for managing bank teller attendance at Gelanigama Interchange with shift tracking, overtime calculation, and leave management.

## Features

- **User Authentication**: Secure signup/login with user profiles
- **Attendance Tracking**: Track daily attendance with arrival/departure times
- **Shift Management**: Support for Day, Night, and Off shifts
- **Smart Calculations**:
  - Automatic time rounding (arrival up, departure down to nearest 15 min)
  - Overtime calculation (hours > 8)
  - Late arrival detection
  - Short leave and half-day tracking
  - Monthly aggregation (4 Lates = 1 Short Leave, 2 Short Leaves = 1 Half Day)
- **Roster Integration**: Fetches shift and booth assignments from roster
- **Monthly Summary**: View aggregated statistics for work hours, OT, and leaves
- **Print Functionality**: Print monthly attendance reports
- **Dark Mode**: Toggle between light and dark themes
- **PWA Support**: Installable app with offline capability
- **Mobile-Friendly**: Responsive design optimized for mobile devices

## Setup Instructions

### 1. Database Setup

The Supabase database is already configured with the following tables:
- `profiles`: User profile information
- `roster`: Daily shift assignments
- `attendance`: Attendance records

### 2. Environment Variables

Make sure you have the following environment variables in your `.env` file:
```
VITE_SUPABASE_URL=your_supabase_url
VITE_SUPABASE_ANON_KEY=your_supabase_anon_key
```

### 3. Populating Roster Data

To populate the roster for your teams, you can use SQL queries in the Supabase SQL editor:

```sql
-- Example: Add roster entries for a date range
INSERT INTO roster (date, teller_id, team, shift, booth) VALUES
  ('2026-02-01', 'T001', 'Team1', 'Day', 'Booth A'),
  ('2026-02-01', 'T002', 'Team2', 'Night', 'Booth B'),
  ('2026-02-01', 'T003', 'Team3', 'Off', NULL),
  ('2026-02-02', 'T001', 'Team1', 'Day', 'Booth A'),
  ('2026-02-02', 'T002', 'Team2', 'Night', 'Booth B'),
  ('2026-02-02', 'T003', 'Team3', 'Off', NULL);
```

### 4. User Registration

1. Open the app
2. Click "Don't have an account? Sign up"
3. Fill in your profile information:
   - Email and password
   - Full name with initials
   - Nickname (optional)
   - Teller ID (must match the roster)
   - Team (Team1, Team2, or Team3)
   - Mobile number, PF number, and basic salary (optional)
4. Click "Create Account"

### 5. Using the App

After logging in:
- View your monthly attendance automatically loaded from the roster
- Edit arrival/departure times by clicking the edit icon
- Navigate between months using the arrow buttons
- View monthly summary with aggregated statistics
- Print reports using the Print button
- Toggle dark mode using the moon/sun icon

## Default Shift Times

- **Day Shift**: 06:30 - 19:30
- **Night Shift**: 18:30 - 07:30

## Late Window

- **Day Shift**: 06:30 - 06:45
- **Night Shift**: 18:30 - 18:45

## Leave Rules

- **Short Leave**: 1.5 hours early/late arrival or departure
- **Half Day**: Arrival at 12:30 or departure at 1:00
- **Aggregation**:
  - 4 Lates = 1 Short Leave
  - 2 Short Leaves = 1 Half Day

## PWA Installation

### On Mobile (Android/iOS):
1. Open the app in your browser
2. Look for the "Add to Home Screen" prompt
3. Follow the installation steps

### On Desktop:
1. Open the app in Chrome/Edge
2. Look for the install icon in the address bar
3. Click "Install"

## Technology Stack

- React + TypeScript
- Tailwind CSS
- Supabase (Database & Auth)
- Vite
- PWA with Service Worker
- Lucide React (Icons)

## Development

```bash
# Install dependencies
npm install

# Run development server
npm run dev

# Build for production
npm run build

# Preview production build
npm run preview
```

## License

All rights reserved.
