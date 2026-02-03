# Our Life Together Dashboard - Setup Guide

## ✅ What's Been Completed

The "Our Life Together" dashboard has been fully implemented with a responsive two-column layout that includes:

### Left Column
- 🛂 Immigration Timeline Tracker (with progress bar and milestone tracking)
- ⏰ Countdown System (payday + 3 custom countdowns)
- 💕 Love Notes (rotating every 4 hours)

### Right Column
- 🛒 Grocery List (20 items with checkboxes)
- 📚 Reading List (10 books with status tracking)
- 💳 Payment Tracker (10 payments with due dates)
- 💑 Relationship Journey Timeline (past and future milestones)

## 🚀 Quick Start

### 1. Restart Home Assistant

The dashboard is already configured and ready to use. Simply restart Home Assistant:

```bash
# Option 1: Through UI
Settings > System > Restart

# Option 2: Through CLI (if available)
ha core restart
```

### 2. Access the Dashboard

After restart, you'll find "Our Life Together" in your sidebar with a ❤️ icon.

Or navigate directly to: `http://your-home-assistant-url/our-life-together/home`

### 3. Start Adding Your Data

The dashboard is ready to use! Start by:

1. **Set Immigration Milestones**: Click on dates to set them, toggle completion status
2. **Add Love Notes**: Edit the 10 love notes to personalize them
3. **Create Grocery List**: Enter items you need to buy
4. **Track Payments**: Add your bills and due dates
5. **Build Reading List**: Add books you want to read together
6. **Record Milestones**: Set dates for your relationship journey

## 📱 Responsive Design

The dashboard automatically adapts to your screen size:

- **Desktop/Tablet**: Two-column layout for efficient viewing
- **Mobile**: Columns stack vertically for easy scrolling

## 🎨 Layout Structure

```
┌─────────────────────────────────────────────────────┐
│              Our Life Together Dashboard             │
├──────────────────────┬──────────────────────────────┤
│   LEFT COLUMN        │   RIGHT COLUMN               │
├──────────────────────┼──────────────────────────────┤
│ 📅 Calendar*         │ 📝 Shared Lists              │
│ 🛂 Immigration       │   🛒 Grocery List            │
│ ⏰ Countdowns        │   🍽️ Meal Planner*          │
│ 💕 Love Notes        │   📚 Reading List            │
│                      │   💳 Payment Tracker         │
│                      │ 💑 Relationship Journey      │
└──────────────────────┴──────────────────────────────┘

* Optional features (require Google Calendar setup)
```

## 🔧 Configuration Files

All configuration is complete and located in:

- **Dashboard Layout**: `config/dashboards/our_life_together.yaml`
- **Input Helpers**: `config/configuration.yaml` (input_datetime, input_boolean, input_number, input_text, input_select)
- **Template Sensors**: `config/configuration.yaml` (progress calculations, countdowns, etc.)
- **Automations**: `config/automations.yaml` (love note rotation)

## ⚙️ Optional Features

### Google Calendar Integration

Two features are commented out and require Google Calendar setup:

1. **Shared Calendar View** - Shows upcoming events
2. **Meal Planner** - Calendar-based meal planning

To enable:

1. Set up Google Calendar integration in Home Assistant
2. Edit `config/dashboards/our_life_together.yaml`
3. Search for `# TODO: Uncomment after setting up Google Calendar integration`
4. Remove the `#` comment markers
5. Update entity names to match your calendars
6. Restart Home Assistant

## 📊 Entity Summary

The dashboard uses these entities (all pre-configured):

- **Input DateTime**: 27 entities (milestones, countdowns, payment dates)
- **Input Boolean**: 25 entities (milestone completion, grocery checkboxes)
- **Input Number**: 11 entities (love note index, payment amounts)
- **Input Text**: 53 entities (grocery items, books, payments, love notes)
- **Input Select**: 10 entities (reading status)
- **Template Sensors**: 17 entities (progress, countdowns, displays)
- **Automations**: 2 entities (love note rotation, celebration trigger)

## 🎯 Next Steps

### Immediate Actions

1. ✅ Restart Home Assistant
2. ✅ Access the dashboard from sidebar
3. ✅ Start entering your personal data

### Recommended Setup Order

1. **Immigration Timeline**: Set milestone dates and mark completed ones
2. **Relationship Journey**: Add past milestone dates (first date, arrival, etc.)
3. **Love Notes**: Personalize all 10 messages
4. **Payment Tracker**: Add recurring bills and due dates
5. **Grocery List**: Add items you regularly buy
6. **Reading List**: Add books you want to read together
7. **Custom Countdowns**: Set important upcoming dates

### Optional Enhancements

- Set up Google Calendar integration for calendar view and meal planner
- Install custom cards from HACS for enhanced styling
- Customize colors and styling in the YAML file
- Add more list items by duplicating input helpers

## 🐛 Troubleshooting

### Dashboard not visible
- Ensure you've restarted Home Assistant
- Check sidebar for "Our Life Together" with ❤️ icon
- Verify configuration.yaml includes the lovelace dashboard entry

### Entities showing "unavailable"
- All entities should be pre-configured in configuration.yaml
- If any are missing, restart Home Assistant
- Check home-assistant.log for errors

### Layout issues
- Clear browser cache (Ctrl+F5 or Cmd+Shift+R)
- Try different browser
- Check that you're using Home Assistant 2024.11 or later

### Custom cards not working
- The dashboard uses `custom:fold-entity-row` for collapsible sections
- Install from HACS if not already installed
- Or replace with standard `entities` cards

## 📚 Documentation

Full documentation available in:
- `config/dashboards/README.md` - Complete dashboard documentation
- `config/dashboards/our_life_together.yaml` - Dashboard configuration with comments

## 🎉 Enjoy Your Dashboard!

Your "Our Life Together" dashboard is ready to help you manage and celebrate your shared life. Start adding your data and make it your own!

---

**Need Help?**
- Check the README.md for detailed documentation
- Review the YAML file for configuration examples
- Consult Home Assistant documentation for general help
