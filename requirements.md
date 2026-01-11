# Requirement Specifications for Airbnb Clone Backend

## 1. User Authentication
- **Objective:** Securely manage user access and identity.
- **API Endpoints:**
  - `POST /api/auth/register`: Inputs: email, password, first_name, last_name, role.
  - `POST /api/auth/login`: Inputs: email, password. Returns: JWT token.
- **Validation:** - Password must be at least 8 characters and hashed with bcrypt.
  - Email must be unique.
- **Security:** All protected routes must require a valid JWT in the Authorization header.

## 2. Property Management
- **Objective:** Enable hosts to list and manage rental properties.
- **API Endpoints:**
  - `POST /api/properties`: Inputs: name, description, location, price_per_night. (Host Only)
  - `GET /api/properties`: Inputs: query parameters for location/price filters.
- **Validation:** - `price_per_night` must be a positive decimal.
  - Required fields (name, location) cannot be empty.

## 3. Booking & Payment System
- **Objective:** Handle property reservations and financial transactions.
- **API Endpoints:**
  - `POST /api/bookings`: Inputs: property_id, start_date, end_date.
  - `POST /api/payments/charge`: Inputs: booking_id, payment_token.
- **Validation:** - System must verify that `start_date` is before `end_date`.
  - Double-booking check: Search `bookings` table for overlapping dates before confirmation.
- **Integrations:** Uses Stripe API for payment processing.