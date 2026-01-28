# School Lost-and-Found Website - Design Guidelines

## Design Approach
**System-Based Approach**: Material Design principles adapted for educational utility. This functional web application prioritizes clarity, efficiency, and ease of use for students and staff managing lost items. Focus on clean data presentation, intuitive forms, and straightforward navigation over visual flair.

## Typography System
- **Primary Font**: Inter or Roboto via Google Fonts CDN
- **Headings**: Bold weight (700) for page titles, semibold (600) for section headers
- **Body Text**: Regular weight (400), size 16px for optimal readability
- **Labels/Metadata**: Medium weight (500), size 14px for form labels and item metadata
- **Hierarchy**: Large titles (text-3xl to text-4xl), section headers (text-xl to text-2xl), body text (text-base)

## Layout System
**Spacing Primitives**: Tailwind units of 2, 4, 6, 8, and 12 for consistent rhythm
- Component padding: p-4 to p-6
- Section spacing: space-y-8 to space-y-12
- Card gaps: gap-6
- Container max-width: max-w-7xl with px-4 to px-8

## Core Components

### Navigation
- Clean horizontal navbar with school branding (text/logo)
- Links: Home, Browse Items, Report Found Item, Admin (protected)
- Sticky positioning for accessibility across pages
- Mobile: Hamburger menu with slide-out drawer

### Home Page
- Welcome banner with concise explanation of the service
- Recent found items grid (3-4 columns on desktop, responsive to 1 column mobile)
- Quick action cards: "Report a Found Item" and "Search for Your Item"
- Statistics display: Total items found, items claimed, active listings
- Minimal decorative elements - focus on functionality

### Item Submission Form
- Single-column form layout (max-w-2xl centered)
- Form fields: Item name, category dropdown, detailed description textarea, location found, date found, finder's contact info
- Photo upload zone with drag-and-drop support and preview thumbnails
- Clear field labels above inputs
- Primary submit button at bottom
- Form validation with inline error messages

### Item Listings Page
- Sidebar filters (desktop) / collapsible filter panel (mobile)
- Filter options: Category, date range, location, keyword search
- Grid layout for items (grid-cols-1 md:grid-cols-2 lg:grid-cols-3)
- Each item card: Photo thumbnail, item name, category badge, location, date found
- "View Details" action on each card
- Pagination or infinite scroll for large datasets

### Item Detail View
- Two-column layout: Image gallery (left), item information (right)
- Photo carousel for multiple images
- Complete item details: Category, description, location found, date, item ID
- "Claim This Item" prominent button
- Breadcrumb navigation back to listings

### Claim Form
- Modal overlay or dedicated page
- Fields: Your name, contact info, description of your lost item, additional verification details
- Reference to claimed item with small thumbnail
- Submit button triggers notification to admin

### Admin Dashboard
- Protected route with basic authentication
- Tabs: Pending items, Active listings, Claim requests
- Data table view with columns: Item name, category, date submitted, status, actions
- Action buttons: Approve, Edit, Delete
- Claim request queue with approve/reject options
- Simple statistics overview

## Component Styling Patterns
- **Cards**: Rounded corners (rounded-lg), subtle shadow (shadow-md), white background, border for definition
- **Forms**: Input fields with border, focus ring, adequate padding (p-3)
- **Buttons**: Primary (solid fill), secondary (outlined), sizes (px-6 py-3 for primary actions)
- **Badges**: Small rounded pills for categories and status indicators
- **Tables**: Alternating row backgrounds, header with border-bottom
- **Modals**: Centered overlay with backdrop blur

## Icons
Use **Heroicons** via CDN for consistent iconography throughout:
- Search icon, filter icon, upload icon, user icon, location pin, calendar
- Navigation icons, action icons (edit, delete, check, close)

## Images
**Hero**: No large hero image - this is a utility application, not marketing
**Item Photos**: User-uploaded images displayed as thumbnails in grids and full-size in detail views with placeholder images for items without photos
**Placeholders**: Use simple icon or "No Image" state for items without uploaded photos

## Responsive Behavior
- Mobile-first approach
- Navigation collapses to hamburger menu
- Multi-column grids stack to single column
- Filters move to collapsible panel
- Form fields remain single column
- Admin tables become scrollable or card-based on mobile

## Accessibility
- Semantic HTML throughout
- Proper form labels and ARIA attributes
- Keyboard navigation support
- Focus indicators on all interactive elements
- Alt text for all images
- Sufficient color contrast (ensure when colors are added)

## Animations
Minimal and purposeful only:
- Smooth page transitions (fade-in)
- Filter panel slide animations
- Modal enter/exit animations
- Hover state transitions on cards and buttons (transform: scale(1.02))
- No decorative animations

**Critical**: Create a complete, professional application with all sections fully designed. Each page should feel polished and production-ready with comprehensive layouts, not minimal wireframes.