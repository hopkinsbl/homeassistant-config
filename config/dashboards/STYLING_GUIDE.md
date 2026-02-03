# Our Life Together Dashboard - Styling Guide

## Color Scheme

The dashboard uses a consistent, emotionally meaningful color palette:

### Primary Colors

- **Immigration Journey**: `#4CAF50` (Green) - Represents growth, progress, and new beginnings
- **Countdowns**: `#FF9800` (Orange) - Represents anticipation and energy
- **Love Notes**: `#f093fb` to `#f5576c` (Pink gradient) - Represents love and romance
- **Shared Lists**: `#2196F3` (Blue) - Represents organization and clarity
- **Relationship Journey**: `#E91E63` (Pink) - Represents love and connection

### Accent Colors

- **Grocery List**: `#4CAF50` (Green) - Fresh and practical
- **Reading List**: `#9C27B0` (Purple) - Creative and intellectual
- **Payment Tracker**: `#FF9800` (Orange) - Important and attention-grabbing
- **Celebration**: `#667eea` to `#764ba2` (Purple gradient) - Festive and joyful

## Design Principles

### 1. Consistent Styling

All cards follow these standards:
- **Border Radius**: 12px for standard cards, 16px for featured cards
- **Box Shadow**: `0 2px 8px rgba(0,0,0,0.08)` for subtle depth
- **Border Left**: 4px solid accent color for category identification
- **Padding**: 16-24px for content cards

### 2. Visual Hierarchy

- **Section Headers**: Gradient backgrounds with matching accent colors
- **Featured Cards**: Larger padding, enhanced shadows, gradient backgrounds
- **Interactive Elements**: Clear hover states and touch targets (min 44px)

### 3. Mobile Optimization

The dashboard uses responsive grid layout:
- **Desktop**: 2-column layout (1fr 1fr)
- **Mobile** (< 800px): Single column layout
- **Grid Gap**: 16px for comfortable spacing

### 4. Typography

- **Headers**: Larger font sizes (1.8em for main headers)
- **Body Text**: 1.1em for readability
- **Line Height**: 1.6 for comfortable reading

## Card Styling Patterns

### Standard Card
```yaml
card_mod:
  style: |
    ha-card {
      border-radius: 12px;
      box-shadow: 0 2px 8px rgba(0,0,0,0.08);
    }
```

### Category Header Card
```yaml
card_mod:
  style: |
    ha-card {
      background: linear-gradient(135deg, rgba(COLOR, 0.1) 0%, rgba(COLOR, 0.05) 100%);
      border-radius: 12px;
      padding: 8px;
      box-shadow: 0 2px 8px rgba(0,0,0,0.1);
    }
```

### Featured/Highlight Card
```yaml
card_mod:
  style: |
    ha-card {
      background: linear-gradient(135deg, rgba(COLOR, 0.15) 0%, rgba(COLOR, 0.05) 100%);
      border-left: 4px solid COLOR;
      border-radius: 12px;
      padding: 16px;
      box-shadow: 0 2px 8px rgba(0,0,0,0.08);
    }
```

### List Card with Category Color
```yaml
card_mod:
  style: |
    ha-card {
      border-radius: 12px;
      box-shadow: 0 2px 8px rgba(0,0,0,0.08);
      border-left: 4px solid CATEGORY_COLOR;
    }
```

### Celebration/Special Card
```yaml
card_mod:
  style: |
    ha-card {
      background: linear-gradient(135deg, COLOR1 0%, COLOR2 100%);
      color: white;
      border-radius: 16px;
      padding: 24px;
      text-align: center;
      box-shadow: 0 6px 20px rgba(COLOR, 0.4);
      animation: pulse 2s infinite;
    }
```

## Icon Usage

Icons are chosen to be intuitive and emotionally resonant:

- **Immigration**: `mdi:airplane-landing`, `mdi:file-document`, `mdi:progress-check`
- **Countdowns**: `mdi:calendar-clock`, `mdi:cash-multiple`, `mdi:calendar-star`
- **Love Notes**: `mdi:heart`, `mdi:heart-multiple`
- **Lists**: `mdi:cart`, `mdi:book-open-page-variant`, `mdi:cash`
- **Journey**: `mdi:calendar-heart`, `mdi:home-heart`, `mdi:flag-variant`

## Animations

### Pulse Animation (Celebrations)
```css
@keyframes pulse {
  0%, 100% { 
    transform: scale(1); 
    box-shadow: 0 4px 20px rgba(102, 126, 234, 0.4); 
  }
  50% { 
    transform: scale(1.02); 
    box-shadow: 0 6px 30px rgba(102, 126, 234, 0.6); 
  }
}
```

## Accessibility Considerations

- **Color Contrast**: All text meets WCAG AA standards
- **Touch Targets**: Minimum 44x44px for interactive elements
- **Focus States**: Clear visual indicators for keyboard navigation
- **Semantic HTML**: Proper heading hierarchy in markdown cards

## Testing Checklist

- [ ] Desktop view (1920x1080)
- [ ] Tablet view (768x1024)
- [ ] Mobile view (375x667)
- [ ] Dark mode compatibility
- [ ] Light mode compatibility
- [ ] Color contrast ratios
- [ ] Touch target sizes
- [ ] Animation performance
- [ ] Card loading states
- [ ] Empty state displays

## Future Enhancements

Consider these improvements:
- Custom theme integration
- Seasonal color variations
- Dark mode optimized gradients
- Enhanced animations for milestone achievements
- Custom fonts for personal touch
