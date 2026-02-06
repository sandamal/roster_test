# Quick Setup Guide

## Step 1: Database is Ready
Your Supabase database has been set up with all necessary tables:
- ✅ profiles (user information)
- ✅ roster (shift assignments)
- ✅ attendance (attendance records)

## Step 2: Add Roster Data

Before users can track attendance, you need to populate the roster table. You have two options:

### Option A: Use the Automated Script
1. Open Supabase SQL Editor
2. Copy the contents of `scripts/generate-roster.sql`
3. Update the teller IDs and date range
4. Run the script

### Option B: Manual Entry
```sql
INSERT INTO roster (date, teller_id, team, shift, booth) VALUES
  ('2026-02-06', 'T001', 'Team1', 'Day', 'Booth A'),
  ('2026-02-06', 'T002', 'Team2', 'Night', 'Booth B'),
  ('2026-02-06', 'T003', 'Team3', 'Off', NULL);
```

## Step 3: User Registration

Each teller needs to create an account:
1. Open the app
2. Click "Don't have an account? Sign up"
3. Enter details (Teller ID must match roster)
4. Submit

## Step 4: Start Using

Once logged in:
- Attendance records are automatically created from the roster
- Edit times by clicking the edit icon
- View monthly summaries
- Print reports
- Install as PWA for easy access

## Key Features

### Automatic Time Rounding
- Arrival times: rounded UP to nearest 15 minutes
- Departure times: rounded DOWN to nearest 15 minutes

### Default Shift Times
- Day: 06:30 - 19:30
- Night: 18:30 - 07:30

### Overtime Calculation
- Work hours > 8 = OT hours
- Automatically calculated

### Leave Tracking
- Late: Arrival within 15-min window after shift start
- Short Leave: 1.5h early/late
- Half Day: Arrival at 12:30 or departure at 1:00
- Auto-aggregation: 4 Lates = 1 SL, 2 SL = 1 HD

## Mobile Installation

### Android
1. Open in Chrome
2. Tap menu (⋮)
3. Select "Add to Home screen"

### iOS
1. Open in Safari
2. Tap Share button
3. Select "Add to Home Screen"

## Troubleshooting

### Attendance not showing?
- Check if roster data exists for the teller_id
- Verify the date range matches

### Can't edit times?
- Make sure you're logged in
- Check that the attendance record exists

### Dark mode not saving?
- Clear browser cache
- Try toggling again

## Support

For issues or questions:
1. Check the README.md for detailed documentation
2. Verify database setup in Supabase
3. Check browser console for errors

## Next Steps

1. ✅ Populate roster for all tellers
2. ✅ Have each teller create an account
3. ✅ Verify attendance tracking works
4. ✅ Install as PWA on mobile devices
5. ✅ Start tracking daily attendance
