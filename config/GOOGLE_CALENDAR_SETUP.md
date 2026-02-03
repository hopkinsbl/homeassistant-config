# Google Calendar Setup Guide

This guide will help you set up Google Calendar integration in Home Assistant.

## Steps to Configure Google Calendar

1. **Remove Old Integration (if needed)**
   - Go to Settings > Devices & Services
   - Find "Google Calendar" in the list
   - Click the three dots menu and select "Delete"
   - Confirm deletion

2. **Add Google Calendar Integration**
   - Go to Settings > Devices & Services
   - Click "+ ADD INTEGRATION" button
   - Search for "Google Calendar"
   - Click on "Google Calendar"

3. **Authenticate with Google**
   - You'll be redirected to Google's authentication page
   - Sign in with your Google account
   - Grant Home Assistant permission to access your calendars
   - You may need to authorize specific calendar access

4. **Select Calendars**
   - After authentication, you'll see a list of your Google Calendars
   - Select the calendars you want to use in Home Assistant
   - For this setup, you'll want at least:
     - Your main shared calendar (for "Our Shared Calendar")
     - A meal planning calendar (create one in Google Calendar if needed)

5. **Find Calendar Entity Names**
   - After setup, go to Developer Tools > States
   - Search for "calendar." to see all your calendar entities
   - Note the entity IDs (e.g., `calendar.our_shared_calendar`, `calendar.meal_plan`)

6. **Update Dashboard Configuration**
   - Open `config/dashboards/our_life_together.yaml`
   - Find the commented-out calendar sections (marked with TODO)
   - Uncomment the sections and replace the entity names with your actual calendar entity IDs
   - Example: Replace `calendar.your_google_calendar_name` with `calendar.our_shared_calendar`

## Calendar Entity Examples

After setup, your calendar entities might look like:
- `calendar.our_shared_calendar` - Main shared calendar
- `calendar.meal_plan` - Meal planning calendar
- `calendar.family_events` - Family events calendar

## Troubleshooting

### Authentication Issues
- Make sure you're using the correct Google account
- Check that Home Assistant has internet access
- Try using an incognito/private browser window

### Calendar Not Showing
- Verify the calendar is selected in the integration settings
- Check that the calendar entity exists in Developer Tools > States
- Restart Home Assistant after making changes

### Permission Errors
- Go to your Google Account security settings
- Check "Third-party apps with account access"
- Make sure Home Assistant is listed and has calendar permissions

## Next Steps

Once Google Calendar is configured:
1. Uncomment the calendar sections in `our_life_together.yaml`
2. Update the entity names to match your actual calendar entities
3. Restart Home Assistant to apply changes
4. Test the calendar display in your dashboard
