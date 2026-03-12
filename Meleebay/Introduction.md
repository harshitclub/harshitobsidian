## 1. Product Name

API Tracker

## 2. Product Type

Developer productivity tool  
Software as a Service (SaaS) web application

## 3. Product Overview

API Tracker is a web application designed to help developers **plan, organize, and monitor APIs during backend development**.

When building backend systems, developers usually work with dozens or even hundreds of APIs across multiple modules such as authentication, users, admin, payments, and system services. Developers often track these APIs manually using spreadsheets, notes, or general-purpose workspace tools. These methods are not optimized for backend development workflows and become difficult to maintain as projects grow.

API Tracker provides a **structured environment specifically designed for organizing APIs and tracking their development lifecycle**.

The product focuses on **API planning and development tracking**, not API testing or request execution.

# 4. Problem Statement

Backend development requires developers to keep track of many APIs across different modules and services. Managing this information manually leads to several challenges.

Common issues developers face:
- APIs scattered across different notes or tools
- No clear system for organizing APIs by module
- Difficulty tracking which APIs are implemented
- No visibility into testing status
- Hard to maintain backend architecture as projects scale

Most existing tools solve different problems:

| Tool Category            | Purpose                            |
| ------------------------ | ---------------------------------- |
| API clients              | API request testing                |
| Documentation tools      | Public API reference documentation |
| Project management tools | General task tracking              |

None of these tools are built specifically to **track APIs as development entities during backend implementation**.

# 5. Solution

API Tracker provides a structured system where developers can define and manage APIs as **organized records within a project**.

Developers can:
- Define APIs as structured entries
- Organize APIs into modules
- Track implementation progress
- Track testing status
- Maintain visibility over backend architecture

The system acts as a **backend API planning and tracking platform**.

# 6. System Structure

The product organizes data using a hierarchical structure.

**Structure:**
Workspace  
→ Project  
→ Module  
→ API Registry

**Description of each layer:**

**Workspace**  
A user’s primary environment where development projects are organized.

**Project**  
Represents a backend system or application.

**Examples:**
- Learning Management System Backend
- Ecommerce Backend
- Social Platform Backend

**Module**  
A logical grouping of APIs within a project.

**Examples:**
- Authentication
- Users
- Admin
- Payments
- Notifications

API Registry  
A structured table that stores API records for a module.

Each row represents a single API.

# 7. API Registry Fields

Each API entry contains a set of default fields used to describe the endpoint and track its development status.

Default fields include:

| Field                   | Description                                         |
| ----------------------- | --------------------------------------------------- |
| API Name                | Human-readable name of the API                      |
| Endpoint Path           | URL route of the API                                |
| HTTP Method             | GET, POST, PATCH, DELETE                            |
| Authentication Required | Indicates whether authentication is needed          |
| Access Level            | Defines access scope such as Public, User, or Admin |
| Development Status      | Current implementation status                       |
| API Version             | Version identifier (for example v1, v2)             |
| Testing Status          | Indicates whether the API has been verified         |
| Notes                   | Optional notes for developers                       |
| Created Date            | Timestamp when the API entry was created            |

Example entry:

|API Name|Endpoint|Method|Status|
|---|---|---|---|
|User Signup|/api/v1/users/signup|POST|Completed|
|User Login|/api/v1/users/login|POST|Completed|
|Get Profile|/api/v1/users/me|GET|In Progress|


# 8. Custom Fields

While the system provides a standard set of fields, different projects may require additional metadata for APIs. To support this flexibility, API Tracker allows users to **create custom fields** within an API registry.

Custom fields allow teams to extend the table structure based on their specific development needs.

Examples of custom fields:

|Field Example|Purpose|
|---|---|
|Request Body Schema|Store request payload structure|
|Response Schema|Define response format|
|Rate Limit|Define API request limits|
|Owner|Developer responsible for the API|
|Priority|Development priority level|
|Estimated Completion|Planned completion timeline|
|Service Name|Microservice that owns the API|

Custom fields may support different data types, such as:

Text  
Number  
Boolean  
Selection list  
Date

This flexible field system allows each project to **adapt the API registry to its own architecture and workflow**.

# 9. Development Status Tracking

Each API entry includes a development lifecycle status.

Typical states include:

Not Started  
In Progress  
Completed  
Deprecated

This allows developers to track backend implementation progress across the system.

# 10. Testing Status Tracking

Testing status indicates whether the API has been verified during development.

Example states:

Not Tested  
Manually Verified  
Integration Tested  
Production Ready

This helps maintain visibility into API reliability before deployment.

# 11. API Organization

Projects are divided into modules to reflect backend architecture.

Example structure:

Project: Learning Platform Backend

Modules:

Authentication APIs  
User Management APIs  
Admin APIs  
System APIs

Each module contains its own API registry.

This structure helps mirror how backend systems are typically designed.

# 12. Filtering and Sorting

The API registry allows developers to filter and sort APIs based on field values.

Example filters:

Show APIs that are not tested  
Show APIs that are still in development  
Show APIs requiring authentication  
Show APIs belonging to the admin access level

Filtering helps developers manage large API collections efficiently.

# 13. Templates

To accelerate project setup, the system provides predefined templates that include common module structures and default fields.

Example template structure:

Authentication APIs  
User Management APIs  
Administrative APIs  
System APIs

Developers can modify templates to fit the needs of their project.

# 14. Target Users

Primary users:

Backend developers  
Full stack developers  
Startup engineers  
Freelance developers building backend systems

Secondary users:

Engineering teams  
Technical leads  
Backend architects

# 15. Minimum Viable Product (MVP)

The first version of API Tracker includes the following capabilities:

User authentication  
Workspace creation and management  
Project creation  
Module organization  
API registry system  
Default API fields  
Custom field support  
Development status tracking  
Testing status tracking  
Filtering and sorting

These features provide a complete environment for managing APIs during backend development.

# 16. Future Expansion

Potential future improvements include:

Team collaboration capabilities  
API progress dashboards  
API dependency visualization  
Automatic API documentation generation  
Integration with version control systems  
Automatic API detection from backend frameworks

These features could evolve the system into a collaborative backend development platform.

# 17. Product Value

API Tracker provides a structured solution for managing APIs during backend development.

Key benefits include:

Improved API organization  
Clear visibility of development progress  
Structured backend planning  
Reduced complexity when managing large API systems

The product aims to become a **dedicated API tracking and planning platform for backend engineers**.