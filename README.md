# Car Rental System

This project is a simple car rental system with user management, car management, rental management, and booking management features. The system is implemented using Oracle SQL.

## Tables

The following tables are created in the `car_rental_system` schema:

- `users`
- `cars`
- `rentals`
- `locations`
- `bookings`

## Users

The `users` table stores information about the users of the system. The table has the following columns:

- `user_id`: unique identifier for each user
- `username`: unique username for each user
- `password`: password for each user
- `role`: role of the user (admin, employee, or customer)

## Cars

The `cars` table stores information about the cars available for rent. The table has the following columns:

- `car_id`: unique identifier for each car
- `brand`: brand of the car
- `model`: model of the car
- `year`: year of the car
- `available`: availability status of the car (1 for available, 0 for unavailable)

## Rentals

The `rentals` table stores information about the rentals. The table has the following columns:

- `rental_id`: unique identifier for each rental
- `user_id`: foreign key referencing the `users` table
- `car_id`: foreign key referencing the `cars` table
- `location_id`: foreign key referencing the `locations` table
- `booking_id`: foreign key referencing the `bookings` table
- `rental_date`: date when the rental started
- `return_date`: date when the rental ended
- `price`: price of the rental

## Locations

The `locations` table stores information about the locations where the cars can be rented. The table has the following columns:

- `location_id`: unique identifier for each location
- `city`: city where the location is
- `country`: country where the location is
- `street`: street address of the location
- `zip_code`: zip code of the location

## Bookings

The `bookings` table stores information about the bookings. The table has the following columns:

- `booking_id`: unique identifier for each booking
- `user_id`: foreign key referencing the `users` table
- `location_id`: foreign key referencing the `locations` table
- `car_id`: foreign key referencing the `cars` table
- `booking_date`: date when the booking was made
- `booking_status`: status of the booking (Unbooked, Booked)

## Triggers

The following triggers are created in the `car_rental_system` schema:

- `booking_status_update_trigger`: updates the `booking_status` and `booking_date` columns in the `bookings` table when they are updated
- `validate_booking_date`: validates that the `booking_date` column in the `bookings` table is not in the past when it is updated
- `io_customer_booking_update`: updates the `booking_status` and `booking_date` columns in the `customer_booking` view when they are updated
- `io_employee_booking_update`: updates the `booking_status` and `booking_date` columns in the `employee_booking` view when they are updated

## Procedures

The following procedures are created in the `car_rental_system` schema:

- `update_customer_booking_date`: updates the `booking_date` column in the `customer_booking` view for a specific car
- `check_and_unbook_cars`: updates the `booking_status` and `booking_date` columns in the `bookings` table and updates the `available` column in the `cars` table for cars that have been returned

## Scheduled Job

A scheduled job is created to run the `check_and_unbook_cars` procedure every day at a specific time.

## Usage

To use the car rental system, you can connect to the `car_rental_system` schema and perform the following operations:

- Create new users
- Update user information
- Create new cars
- Update car information
- Create new rentals
- Update rental information
- Create new bookings
- Update booking information
- Run the `check_and_unbook_cars` procedure to unbook cars that have been returned

## Permissions

The following permissions are granted to the users of the system:

- `car_rental_admin`: can perform all operations on all tables
- `car_rental_employee`: can perform all operations on the `cars` and `rentals` tables, and can view the `employee_booking` view
- `car_rental_customer`: can perform all operations on the `users` and `bookings` tables, and can view the `customer_booking` view

## Limitations

This car rental system is a simple implementation and has the following limitations:

- It does not handle multiple rentals for the same car at the same time
- It does not handle overdue rentals
- It does not handle rental discounts or promotions
- It does not handle payment processing

## Future Work

Future work for this project could include:

- Adding more advanced features, such as rental discounts or promotions
- Improving the user interface for the system
- Adding more detailed reporting and analytics capabilities
- Integrating the system with a payment processing service
