# Cinematic Intro Sequence Documentation

## Overview
A lightweight, interactive intro sequence that creates a cinematic welcome experience when users first visit your portfolio.

## Features Implemented ✨

### 1. **Typing Animation**
- Smooth typewriter effect displaying:
  - "Hi, I'm Harshit Vaishnav"
  - "Welcome to my world."
- Blinking cursor with CSS animation
- 80ms character delay for natural typing feel
- 1200ms pause between lines

### 2. **Two-Choice Cards**
After typing animation completes, two beautiful image cards fade in:

#### Professional Card
- **Purpose**: Leads to main portfolio
- **Image**: Coding/tech workspace
- **Action**: Shows portfolio content on click
- **Style**: Professional dev workspace aesthetic

#### Personal Card
- **Purpose**: Links to personal interests/hobbies
- **Image**: Music/creative space
- **Action**: Navigates to About section (placeholder)
- **Style**: Creative/personal aesthetic

### 3. **Interactive Effects**
- **Hover Zoom**: Images scale to 1.15x on hover
- **Card Lift**: Cards translate up 8px on hover
- **Overlay**: Gradient overlay with labels appears on hover
- **Smooth Transitions**: All animations use cubic-bezier easing

### 4. **Skip Button**
- Top-right corner skip functionality
- Allows users to bypass intro
- Glassmorphism design with blur effect
- Orange accent on hover

## Technical Implementation

### Performance Optimizations
- **GPU Accelerated**: All transforms use CSS `will-change`
- **Minimal JS**: ~60 lines for typing logic
- **No Dependencies**: Pure React + Framer Motion (already loaded)
- **Lazy Loading**: Images from Unsplash CDN
- **Total Size**: <5KB (excluding images)

### Component Structure
```javascript
IntroSequence Component
├── Skip Button
├── Typing Text Container
│   ├── Typed Text
│   └── Blinking Cursor
└── Choice Cards Container
    ├── Professional Card
    │   ├── Image
    │   └── Hover Overlay
    └── Personal Card
        ├── Image
        └── Hover Overlay
```

### State Management
```javascript
const [showIntro, setShowIntro] = useState(true);
const [introComplete, setIntroComplete] = useState(false);
const [typedText, setTypedText] = useState('');
const [fadeOut, setFadeOut] = useState(false);
const [showChoices, setShowChoices] = useState(false);
```

### Timeline
1. **0-3s**: Typing animation plays
2. **3-3.5s**: Text fades out
3. **3.5s**: Cards fade in with stagger
4. **User Click**: Instant transition to portfolio

## Responsive Design

### Desktop (>768px)
- Cards side-by-side
- 380px width, 480px height
- 2rem gap between cards
- Large typography (4rem)

### Mobile (≤768px)
- Cards stacked vertically
- Full width cards
- 320px height
- 1.5rem gap
- Smaller typography (2.5rem)

## Customization Guide

### Change Typing Text
Edit the `lines` array in `IntroSequence` component:
```javascript
const lines = [
    "Your First Line",
    "Your Second Line."
];
```

### Change Images
Replace Unsplash URLs with your own:
```javascript
// Professional Card
src="your-professional-image.jpg"

// Personal Card
src="your-personal-image.jpg"
```

### Adjust Timing
```javascript
// Character typing speed
setTimeout(typeText, 80); // 80ms per character

// Pause between lines
setTimeout(() => { ... }, 1200); // 1200ms

// Fade out duration
transition={{ duration: 0.6 }} // 600ms
```

### Card Actions
Modify `handleCardClick` function:
```javascript
const handleCardClick = (type) => {
    if (type === 'professional') {
        onComplete(); // Show portfolio
    } else {
        window.location.href = '/personal-page'; // Your URL
    }
};
```

## CSS Classes Reference

### Main Container
- `.intro-overlay` - Full screen overlay
- `.intro-text-container` - Centers typing text
- `.choice-container` - Holds both cards

### Typography
- `.intro-typed-text` - Main text styling
- `.intro-cursor` - Blinking cursor animation
- `.choice-label` - Card title text
- `.choice-subtitle` - Card subtitle text

### Cards
- `.choice-card` - Individual card wrapper
- `.choice-overlay` - Hover overlay with gradient
- `.professional` - Professional card modifier
- `.personal` - Personal card modifier

### Utilities
- `.intro-skip-button` - Skip button styling
- `.fade-out` - Fade out animation class
- `.show` - Show animation class

## Browser Compatibility
- ✅ Chrome 90+
- ✅ Firefox 88+
- ✅ Safari 14+
- ✅ Edge 90+

## Accessibility
- Keyboard navigable (Tab to skip button)
- Semantic HTML structure
- Alt text on images
- Focus states on interactive elements

## File Size Breakdown
- CSS: ~3KB
- JavaScript: ~2KB
- Total: ~5KB (excluding images)

## Future Enhancements (Optional)
- [ ] Add sound effects for typing
- [ ] Add particle effects on card hover
- [ ] Save user choice in localStorage
- [ ] Add more card options (3-4 pathways)
- [ ] Add video backgrounds to cards
- [ ] Implement progress bar for typing
- [ ] Add keyboard shortcuts (1/2 for card selection)

## Testing Checklist
- [x] Typing animation plays smoothly
- [x] Cards fade in after typing completes
- [x] Hover effects work correctly
- [x] Skip button functions properly
- [x] Mobile responsive layout works
- [x] Images load properly
- [x] Transitions are smooth (60fps)
- [x] No console errors
- [x] Body scroll locked during intro
- [x] Portfolio fades in after card click

## Credits
- Design Inspiration: Apple, Stripe, Linear
- Images: Unsplash (to be replaced with custom images)
- Typography: SF Pro Display (system font)
- Animation: Framer Motion
