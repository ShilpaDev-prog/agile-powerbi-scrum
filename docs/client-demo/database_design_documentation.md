# Database Schema Design Documentation – Streaming Platform

## 1. Overview

The database is designed to store and connect user activity data in a structured format. It follows a relational model to ensure the data is well-organized, consistent, and easy to analyse.

## 2. Tables

### Movies (`movies_clean`)
The Movies (`movies_clean`) table stores core movie information such as `MoviesID` (primary key), title, year, language, country, and `total_views`. This table is used to analyse movie metadata and viewing trends.

### Users
The Users table contains user-related information including `UserID` (primary key), age, gender, country, subscription status, total watch time, and device type. It is used to understand user demographics and engagement behaviour.

### Ratings
The Ratings table captures user feedback on movies. It includes `RatingID` (primary key), `UserID` and `MovieID` (foreign keys), rating value, and timestamp. This table connects users and movies and supports recommendation and rating analysis.

### Genres
The Genres table stores genre categories with `GenreID` as the primary key and `Genre_Name` as the attribute. It provides a standard classification system for movies.

### Movies_Genres
The Movies_Genres junction table links Movies and Genres using `MoviesID` and `GenreID` as composite primary and foreign keys. It resolves the many-to-many relationship where a movie can belong to multiple genres, and a genre can include multiple movies.

## 3. Relationships

The schema includes one-to-many relationships between Users and Ratings, and between Movies and Ratings. It also includes a many-to-many relationship between Movies and Genres, which is implemented through the Movies_Genres junction table.

## 4. Design Rationale

The separation of Ratings from Users and Movies allows scalable analysis of user behaviour and movie performance. The junction table ensures proper handling of complex relationships between movies and genres, while foreign keys maintain referential integrity across all tables.

## 5. Key Benefits

This schema supports efficient querying, scalable analytics, and recommendation system development. It ensures clean data separation, reduces duplication, and provides a strong foundation for analysing user behaviour, movie trends, and genre distribution.