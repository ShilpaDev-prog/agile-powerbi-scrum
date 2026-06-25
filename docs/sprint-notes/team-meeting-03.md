# Team Meeting 03 Notes (Sprint 1)

**Date:** 19/06/2026
**Project:** DataLens Streaming
**Client:** StreamFlix
**Meeting purpose:** Dataset Review & Data Exploration

This third team meeting was facilitated by the Product Owner to review and explore the newly received datasets (`Users.csv` and `Ratings_Dataset.csv`) to support Sprint 1 activities and prepare recommendations for schema design.

## Meeting Agenda

The team followed a structured agenda to assess the newly acquired data files.

- Review `Users.csv` and `Ratings_Dataset.csv` structure
- Identify keys and establish table relationships
- Assess overall data quality and completeness
- Capture critical observations and underlying assumptions
- Recommend database schema design considerations

## Dataset Overview & Structure

The team reviewed the structural composition and volume of the provided datasets.

- **`Users.csv`**: Contains **6,040 records**
- **`Ratings_Dataset.csv`**: Contains **10,000 records**

### Key Definitions & Relationships
**Primary Keys Identified**

- `UserID` was identified as the Primary Key in `Users.csv`
- `RatingID` was identified as the Primary Key in `Ratings_Dataset.csv`

**Table Relationships**

- `Ratings.UserID` -> `Users.UserID`
- `Ratings.MovieID` -> `Movies.MovieID`

**Relationship Types**

- **Users to Ratings**: One-to-Many (1 -> N)
- **Movies to Ratings**: One-to-Many (1 -> N)

## Data Quality Assessment

A preliminary exploration of the fields indicated strong data hygiene in the following areas.

- **Missing Values**: No missing values were identified in the reviewed fields
- **Duplicates**: No duplicate full rows were detected within either dataset
- **Value Range**: Rating values fall entirely within the expected range of **1–5**
- **Completeness**: The `Users` dataset appears fully complete across all descriptive attributes

## Key Observations & Assumptions

**Referential Integrity Issues**: Some `UserID` values present in `Ratings_Dataset.csv` do not exist in `Users.csv`. This requires immediate validation to determine whether it is a true referential integrity failure or an artifact of an incomplete data loading process.

**Timestamp Granularity**: The `Timestamp` field was found to contain a fixed, static time value (`04:32:50`). The team recommends treating this as a **date field** rather than a precise or meaningful timestamp.

**Uniqueness Constraints**: If duplicate ratings from the exact same user for the exact same movie are not expected, the team will consider implementing a uniqueness validation on the composite key `(UserID, MovieID)`.

## Recommendations for Schema Design

The team proposed moving forward with a robust dimensional data model.

1. Validate unmatched `UserID` values prior to finalising the schema structure
2. Convert the static `Timestamp` field into a simplified date-level attribute
3. Implement structural referential integrity checks
4. Enforce uniqueness constraints where business logic dictates
5. Proceed with a **Star Schema Design** organised as follows:
   - **Fact Table**: `Ratings`
   - **Dimension Table**: `Users`
   - **Dimension Table**: `Movies`

## Action Items

The following immediate actions were assigned to ensure readiness for implementation.

| Action | Owner | Due Date |
|---|---|---|
| Validate unmatched `UserID`s | Data Team | Before review session |
| Confirm `Timestamp` business rule | Product Owner | Before schema finalisation |
| Prepare draft schema model | Data Team | Sprint 1 Review |
| Document assumptions and decisions | Data Team | Sprint 1 Closure |

## Next Steps

- Finalise the ongoing data validation tasks
- Review the upcoming schema design proposal
- Confirm all listed assumptions and observations with relevant stakeholders prior to physical database implementation