# Final-project-learntrack-lms-pipeline
An end-to-end LMS batch data engineering pipeline built on Azure Databricks and Delta Lake using the Medallion Architecture. Ingests raw learner activity data to structure, clean, and materialize key business aggregates for EdTech performance tracking and optimization.
## About the Project
LearnTrack is intended to serve as a robust batch data engineering pipeline capable of providing a seamless connection between operational LMS (Learning Management System) storage and strategic business intelligence. Each day, online learning platforms create enormous amounts of transactional logs such as course enrollments, track progress logs, and test attempts. As a result, vital patterns like learner churn risk, course drop-off points, and instructor performance stay hidden without a proper analytics framework. 
The project demonstrates the effective implementation of a three-layer Medallion Architecture in Azure Databricks for the purpose of cleaning, enriching, and transforming raw operational files into analytical databases that can be used in production.

## Core Architecture & Features
# Bronze (Data Collection): 
Programmatic handling of the parameters of the data collected in the form of CSV files (learners.csv, courses.csv, enrolment_activity.csv) into unchangeable Delta Lake tables.
# Silver (Data Preparation & Improvement): 
Removal of duplicate important records, programmatic reconstruction of instructor profiles that are missing, uniformity of date formats, and SLA calculation of completion time in minutes.
# Gold (Business Analyses): 
Generated useful metrics that are ready to be used and made with the use of complex SQL window functions and CTE (window function ROW_NUMBER() is used to determine the results):
- Churn Risk of Learners: Determining the students who have not been active for $>30$ days.
- Instructor Effectiveness: Establishing ranking and assessing instructors depending on their performance in the course in terms of the number of students who completed the course and their scores.
- True Re-enrolment Detection: Recognizing the students who repeat the course several times because of its complexity.
- Course bottlenecks and ineffective courses: Detection of ineffective course organization/completion of difficult tests.

## Tech Stack
- Processing Engine: Apache PySpark (Databricks Runtime)
- Storage Layer: Delta Lake (with schema enforcement and transactional integrity)
- Data Governance: Unity Catalog Namespace  
- Analytical Queries: Spark SQL
- Language: Python & PySpark
