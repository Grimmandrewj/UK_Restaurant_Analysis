# Goal
- For this project, I was tasked with evaluating restaurant rating data from the UK Food Standards Agency to assist journalists and food critis from a food magazine, *Eat Save, Love*, in order that they can decide where to focus future articles
- For Part 1, I was to set up the database and jupyter notebook to prepare for the analysis
- For Part 2, I was to Update the database with the appropriate data and datatypes
- For Part 3, I was to complete the exploratory analysis of the data


# Method
- Part 1 - Database and Jupyter Notebook Setup
  - First, I included the mongo code utilized to import the .json data and create the       database to contain the data in a markdown cell   in the jupyter notebook 
  - Then, I imported the necessary dependencies, created an instance of MongoClient,         reviewed a document from the collection to get a feel for the data, and assigned the       collection to a variable
- Part 2 - Update the Database
  - First, I created a dictionary with provided information for a new restaurant called     Penang Flavours
  - Then, I inserted the restaurant info as a new document in the collection
  - I found the BusinessTypeID for the BusinessType 'Restaurant/Cafe/Canteen' (1) and       updated the new document with this ID (as it was previously blank)
  - Then, I deleted all documents with the 'LocalAuthorityName' of Dover (994 documents)     as the magazine was not intereted in evaluating any establishments in that area
  - I then changed the datatype for the 'geocode.latitude' and '.longitude' entries for     all the documents from a String to a Double to ensure accurate datatypes
- *Note: the Jupyter Notebook for Parts 1 and 2 is titled *NoSQL_setup.ipynb*
- Part 3 - Exploratory Analysis
  - First, I again imported the necessary dependencies, created an instance of 
  MongoClient, assigned the database to a variable, reviewed the collection and assigned   it to a variable as well
  - Then, I filtered the data to find which establishments have a hygiene score equal to 
  20 (the higher the score, the worse the hygiene conditions) using query.  I confirmed 
  there were 41 establishments with a hygiene rating equal to 20
  - I then converted the results to a DataFrame for ease of review: 
  
  ![image](https://user-images.githubusercontent.com/120341249/228990957-4bc99314-811a-4e38-b67d-0dce17938513.png)

  - I then created a query to find which establishments in London have a RatingValue 
  greater than or equal to 4 using the '$regex' and '$gte' methods and displayed the 
  results in a DataFrame:
  
  ![image](https://user-images.githubusercontent.com/120341249/228991176-8728af7c-f29b-4911-a379-d0cc724eca7a.png)

  - Then, I created a query to find the top five establishments with a RatingValue of 5, 
  sorted the results by lowest hygiene score, and nearest to the Penang Flavours 
  restaurant.
  - I displayed the latitude and longitude values for the restaurant, found all 
  establishments with lat and long values within .01 of the restaurant to find the 
  nearest, and sorted by the hygiene score in ascending order.  These results were also 
  converted to a DataFrame:
  
  ![image](https://user-images.githubusercontent.com/120341249/228991502-aeccf62c-f8ea-40e9-88a7-49406c1b651d.png)

  - Finally, I created a match query and group query to determine how many 
  establishments in each local authority have a hygiene score of 0 (the best rating) 
  using the '$match' and '$group' methods.  The queries were added to a pipeline and the 
  results displayed
  - The results were then converted into a DataFrame:
  
  ![image](https://user-images.githubusercontent.com/120341249/228991627-76d90f39-cb59-4915-953f-d80f1dbfd3a5.png)
  
- *Note: the Jupyter Notebook for Part 3 is titled *NoSQL_analysis.ipynb*
  
# Summary and Results
- I was successfully able to import the .json data and create a database with the data
- I was then able to update the database with the appropriate data and convert the 
datatypes to ensure they are accurate
- I was then able to complete the exploratory analysis of the data to query the required data from the database and convert the results into corresponding DataFrames
