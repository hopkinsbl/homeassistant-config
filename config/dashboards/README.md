# Home Assistant Dashboards

This directory contains YAML configurations for custom Home Assistant dashboards.

## Available Dashboards

### 1. Daily Rituals Dashboard
Configuration for the Daily Rituals & Moments dashboard.

### 2. Our Life Together Dashboard
A comprehensive dashboard for couples to track their shared life, including immigration milestones, countdowns, shared lists, love notes, and relationship journey.

## Installation

The dashboard is automatically registered in `configuration.yaml` and will appear in your Home Assistant sidebar after restarting.

### Steps to Activate:

1. **Restart Home Assistant** to load the dashboard configuration
   - Go to: Settings > System > Restart
   - Or use CLI: `ha core restart`

2. **Access the Dashboard**
   - Look for "Daily Rituals" in the sidebar (icon: ⭐)
   - Or navigate to: `/daily-rituals/overview`

## Dashboard Features

### 🌅 Morning Routines
- Status of morning routine automations for both users
- Last phone unlock timestamps
- Manual trigger buttons for testing

### 🏠 Welcome Home
- Welcome home automation status
- Current location tracking
- Manual trigger buttons

### 🤖 AI Daily Summaries
- Morning (7 AM) and home arrival summary automations
- Display of latest AI-generated summary
- Weather and calendar context information
- Manual generation button

### 📚 Daily Book Recommendations
- Daily 6 PM book recommendation automation
- Current book recommendation display (title, author, description)
- Genre preference setting
- Manual fetch button

### ⚡ Quick Actions
- One-click buttons to manually trigger any ritual
- Useful for testing and on-demand execution

### 🏥 Automation Health
- At-a-glance status of all ritual automations
- Color-coded indicators (green = enabled, red = disabled)
- Last triggered timestamps

## Customization

To customize the dashboard:

1. Edit `config/dashboards/daily_rituals.yaml`
2. Modify card layouts, add/remove sections, or adjust styling
3. Save changes
4. Refresh your browser (Ctrl+F5 or Cmd+Shift+R)

### Common Customizations:

- **Change card order**: Rearrange the `cards:` list in the YAML
- **Add new cards**: Insert additional card configurations
- **Modify entity IDs**: Update to match your actual entity names
- **Adjust styling**: Add `card_mod` configurations for custom CSS

## Troubleshooting

### Dashboard not appearing in sidebar
- Verify `configuration.yaml` includes the lovelace dashboard configuration
- Restart Home Assistant
- Check logs for YAML syntax errors: `home-assistant.log`

### Entities showing as "unavailable"
- Ensure all automations are created in `automations.yaml`
- Verify template sensors exist in `configuration.yaml`
- Check that person entities and mobile app integrations are configured

### Cards not displaying correctly
- Validate YAML syntax: Settings > Developer Tools > YAML > Check Configuration
- Check browser console for JavaScript errors
- Try clearing browser cache

## Entity Requirements

The dashboard expects these entities to exist:

**Automations:**
- `automation.morning_routine_bookish`
- `automation.morning_routine_jester`
- `automation.welcome_home_bookish`
- `automation.welcome_home_jester`
- `automation.ai_summary_morning`
- `automation.ai_summary_home_arrival`
- `automation.book_recommendation_daily`
- `automation.book_recommendation_try_again_bookish`
- `automation.book_recommendation_try_again_jester`

**Sensors:**
- `sensor.bookish_phone_last_unlock`
- `sensor.jester_phone_last_unlock`

**Person Entities:**
- `person.bookish`
- `person.jester`

**Input Text Helpers:**
- `input_text.ai_summary_response`
- `input_text.ai_weather_context`
- `input_text.ai_calendar_context`
- `input_text.book_recommendation_title`
- `input_text.book_recommendation_author`
- `input_text.book_recommendation_description`
- `input_text.book_genre_preference`

**Scripts:**
- `script.morning_greeting_bookish`
- `script.morning_greeting_jester`
- `script.welcome_home_bookish`
- `script.welcome_home_jester`
- `script.generate_ai_summary`
- `script.fetch_book_recommendation`

If any entities are missing, the dashboard will show them as "unavailable" but will still function for available entities.


---

# Our Life Together Dashboard

## Overview

The "Our Life Together" dashboard is a comprehensive interface designed for couples to manage and celebrate their shared life. It combines practical tools (calendars, lists, trackers) with sentimental elements (love notes, milestone timeline) in a responsive two-column layout.

## Dashboard Layout

The dashboard uses a responsive two-column grid layout:

### Left Column
- **Calendar View** (optional - requires Google Calendar setup)
- **Immigration Timeline Tracker** - Progress bar and milestone tracking
- **Countdown System** - Payday and custom event countdowns
- **Love Notes** - Rotating personalized messages

### Right Column
- **Shared Lists Section**
  - Grocery List (20 items with checkboxes)
  - Meal Planner (optional - requires calendar setup)
  - Reading List (10 books with status tracking)
  - Payment Tracker (10 payments with due dates)
- **Relationship Journey Timeline** - Past and future milestones

### Responsive Design

The dashboard automatically adapts to different screen sizes:
- **Desktop/Tablet**: Two-column layout for efficient use of space
- **Mobile**: Columns stack vertically for easy scrolling

## Installation

The dashboard is automatically registered in `configuration.yaml` and will appear in your Home Assistant sidebar after restarting.

### Steps to Activate:

1. **Restart Home Assistant** to load the dashboard configuration
   - Go to: Settings > System > Restart
   - Or use CLI: `ha core restart`

2. **Access the Dashboard**
   - Look for "Our Life Together" in the sidebar (icon: ❤️)
   - Or navigate to: `/our-life-together/home`

## Features

### 🛂 Immigration Timeline Tracker
- Visual progress bar showing completion percentage
- Track 5 major immigration milestones
- Highlight next upcoming milestone with countdown
- Mark milestones as complete with toggle switches

### ⏰ Countdown System
- Automatic payday countdown (15th of each month)
- 3 customizable important date countdowns
- Celebration message display when countdowns reach zero
- 24-hour celebration display period

### 📝 Shared Lists
- **Grocery List**: 20 items with checkbox completion tracking
- **Reading List**: 10 books with title, author, and status (To Read/Reading/Completed)
- **Payment Tracker**: 10 payments with amounts, due dates, and countdown timers
- **Meal Planner**: Calendar-based meal planning (requires Google Calendar setup)

### 💕 Love Notes
- Rotating display of 10 personalized love notes
- Automatic rotation every 4 hours
- Editable notes through the dashboard
- Beautiful gradient styling

### 💑 Relationship Journey
- Track days since arrival
- Display past milestones organized by category (Relationship, Visa, Housing)
- Show next upcoming milestone with countdown
- Comprehensive timeline of your shared story

## Optional Features

### Google Calendar Integration

Two calendar features are available but commented out by default:

1. **Shared Calendar View** - Shows upcoming events for the next 7 days
2. **Meal Planner** - Calendar-based meal planning

To enable these features:

1. Set up Google Calendar integration:
   - Go to Settings > Devices & Services > Add Integration
   - Search for "Google Calendar" and follow setup instructions

2. Uncomment the calendar sections in `our_life_together.yaml`:
   - Search for `# TODO: Uncomment after setting up Google Calendar integration`
   - Remove the `#` comment markers from the calendar card sections
   - Update entity names to match your calendar entities

3. Restart Home Assistant to apply changes

## Customization

### Editing the Dashboard

1. Edit `config/dashboards/our_life_together.yaml`
2. Modify card layouts, add/remove sections, or adjust styling
3. Save changes
4. Refresh your browser (Ctrl+F5 or Cmd+Shift+R)

### Common Customizations

- **Change payday date**: Edit the `payday` variable in the template sensor (configuration.yaml)
- **Add more list items**: Duplicate existing input helpers and add to dashboard
- **Customize love notes**: Edit through the dashboard or modify initial values in configuration.yaml
- **Adjust colors**: Modify `card_mod` styling sections in the YAML
- **Reorder sections**: Rearrange cards within the left/right column vertical-stacks

### Layout Customization

The dashboard uses a two-column layout with vertical-stacks. To modify:

- **Single column layout**: Remove the horizontal-stack wrapper and keep only one vertical-stack
- **Three columns**: Add a third vertical-stack card to the main cards array
- **Reorder columns**: Move entire vertical-stack sections between left and right columns

## Troubleshooting

### Dashboard not appearing in sidebar
- Verify `configuration.yaml` includes the lovelace dashboard configuration
- Check that the dashboard file path is correct: `dashboards/our_life_together.yaml`
- Restart Home Assistant
- Check logs for YAML syntax errors: `home-assistant.log`

### Entities showing as "unavailable"
- Ensure all input helpers are defined in `configuration.yaml`
- Verify template sensors exist in `configuration.yaml`
- Check that automations are created in `automations.yaml`
- Restart Home Assistant after configuration changes

### Cards not displaying correctly
- Validate YAML syntax: Settings > Developer Tools > YAML > Check Configuration
- Check browser console for JavaScript errors
- Try clearing browser cache
- Verify all entity IDs match those defined in configuration.yaml

### Custom cards not working
The dashboard uses `custom:fold-entity-row` for collapsible sections. If these don't work:
- Install the fold-entity-row custom card from HACS
- Or replace `custom:fold-entity-row` with standard `entities` cards

### Layout issues on mobile
- The two-column layout should automatically stack on mobile
- If not, try refreshing the browser or clearing cache
- Check that you're using a recent version of Home Assistant

## Entity Requirements

The dashboard expects these entities to exist (all defined in configuration.yaml):

**Input DateTime Helpers:**
- Immigration milestones (5 entities)
- Relationship milestones (9 entities)
- Custom countdown dates (3 entities)
- Payment due dates (10 entities)

**Input Boolean Helpers:**
- Immigration milestone completion (5 entities)
- Grocery item checkboxes (20 entities)

**Input Number Helpers:**
- Love note rotation index
- Payment amounts (10 entities)

**Input Text Helpers:**
- Grocery items (20 entities)
- Reading list books and authors (20 entities)
- Payment names (10 entities)
- Love notes (10 entities)
- Custom countdown names (3 entities)

**Input Select Helpers:**
- Reading list status (10 entities)

**Template Sensors:**
- Immigration progress percentage
- Next immigration milestone
- Days until next immigration milestone
- Payday countdown
- Custom countdowns (3 sensors)
- Payment countdowns (10 sensors)
- Current love note display
- Days since arrival
- Next relationship milestone
- Days until next relationship milestone

**Automations:**
- Love note rotation (every 4 hours)
- Countdown celebration trigger

If any entities are missing, the dashboard will show them as "unavailable" but will still function for available entities.

## Data Entry

### Setting Up Your Data

1. **Immigration Milestones**: Click on each milestone date to set it, then toggle completion status
2. **Relationship Milestones**: Set dates for past and future milestones
3. **Love Notes**: Edit the 10 love notes through the dashboard or configuration.yaml
4. **Grocery List**: Enter item names and check off as you shop
5. **Reading List**: Add book titles, authors, and update status as you read
6. **Payment Tracker**: Enter payment names, amounts, and due dates
7. **Custom Countdowns**: Set important dates and give them meaningful names

### Maintaining Your Data

- **Grocery List**: Check items off as purchased, clear checkboxes when creating new list
- **Reading List**: Update status from "To Read" → "Reading" → "Completed"
- **Payment Tracker**: Update due dates after each payment
- **Love Notes**: Edit periodically to keep messages fresh and meaningful
- **Milestones**: Add new milestones as your journey continues

## Tips for Best Experience

1. **Set dates chronologically**: Enter past milestones in order for a meaningful timeline
2. **Use descriptive names**: Make countdown and payment names clear and specific
3. **Regular updates**: Keep lists current by updating weekly
4. **Personalize love notes**: Make them specific to your relationship
5. **Celebrate milestones**: Mark immigration milestones complete as you achieve them
6. **Mobile access**: Add dashboard to home screen for quick access
7. **Backup data**: Export configuration.yaml regularly to preserve your data

## Future Enhancements

Potential additions to consider:

- Photo gallery integration for milestone memories
- Shared to-do list with task assignments
- Budget tracker with spending categories
- Anniversary countdown with special styling
- Weather-based date suggestions
- Integration with shared calendar for automatic event display
- Notification system for upcoming payments and milestones

---

