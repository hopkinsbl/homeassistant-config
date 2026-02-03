# Our Life Together Dashboard

A centralized dashboard displaying shared life information, relationship milestones, and day-to-day planning tools.

## Features Implemented

### ✅ Calendar Integration (Task 2)

**Calendar View Card**
- Displays events from "Our Shared Calendar"
- Shows 7-day view window (listWeek format)
- Highlights events occurring in the next 24 hours
- Shows event title, date, time, and location
- Auto-refreshes every 15 minutes

**Calendar Entity**: `calendar.our_shared_calendar`

**How to Use**:
1. Navigate to the Calendar section in Home Assistant
2. Click on "Our Shared Calendar"
3. Add events by clicking on dates
4. Events automatically appear on the dashboard

**Event Display**:
- Main calendar card shows all events in a 7-day list view
- Conditional card highlights the next event within 24 hours
- Event details include:
  - Event title
  - Location (if specified)
  - Start and end times

## Dashboard Access

- **Sidebar**: Click "Our Life Together" (heart icon)
- **URL**: `/our-life-together/home`

## Configuration Files

- **Dashboard**: `config/dashboards/our_life_together.yaml`
- **Calendar Config**: `config/configuration.yaml` (calendar section)
- **Setup Guide**: `config/CALENDAR_SETUP.md`

## Requirements Satisfied

### Requirement 1: Shared Calendar View
- ✅ 1.1: Display events from shared calendar for next 7 days
- ✅ 1.2: Highlight events within next 24 hours
- ✅ 1.3: Show event title, date, and time
- ✅ 1.4: Update calendar data every 15 minutes

## Next Steps

The following features are planned for future implementation:
- Immigration timeline tracker (Task 3)
- Countdown system (Task 4)
- Shared lists (Task 5)
- Love notes rotation (Task 6)
- Relationship journey tracker (Task 7)

## Customization

### Changing Calendar Source

To use Google Calendar or CalDAV instead of the local calendar:

1. Follow instructions in `CALENDAR_SETUP.md`
2. Update the calendar entity in `our_life_together.yaml`:
   ```yaml
   entities:
     - calendar.your_calendar_name
   ```

### Styling

The dashboard uses Home Assistant's default theme. To customize:
- Add `card_mod` styling to individual cards
- Create a custom theme in the `themes/` directory
- Apply theme via user profile settings

## Troubleshooting

**Calendar not showing events**:
- Verify calendar entity exists: Developer Tools > States > `calendar.our_shared_calendar`
- Check Home Assistant logs for calendar errors
- Ensure events are added to the correct calendar

**Dashboard not appearing in sidebar**:
- Restart Home Assistant
- Check `configuration.yaml` for syntax errors
- Verify dashboard file exists at `dashboards/our_life_together.yaml`

**24-hour highlight not working**:
- Ensure there's an active event in the next 24 hours
- The conditional card only shows when calendar state is "on"
- Check that event times are correctly formatted
