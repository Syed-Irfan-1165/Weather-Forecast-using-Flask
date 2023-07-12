# Weather Portal with User Accounts and Alerts

![3d-render-weather-icons-set-sun-shining-clouds](https://github.com/Syed-Irfan-1165/Weather-Forecast-using-Flask/assets/123230589/dc605d7a-72ed-456e-900c-807208814830)


This is a Weather Portal application that allows users to register, add cities to their accounts, and receive weather alerts for specific conditions.

## Features
### User Management:
- Users can create accounts with their email address and password.
- Secure authentication methods are used for user login.

### City Management:
- Logged-in users can add multiple cities to their accounts.
- The system can automatically select the user's location as the first city.
- Users can remove cities from their accounts.

### Weather Information:
- Integrated with a weather API to retrieve weather data for added cities.
- Displays weather information including temperature, humidity, wind speed, and other relevant data.
- Regularly updates and displays accurate weather information.

### Alerts System:
- Users can set alerts for specific weather events.
- Users can define conditions for alerts, such as temperature thresholds or specific weather conditions.
- Notifies users through the portal or via email (optional) when an alert condition is met.

### Database Design:
- Utilizes SQLAlchemy as an ORM (Object-Relational Mapping) tool to interact with the database.
- Implements suitable relationships between tables to ensure data integrity and efficiency.
- Stores user information, city preferences, and weather data in the database.

## Technologies Used
- Python
- Flask
- SQLAlchemy
- Werkzeug.security
- HTML/CSS (for the front-end)
- Weather API (OpenWeatherMap)

## Weather API
To integrate weather data into your application, you can choose a suitable weather API. Some popular weather APIs include:

1. [OpenWeatherMap](https://openweathermap.org/)
   - Provides current weather data, forecasts, and historical data.
   - Offers a wide range of weather parameters and supports multiple languages.
   - Requires signing up for an API key.


## Database Schema

The Weather Portal application uses a database to store user information, city preferences, weather data, and alerts. Below is an overview of the database schema:

![Untitled](https://github.com/Syed-Irfan-1165/Weather-Forecast-using-Flask/assets/123230589/671ccf48-df0d-42eb-bf07-6ed4c9c091af)

https://dbdiagram.io/d/64a7ecea02bd1c4a5eac464a

### Users Table

- `user_id` (INT, PK, increment): Unique identifier for each user.
- `username` (VARCHAR(255), not null): User's username.
- `email` (VARCHAR(255), not null): User's email address.
- `password` (VARCHAR(255), not null): User's password.
- `created_at` (TIMESTAMP, default: `CURRENT_TIMESTAMP`): Timestamp of user creation.

### Cities Table

- `city_id` (INT, PK, increment): Unique identifier for each city.
- `city_name` (VARCHAR(255), not null): Name of the city.
- `country` (VARCHAR(255), not null): Country of the city.

### UserCities Table

- `user_id` (INT): Foreign key referencing the user who added the city.
- `city_id` (INT): Foreign key referencing the city added by the user.
- `added_at` (TIMESTAMP, default: `CURRENT_TIMESTAMP`): Timestamp of city addition.

### WeatherData Table

- `data_id` (INT, PK, increment): Unique identifier for each weather data entry.
- `city_id` (INT): Foreign key referencing the city for which the weather data is recorded.
- `temperature` (DECIMAL(5,2)): Temperature data for the city.
- `humidity` (DECIMAL(5,2)): Humidity data for the city.
- `wind_speed` (DECIMAL(5,2)): Wind speed data for the city.
- `other_weather_details` (VARCHAR(255)): Other relevant weather details.
- `recorded_at` (TIMESTAMP, default: `CURRENT_TIMESTAMP`): Timestamp of weather data recording.

### Alerts Table

- `alert_id` (INT, PK, increment): Unique identifier for each alert.
- `user_id` (INT): Foreign key referencing the user who set the alert.
- `city_id` (INT): Foreign key referencing the city for which the alert is set.
- `alert_type` (VARCHAR(255)): Type of the alert.
- `condition_operator` (VARCHAR(255)): Operator for the alert condition.
- `condition_value` (DECIMAL(5,2)): Value for the alert condition.
- `created_at` (TIMESTAMP, default: `CURRENT_TIMESTAMP`): Timestamp of alert creation.

#### Relationships

- The `Users` table has a one-to-many relationship with the `UserCities` table based on the `user_id` column.
- The `Cities` table has a one-to-many relationship with the `UserCities` and `WeatherData` tables based on the `city_id` column.
- The `Users` table has a one-to-many relationship with the `Alerts` table based on the `user_id` column.
- The `Cities` table has a one-to-many relationship with the `Alerts` table based on the `city_id` column.




