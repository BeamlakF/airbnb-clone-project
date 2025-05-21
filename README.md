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


