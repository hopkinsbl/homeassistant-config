# Dashboard Testing Checklist

## Overview

This checklist ensures the "Our Life Together" dashboard is fully functional, visually appealing, and performs well across all devices and scenarios.

## Pre-Testing Setup

- [ ] card-mod installed via HACS
- [ ] Home Assistant restarted after card-mod installation
- [ ] Browser cache cleared (Ctrl+Shift+R)
- [ ] Dashboard loaded successfully
- [ ] No errors in browser console (F12)

## Visual Styling Tests

### Color Scheme

- [ ] Immigration Journey section has green accent (#4CAF50)
- [ ] Countdowns section has orange accent (#FF9800)
- [ ] Love Notes card has pink gradient background
- [ ] Shared Lists section has blue accent (#2196F3)
- [ ] Relationship Journey section has pink accent (#E91E63)
- [ ] All section headers have gradient backgrounds
- [ ] All cards have rounded corners (12px radius)
- [ ] All cards have subtle shadows

### Card Styling

- [ ] All cards have consistent border-radius
- [ ] Category cards have 4px left border in accent color
- [ ] Grocery List has green left border
- [ ] Reading List has purple left border
- [ ] Payment Tracker has orange left border
- [ ] Featured cards have enhanced shadows
- [ ] Markdown cards have proper padding

### Typography

- [ ] Section headers are large and readable (1.8em)
- [ ] Body text is comfortable size (1.1em)
- [ ] Line height provides good readability (1.6)
- [ ] All text has sufficient contrast
- [ ] Emoji display correctly
- [ ] Icons are properly sized

## Functional Tests

### Immigration Timeline

- [ ] Progress percentage calculates correctly
- [ ] Gauge card displays progress visually
- [ ] Next milestone displays correctly
- [ ] Days until next milestone calculates accurately
- [ ] Milestone completion toggles work
- [ ] Completed milestones show checkmarks
- [ ] Milestone dates can be edited
- [ ] Fold-entity-row expands/collapses properly

### Countdowns

- [ ] Payday countdown calculates correctly
- [ ] Custom countdown 1 works
- [ ] Custom countdown 2 works
- [ ] Custom countdown 3 works
- [ ] Countdown names display correctly
- [ ] Days remaining update daily
- [ ] Celebration message appears when countdown reaches zero
- [ ] Celebration message has pulse animation
- [ ] Celebration message disappears after 24 hours

### Love Notes

- [ ] Current love note displays correctly
- [ ] Love note rotates every 4 hours
- [ ] Love note index increments properly
- [ ] Love note wraps around at 10
- [ ] All 10 love notes can be edited
- [ ] Love note card has gradient background
- [ ] Love note card has proper styling
- [ ] Rotation indicator shows current note number

### Shared Lists

#### Grocery List
- [ ] All 20 grocery items display
- [ ] Items 11-20 are collapsed by default
- [ ] Item text can be edited
- [ ] Checkboxes toggle on/off
- [ ] Checked items persist after refresh
- [ ] Empty items don't cause errors

#### Reading List
- [ ] All 10 books display
- [ ] Books 6-10 are collapsed by default
- [ ] Book titles can be edited
- [ ] Author names can be edited
- [ ] Status dropdown works (To Read, Reading, Completed)
- [ ] Status changes persist

#### Payment Tracker
- [ ] All 10 payments display
- [ ] Payments 6-10 are collapsed by default
- [ ] Payment names can be edited
- [ ] Payment amounts can be edited
- [ ] Due dates can be set
- [ ] Days until due calculates correctly
- [ ] Overdue payments show "Overdue"

### Relationship Journey

- [ ] Days since Sharlene arrived calculates correctly
- [ ] Arrival date displays in readable format
- [ ] Next milestone displays correctly
- [ ] Days until next milestone calculates accurately
- [ ] Past milestones are organized by category
- [ ] Relationship milestones fold/unfold
- [ ] Visa milestones fold/unfold
- [ ] Housing milestones fold/unfold
- [ ] All milestone dates can be edited

## Responsive Design Tests

### Desktop (>800px)

- [ ] Two-column layout displays
- [ ] Left column: Immigration, Countdowns, Love Notes
- [ ] Right column: Shared Lists, Relationship Journey
- [ ] Cards are evenly distributed
- [ ] Grid gap is 16px
- [ ] No horizontal scrolling
- [ ] All cards visible without excessive scrolling

### Tablet (768px - 800px)

- [ ] Layout transitions smoothly
- [ ] Single column layout at 800px breakpoint
- [ ] Cards stack vertically
- [ ] Touch targets are adequate
- [ ] Text remains readable

### Mobile (<768px)

- [ ] Single column layout
- [ ] Cards stack vertically
- [ ] Full-width cards
- [ ] No horizontal scrolling
- [ ] Touch targets minimum 44px
- [ ] Text is readable without zooming
- [ ] Collapsible sections work
- [ ] Scrolling is smooth

## Browser Compatibility

### Chrome/Edge

- [ ] Dashboard loads correctly
- [ ] All styling appears
- [ ] Animations work
- [ ] No console errors
- [ ] Touch/click interactions work

### Firefox

- [ ] Dashboard loads correctly
- [ ] All styling appears
- [ ] Animations work
- [ ] No console errors
- [ ] Touch/click interactions work

### Safari (iOS)

- [ ] Dashboard loads correctly
- [ ] All styling appears
- [ ] Animations work
- [ ] Touch interactions work
- [ ] Swipe gestures work

### Home Assistant App

- [ ] Dashboard loads in iOS app
- [ ] Dashboard loads in Android app
- [ ] All features work in app
- [ ] Notifications work (if configured)

## Performance Tests

### Load Time

- [ ] Initial load < 3 seconds
- [ ] First Contentful Paint < 1.5 seconds
- [ ] Time to Interactive < 3 seconds
- [ ] No layout shifts during load

### Runtime Performance

- [ ] Smooth scrolling (60fps)
- [ ] No lag when interacting
- [ ] Animations are smooth
- [ ] Template sensors update quickly
- [ ] No memory leaks over time

### Data Usage

- [ ] Initial load < 100KB
- [ ] Updates < 10KB
- [ ] No unnecessary API calls
- [ ] Efficient template calculations

## Accessibility Tests

### Screen Readers

- [ ] VoiceOver (iOS) reads all content
- [ ] TalkBack (Android) reads all content
- [ ] Heading hierarchy is logical
- [ ] Form labels are present
- [ ] Interactive elements are announced

### Keyboard Navigation

- [ ] Tab key navigates through elements
- [ ] Enter/Space activates buttons
- [ ] Focus indicators are visible
- [ ] No keyboard traps
- [ ] Logical tab order

### Color Contrast

- [ ] All text meets WCAG AA (4.5:1)
- [ ] Large text meets WCAG AA (3:1)
- [ ] Interactive elements have sufficient contrast
- [ ] Focus indicators are visible

### Font Scaling

- [ ] Dashboard works with 200% zoom
- [ ] Text doesn't overflow containers
- [ ] Layout remains usable
- [ ] No horizontal scrolling at 200% zoom

## Edge Cases & Error Handling

### Empty Data

- [ ] Empty grocery items don't cause errors
- [ ] Empty love notes show placeholder
- [ ] Unset dates show "Not set"
- [ ] Missing milestones handled gracefully

### Invalid Data

- [ ] Invalid dates handled gracefully
- [ ] Negative numbers handled correctly
- [ ] Special characters in text fields work
- [ ] Very long text doesn't break layout

### Boundary Conditions

- [ ] Countdown at 0 days works
- [ ] Countdown at negative days shows 0
- [ ] Progress at 0% displays correctly
- [ ] Progress at 100% displays correctly
- [ ] Love note index at 1 works
- [ ] Love note index at 10 works

## Integration Tests

### Calendar Integration

- [ ] Calendar card displays (if configured)
- [ ] Events show for next 7 days
- [ ] Next 24 hours highlighted
- [ ] Calendar syncs correctly

### Automation Integration

- [ ] Love note rotation automation triggers
- [ ] Countdown celebration automation triggers
- [ ] Celebration message clears after 24 hours

### Template Sensors

- [ ] All template sensors have valid states
- [ ] No "unknown" or "unavailable" errors
- [ ] Sensors update on data change
- [ ] Calculations are accurate

## User Experience Tests

### First-Time User

- [ ] Dashboard is intuitive
- [ ] Section purposes are clear
- [ ] Icons are meaningful
- [ ] Instructions are clear (if any)

### Daily Use

- [ ] Quick to scan for information
- [ ] Easy to update lists
- [ ] Milestones are motivating
- [ ] Love notes are delightful

### Emotional Impact

- [ ] Love notes feel personal
- [ ] Milestones celebrate progress
- [ ] Countdowns build anticipation
- [ ] Overall tone is positive

## Documentation Tests

- [ ] STYLING_GUIDE.md is accurate
- [ ] STYLING_SETUP.md is complete
- [ ] MOBILE_OPTIMIZATION.md is helpful
- [ ] OUR_LIFE_TOGETHER_SETUP.md is current
- [ ] All code examples work

## Regression Tests

After any changes:

- [ ] All previous tests still pass
- [ ] No new console errors
- [ ] No broken styling
- [ ] No broken functionality
- [ ] Performance hasn't degraded

## Sign-Off

### Desktop Testing

- [ ] Tested on Windows
- [ ] Tested on macOS
- [ ] Tested on Linux
- [ ] All tests passed

### Mobile Testing

- [ ] Tested on iPhone
- [ ] Tested on Android phone
- [ ] Tested on iPad
- [ ] Tested on Android tablet
- [ ] All tests passed

### Browser Testing

- [ ] Chrome tested
- [ ] Firefox tested
- [ ] Safari tested
- [ ] Edge tested
- [ ] All tests passed

### Final Approval

- [ ] All critical tests passed
- [ ] All styling is correct
- [ ] All functionality works
- [ ] Performance is acceptable
- [ ] Documentation is complete
- [ ] Ready for production use

## Notes

Use this section to document any issues found during testing:

```
Date: ___________
Tester: ___________

Issues Found:
1. 
2. 
3. 

Issues Resolved:
1. 
2. 
3. 

Outstanding Issues:
1. 
2. 
3. 
```

## Continuous Testing

Recommended testing schedule:

- **Daily**: Quick visual check
- **Weekly**: Functional tests
- **Monthly**: Full regression test
- **After Updates**: Complete checklist
- **After Changes**: Relevant sections

## Automated Testing

Consider setting up:
- Lighthouse CI for performance
- Accessibility testing tools
- Visual regression testing
- Load testing for template sensors

## Resources

- [WCAG Guidelines](https://www.w3.org/WAI/WCAG21/quickref/)
- [Lighthouse](https://developers.google.com/web/tools/lighthouse)
- [Home Assistant Testing](https://www.home-assistant.io/docs/configuration/testing/)
