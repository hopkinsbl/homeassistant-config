# Template Sensor Timezone Fix

## Issue

The Home Assistant logs show template errors related to timezone-aware vs timezone-naive datetime comparisons. These errors are in the `configuration.yaml` template sensors, not in the dashboard styling.

## Error Messages

```
TypeError: can't subtract offset-naive and offset-aware datetimes
TypeError: can't compare offset-naive and offset-aware datetimes
```

## Affected Sensors

- `sensor.days_until_next_immigration_milestone`
- `sensor.countdown_important_date_1`
- `sensor.countdown_important_date_2`
- `sensor.countdown_important_date_3`
- `sensor.days_until_payment_1` through `sensor.days_until_payment_10`
- `sensor.days_since_sharlene_arrived`
- `sensor.next_relationship_milestone`
- `sensor.days_until_next_relationship_milestone`

## Root Cause

The `as_datetime()` function in Home Assistant templates returns a timezone-naive datetime when given a date string from `input_datetime` entities. When comparing or subtracting with `now()` (which is timezone-aware), Python raises a TypeError.

## Solution

Replace all datetime operations in template sensors to use `today_at()` or ensure both datetimes have timezone information.

### Fix Pattern

**Before (causes error):**
```yaml
{% set days = (as_datetime(date) - now()).days %}
```

**After (works correctly):**
```yaml
{% set target = as_datetime(date).replace(tzinfo=now().tzinfo) %}
{% set days = (target - now()).days %}
```

Or use the simpler approach:
```yaml
{% set days = (as_datetime(date ~ ' 00:00:00').replace(tzinfo=now().tzinfo) - now()).days %}
```

## Quick Fix for All Sensors

The template sensors in `configuration.yaml` need to be updated. Here's the pattern for countdown sensors:

```yaml
- name: "Countdown Important Date 1"
  unique_id: countdown_important_date_1
  state: >
    {% set date = states('input_datetime.important_date_1') %}
    {% if date not in ['unknown', 'unavailable', ''] %}
      {% set target = as_datetime(date ~ ' 00:00:00').replace(tzinfo=now().tzinfo) %}
      {% set days = (target - now()).days %}
      {{ days if days >= 0 else 0 }}
    {% else %}
      Not set
    {% endif %}
  unit_of_measurement: "days"
  icon: mdi:calendar-star
```

## Impact on Dashboard

- The dashboard styling is complete and correct
- The dashboard YAML file has no errors
- The template sensor errors don't affect the dashboard layout or styling
- Once the template sensors are fixed, all countdown and milestone features will work correctly

## Recommended Action

1. **Immediate**: The dashboard styling is complete and functional
2. **Next Step**: Fix the template sensors in `configuration.yaml` (separate task)
3. **Testing**: After fixing templates, restart Home Assistant and verify sensors

## Note

This issue existed before the styling task and is unrelated to the dashboard styling changes. The styling task (Task 10) is complete and successful. The template sensor fixes should be addressed as a separate maintenance task.

## Status

- ✅ Dashboard styling: Complete
- ⚠️ Template sensors: Need timezone fixes (separate issue)
- ✅ Dashboard functionality: Works (displays "Not set" for uninitialized dates)

## Related Files

- **Dashboard**: `config/dashboards/our_life_together.yaml` (no errors)
- **Templates**: `config/configuration.yaml` (needs timezone fixes)
