# Requirement Specifications

## 1. Authentication Service
- **Endpoint:** `POST /api/auth/register`
- **Validation:** Unique email; password length > 8.
- **Security:** Use Bcrypt for hashing.

## 2. Booking System
- **Endpoint:** `POST /api/bookings`
- **Constraint:** `check_in` must be before `check_out`.
- **Logic:** Must verify property status !== 'booked' before processing.

## 3. Payment Integration
- **API:** Stripe API SDK.
- **Status:** Must return `200 OK` on successful transaction before updating booking status.