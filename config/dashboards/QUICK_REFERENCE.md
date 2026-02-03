# Dashboard Styling - Quick Reference

## 🎨 Color Palette

| Section | Color | Hex Code |
|---------|-------|----------|
| Immigration | Green | #4CAF50 |
| Countdowns | Orange | #FF9800 |
| Love Notes | Pink Gradient | #f093fb → #f5576c |
| Shared Lists | Blue | #2196F3 |
| Relationship | Pink | #E91E63 |
| Grocery | Green | #4CAF50 |
| Reading | Purple | #9C27B0 |
| Payments | Orange | #FF9800 |

## 📱 Responsive Breakpoints

- **Desktop**: > 800px (2 columns)
- **Mobile**: ≤ 800px (1 column)

## 🔧 Quick Setup

1. Install card-mod: `HACS → Frontend → card-mod`
2. Restart Home Assistant
3. Clear cache: `Ctrl+Shift+R`
4. View dashboard

## 📐 Design Standards

- **Border Radius**: 12px (standard), 16px (featured)
- **Box Shadow**: `0 2px 8px rgba(0,0,0,0.08)`
- **Border Accent**: 4px left border
- **Padding**: 16-24px
- **Font Size**: 1.1em (body), 1.8em (headers)
- **Line Height**: 1.6
- **Grid Gap**: 16px
- **Touch Targets**: 44px minimum

## 📚 Documentation

| File | Purpose |
|------|---------|
| STYLING_GUIDE.md | Complete design system |
| STYLING_SETUP.md | Installation guide |
| MOBILE_OPTIMIZATION.md | Mobile best practices |
| TESTING_CHECKLIST.md | Testing procedures |
| STYLING_COMPLETE.md | Implementation summary |

## 🎯 Common Customizations

### Change Section Color
```yaml
background: linear-gradient(135deg, rgba(R, G, B, 0.1) 0%, rgba(R, G, B, 0.05) 100%);
```

### Change Border Color
```yaml
border-left: 4px solid #YOUR_COLOR;
```

### Adjust Rounding
```yaml
border-radius: 16px;
```

### Larger Text
```yaml
font-size: 1.3em;
```

## ⚡ Performance Tips

- Disable animations on mobile if slow
- Use collapsible sections for long lists
- Clear browser cache regularly
- Update Home Assistant regularly

## 🐛 Troubleshooting

| Issue | Solution |
|-------|----------|
| No styling | Install card-mod, restart HA |
| Layout broken | Check browser console (F12) |
| Slow loading | Disable animations, reduce cards |
| Mobile issues | Test with responsive mode |

## ✅ Quick Test

1. Check colors match palette
2. Verify rounded corners
3. Test mobile layout (< 800px)
4. Confirm touch targets work
5. Validate animations smooth

## 🔗 Quick Links

- [card-mod GitHub](https://github.com/thomasloven/lovelace-card-mod)
- [HACS](https://hacs.xyz/)
- [Home Assistant Docs](https://www.home-assistant.io/docs/)
- [Material Design Icons](https://materialdesignicons.com/)

## 💡 Pro Tips

- Use browser DevTools for testing
- Test on real devices, not just emulators
- Keep documentation updated
- Take screenshots before changes
- Version control your configs

---

**Need Help?** Check the full documentation in the dashboards folder.
