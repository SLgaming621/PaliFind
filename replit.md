# School Lost & Found System

## Overview

A web-based lost-and-found management system designed for educational institutions. The application enables students and staff to report found items, browse lost items, submit claims, and manage the entire lost-and-found workflow through an admin interface. Built with a focus on clarity, efficiency, and ease of use following Material Design principles adapted for educational utility.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture

**Framework & Build System**
- **React** with TypeScript for type-safe component development
- **Vite** as the build tool and development server with HMR (Hot Module Replacement)
- **Wouter** for client-side routing (lightweight React Router alternative)
- **TanStack Query (React Query)** for server state management, caching, and data synchronization

**UI Component System**
- **shadcn/ui** component library using Radix UI primitives
- **Tailwind CSS** for utility-first styling with custom design tokens
- **Design system** follows "New York" variant with neutral base colors
- Custom theme configuration with CSS variables for light/dark mode support
- Component aliases configured for clean imports (`@/components`, `@/lib`, `@/hooks`)

**Key Design Patterns**
- Form management using **React Hook Form** with **Zod** validation schemas
- Reusable UI components following the compound component pattern (Radix UI)
- Client-side routing with declarative route definitions
- Optimistic UI updates and automatic cache invalidation
- Toast notifications for user feedback

**Page Structure**
- **Home**: Dashboard with statistics and recent items
- **Browse**: Filterable item listings with category/location/search filters
- **Item Detail**: Individual item view with photo carousel and claim functionality
- **Submit**: Multi-step form for reporting found items with photo uploads
- **Admin**: Protected dashboard for approving items and managing claims

### Backend Architecture

**Runtime & Framework**
- **Node.js** with **Express.js** for the REST API server
- **TypeScript** throughout for type safety across client and server
- ES Modules (ESM) used consistently across the codebase

**API Design**
- RESTful endpoints organized by resource (`/api/items`, `/api/claims`, `/api/stats`)
- JSON request/response format
- Multipart form data support for file uploads via **Multer**
- Centralized error handling and request logging middleware
- CORS and file serving configured for uploaded assets

**File Upload Strategy**
- Local filesystem storage in `/uploads` directory
- Unique filename generation using timestamps and random suffixes
- File type validation (images only: jpeg, jpg, png, gif)
- 10MB file size limit enforced at middleware level
- Static file serving with CORS headers for cross-origin requests

**Development Environment**
- Separate dev/production configurations
- Vite middleware integration for development with SSR-ready setup
- Custom logging with timestamp formatting
- Request/response capture for API debugging

### Data Layer

**Database**
- **PostgreSQL** via **Neon Database** (serverless Postgres)
- **Drizzle ORM** for type-safe database queries and schema management
- WebSocket connection support for serverless environments

**Schema Design**

*Items Table*
- Primary entity for lost-and-found items
- Fields: name, category (enum), description, location found, date found, status (pending/approved/claimed)
- Photo URLs stored as array of strings
- Finder contact information (name, contact details)
- Automatic UUID generation for primary keys
- Timestamp tracking for creation date

*Claims Table*
- One-to-many relationship with items (multiple claims per item)
- Claimer information: name, email, phone
- Description field for claim verification
- Status tracking (pending/approved/rejected)
- Cascade delete when parent item is removed

**Category System**
- Predefined categories as PostgreSQL enum: electronics, clothing, books, accessories, keys, water-bottles, sports-equipment, other
- Category badges displayed throughout UI with human-readable labels

**Status Workflow**
- Items: pending → approved → claimed (linear progression)
- Claims: pending → approved/rejected (branch workflow)
- Admin approval required before items appear in public listings

**Data Access Pattern**
- Repository pattern via `DatabaseStorage` class implementing `IStorage` interface
- Separation of concerns between routes, storage layer, and database client
- Drizzle relations for automatic join queries
- Descending sort by creation date for recency-based displays

### External Dependencies

**UI Component Libraries**
- **Radix UI** primitives (22+ components): dialogs, dropdowns, forms, navigation, popovers, etc.
- **Lucide React** for consistent icon system
- **cmdk** for command palette functionality
- **date-fns** for date formatting and manipulation
- **class-variance-authority** for variant-based component styling
- **tailwind-merge** and **clsx** for conditional className management

**Form & Validation**
- **react-hook-form** for performant form state management
- **zod** for runtime schema validation
- **@hookform/resolvers** for integrating Zod with React Hook Form
- **drizzle-zod** for generating Zod schemas from Drizzle tables

**Database & ORM**
- **@neondatabase/serverless** for Neon Postgres connection
- **drizzle-orm** for queries and schema definition
- **drizzle-kit** for migrations and schema pushing
- **ws** (WebSocket) for serverless database connections

**File Handling**
- **multer** for multipart/form-data file uploads
- **@types/multer** for TypeScript definitions

**Development Tools**
- **@replit/vite-plugin-runtime-error-modal** for error overlays
- **@replit/vite-plugin-cartographer** and **@replit/vite-plugin-dev-banner** for Replit integration
- **tsx** for TypeScript execution in development
- **esbuild** for production builds

**Build Configuration**
- PostCSS with Tailwind CSS and Autoprefixer
- Path aliases for clean imports
- Separate client and server build outputs
- Static asset handling for uploads directory