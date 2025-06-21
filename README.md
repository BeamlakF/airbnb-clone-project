# airbnb-clone-project
## Team Roles

This project simulates a professional software development environment. Below are the typical team roles involved, based on standard practices and the ITRexGroup blog. Currently, all responsibilities are handled individually.

###  Backend Developer  
Responsible for building and maintaining API endpoints, implementing authentication, business logic, and handling user interactions.

###  Database Administrator (DBA)  
Designs and manages database schemas, ensures data integrity, creates indexes for performance, and maintains backups and optimization.

###  DevOps Engineer  
Sets up Docker containers, manages deployment pipelines, configures environment variables, handles system monitoring, and ensures high availability.

###  QA Engineer  
Writes and runs automated and manual tests to ensure feature reliability, tracks bugs, and validates that new code meets project standards.

##  Technology Stack

- **Django**: A high-level Python web framework used to develop the main server-side logic and RESTful API.
- **Django REST Framework (DRF)**: Simplifies the creation of robust REST APIs by providing serialization, views, and authentication tools.
- **PostgreSQL**: A powerful, open-source relational database system used for storing and querying structured data like users, bookings, and properties.
- **GraphQL**: Offers a flexible and efficient way for clients to query only the data they need, improving performance and developer experience.
- **Celery**: Manages background tasks such as sending email notifications or processing asynchronous jobs like payments.
- **Redis**: An in-memory data store used for caching, improving API response times, and managing Celery task queues.
- **Docker**: Enables containerization of the entire app, ensuring consistent development, testing, and production environments.
- **CI/CD Pipelines**: Automatically runs tests and deploys code to ensure fast, safe integration of changes.

##  Database Design

This project uses a relational database to manage various entities and their relationships. 

###  Users
Represents both guests and hosts in the platform.
- `id`: Unique identifier for each user.
- `name`: Full name of the user.
- `email`: User’s email address (used for login).
- `role`: Indicates if the user is a guest or host.
- `created_at`: Timestamp when the user account was created.

🔗 **Relationships**:
- A user can list multiple properties (host).
- A user can make multiple bookings (guest).
- A user can leave multiple reviews.

---

###  Properties
Represents rental listings on the platform.
- `id`: Unique identifier for each property.
- `title`: Property name or title.
- `description`: Details about the property.
- `price_per_night`: Cost of booking per night.
- `owner_id`: References the user who owns the property.

🔗 **Relationships**:
- A property belongs to one user (host).
- A property can have multiple bookings and reviews.

---

###  Bookings
Represents reservations made by users.
- `id`: Unique identifier for the booking.
- `property_id`: References the booked property.
- `user_id`: References the user who made the booking.
- `start_date`: Check-in date.
- `end_date`: Check-out date.

🔗 **Relationships**:
- A booking belongs to one user and one property.
- A booking can have one associated payment.

---

###  Payments
Represents transactions for bookings.
- `id`: Unique identifier for the payment.
- `booking_id`: References the associated booking.
- `amount`: Total paid.
- `status`: Payment status (e.g., completed, pending).
- `timestamp`: When the payment was made.

🔗 **Relationships**:
- A payment is linked to a single booking.

---

###  Reviews
User feedback for properties.
- `id`: Unique identifier for the review.
- `user_id`: References the user who wrote the review.
- `property_id`: References the reviewed property.
- `rating`: Score given by the user.
- `comment`: Text review.

🔗 **Relationships**:
- A review belongs to one user and one property.

---

###  Database Optimizations

- **Indexing**: Applied to frequently queried fields such as `user_id`, `property_id`, and `booking_id` for faster lookup.
- **Caching**: Redis is used to cache frequent read operations like listing properties or retrieving user profiles to reduce database load and improve performance.

## Feature Breakdown

### API Documentation

- Uses the **OpenAPI (Swagger)** standard to document all backend endpoints.
- Built with **Django REST Framework (DRF)** to expose RESTful APIs.
- Includes **GraphQL** support for flexible and efficient client-side data querying.

---

### User Authentication

**Endpoints:**
```

POST /users/              # Register a new user
GET /users/{user\_id}/     # Get user profile
PUT /users/{user\_id}/     # Update profile
DELETE /users/{user\_id}/  # Delete user

```

**Features:**
- User registration and login
- Token-based authentication
- Profile management (view, update, delete)

---

### Property Management

**Endpoints:**
```

GET /properties/              # List all properties
POST /properties/             # Add a new property
GET /properties/{id}/         # Get property details
PUT /properties/{id}/         # Update property information
DELETE /properties/{id}/      # Delete a property

```

**Features:**
- Create, update, and delete property listings
- Associate listings with host users
- Manage visibility and accuracy of property information

---

### Booking System

**Endpoints:**
```

GET /bookings/              # List all bookings
POST /bookings/             # Create a new booking
GET /bookings/{id}/         # View booking details
PUT /bookings/{id}/         # Update a booking
DELETE /bookings/{id}/      # Cancel a booking

```

**Features:**
- Reserve properties for specific dates
- Modify or cancel existing bookings
- Manage check-in/check-out details

---

### Payment Processing

**Endpoints:**
```

POST /payments/             # Process a new payment

```

**Features:**
- Handle secure payment transactions
- Link payments to specific bookings
- Integration-ready with Stripe or PayPal

---

### Review System

**Endpoints:**
```

GET /reviews/               # View all reviews
POST /reviews/              # Submit a new review
GET /reviews/{id}/          # View a specific review
PUT /reviews/{id}/          # Edit a review
DELETE /reviews/{id}/       # Delete a review

```

**Features:**
- Guests can rate and review properties
- Users can update or remove their own reviews
- Strengthens transparency on the platform

---

### Database Optimizations

- **Indexing**: Indexes applied to commonly queried fields such as `user_id`, `property_id`, and `booking_id`.
- **Caching**: Redis is used to cache frequently requested data, reducing database load and improving response times.

---

### API Security

- **Authentication & Authorization**: Controls access to data and actions based on user identity.
- **HTTPS Enforcement**: Encrypts all traffic to protect data in transit.
- **Input Validation**: Sanitizes input to prevent SQL injection and other attacks.
- **Password Hashing**: Passwords are securely stored using cryptographic hashing.
- **Rate Limiting**: Throttles requests to prevent abuse and DoS attacks.
- **RBAC (Role-Based Access Control)**: Limits sensitive actions based on user roles (e.g., guest, host).

---

### CI/CD Pipeline Integration

- **Continuous Integration**: Automatically runs tests and checks on new code pushes.
- **Continuous Deployment**: Automatically deploys updates to staging/production environments.
- **Improved Code Quality**: Enforces formatting and linting rules across all contributors.
- **Bug Detection**: Catches bugs early with automated testing workflows.
- **Team Collaboration**: Enables frequent code merging and syncing among team members.
- **Scalability**: Designed for growth without sacrificing stability or speed.
```




