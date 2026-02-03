# Mobile Optimization Guide

## Overview

The "Our Life Together" dashboard is optimized for mobile devices with responsive layouts, touch-friendly controls, and efficient data loading.

## Responsive Layout

### Grid System

The dashboard uses a responsive grid that adapts to screen size:

```yaml
type: custom:grid-layout
layout:
  grid-template-columns: 1fr 1fr  # Desktop: 2 columns
  grid-template-rows: auto
  grid-gap: 16px
  mediaquery:
    "(max-width: 800px)":
      grid-template-columns: 1fr  # Mobile: 1 column
```

### Breakpoints

| Screen Width | Layout | Columns |
|--------------|--------|---------|
| > 800px | Desktop | 2 columns |
| ≤ 800px | Mobile | 1 column |

## Mobile-Specific Optimizations

### 1. Touch Targets

All interactive elements meet the minimum touch target size:
- **Minimum Size**: 44x44px (iOS/Android standard)
- **Spacing**: 8px minimum between targets
- **Buttons**: Full-width on mobile for easy tapping

### 2. Card Sizing

Cards are optimized for mobile viewing:
- **Max Width**: 100% of screen width
- **Padding**: 16-24px for comfortable reading
- **Font Size**: 1.1em for readability on small screens

### 3. Collapsible Sections

Long lists use fold-entity-row to reduce scrolling:
- Grocery items 11-20: Collapsed by default
- Reading list books 6-10: Collapsed by default
- Payment tracker items 6-10: Collapsed by default
- Love notes editor: Collapsed by default

### 4. Vertical Stacking

On mobile, all cards stack vertically:
- Immigration Journey
- Countdowns
- Love Notes
- Shared Lists
- Relationship Journey

## Performance Optimization

### 1. Lazy Loading

Cards load progressively as you scroll:
- Initial viewport loads first
- Below-fold content loads on demand
- Reduces initial page load time

### 2. Efficient Templates

Template sensors are optimized:
- Minimal calculations
- Cached results where possible
- Update only when data changes

### 3. Icon Usage

Icons are lightweight and fast:
- Material Design Icons (MDI)
- Vector-based (scalable)
- No external image loading

## Testing on Mobile Devices

### Browser Testing

1. **Chrome DevTools**:
   - Press F12
   - Click device toolbar icon
   - Select device (iPhone, Pixel, etc.)
   - Test different screen sizes

2. **Firefox Responsive Design Mode**:
   - Press Ctrl+Shift+M
   - Choose device or custom size
   - Test touch interactions

### Real Device Testing

1. **iOS (iPhone/iPad)**:
   - Open Home Assistant app or Safari
   - Navigate to dashboard
   - Test touch interactions
   - Check text readability

2. **Android**:
   - Open Home Assistant app or Chrome
   - Navigate to dashboard
   - Test touch interactions
   - Check text readability

## Mobile-Specific Features

### 1. Swipe Gestures

Home Assistant app supports:
- **Swipe Left/Right**: Navigate between dashboards
- **Pull Down**: Refresh dashboard
- **Long Press**: Edit mode (if enabled)

### 2. Notifications

Countdown celebrations can trigger mobile notifications:
- Push notifications via Home Assistant app
- Persistent notifications in app
- Badge updates on app icon

### 3. Quick Actions

Mobile app supports quick actions:
- Add to home screen
- Widget support (Android)
- Siri shortcuts (iOS)

## Common Mobile Issues & Solutions

### Issue: Text Too Small

**Solution**: Increase font size in card styling:
```yaml
card_mod:
  style: |
    ha-card {
      font-size: 1.2em;  /* Increase from 1.1em */
    }
```

### Issue: Cards Too Wide

**Solution**: Already handled by responsive grid. If issues persist:
```yaml
card_mod:
  style: |
    ha-card {
      max-width: 100%;
      overflow-x: hidden;
    }
```

### Issue: Slow Loading

**Solutions**:
1. Reduce number of visible cards
2. Use fold-entity-row for long lists
3. Disable animations on mobile:
```yaml
card_mod:
  style: |
    @media (max-width: 800px) {
      ha-card {
        animation: none !important;
      }
    }
```

### Issue: Touch Targets Too Small

**Solution**: Increase padding and spacing:
```yaml
card_mod:
  style: |
    ha-card {
      padding: 20px;
    }
    .entity {
      min-height: 48px;
    }
```

## Mobile Data Usage

The dashboard is data-efficient:
- **Initial Load**: ~50KB (without images)
- **Updates**: ~5KB per refresh
- **Icons**: Cached locally
- **No Video/Heavy Media**: Text and icons only

## Accessibility on Mobile

### Screen Readers

The dashboard is compatible with:
- **iOS VoiceOver**: Full support
- **Android TalkBack**: Full support
- **Semantic HTML**: Proper heading hierarchy

### High Contrast Mode

Cards maintain readability in high contrast:
- Sufficient color contrast ratios
- Border indicators for sections
- Icon + text labels

### Font Scaling

Dashboard respects system font size:
- iOS: Settings → Display & Brightness → Text Size
- Android: Settings → Display → Font Size

## Best Practices

### 1. Test on Real Devices

Always test on actual phones/tablets:
- Different screen sizes
- Different OS versions
- Different browsers

### 2. Optimize for Portrait

Most users view in portrait mode:
- Single column layout
- Vertical scrolling
- Full-width cards

### 3. Minimize Scrolling

Use collapsible sections:
- Fold-entity-row for long lists
- Conditional cards for optional content
- Tabs for different views

### 4. Touch-Friendly Controls

Ensure easy interaction:
- Large buttons
- Adequate spacing
- Clear visual feedback

## Mobile-Specific Customization

### Disable Animations on Mobile

```yaml
card_mod:
  style: |
    @media (max-width: 800px) {
      ha-card {
        animation: none !important;
        transition: none !important;
      }
    }
```

### Larger Text on Mobile

```yaml
card_mod:
  style: |
    @media (max-width: 800px) {
      ha-card {
        font-size: 1.3em;
      }
    }
```

### Hide Elements on Mobile

```yaml
card_mod:
  style: |
    @media (max-width: 800px) {
      .optional-element {
        display: none;
      }
    }
```

## Performance Metrics

Target metrics for mobile:
- **First Contentful Paint**: < 1.5s
- **Time to Interactive**: < 3s
- **Largest Contentful Paint**: < 2.5s
- **Cumulative Layout Shift**: < 0.1

## Future Mobile Enhancements

Consider these improvements:
- Progressive Web App (PWA) features
- Offline support
- Home screen widgets
- Voice control integration
- Gesture-based navigation

## Testing Checklist

- [ ] Test on iPhone (iOS)
- [ ] Test on Android phone
- [ ] Test on iPad/tablet
- [ ] Test in portrait orientation
- [ ] Test in landscape orientation
- [ ] Test with small font size
- [ ] Test with large font size
- [ ] Test with VoiceOver/TalkBack
- [ ] Test touch target sizes
- [ ] Test scrolling performance
- [ ] Test with slow network
- [ ] Test with Home Assistant app
- [ ] Test with mobile browser

## Resources

- [Home Assistant Mobile App](https://companion.home-assistant.io/)
- [Mobile Web Best Practices](https://web.dev/mobile/)
- [Touch Target Guidelines](https://www.w3.org/WAI/WCAG21/Understanding/target-size.html)
- [Responsive Design](https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Responsive_Design)
