# nosql-challenge
## UWA Week 12 Challenge - Eat, Pray, Love 

## Instructions
The UK Food Standards Agency evaluates various establishments across the United Kingdom, and gives them a food hygiene rating. You've been contracted by the editors of a food magazine, Eat Safe, Love, to evaluate some of the ratings data in order to help their journalists and food critics decide where to focus future articles.

## Contents:  
1. [`NoSQL_setup_starter.ipynb`](https://github.com/jflengkong/nosql-challenge/blob/main/NoSQL_setup_starter.ipynb) - Jupyter Notebook database setup.
2. [`NoSQL_analysis_starter.ipynb`](https://github.com/jflengkong/nosql-challenge/blob/main/NoSQL_analysis_starter.ipynb) - Jupyter Notebook for database analysis.
3. `Resources` Folder with original [`establishments.json`](https://github.com/jflengkong/nosql-challenge/blob/main/Resources/establishments.json) file for import and analysis

## The instructions for this mini project are divided into the following subsections:
- [Part 1:](https://github.com/jflengkong/Crowdfunding_ETL_Grp_1/tree/main#Part-1-Database-and-Jupyter-Notebook-Set-Up)Database and Jupyter Notebook Set Up 
- [Part 2: ](https://github.com/jflengkong/Crowdfunding_ETL_Grp_1/tree/main#Part-2-Update-the-Database)Update the Database
- [Part 3: ](https://github.com/jflengkong/Crowdfunding_ETL_Grp_1/tree/main#Part-3-Exploratory-Analysis)Exploratory Analysis

## Part 1: Database and Jupyter Notebook Set Up
 [`NoSQL_setup_starter.ipynb`](https://github.com/jflengkong/nosql-challenge/blob/main/NoSQL_setup_starter.ipynb) was used in this part to import the provided [`establishments.json`](https://github.com/jflengkong/nosql-challenge/blob/main/Resources/establishments.json). The test `"C:\Program Files\MongoDB\Server\7.0\bin\mongod.exe" --dbpath="c:\data\db"` was actioned in Terminal prior to starting to ensure connection to MongoDB was implemented. Here the setup involved ensuring the created database loaded the data properly. 
<b> Instructions: </b> 
- List the databases you have in MongoDB. Confirm that uk_food is listed.
- List the collection(s) in the database to ensure that establishments is there.
- Find and display one document in the establishments collection using find_one and display with pprint.
- Assign the establishments collection to a variable to prepare the collection for use.

## Part 2: Update the Database
[`NoSQL_analysis_starter.ipynb`](https://github.com/jflengkong/nosql-challenge/blob/main/NoSQL_analysis_starter.ipynb) was used for this section of the challenge.
<b>Instructions: </b> 
The magazine editors have some requested modifications for the database before you can perform any queries or analysis for them. Make the following changes to the establishments collection. 
An exciting new halal restaurant just opened in Greenwich, but hasn't been rated yet. The magazine has asked you to include it in your analysis. Add the following information to the database: 
- Add the restaurant with the code provided below
- Find the BusinessTypeID for "Restaurant/Cafe/Canteen" and update the new restaurany with the BusinessTypeID found
- The magazine is not interested in any establishments in Dover, so check how many documents contain the Dover Local Authority. Then, remove any establishments within the Dover Local Authority from the database, and check the number of documents to ensure they were deleted.
- Use update_many to convert latitude and longitude to decimal numbers.
- Use update_many to convert RatingValue to integer numbers.

<b> New Restaurant information </b> 

```python
{"BusinessName":"Penang Flavours",
"BusinessType":"Restaurant/Cafe/Canteen",
    
    "BusinessTypeID":"",
    "AddressLine1":"Penang Flavours",
    "AddressLine2":"146A Plumstead Rd",
    "AddressLine3":"London",
    "AddressLine4":"",
    "PostCode":"SE18 7DY",
    "Phone":"",
    "LocalAuthorityCode":"511",
    "LocalAuthorityName":"Greenwich",
    "LocalAuthorityWebSite":"http://www.royalgreenwich.gov.uk",
    "LocalAuthorityEmailAddress":"health@royalgreenwich.gov.uk",
    "scores":{
        "Hygiene":"",
        "Structural":"",
        "ConfidenceInManagement":""
    },
    "SchemeType":"FHRS",
    "geocode":{
        "longitude":"0.08384000",
        "latitude":"51.49014200"
    },
    "RightToReply":"",
    "Distance":4623.9723280747176,
    "NewRatingPending":True
}
``` 

## Part 3: Exploratory Analysis 
Eat Safe, Love has specific questions they want you to answer, which will help them find the locations they wish to visit and avoid.

The [`NoSQL_analysis_starter.ipynb`](https://github.com/jflengkong/nosql-challenge/blob/main/NoSQL_analysis_starter.ipynb) was used for this section. 

<b> Instructions: </b> 
Use the following questions to explore the database, and find the answers, so you can provide them to the magazine editors. 
Unless otherwise stated, for each question:

1. <b> Which establishments have a hygiene score equal to 20? </b> 
    - There are <b> 41 establishments </b> which have a hygiene score equal to 20
    - Refer to [`NoSQL_analysis_starter.ipynb`](https://github.com/jflengkong/nosql-challenge/blob/main/NoSQL_analysis_starter.ipynb) to see the full list of establishments
    
2. <b> Which establishments in London have a RatingValue greater than or equal to 4? </b> 
    - There are <b>33 establishments</b> that have a RatingValue greater than or equal to 4 

5. <b>What are the top 5 establishments with a RatingValue of 5, sorted by lowest hygiene score, nearest to the new restaurant added, "Penang Flavours"?</b>
    - Volunteer
    - Atlantic Fish Bar
    - Plumstead Manor Nursery
    - Iceland
    - Howe and Co Fish and Chips - Van 17
    
7. <b>How many establishments in each Local Authority area have a hygiene score of 0? Sort the results from highest to lowest, and print out the top ten local authority areas.</b>
   - There are a total of <b>55 establishments</b> with a hygiene score of 0

| Local Authority | Establishment Count |
|-----------------|---------------------|
| Thanet          | 1130                |
| Greenwich       | 882                 |
| Maidstone       | 713                 |
| Newham          | 711                 |
| Swale           | 686                 |
| Chelmsford      | 680                 |
| Medway          | 672                 |
| Bexley          | 607                 |
| Southend-On-Sea | 586                 |
| Tendring        | 542                 |


## References 
[1] UK Food Standards Agency - [UK Food standard Agency](https://www.food.gov.uk/). (2022).

[2] UK food hygiene rating data API - [UK food Hygiene Rating](https://ratings.food.gov.uk/open-data/en-GBLinks) Contains public sector information licensed under the [Open Government Licence v3.0](https://www.nationalarchives.gov.uk/doc/open-government-licence/version/3/). Accessed Sept 9, 2022 and Sept 12, 2022 with the establishment settings as follows: longitude=51.5072, latitude=-0.1276, maxdistancelimit=4567, pagesize=10000, sortoptionkey=distance, pagenumber=(1,2,3,4,5,6,7,8). 
