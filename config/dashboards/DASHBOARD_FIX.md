# Dashboard Loading Issue - Diagnosis and Fix

## Problem

The "Our Life Together" dashboard is not loading in Home Assistant.

## Root Cause

The dashboard uses `card-mod` for custom styling, which is a custom component that must be installed via HACS. If `card-mod` is not installed, the dashboard will fail to load.

## Solution

### Option 1: Install card-mod (Recommended for Full Styling)

1. **Install HACS** (if not already installed):
   - Follow: https://hacs.xyz/docs/setup/download

2. **Install card-mod**:
   - Open Home Assistant
   - Go to HACS → Frontend
   - Click the "+" button
   - Search for "card-mod"
   - Click "Install"
   - Restart Home Assistant

3. **Verify Installation**:
   - Go to Settings → Dashboards → Resources
   - You should see `card-mod` listed

4. **Reload the Dashboard**:
   - Navigate to "Our Life Together" in the sidebar
   - The dashboard should now load with full styling

### Option 2: Use Basic Dashboard (Temporary Workaround)

I've created a basic version without custom styling that will load immediately:

1. **Update configuration.yaml**:
   ```yaml
   lovelace:
     mode: storage
     dashboards:
       our-life-together:
         mode: yaml
         title: Our Life Together
         icon: mdi:heart
         show_in_sidebar: true
         filename: dashboards/our_life_together_basic.yaml  # Changed from our_life_together.yaml
   ```

2. **Restart Home Assistant**

3. **The basic dashboard will load** (without advanced styling)

### Option 3: Remove card-mod Styling from Main Dashboard

If you want to use the full dashboard without card-mod:

Run this command to remove all card_mod sections:
```bash
# This will create a backup and remove card_mod styling
cp config/dashboards/our_life_together.yaml config/dashboards/our_life_together_backup.yaml
```

Then manually remove all `card_mod:` sections from the file.

## Verification Steps

After applying the fix:

1. **Check Home Assistant Logs**:
   - Settings → System → Logs
   - Look for errors related to "our_life_together" or "card-mod"

2. **Test Dashboard Loading**:
   - Click "Our Life Together" in the sidebar
   - Dashboard should load (may take a few seconds)

3. **Verify Entities**:
   - All sensors should show values or "Not set"
   - No "unavailable" or "unknown" errors for entities

## Additional Issues Found

### Template Sensor Timezone Errors

The template sensors in `configuration.yaml` have timezone issues (separate from dashboard loading). These cause:
- Countdown sensors to show errors
- Milestone calculations to fail

**Fix**: See `TEMPLATE_SENSOR_FIX.md` for details on fixing these.

## Current Dashboard Status

- ✅ YAML syntax: Valid
- ✅ Dashboard registration: Correct
- ✅ File structure: Correct
- ⚠️ card-mod dependency: Not installed (likely cause)
- ⚠️ Template sensors: Have timezone errors (separate issue)

## Quick Test

To quickly test if card-mod is the issue:

1. Open Home Assistant
2. Press F12 (open browser console)
3. Navigate to "Our Life Together"
4. Look for errors mentioning "custom:grid-layout" or "card-mod"
5. If you see these errors, card-mod is not installed

## Recommended Action Plan

1. **Immediate**: Use the basic dashboard (Option 2) to get it working now
2. **Short-term**: Install card-mod (Option 1) for full styling
3. **Long-term**: Fix template sensor timezone issues (see TEMPLATE_SENSOR_FIX.md)

## Files Created

- `our_life_together_basic.yaml` - Simplified dashboard without card-mod
- `DASHBOARD_FIX.md` - This file
- `TEMPLATE_SENSOR_FIX.md` - Guide for fixing template sensors

## Support

If the dashboard still doesn't load after trying these solutions:

1. Check Home Assistant logs for specific errors
2. Verify all entities exist in Developer Tools → States
3. Try restarting Home Assistant
4. Check browser console for JavaScript errors
