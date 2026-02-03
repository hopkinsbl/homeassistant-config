# Calendar Integration Setup Guide

This guide explains how to set up calendar integration for the "Our Life Together" dashboard.

## Current Configuration

The system is configured with a **Local Calendar** that stores events directly in Home Assistant. This calendar is accessible at:
- Entity ID: `calendar.our_shared_calendar`
- Name: "Our Shared Calendar"

## Using the Local Calendar

The local calendar is ready to use immediately:

1. Navigate to **Calendar** in the Home Assistant sidebar
2. Click on "Our Shared Calendar"
3. Add events by clicking on dates
4. Events will automatically appear on the dashboard

## Alternative: Google Calendar Integration

For syncing with Google Calendar:

1. Go to **Settings** > **Devices & Services**
2. Click **Add Integration**
3. Search for "Google Calendar"
4. Follow the authentication flow
5. Select which calendars to sync
6. Update the dashboard configuration to use `calendar.google_calendar_name`

## Alternative: CalDAV Integration

For CalDAV (iCloud, Nextcloud, etc.):

1. Install the CalDAV integration via HACS or manually
2. Add credentials to `secrets.yaml`:
   ```yaml
   caldav_url: "https://caldav.example.com/calendars/username/calendar-name/"
   caldav_username: "your_username"
   caldav_password: "your_password"
   ```
3. Add to `configuration.yaml`:
   ```yaml
   calendar:
     - platform: caldav
       url: !secret caldav_url
       username: !secret caldav_username
       password: !secret caldav_password
       calendars:
         - "Calendar Name"
   ```
4. Restart Home Assistant
5. Update the dashboard configuration to use the CalDAV calendar entity

## Testing Calendar Sync

After configuration:

1. Add a test event to your calendar
2. Wait up to 15 minutes for sync (or restart Home Assistant)
3. Check **Developer Tools** > **States** for `calendar.our_shared_calendar`
4. Verify the event appears in the calendar view

## Troubleshooting

- **Events not appearing**: Check Home Assistant logs for calendar sync errors
- **Authentication failed**: Verify credentials in `secrets.yaml`
- **Calendar not found**: Ensure the calendar entity exists in Developer Tools > States
- **Sync delays**: Calendar data refreshes every 15 minutes by default
