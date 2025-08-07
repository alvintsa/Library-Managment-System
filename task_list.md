# Library Management System - Task List

## Setup Tasks
- [ ] Create new console project
- [ ] Install Entity Framework Core packages (SQLite provider, Tools)
- [ ] Set up folder structure: Models/, Data/, Services/, Exceptions/

## Phase 1: Core Object Model (Focus: Inheritance & Polymorphism)

### Abstract Base Classes
- [ ] **Task 1.1**: Design and implement `Person` abstract class
  - Consider what properties all people share
  - Define abstract methods that subclasses must implement
  - Add a computed property for display purposes

- [ ] **Task 1.2**: Design and implement `Item` abstract class  
  - Think about what all library items have in common
  - Define abstract methods for business rules (loan periods, fees)
  - Include status tracking properties

### Concrete Implementations
- [ ] **Task 1.3**: Implement `Member` class inheriting from `Person`
  - Add membership-specific properties
  - Override abstract methods with member-specific logic
  - Implement business rules for borrowing limits

- [ ] **Task 1.4**: Implement `Librarian` class inheriting from `Person`
  - Consider what permissions a librarian needs
  - Override abstract methods appropriately

- [ ] **Task 1.5**: Implement `Book` class inheriting from `Item`
  - Add book-specific properties (ISBN, author, etc.)
  - Define book-specific loan rules
  - Override abstract methods

- [ ] **Task 1.6**: Create `Magazine` and `DVD` classes
  - Consider how their loan rules might differ from books
  - Add type-specific properties

- [ ] **Task 1.7**: Design `Loan` class for tracking borrowing
  - Think about the relationship between members, items, and loans
  - Include date tracking and fee calculation logic
  - Add computed properties for overdue status

### Validation Challenge
- [ ] **Task 1.8**: Add comprehensive validation to all models
  - Email validation, required fields, date logic
  - Consider where validation belongs (properties vs methods)

## Phase 2: Database Layer (Focus: EF Core & Relationships)

### Context Setup
- [ ] **Task 2.1**: Create `LibraryContext` inheriting from `DbContext`
  - Configure connection string for SQLite
  - Add DbSets for all your entities

- [ ] **Task 2.2**: Configure inheritance mapping in `OnModelCreating`
  - Research Table-Per-Hierarchy (TPH) pattern
  - Set up discriminators for Person and Item hierarchies

- [ ] **Task 2.3**: Configure entity relationships
  - One-to-many between Member and Loans
  - One-to-many between Item and Loans
  - Consider navigation properties

### Migration & Testing
- [ ] **Task 2.4**: Create and run your first migration
  - Use EF Tools to generate migration
  - Examine the generated SQL to understand what EF created

- [ ] **Task 2.5**: Create a simple console test
  - Add a few test records to verify your setup works
  - Query data back to confirm relationships work

## Phase 3: Service Layer (Focus: Business Logic & LINQ)

### Core Services
- [ ] **Task 3.1**: Design `LibraryService` class
  - Think about what operations a library needs
  - Consider method signatures (what parameters, return types)
  - Plan for async operations

- [ ] **Task 3.2**: Implement member registration
  - Generate membership numbers (create your own algorithm)
  - Set expiry dates, validate input
  - Handle duplicate email scenarios

- [ ] **Task 3.3**: Implement item borrowing logic
  - Validate member can borrow (not over limit, membership valid)
  - Validate item is available
  - Create loan record, update item status
  - Consider transaction boundaries

- [ ] **Task 3.4**: Implement item return logic
  - Find active loan, set return date
  - Calculate late fees if overdue
  - Update item availability
  - Handle edge cases (item already returned, etc.)

- [ ] **Task 3.5**: Add item management methods
  - Add books, magazines, DVDs to catalog
  - Update item details
  - Remove/deactivate items

### Search & Query Features
- [ ] **Task 3.6**: Implement search functionality using LINQ
  - Search items by title, author, ISBN
  - Search members by name, email, membership number
  - Practice different LINQ operators

- [ ] **Task 3.7**: Build inventory queries
  - Available items by type
  - Items currently on loan
  - Overdue items
  - Most popular items (using GroupBy)

## Phase 4: Reporting Service (Focus: Advanced LINQ)

### Report Challenges
- [ ] **Task 4.1**: Popular items report
  - Group loans by item, count frequency
  - Order by popularity
  - Include current availability status

- [ ] **Task 4.2**: Member activity report  
  - Members with most loans (historically)
  - Members with overdue items
  - Members nearing borrowing limits

- [ ] **Task 4.3**: Financial reporting
  - Calculate total outstanding late fees
  - Revenue projections based on membership renewals
  - Late fee trends over time

- [ ] **Task 4.4**: Advanced analytics
  - Average loan duration by item type
  - Peak borrowing times/seasons
  - Genre popularity analysis

### LINQ Mastery Tasks
- [ ] **Task 4.5**: Complex join operations
  - Join across multiple tables
  - Use GroupJoin for hierarchical data
  - Practice with anonymous types

- [ ] **Task 4.6**: Aggregation challenges
  - Use Sum, Average, Count, Max, Min
  - Combine with GroupBy for categorical analysis
  - Calculate running totals or moving averages

## Phase 5: Error Handling & Polish

### Custom Exceptions
- [ ] **Task 5.1**: Design custom exception hierarchy
  - Base `LibraryException` class
  - Specific exceptions for different error types
  - Include helpful error messages and context

- [ ] **Task 5.2**: Implement comprehensive error handling
  - Wrap service calls in try-catch blocks
  - Log errors appropriately
  - Provide user-friendly error messages

### User Interface
- [ ] **Task 5.3**: Build console menu system
  - Clean, intuitive navigation
  - Input validation and error recovery
  - Professional presentation of data

- [ ] **Task 5.4**: Add data seeding
  - Create sample data for testing
  - Include edge cases (overdue loans, expired memberships)

## Advanced Challenges (Optional)

### Repository Pattern
- [ ] **Task 6.1**: Implement generic repository pattern
  - Create `IRepository<T>` interface
  - Implement concrete repository classes
  - Refactor services to use repositories

### Performance Optimization
- [ ] **Task 6.2**: Optimize database queries
  - Use Include() for eager loading
  - Implement pagination for large result sets
  - Add database indexes where appropriate

### Testing
- [ ] **Task 6.3**: Write unit tests
  - Test business logic in isolation
  - Mock dependencies
  - Test edge cases and error conditions

### Architecture Improvements
- [ ] **Task 6.4**: Add dependency injection
  - Configure service container
  - Inject dependencies into classes
  - Follow SOLID principles

## Learning Checkpoints

After each phase, challenge yourself:
- Can you explain the design decisions you made?
- What would you do differently if you started over?
- How would this scale with 100,000 members and 1 million books?
- What security considerations are you missing?

## Success Criteria

You'll know you're succeeding when:
- Your code compiles and runs without errors
- You can demonstrate all core functionality
- Your LINQ queries return correct results
- You can explain the inheritance relationships
- You handle edge cases gracefully
- Your database operations are efficient

Remember: The goal isn't to copy code, it's to understand principles. Each task should make you think and research. When you get stuck, that's where the real learning happens!