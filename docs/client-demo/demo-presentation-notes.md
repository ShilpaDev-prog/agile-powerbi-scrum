# Sprint 2 Client Demo — Presentation Notes
*Created for the Sprint 2 client demo presentation.*

## Opening and Session Goals

- Briefly restate the client context: streaming platform analytics, with a focus on understanding users, content, and ratings.
- Outline what will be covered: schema design, ERD, SQL implementation, and how the data supports the client’s business questions.
- Make the outcome explicit: “By the end, you can see what questions this database can answer and how the pieces fit together.”

## Business Questions and Data Needed

- Summarise the main questions the database is designed to support, such as who is watching what, how users rate content, and how behaviour changes over time.
- Map these questions to the core data domains: users, movies, ratings, and genres.
- Emphasise that these business questions directly shaped the database design.

## Schema Enhancements vs a Flat Table

- Describe a naive single-table approach and its limitations, including duplication, harder maintenance, and reduced flexibility.
- Explain the key benefits of the relational design:
  - Makes searching and filtering faster.
  - Prevents messy typos and inconsistencies.
  - Eliminates wasted space and duplication.
  - Supports future growth.
- Present the actual schema design: separate tables for `users`, `movies_clean`, `ratings`, `genres`, and the `movie_genres` junction table.
- Highlight specific enhancements such as `total_views`, `total_watch_time`, and a separate genres table, and explain how these improve analysis.

## ERD Walkthrough — Entities and Relationships

- Walk through the five main entities: `movies_clean`, `users`, `ratings`, `genres`, and `movie_genres`.
- Explain the relationships in simple terms:
  - Users → Ratings: one user can give many ratings.
  - Movies → Ratings: one movie can receive many ratings.
  - Movies ↔ Genres via `movie_genres`: one movie can belong to many genres, and one genre can apply to many movies.
- Link attributes back to business questions:
  - **Movies:** title, year, language, country, `total_views`
  - **Users:** demographics, subscription status, device
  - **Ratings:** rating value and timestamp
- Key talking point: “These movie attributes let us see which titles are most watched, how performance differs by country and language, and how newer vs older releases are doing.”

## Table-by-Table Design Rationale

### `movies_clean`
- Stores one row per title.
- Fields include: `MovieID`, `Movie_Title`, `Year`, `Language`, `Country`, `Total_Views`.
- Used to analyse content performance, such as top-performing titles, regional trends, and comparisons over time.

### `users`
- Stores one row per viewer.
- Fields include: `UserID`, `Age`, `Gender`, `Country`, `Subscription_Status`, `Total_Watch_Time`, `Device`.
- Used for demographic segmentation and engagement analysis.

### `ratings`
- Stores one row per rating event.
- Fields include: `RatingID`, `UserID`, `MovieID`, rating value, and `Rating_Timestamp`.
- Connects individual users with individual titles and captures feedback at a specific point in time.

### `genres` and `movie_genres`
- `genres` stores the standard genre list using `GenreID` and `Genre_Name`.
- `movie_genres` uses a composite key of `MovieID` and `GenreID` so that each movie can be linked to multiple genres without duplication.
- Together, these tables support flexible genre-based analysis.

## SQL Database Created

- Confirm that the database has been created.
- State that all tables have been implemented and populated with data.

## Visualisation Strategy

- Explain that the purpose at this stage is to show that the schema supports useful analysis, without presenting actual charts yet.
- Popular content can be explored through comparisons across titles or genres using `total_views`.
- Behaviour over time can be analysed using `Rating_Timestamp`, such as monthly average ratings.
- Audience segments can be compared across age, country, subscription status, or device using `Total_Watch_Time`.
- Keep the discussion at a high level: compare categories, observe change over time, and identify patterns relevant to stakeholder decisions.

## Closing and Feedback Prompts

- Restate what is now in place: a clean relational schema, implemented SQL tables, and imported data ready for analysis.
- Ask focused follow-up questions:
  - “Are there any additional user or movie attributes you’d like us to capture?”
  - “Which analytics questions would you like us to prototype first on top of this database?”
- Confirm that the design can be refined based on client feedback as the project develops.