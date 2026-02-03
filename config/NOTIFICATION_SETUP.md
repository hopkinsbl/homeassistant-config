# Notification Setup Guide

## Changes Made

### 1. Updated Notification Format
All notification services have been updated to use the correct format:
- Changed from `service:` to `action:`
- Updated entity IDs to match actual mobile app integrations:
  - **Bookish**: `notify.mobile_app_bookish_iphone_17`
  - **Jester**: `notify.mobile_app_bens_iphone`
- Simplified message formatting (removed nested `data:` blocks)
- Added `continue_on_error: true` to all notification calls

### 2. Changed Morning Routine Trigger
Switched from phone unlock detection to step count detection:

**Old Method**: Tracked `sensor.bookish_iphone_17_last_update_trigger` and `sensor.bens_iphone_last_update_trigger`
- Problem: `last_update_trigger` is not available on iOS devices

**New Method**: Tracks step sensors
- **Bookish**: `sensor.bookish_iphone_17_steps`
- **Jester**: `sensor.bens_iphone_steps`

**How It Works**:
- Triggers when step count increases after 5 AM
- Only triggers if steps > 10 (filters out sensor noise)
- Time window: 5:00 AM - 11:00 AM
- Once per day cooldown (checks `last_triggered` attribute)

### 3. Updated Template Sensors
Replaced phone unlock tracking sensors with step tracking sensors in `configuration.yaml`:
- `sensor.bookish_daily_steps` - Tracks Bookish's daily steps
- `sensor.jester_daily_steps` - Tracks Jester's daily steps

### 4. Updated Dashboard
Modified `config/dashboards/daily_rituals.yaml` to display:
- Current step counts instead of phone unlock times
- Daily step tracker sensors

## Scripts Updated

All notification scripts now use the correct format:

1. `weather_notification_bookish` ✓
2. `weather_notification_jester` ✓
3. `calendar_notification_bookish` ✓
4. `calendar_notification_jester` ✓
5. `welcome_notification_bookish` ✓
6. `welcome_notification_jester` ✓
7. `deliver_ai_summary_bookish` ✓
8. `deliver_ai_summary_jester` ✓
9. `deliver_book_recommendation_bookish` ✓
10. `deliver_book_recommendation_jester` ✓

## Automations Updated

1. `morning_routine_bookish` - Now triggers on step count
2. `morning_routine_jester` - Now triggers on step count

## Testing the Changes

### 1. Verify Mobile App Integration
Check that these entities exist in Home Assistant:
- `notify.mobile_app_bookish_iphone_17`
- `notify.mobile_app_bens_iphone`

Go to: Developer Tools > States > Filter by "notify"

### 2. Verify Step Sensors
Check that these sensors are reporting data:
- `sensor.bookish_iphone_17_steps`
- `sensor.bens_iphone_steps`

Go to: Developer Tools > States > Filter by "steps"

### 3. Test Notifications Manually
Developer Tools > Services > Select notification service > Call Service

Example:
```yaml
service: notify.mobile_app_bens_iphone
data:
  title: "Test"
  message: "This is a test notification"
```

### 4. Test Morning Routine
Option A: Wait until morning (5-11 AM) and take 10+ steps
Option B: Manually trigger the automation:
- Developer Tools > Services > `automation.trigger`
- Entity: `automation.morning_routine_jester` or `automation.morning_routine_bookish`

### 5. Monitor Automation Traces
After triggering, check the trace:
- Settings > Automations & Scenes > Select automation > View Traces
- Look for any errors in the execution path

## Troubleshooting

### Notifications Not Arriving
1. Verify mobile app is installed and logged in
2. Check notification permissions on phone
3. Verify entity ID exists in Developer Tools > States
4. Check Home Assistant logs for errors

### Morning Routine Not Triggering
1. Verify step sensor is updating (check Developer Tools > States)
2. Ensure time is between 5 AM - 11 AM
3. Check that step count is > 10
4. Verify automation hasn't already triggered today (check last_triggered)
5. Review automation trace for condition failures

### Step Sensor Shows "Unknown"
1. Ensure Home Assistant Companion app has permission to access Health data
2. On iPhone: Settings > Privacy & Security > Health > Home Assistant > Enable "Steps"
3. Restart Home Assistant Companion app
4. Wait a few minutes for data to sync

## Next Steps

After verifying everything works:
1. Restart Home Assistant to load all changes
2. Test each notification script manually
3. Monitor morning routine automations for a few days
4. Adjust step threshold (currently 10) if needed
5. Adjust time window if needed (currently 5-11 AM)
