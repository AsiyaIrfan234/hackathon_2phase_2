# Data Model for Frontend UI Specification

## Task Entity

### Fields
- `id`: string (UUID) - Unique identifier for the task
- `title`: string (required, max 255 characters) - Task title/description
- `description`: string (optional, max 1000 characters) - Detailed task description
- `completed`: boolean - Completion status
- `priority`: enum ('low', 'normal', 'high', 'urgent') - Task priority level
- `dueDate`: Date (optional) - Deadline for the task
- `createdAt`: Date - Timestamp of creation
- `updatedAt`: Date - Timestamp of last update
- `userId`: string (UUID) - Reference to the user who owns the task
- `categoryId`: string (UUID, optional) - Category classification
- `tags`: array<string> (optional) - Array of tag strings for categorization

### Relationships
- One User to Many Tasks (user has many tasks)
- One Category to Many Tasks (category has many tasks)
- Many Tasks to Many Tags (tasks can have multiple tags)

### Validation Rules
- Title must be 1-255 characters
- Description must be ≤ 1000 characters if provided
- Due date must be in the future if provided
- Priority must be one of the allowed enum values
- CreatedAt must be set on creation and immutable
- UpdatedAt must update on every modification

### State Transitions
- New → Active (on creation)
- Active ↔ Completed (toggle complete/incomplete)
- Active → Archived (when moved to archive)
- Completed → Deleted (after archival period)

## User Entity

### Fields
- `id`: string (UUID) - Unique identifier for the user
- `email`: string (required, unique) - User's email address
- `name`: string (required, max 100 characters) - User's display name
- `avatar`: string (optional) - URL to user's avatar image
- `createdAt`: Date - Account creation timestamp
- `updatedAt`: Date - Last account update timestamp
- `lastLoginAt`: Date (optional) - Last login timestamp
- `preferences`: object - User preferences including theme, notification settings

### Relationships
- One User to Many Tasks (user owns many tasks)
- One User to Many Categories (user creates many categories)

### Validation Rules
- Email must be a valid email format
- Email must be unique across all users
- Name must be 1-100 characters
- CreatedAt must be set on creation and immutable

## Category Entity

### Fields
- `id`: string (UUID) - Unique identifier for the category
- `name`: string (required, max 50 characters) - Category name
- `color`: string (required) - Hex color code for visual identification
- `userId`: string (UUID) - Reference to the user who owns the category
- `createdAt`: Date - Creation timestamp
- `updatedAt`: Date - Last update timestamp
- `sortOrder`: number - Order in which categories should be displayed

### Relationships
- One User to Many Categories (user has many categories)
- One Category to Many Tasks (category has many tasks)

### Validation Rules
- Name must be 1-50 characters
- Color must be a valid hex color format
- SortOrder must be a non-negative integer

## Tag Entity

### Fields
- `id`: string (UUID) - Unique identifier for the tag
- `name`: string (required, max 30 characters) - Tag name
- `color`: string (optional) - Hex color for tag visual representation
- `userId`: string (UUID) - Reference to the user who owns the tag
- `createdAt`: Date - Creation timestamp
- `updatedAt`: Date - Last update timestamp

### Relationships
- One User to Many Tags (user has many tags)
- Many Tags to Many Tasks (tags can belong to multiple tasks)

### Validation Rules
- Name must be 1-30 characters
- Color must be a valid hex color format if provided

## Session Entity

### Fields
- `id`: string (UUID) - Unique identifier for the session
- `userId`: string (UUID) - Reference to the user
- `token`: string (required) - Session/JWT token
- `expiresAt`: Date - Expiration timestamp
- `createdAt`: Date - Creation timestamp
- `lastAccessedAt`: Date - Last access timestamp
- `deviceInfo`: object - Information about the device used

### Relationships
- One User to Many Sessions (user can have multiple sessions)
- One Session to One User (session belongs to one user)

### Validation Rules
- Token must be properly formatted JWT
- ExpiresAt must be in the future when created
- LastAccessedAt must update with each session usage