NewsApp Aggregator

A Spring Boot-based News Aggregator application that allows users to register, login, set news preferences, and fetch news articles from multiple categories using NewsAPI.

Features

User Registration & Authentication
Secure user registration and login with JWT-based authentication.
Preferences Management
Users can select news categories (e.g., technology, sports, health) to receive personalized news.
News Fetching
Fetches news articles based on user preferences from the NewsAPI. Returns parsed JSON objects for easy use.
Security
JWT-based stateless authentication
Passwords hashed using BCrypt
Spring Security integration
H2 In-memory Database
For quick testing and development. No external database required.
Technologies Used

Java 17
Spring Boot 3
Spring Security (JWT)
Hibernate / JPA
H2 Database
RestTemplate & Jackson for NewsAPI integration
Postman for API testing
Setup Instructions

Clone the repository
bash

CopyEdit

git clone <your-repo-url>

cd newsapp

Update NewsAPI key
Open NewsService.java and replace the placeholder with your NewsAPI key:

java

CopyEdit

private final String API_KEY = "YOUR_NEWSAPI_KEY";

Run the application
bash

CopyEdit

mvn spring-boot:run

The app runs on port 8081 (change application.properties if needed).

Test APIs using Postman
Registration

POST http://localhost:8081/api/register
Body (JSON):
json

CopyEdit

{

  "username": "yourusername",

  "password": "yourpassword"

}

Login

POST http://localhost:8081/api/login
Body (JSON):
json

CopyEdit

{

  "username": "yourusername",

  "password": "yourpassword"

}

Copy the returned JWT token for authenticated requests.
Add Preferences

POST http://localhost:8081/api/preferences/add
Headers:
pgsql

CopyEdit

Authorization: Bearer <your-token>

Content-Type: application/json

Body (JSON array):
json

CopyEdit

["technology", "sports", "health"]

Get News

GET http://localhost:8081/api/news
Headers:
makefile

CopyEdit

Authorization: Bearer <your-token>

Returns JSON news articles based on user preferences.
Notes

Make sure you have a valid NewsAPI key; otherwise, GET /api/news will return a 401 error.
Passwords are securely hashed.
CSRF is disabled for Postman testing; do not use in production as-is.
