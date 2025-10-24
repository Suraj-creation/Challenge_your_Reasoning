# Echo Chamber Buster - Design Specification

## Design Philosophy

### Visual Language
- **Minimalist Interface**: Clean, distraction-free design focusing on the conversation
- **ChatGPT-Inspired Layout**: Familiar interface patterns to reduce cognitive load
- **Typography-First**: Clear hierarchy using system fonts for optimal readability
- **Subtle Animations**: Smooth transitions that enhance rather than distract

### Color Palette
- **Light Mode**:
  - Background: #FFFFFF
  - Sidebar: #F7F7F8
  - User Messages: #10A37F
  - AI Messages: #F2F2F2
  - Text: #1A1A1A
  - Secondary Text: #6B7280

- **Dark Mode**:
  - Background: #343541
  - Sidebar: #202123
  - User Messages: #10A37F
  - AI Messages: #444654
  - Text: #ECECF1
  - Secondary Text: #8E8EA0

### Typography
- **Primary Font**: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto
- **Message Text**: 16px regular
- **Sidebar Text**: 14px regular
- **Headers**: 18px semibold
- **Code/Quotes**: 14px monospace

## Layout Structure

### Desktop Layout (1200px+)
- **Sidebar**: 260px fixed width, left-aligned
- **Main Chat**: Flexible width, centered max 800px
- **Input Area**: Full width within main chat

### Tablet Layout (768px - 1199px)
- **Sidebar**: 240px fixed width
- **Main Chat**: Flexible width, centered max 700px

### Mobile Layout (320px - 767px)
- **Sidebar**: Full-width overlay, hidden by default
- **Main Chat**: Full width, 16px horizontal padding
- **Input Area**: Full width, sticky bottom

## Component Specifications

### Sidebar
- **Background**: Dark theme (#202123) / Light theme (#F7F7F8)
- **App Title**: "Echo Chamber Buster" with subtle icon
- **New Chat Button**: Prominent, always visible
- **History List**: Last 5 conversations with topic previews
- **Theme Toggle**: Moon/Sun icon with smooth transition
- **Mobile**: Hamburger menu trigger

### Chat Messages
- **User Messages**:
  - Right-aligned, blue background (#10A37F)
  - Rounded corners, subtle shadow
  - Timestamp below message
  
- **AI Messages**:
  - Left-aligned, gray background (#444654 dark, #F2F2F2 light)
  - Rounded corners, subtle shadow
  - "Skeptos" avatar/icon
  - Timestamp below message

### Input Area
- **Textarea**: Auto-resize, placeholder "Share your take..."
- **Send Button**: Arrow icon, disabled state, loading spinner
- **Mic Button**: Placeholder for future voice input
- **Character Count**: Shows when approaching limits

### Loading States
- **Typing Indicator**: Three animated dots
- **Send Button**: Spinner animation
- **Message Fade-in**: Smooth opacity transition

## Interactive Elements

### Hover Effects
- **Buttons**: Subtle scale (1.02x) with soft shadow
- **Messages**: Slight lift with increased shadow
- **Sidebar Items**: Background color change

### Focus States
- **Input**: Blue border, subtle glow
- **Buttons**: Outline for keyboard navigation

### Animations
- **Message Appearance**: Fade up (200ms ease-out)
- **Sidebar Toggle**: Slide transition (300ms ease-in-out)
- **Theme Switch**: Cross-fade transition (400ms ease-in-out)
- **Loading Dots**: Pulsing animation (1.5s infinite)

## Responsive Behavior

### Breakpoints
- **Mobile**: 320px - 767px
- **Tablet**: 768px - 1199px
- **Desktop**: 1200px+

### Mobile Adaptations
- **Sidebar**: Overlay drawer, swipe to close
- **Input**: Larger touch targets (44px minimum)
- **Typography**: Slightly larger for readability
- **Spacing**: Increased padding for thumb navigation

## Accessibility Features

### ARIA Labels
- **Main Regions**: Proper landmark roles
- **Interactive Elements**: Descriptive labels
- **Live Regions**: Status updates for screen readers

### Keyboard Navigation
- **Tab Order**: Logical flow through interface
- **Shortcuts**: Enter to send, Escape to cancel
- **Focus Indicators**: Clear visual feedback

### Color Contrast
- **Text**: 4.5:1 minimum ratio maintained
- **Interactive Elements**: 3:1 minimum for large text
- **Dark/Light Modes**: Both WCAG AA compliant

## Error Handling UI

### API Errors
- **Connection Issues**: "Connection hiccup—retrying..."
- **Rate Limits**: "Taking a breather—be right back"
- **Invalid Responses**: "Let's try that again"

### User Feedback
- **Empty States**: Helpful prompts to get started
- **Loading States**: Clear progress indication
- **Success States**: Subtle confirmation animations