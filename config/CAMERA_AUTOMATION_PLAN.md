# Tapo Camera Automation Plan

## Overview

Smart camera automation that respects privacy when home and provides security when away.

## Automation Goals

1. **Privacy First**: Bedroom camera privacy mode when anyone is home
2. **Smart Detection**: Enable pet detection when away
3. **Contextual Alerts**: Notifications only when away from home
4. **Intelligent Transitions**: Smooth mode changes with delays

## Proposed Automations

### 1. Bedroom Privacy Mode (When Home)

**Trigger**: Anyone arrives home  
**Action**: Enable privacy mode on bedroom camera  
**Delay**: 2 minutes (allows for quick trips)  
**Override**: Manual guest mode switch

### 2. Bedroom Privacy Mode Off (When Away)

**Trigger**: Everyone leaves home  
**Action**: Disable privacy mode on bedroom camera  
**Delay**: 5 minutes (prevents false triggers)  
**Condition**: Not in guest mode

### 3. Pet Detection (When Away)

**Trigger**: Everyone leaves home  
**Action**: Enable pet detection on all cameras  
**Delay**: 5 minutes  
**Additional**: Enable motion detection

### 4. Pet Detection Off (When Home)

**Trigger**: Anyone arrives home  
**Action**: Disable pet detection on all cameras  
**Delay**: 2 minutes

### 5. Motion Alerts (When Away)

**Trigger**: Motion/person/pet detected  
**Condition**: Everyone is away  
**Action**: Send notification with snapshot  
**Priority**: Person > Pet > Motion

### 6. Night Mode Override

**Trigger**: 10 PM  
**Action**: Force bedroom privacy mode ON  
**Condition**: Anyone is home  
**Note**: Stays on until morning or everyone leaves

## Required Entities

You'll need to identify:
- `camera.bedroom_camera` (or similar)
- `camera.living_room_camera` (example)
- `person.bookish`
- `person.jester` (or your person entity)
- `zone.home`

## Helper Entities Needed

```yaml
input_boolean:
  guest_mode:
    name: "Guest Mode"
    icon: mdi:account-multiple
  
  camera_alerts_enabled:
    name: "Camera Alerts Enabled"
    icon: mdi:bell-alert
```

## Services to Use

Tapo Control provides these services:
- `tapo_control.set_privacy_mode`
- `tapo_control.set_motion_detection_mode`
- `tapo_control.set_alarm_mode`

## Notification Strategy

### High Priority (Immediate)
- Person detected when away
- Motion in bedroom when away

### Medium Priority (Grouped)
- Pet detected when away
- Motion in common areas when away

### Low Priority (Summary)
- Daily summary of detections

## Additional Features

1. **Vacation Mode**: Extended away mode with enhanced alerts
2. **Sleep Mode**: All cameras on privacy except exterior
3. **Party Mode**: Disable bedroom camera, keep others active
4. **Quick Actions**: Dashboard buttons for mode changes

## Privacy Considerations

- ✅ Bedroom camera always private when home
- ✅ No recording during privacy mode (optional)
- ✅ Clear visual indicators of camera status
- ✅ Manual overrides always available
- ✅ Notification preferences per person

## Testing Plan

1. Test arrival/departure triggers
2. Verify delay timings
3. Test manual overrides
4. Verify notification delivery
5. Test edge cases (one person home, one away)

## Next Steps

1. Identify your camera entity IDs
2. Confirm person entity IDs
3. Create helper entities
4. Implement automations
5. Test and refine delays
6. Set up notification preferences

Would you like me to proceed with implementation?
