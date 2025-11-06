# Design Guidelines: Real-Time Collaborative Text Editor

## Design Approach
**System**: Custom design drawing from Google Docs (functionality), Linear (clean aesthetics), and Notion (modern interface patterns)  
**Rationale**: Utility-focused application requiring efficiency, clarity, and distraction-free editing experience

## Core Design Principles
1. **Focus Mode**: Minimal UI chrome to maximize editing space
2. **Collaborative Clarity**: Clear visual indicators for multi-user presence
3. **Functional Hierarchy**: Editor content takes precedence over UI controls

## Layout System

### Application Structure
- **Left Sidebar** (260px fixed): Document list navigation
- **Main Editor Area** (flex-1): Full-height editing canvas with centered content
- **Top Toolbar** (56px fixed): Document title and collaboration controls

### Spacing Primitives
Use Tailwind units: **2, 3, 4, 6, 8, 12** for consistent rhythm
- Component padding: p-4, p-6
- Section spacing: gap-4, gap-6
- Editor margins: mx-auto with max-w-4xl for optimal reading width

## Typography

### Font Stack
- **Primary**: Inter (via Google Fonts CDN) - UI elements, toolbar, sidebar
- **Editor**: "SF Mono", Consolas, monospace - Code/tech aesthetic for content area

### Type Scale
- Document titles: text-2xl font-semibold (24px)
- Editor content: text-base leading-relaxed (16px, 1.625 line-height)
- Sidebar items: text-sm (14px)
- Toolbar labels: text-xs font-medium uppercase tracking-wide (12px)

## Component Library

### Document Sidebar
- **List Items**: Full-width interactive cards with document name, last edited timestamp
- **Hover State**: Subtle background shift with smooth transition
- **Active Document**: Distinct background treatment with left border accent
- **New Document Button**: Prominent at top with icon (Heroicons 'plus')
- **Empty State**: Centered message with icon when no documents exist

### Editor Canvas
- **Content Container**: max-w-4xl mx-auto, generous py-12 for breathing room
- **Textarea/ContentEditable**: Borderless, full-width, seamless appearance
- **Focus State**: No visible outline - editor is always "in focus" visually

### Toolbar Components
- **Document Title**: Inline-editable text field, large and prominent
- **User Avatars**: Stacked circles (32px) showing active collaborators (max 5 visible + count)
- **Action Buttons**: Icon-only (20px) with tooltips - Save status, Share, Settings
- **Status Indicator**: "Saving..." / "Saved" micro-text with icon

### Presence Indicators
- **Active Cursors**: Colored vertical bars with username labels (8 predefined colors cycling)
- **User List**: Compact overlay showing all active users on hover of avatar stack

### Modal Patterns
- **Share Dialog**: Centered (max-w-md), with copy-link input and access controls
- **New Document**: Simple prompt modal with auto-focused input
- **Delete Confirmation**: Minimal alert with clear action buttons

## Icons
**Library**: Heroicons (outline style via CDN)  
**Usage**: DocumentText, Plus, UserGroup, Share, Cog, Trash, Check icons

## Interaction Patterns

### Real-Time Feedback
- **Typing Indicator**: Subtle pulsing dot next to active user avatars
- **Save Status**: Auto-update in toolbar (debounced)
- **Connection Status**: Small indicator if WebSocket disconnects

### Navigation
- **Document Switching**: Click sidebar items, instant load with smooth content transition
- **Keyboard Shortcuts**: Cmd/Ctrl + N (new), Cmd/Ctrl + S (explicit save)

## Animations
**Minimal Use**: 
- Sidebar hover/active states: 150ms ease transitions
- Modal enter/exit: 200ms scale + opacity
- No scroll animations, no unnecessary motion in editor area

## Responsive Behavior
- **Desktop (1024px+)**: Full sidebar visible
- **Tablet (768-1023px)**: Collapsible sidebar (hamburger toggle)
- **Mobile (<768px)**: Hidden sidebar, full-screen editor with top nav drawer

## Accessibility
- Keyboard navigation for all document operations
- Focus indicators on interactive elements (not editor content)
- ARIA labels for icon buttons
- Sufficient contrast ratios throughout (WCAG AA minimum)

## Images
**No images required** - This is a pure utility application focused on text editing functionality. Any branding/logos would be minimal icon-based marks in the toolbar.