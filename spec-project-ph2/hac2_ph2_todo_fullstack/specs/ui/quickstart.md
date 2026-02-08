# Frontend UI Quickstart Guide

## Prerequisites

- Node.js 20+ installed
- npm or yarn package manager
- Git for version control
- Code editor with TypeScript support

## Setup Instructions

### 1. Clone the Repository
```bash
git clone [repository-url]
cd [repository-name]
```

### 2. Install Dependencies
```bash
cd frontend
npm install
# or
yarn install
```

### 3. Configure Environment Variables
Create a `.env.local` file in the frontend directory:
```env
NEXTAUTH_URL=http://localhost:3000
NEXTAUTH_SECRET=your-secret-key-here
BETTER_AUTH_SECRET=your-better-auth-secret
BETTER_AUTH_URL=http://localhost:3001
```

### 4. Run Development Server
```bash
npm run dev
# or
yarn dev
```

Visit `http://localhost:3000` to see the application.

## Project Structure

```
frontend/
├── app/                    # Next.js App Router pages
│   ├── layout.tsx          # Root layout with theme provider
│   ├── page.tsx            # Home page
│   ├── login/              # Authentication pages
│   ├── signup/
│   └── dashboard/          # Main application pages
├── components/            # Reusable UI components
│   ├── ui/                # Generic UI components
│   ├── auth/              # Authentication-specific components
│   └── tasks/             # Task-related components
├── lib/                   # Utility functions and services
├── styles/                # Global styles and themes
└── public/                # Static assets
```

## Key Technologies

- **Next.js 16+**: React framework with App Router
- **TypeScript 5+**: Type-safe JavaScript
- **Tailwind CSS 3.x**: Utility-first CSS framework
- **Better Auth**: Authentication solution with JWT
- **React Hook Form**: Form handling and validation
- **Framer Motion**: Animation library

## Development Commands

```bash
# Run development server
npm run dev

# Build for production
npm run build

# Run linting
npm run lint

# Run tests
npm run test

# Run tests in watch mode
npm run test:watch
```

## Environment Configuration

### Required Variables
- `NEXTAUTH_URL`: Base URL for the application
- `NEXTAUTH_SECRET`: Secret for JWT encryption
- `BETTER_AUTH_SECRET`: Better Auth secret key
- `BETTER_AUTH_URL`: Better Auth service URL

### Optional Variables
- `NODE_ENV`: Set to 'production' for production builds
- `NEXT_PUBLIC_API_URL`: API base URL (defaults to relative paths)

## Authentication Flow

The application uses Better Auth for secure authentication:

1. User visits `/login` or `/signup`
2. Credentials are verified against the authentication service
3. JWT session token is created and stored securely
4. User is redirected to dashboard upon successful authentication
5. Session is validated on protected routes

## UI Component Usage

### Using Components
```tsx
import { Button, Input, TaskCard } from '@/components/ui'

// Example usage
<Button variant="primary" onClick={handleClick}>
  Click me
</Button>
```

### Component Variants
- **Button**: primary, secondary, ghost, danger
- **Input**: text, email, password, search
- **TaskCard**: default, completed, urgent, selected

## Styling Guidelines

### Color System
- Primary: `#3B82F6` (Indigo 500)
- Success: `#10B981` (Emerald 500)
- Warning: `#F59E0B` (Amber 500)
- Error: `#EF4444` (Red 500)

### Typography Scale
- Display Large: 2.5rem (40px), Weight: 700
- Heading Large: 1.5rem (24px), Weight: 600
- Body Regular: 1rem (16px), Weight: 400
- Caption: 0.75rem (12px), Weight: 400

### Spacing System
- Base Unit: 4px (0.25rem)
- Scale: 0.25rem, 0.5rem, 0.75rem, 1rem, 1.25rem, 1.5rem, 2rem

## Theming

The application supports both light and dark modes:

1. Themes are managed through CSS variables
2. System preference is detected automatically
3. Manual toggle is available in the UI
4. All components are themed consistently

### Theme Customization
```css
:root {
  --color-primary: #3B82F6;
  --color-background: #ffffff;
  --color-text: #1F2937;
}

[data-theme="dark"] {
  --color-primary: #60A5FA;
  --color-background: #111827;
  --color-text: #F9FAFB;
}
```

## Testing

### Running Tests
```bash
# Run all tests
npm run test

# Run tests with coverage
npm run test:coverage

# Run specific test file
npm run test -- [filename]
```

### Test Structure
- Unit tests for individual components
- Integration tests for component interactions
- Snapshot tests for UI consistency
- Accessibility tests for WCAG compliance

## Deployment

### Building for Production
```bash
npm run build
```

### Environment-Specific Configuration
Different configurations for development, staging, and production environments are managed through environment variables.

## Troubleshooting

### Common Issues
- If authentication fails, ensure the auth service is running
- If styles don't load, verify Tailwind CSS is properly configured
- If hot reload doesn't work, restart the development server

### Getting Help
- Check the full specification documents in `/specs/ui/`
- Consult the component documentation
- Reach out to the development team