# Users Model

The `Users` model is designed to manage user accounts within the system. It includes functionalities for user registration, authentication, and role management, ensuring that users have appropriate access to various features of the application.

## Users Table

### Fields

- **id**:
    - A unique identifier for each user. This number is automatically generated by the system to distinguish each user record.

- **name**:
    - A string field for the user's name. This is essential for personal identification within the system.

- **email**:
    - A unique string field for the user's email address. This serves as the primary method for user identification and communication.

- **email_verified_at**:
    - A timestamp that indicates when the user's email address was verified. This field can be null if the email has not been verified.

- **password**:
    - A hashed string field to store the user's password securely.

- **mobile**:
    - An optional string field for the user's mobile number, which can be used for additional authentication methods or notifications.

- **avatar**:
    - A nullable string field that stores the URL or path to the user's avatar image.

- **role**:
    - An enumerated field that defines the user's role within the system. Common roles include:
        - **Developer**: Full access to all features of the application.
        - **Admin**: Has administrative privileges but lacks access to settings for multilingual configurations and the design area.
        - **User**: Standard user with minimal access; permissions must be granted post account creation.

- **rememberToken**:
    - A field used for "remember me" sessions that allows users to stay logged in.

- **softDeletes**:
    - This functionality allows for "soft deletion" of user records, meaning users can be marked as deleted without being permanently removed from the database.

## User Logging

The `admin_logs` table stores logs of user activities within the application. This feature provides insight into user actions, assisting with auditing and monitoring.

### Fields

- **id**:
    - A unique identifier for each log entry.

- **user_id**:
    - A foreign key that links each log entry to the corresponding user, establishing who performed the action.

- **action**:
    - A string describing the action performed by the user (e.g., creating, updating, deleting an item).

- **loggable**:
    - This field allows for polymorphic logging, meaning various entities can be referenced in the logs by relating them to the action performed.

## Access Control

The `accesses` table facilitates fine-grained access control through the Access Control Layer (ACL). This system determines which users have access to specific features and functionalities of the application.

### Fields

- **id**:
    - A unique identifier for each access entry.

- **user_id**:
    - A foreign key reference to the `users` table, linking each access entry to a specific user.

- **route**:
    - A string representing the route or feature to which access is granted or denied. This feature centralizes control over various functionalities on the platform.

- **owner**:
    - A boolean field that indicates whether the user is the owner of a specific resource, which may grant additional permissions.

## Role Descriptions

- **Developer**:
    - Has 100% access to every aspect of the application and can manage all configurations, settings, and user permissions.

- **Admin**:
    - Can manage most features but does not have access to the settings related to multilingual site configurations and does not have access to the design area.

- **User**:
    - Initially has no access rights. Permissions must be explicitly granted after account creation, ensuring that only necessary access is provided.

---

This document outlines the structure of the `Users` model and its related tables while detailing roles, logging, and access control mechanisms. The content is tailored to be informative and easily understandable for users and developers alike.