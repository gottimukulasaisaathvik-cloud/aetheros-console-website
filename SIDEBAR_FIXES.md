# Aetheros Console - Sidebar & Chart Overflow Fixes

## Problem Description
Graphs and line charts are extending beyond their containers and hiding sidebar information.

## Root Causes
1. Z-Index Stacking Issues - Charts may have higher z-index than sidebar
2. Missing Overflow Controls - Parent containers lack overflow constraints
3. Chart Container Sizing - Charts not constrained by max-height
4. Sidebar Positioning - Sidebar lacks proper z-index
5. Flex Layout Issues - Layout system not properly distributing space

## CSS Fixes to Apply

### 1. Sidebar Container Fix
```css
.sidebar, [class*="sidebar"], [class*="Sidebar"] {
  position: relative;
  z-index: 100;
  overflow-y: auto;
  overflow-x: hidden;
  max-height: 100vh;
  flex-shrink: 0;
}
```

### 2. Chart Container Fixes
```css
.chart-container, [class*="chart"], [class*="Chart"],
[class*="graph"], [class*="Graph"],
.recharts-wrapper, .apex-charts {
  position: relative;
  z-index: 1;
  max-height: 400px;
  overflow: hidden;
  display: flex;
  flex-direction: column;
}
```

### 3. Main Content Area Fix
```css
.content, [class*="content"], [class*="main"],
.dashboard, [class*="dashboard"] {
  display: flex;
  flex-direction: column;
  overflow: hidden;
  flex: 1;
  min-height: 0;
}
```

### 4. Layout Container Fix
```css
.layout-container, [class*="layout"],
.app-container {
  display: flex;
  height: 100vh;
  width: 100%;
  overflow: hidden;
}

.layout-container > * {
  min-height: 0;
  min-width: 0;
}
```

## Implementation Steps

1. Copy all CSS fixes above
2. Create a new file: `sidebar-layout-fixes.css`
3. Paste the CSS rules into the file
4. Add to your HTML <head>:
   `<link rel="stylesheet" href="/sidebar-layout-fixes.css">`
5. Test all sidebar and chart interactions
6. Commit and push changes

## Testing Checklist
- [ ] Sidebar is fully visible
- [ ] Charts don't overlap sidebar
- [ ] Scroll works properly
- [ ] No horizontal scrolling
- [ ] All content is accessible

## Debugging Tips
1. Open DevTools (F12)
2. Inspect the chart element
3. Check z-index values
4. Verify overflow settings
5. Toggle CSS in DevTools to test fixes

## For More Help
- Check the exact class names in your HTML
- Adjust max-height values as needed for your design
- Test on different screen sizes
- Use browser DevTools to debug CSS issues
