## NoSQL_Chaalenge

-----------------------------------------------------------------------------
Modules Utilized
-----------------------------------------------------------------------------
- PyMongo
- Pretty Print (pprint)
- Pandas

-----------------------------------------------------------------------------
Background
-----------------------------------------------------------------------------
The UK Food Standards Agency evaluates various establishments across the United Kingdom, and gives them a food hygiene rating. You've been contracted by the editors of a food magazine, Eat Safe, Love, to evaluate some of the ratings data in order to help their journalists and food critics decide where to focus future articles.


-----------------------------------------------------------------------------
Instructions
-----------------------------------------------------------------------------
Part 1: Database and Jupyter Notebook Set Up
1. Use NoSQL_setup_starter.ipynb for this section of the challenge.

2. Import the data provided in the establishments.json file from your Terminal. Name the database uk_food and the collection establishments. Copy the text you used to import your data from your Terminal to a markdown cell in your notebook.

3. Create an instance of the Mongo Client. Confirm that you created the database and loaded the data properly:

4. List the databases you have in MongoDB. Confirm that uk_food is listed.

5. List the collection(s) in the database to ensure that establishments is there.

6. Find and display one document in the establishments collection using find_one and display with pprint.

7. Assign the establishments collection to a variable to prepare the collection for use.



Part 2: Update the Database
1. Use NoSQL_setup_starter.ipynb for this section of the challenge.

2. The magazine editors have some requested modifications for the database before you can perform any queries or analysis for them. Make the following changes to the establishments collection:

3. An exciting new halal restaurant just opened in Greenwich, but hasn't been rated yet. The magazine has asked you to include it in your analysis. Add the following information to the database:
   
<img width="477" alt="Screenshot 2023-11-30 at 4 03 24 PM" src="https://github.com/lleiva25/NoSQL_Challenge/assets/140974405/438c6261-93c0-422c-87b9-fba35fff6d60">

4. Find the BusinessTypeID for "Restaurant/Cafe/Canteen" and return only the BusinessTypeID and BusinessType fields.

5. Update the new restaurant with the BusinessTypeID you found.

6. The magazine is not interested in any establishments in Dover, so check how many documents contain the Dover Local Authority. Then, remove any establishments within the Dover Local Authority from the database, and check the number of documents to ensure they were deleted.

7. Change the data type to the following:
        - Use update_many to convert latitude and longitude to decimal numbers.
        - Use update_many to convert RatingValue to integer numbers.



Part 3: Exploratory Analysis
Use NoSQL_analysis_starter.ipynb for this section of the challenge. Use count_documents to display the number of documents contained in the result. Display the first document in the results using pprint. Convert the result to a Pandas DataFrame, print the number of rows in the DataFrame, and display the first 10 rows. Answer the following questions:
      1. Which establishments have a hygiene score equal to 20?
      2. Which establishments in London have a RatingValue greater than or equal to 4?
            Hint: The London Local Authority has a longer name than "London" so you will need to use $regex as part of your search.
      3. What are the top 5 establishments with a RatingValue of 5, sorted by lowest hygiene score, nearest to the new restaurant added, "Penang Flavours"?
            Hint: You will need to compare the geocode to find the nearest locations. Search within 0.01 degree on either side of the latitude and longitude.
      4. How many establishments in each Local Authority area have a hygiene score of 0? Sort the results from highest to lowest, and print out the top ten local authority areas.
            Hint: You will need to use the aggregation method to answer this.
            
<img width="203" alt="Screenshot 2023-11-30 at 4 08 54 PM" src="https://github.com/lleiva25/NoSQL_Challenge/assets/140974405/2a4f50e7-364b-4734-85d6-4b9751761f9b">


-----------------------------------------------------------------------------
Notes
-----------------------------------------------------------------------------
- RatingValue refers to the overall rating decided by the Food Authority and ranges from 1-5. The higher the value, the better the rating.
          - Note: This field also includes non-numeric values such as 'Pass', where 'Pass' means that the establishment passed their inspection but isn't given a number rating. We will coerce non-numeric values to nulls during the database setup before converting ratings to integers.
  
- The scores for Hygiene, Structural, and ConfidenceInManagement work in reverse. This means, the higher the value, the worse the establishment is in these areas.

-----------------------------------------------------------------------------
