# Unlocking-the-Potential-of-Power-Query-Using-FIFA21-Datasets-for-Data-Cleaning.
![image](https://github.com/user-attachments/assets/52d0c2f3-a24e-4427-bb81-2e4c4a5f38f2)

**Introduction:**

An outstanding video game developed by EA sports with real life simulation of the football, this have provided no dulling moment for all football lovers. A prominent aspect of FIFA 21 is its comprehensive database, which encompasses player statistics, team characteristics, and match information, offering a wealth of data for analytical purposes. This database includes numerous details such as player ratings, positions, nationalities, and performance indicators, rendering it invaluable for various analytical applications, including player scouting, team management, and performance assessment. Nevertheless, similar to many real-world datasets, the data within FIFA 21 can be disorganized and inconsistent. 
Challenges such as absent values, duplicate records, and formatting issues can impede effective analysis and informed decision-making. Consequently, data cleaning is an essential process in preparing these datasets for insightful interpretation. Using power query in excel, with its intuitive interface and skillful data manipulation capabilities, is an ideal tool for this endeavor. In this guide, we will examine the FIFA 21 datasets, emphasizing prevalent data-cleaning techniques applicable in power query.
I will delve into, identifying and addressing missing data, eliminating duplicates, standardizing formats, ensuring data assessment and accuracy. By the conclusion of this guide, you will possess the expertise to convert raw FIFA 21 data into a structured, organized dataset primed for analysis, thereby enabling you to fully leverage the information available to you, for the purpose of making informed decision and having a better insight to the beauty of the game of football.

---
**Overview of the Datasets:**

The FIFA21 datasets contains 77 columns and 18,979 records of top best players around the whole world with inaccuracies, flaws, and inconsistencies ranging from the names, values, wages of players and best position of the players on pitch. Through the efficiency and powerful transformation that power query can provide it will be cleaned and prepared perfect for further analysis and insight discovery.
Due to the source and other issues of data gathering like web scrapping the FIF21 datasets suffers from irregularities and inconsistencies, some of the records are player ID, name, age, contract, wages, value, release clause, nationality, club, position, height, Loan, player position and other attribute like football skills, age, tactical player profile, skillsets, market value, fan popularity, relationship with their clubs, and performance metrics.
During my review of the datasets, I discovered the Id column do not have a unique digit count, spelling irregulates in the player names, value, wages, release clause columns containing special characters like Ã«, Ä‡, Ã¡, Ã³, Ä±, Ã¼, "â‚¬". Although some of these characters may be as a result of language. The physical assessment of players when transferred or loaned to new club’s present columns like contract which contain start/end year, height and weight of players with anomality measurements, columns like value, wage and release clause which is expected to be in currency were observed to contain symbols and letters all through the columns and some other columns like weak foot, skill moves and international Reputation with symbol like star.

![image](https://github.com/user-attachments/assets/19678999-6690-4d82-abaa-f945e0e0aa99)
*Raw data of FIFA21 datasets before loading into power query.*

![image](https://github.com/user-attachments/assets/9da741e5-afd7-424a-89f1-4332173872f2)
*After loading into power query*

**Step1: Loading the FIFA21 Datasets**

The first process was to load the datasets into power query, the best way to do this is opening a blank excel work workbook from the scratch and then proceed to clicking on the data tab from the top side of the excel interface and by the left side of the interface you will see the get data options where you can browse on the method at which you can import the dataset into power query, another way is to load the dataset through table/range option. 
The next process I took will assist me to get rid of special characters as mentioned earlier from the datasets instead using the “find and replace” feature in power query to identify the special characters and impute the correct letters. The important thing is that these special characters are consistent in replacing certain letters especially with names from Italy, Spain, Brazil and Argentina where some of the top players came from. It will be a time-consuming process of checking through 18,979 records while there is a faster way to adopt to remove the special character and at the end data quality is still maintained.
To transform the datasets from the special characters, I selected ‘65001: Unicode (UTF-8)’ as the file origin which helped to remove them. By preserving the original character encoding, the data cleaning process is simplified and the time spent resolving issues related to character encoding errors is significantly minimized. However further cleaning will still be done in other columns as all special character be present in some of the columns.

![image](https://github.com/user-attachments/assets/ea610a24-d971-474e-bd52-327b46e278a0)
*The data look much better*

**Step 2: Handling Whitespace**

After the data is loaded into the **Power Query Editor**, the whitespace in the dataset was very obvious. To handle this, the show **whitespace** option in **view tab** was unchecked so that all whitespaces in the dataset are taken care of, while the column distribution, column quality and column profile still remained unchecked. They are very useful in understanding the datasets and for data cleaning purposes because you could view the empty space in every column and also provide statistics of numerical data at a glance. The result are presented below. 

![image](https://github.com/user-attachments/assets/676a4dcc-4c5b-4775-9ff6-1da3638ffab6)
*Before checking the white space*

![image](https://github.com/user-attachments/assets/8193bbd3-b3d9-4d40-89db-ff29c17954c1)
*After unchecking the whitespace*

**Step 3: Formatting columns**

The columns were not formatted well as some of the columns contain different data types, firstly we rename the ID columns to be Player ID as it can be referenced uniquely to identify each player and will not be expected to perform any mathematical operation on it. To get the name right, a comparison was done between the player ID, Name, Long name and the Player’s URL because the player’s URL contains the player’s name and ID by checking for consistency. Using the power query editor, the function “Transform” allows you to split a column either by delimiter or Number of characters after the assessment was done, I was able to confirm that, there was an exact similarity between the columns, further decision will be made later on which name is preferrable to be dropped as I proceed in the data cleaning.

![image](https://github.com/user-attachments/assets/bde4085f-89fb-4180-99ac-99b1c6936f72)
*Rename the ID Columns to be Player ID*

![image](https://github.com/user-attachments/assets/68e06be7-2a83-46cf-9af3-11d993fc3b57)
*Splitting the player URL to extract the full name and normalize*

![image](https://github.com/user-attachments/assets/b7c3392d-f844-4256-8cac-3d43742d2235)
*After formatting of the Full Name of players*

Secondly, the OVA and POT columns represent the Overall rating and Potential rating of the players, this need to be renamed for better clarity and description.

![image](https://github.com/user-attachments/assets/d5e30d3b-1001-490c-9a25-be7c16bde211)
*Before Renaming OVA and POT Columns*

![image](https://github.com/user-attachments/assets/c1103155-0bc4-4789-9d85-53d80570a760)
*After Renaming OVA and POT Columns*

Another important column that needs to be formatted in a more explicit format is the contract column, it was observed that this column contains start/end year, loan and free agents’ status of a player. To give more clarity to the column I decided to split the columns by using the “Add Column” with conditional formatting, this have help me to separate the column respectively. Then after this was done, I renamed the column according to what is meant having contract/loan begin and contract/loan end. Following this strategy, the columns were formatted to date datatype.

![image](https://github.com/user-attachments/assets/21886af4-ef71-4abe-9089-696ed59140ab)
*contract column*


![image](https://github.com/user-attachments/assets/ddcefe95-8c5f-4e48-b7f9-16db55cc7ea1)

*The result of categorizing the contract column into loan, contract and free*



A conditional column was created for the Contract column in order to separate the Loan from the columns that contains start and end of the contract.

![image](https://github.com/user-attachments/assets/3742df42-b0a1-47e2-9eec-5d47cec8aef6)


![image](https://github.com/user-attachments/assets/b4d4849d-828e-40de-bc79-6ff0a6c3a55c)
*The above show the new column for the contract (Custom)*

The new column for the contract (Custom) was splitted by delimiter (~) using the Right most delimiter.


The next process was to get the column containing loan, I went back to the initial Contract column to extract the records containing loan using the below conditional formatting.

![image](https://github.com/user-attachments/assets/c8edb1d1-58f1-4684-b931-e4ef6a75a9a7)

The conditional columns interprets if contract column contains Loan in its value, it should be from contact else it should return empty and this generated null value for all cells not having load which is what I was trying to get.

![image](https://github.com/user-attachments/assets/36c42e22-aef3-479e-9822-1491bc3545d2)
*The column Custom.1 contain the Loan values that was separated.*


Before I proceed to getting the Loan year from the column (Custom.1), I changed the null value to none as a strategy to get the data type to be formatted as date. 

![image](https://github.com/user-attachments/assets/a6b42a71-d532-4a9b-9f86-000e760e9c4e)
*Formatting the null value by replacing it with none*


The next process was to remove **On loan** from the date which gives the below result

![image](https://github.com/user-attachments/assets/5531c650-2373-4c4a-bf5a-f8ee1a11d309)
*Result after removing on loan from the records*


I then make an assessment on the column created for the Loan year(column.1) with Loan Date End, I found that there were similarities between them. After justification I proceeded by splitting the (column.1) by delimited at each occurrence to get the year out of the column.

![image](https://github.com/user-attachments/assets/8afb2e44-919f-403f-a9fb-bb960e8eae37)
*The result of the splitting, separated the year out of the column.*


The splitted column containing contract start was merged with column containing the loan year (custom1.2) to have **Contract/Loan Start.** The column Loan Date End was splitted with (/) at Right – most in order to have the loan year end. After this was done, I merge the two column of load date End.1 which contain the year only and contract End from the initial Contract column to form **Contract/Loan End.**


![image](https://github.com/user-attachments/assets/f289d254-957e-44c4-a5b9-8793fd404b60)

Final result of the two columns of **Contract/Loan Start** and **Contract/Loan End.**

I was also able to observe that columns of contract/Loan start and Contract/loan end contained some null values this is as a result of players on free transfer due to their contract type and it is also noticed that they don’t have a club. It is normal for these columns to be null in respect to their Contract status.

**Step4: Formatting the height and Weight Column:**

The height and weight column contains data which have the same similarity in terms of formatting, starting with the height column, it contains records having cm and feet/inches has the measurement. To format the column, I chose to standardize it with the inches. This made me to firstly split the columns using “conditional columns” into two parts (if heights contain “cm” output null else give height values) having the feet/inches column and the records contain “cm” in a different column. 

![image](https://github.com/user-attachments/assets/525786d0-b29b-486f-9145-8a021a1311fe)

*splitting the columns using “Add conditional columns”*

![image](https://github.com/user-attachments/assets/e45af805-59cc-4966-abfb-7453eb66574f)

*Result obtained after splitting column to feet/inches*

To get the data ready in inches for the first column, I split the feet from the inches for example 5’12” means we have 5 feet and 12 inches, according to standard conversion 1 feet ≈ 12 inches by that ((5X12) + 12) inches = 70inches. The column containing feet/inches was also split into two using delimiter using single coat (‘), the next step is to convert the feet column into whole number in order to perform arithmetic operation on it, before having to multiply it by 12 using the Transform tab to get the multiplication from standard, after multiplying by 12, I then merge it with column containing inches already.

 ![image](https://github.com/user-attachments/assets/749f9383-beab-4145-8178-a3fb255a2ce8)
 *After multiplying by 12 and merging the columns of feet/inches*

Going back to the column containing “cm”, I removed the character “cm” using find and replace with nothing, convert the column to whole number and then multiply the records with 0.393701 (1cm ≈ 0.393701) getting the multiply tab from standard ribbon. After this was done, I merge the two columns of the first and second conversion and rename it to be the new height column.

 ![image](https://github.com/user-attachments/assets/437fc82c-761a-4fab-b5e2-33f943a0af6d)

 *Final result of height column changed to whole number*

The same process of height column was repeated for the weight column which has Kg (Kilograms)and lbs (Pound). Choose to calculate the whole weight in Kg which mean I will be multiplying by 0.453592 to convert lbs to kg. By using conditional formatting to separate the values treating them Separately and merging them together and the removing the existing column. Also formatting to whole number.

![image](https://github.com/user-attachments/assets/632301ce-932e-4752-9e91-af5684cdd593)

*Overview of the column containing “lbs” after splitting*

![image](https://github.com/user-attachments/assets/4709b209-e41a-4a6e-914c-ccf16754a79e)

*Overview of the weight column after standardization*

**Step 5: Formatting monetary columns (wages, Value, Release Clause)**

The messy records for the monetary columns were identified to be either as **“€6.8K”** or **“€6.8M”**, the symbol € indicates the euro currency which means players were paid or valued in euro currency and “K” represent Thousands (1,000) while “M” represent Millions (1,000,000). My first step to format the records was to remove the euro currency by highlighting these columns, using find and replace with nothing. The next step was to separate the columns with “K” and “M” from each other, replace **null** with **none** so I can remove the “K” from the data and then return back null by replacement. 

![image](https://github.com/user-attachments/assets/1541ca36-61e3-4076-b110-08e60fa81f50)

*Before formatting the monetary columns*

To perform arithmetic operation on the records of columns containing monetary values, some of the records contain decimal, to do this I formatted it to decimal number to retained the number before the multiplication by 1,000 for the column containing “K”. The same process was used for the columns containing character “M” and then multiplied by 1,000,000. At the end, the columns were formatted to currency since they are monetary columns.
Another method that can be used for the release clause column is to edit the steps of the value column by identifying the step from the formatting section and then edit the code which may be faster.

![image](https://github.com/user-attachments/assets/80a529a6-a80b-428c-bfbb-2d30f3fa8403)

*Process showing the method of formatting the release clause using the same formula of Value column.*

![image](https://github.com/user-attachments/assets/5ac20d29-a953-49cb-9c71-aed92ddbb355)

*Overview of the monetary columns after formatting*

**Step 6: Formatting Columns with Ratings (W/F, S/M, IR)**

Players are rated between 1 to 5, these ratings are grouped by weak foot(W/F), Skill move (S/M) and International Rating (IR), it could be observed that these columns contain star symbol in them (4★). To format these columns, I highlighted the columns one after the other, right click on the column and browse to select find and replace to replace Star with nothing and then change the data type to whole number.

![image](https://github.com/user-attachments/assets/e03d3f88-7282-4ac2-8dc0-afbd6e3cf0bc)

*Before transforming the W/F, SM and IR columns*

![image](https://github.com/user-attachments/assets/eb010ae8-b068-4271-a301-e308a46f5e7b)

*After transforming the W/F, SM and IR columns*

**Step 7: Formatting the Hits column**

The hit column includes values denoted with "K," which is formatted conditionally to identify figures representing thousands. These values should be transferred to a separate column, perform find and replace by replacing null with none, convert the column to whole number and then multiplied by 1000. Additionally, the values that do not contain "K" was extracted into a new column. Subsequently, these two columns should be combined, and the original hit column should be removed, resulting in a new merged hit column.

![image](https://github.com/user-attachments/assets/5360ed8c-e2db-4d4c-b588-c76a29f9d0fb)

*Before conversion of the Hits Column*

![image](https://github.com/user-attachments/assets/046349dd-f2fe-4403-84e6-b637cbe2d629)

*After conversion of the Hits Column*

**Step 8: Dropping of Columns**

After all data quality assessment was done on all the columns in the FIFI21 Datasets, columns not important for data manipulation and analysis were dropped from the datasets. I dropped the Name, LongName, playerURL, photoURL, columns used when formatting and standardizing the datasets. After this was done the datasets can now be used for analysis for meaningful insights and further decision making.

![image](https://github.com/user-attachments/assets/760d3cbe-5c49-4fd3-9108-f138322c9e7f)

*Overview of the cleaned FIFI21 Datasets*

**Conclusion:**

The application process of cleaning a dataset using power query in excel helps me to unlock into the potentials embedded, not only in formatting columns but also to know how effective and efficient it can handle large datasets in performing Extract, transform and Load (ETL) process, automating repetitive tasks and ensuring standardization in transforming data and its engineering capability of obtaining cleaned and accurate data for analysis. 









 

















