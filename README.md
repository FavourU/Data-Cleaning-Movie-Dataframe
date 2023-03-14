# Data Cleaning Movie Dataframe With Python and Excel
Dataset analysing Netflix Movies and TV shows scrapped from IMDB.
This data frame had 9 columns ('MOVIES', 'YEAR', 'GENRE', 'RATING', 'ONE-LINE', 'STARS', 'VOTES', 'RunTime', 'Gross') and 9999 rows.

*PART 1 - DATA CLEANING USING PYTHON* 

Initial-Data-Cleaning-using-Python file

I started Data cleaning with Python on Google colab and mainly used pandas to clean up the dataset.

I imported the necessary dataframe (movies.csv) and assigned it to a variable, df2. From initial analysis of the data, I noticed a few things:

1. Year dates aren't in the same format. Some have only one year. Will need to remove the brackets.

2. Genre and stars have or start with '/n' which needs to be removed and there are 3 or more objects in one cell (list) which may need to be seperated for better analysis

3. Rating, Votes and Runtime have some NaN's. I can check if its necessary to remove these/ fill these

4. Gross seems to have multiple NaN's. Will need to check the percentage to see if this column can be kept

5. One- line has '/n' which needs to be removed. need to consider if this column is neccessarry


From intitial looks at the data frame, csv file, I immediately removed 'One-line' column from the data set as I couldnt see how i would use this in the analysis.

I used '.describe', '.dtypes', '.info', '.isnull().sum()' to review the data and identify steps I would have to take to clean the data.

From this, I could tell that 'Gross' columns had too many nulls and could be dropped, 'YEAR' and 'VOTES' were the wrong data types, and many columns had '/n' in their rows.

The Steps that I did on this python was to:

1. Remove the 'GROSS' and 'One-Line' columns using df2.drop
2. Remove Brackets from the year column using .str.strip('(').str.strip(')')
3. Index Year column to keep only the first year and label this column as 'Start Year' Using .str[:4]
4. Create a column titled 'Series' to differentiate the movies and the Series. Then dropped uneccessary columns Using '.str.len()' and '.where' and '.drop'
5. Removed '\n' from Genre column using str.strip('\n')
6. Added delimeters so that Stars column can be split into Actors and Directors, and then the strings in each column can be split (Using excel) Using 'str.replace' and '.loc'.

I ended this section identifying that there were 337 rows that did not have actors on them. I did not remove these as they could possibly be useful in my analysis later, and could always be removed with excel (or Python) at a later date.

I also contemplated removing the rows where the Rating, Runtime and Votes were NaN. However, that would remove nearly a third of the data and so decided to keep it as i could possibly use it later.

UPDATE: Went back to remove rows as they were disrupting Excel analysis.

*PART 2 - DATA CLEANING USING EXCEL*

I saved the dataframe as a new csv file - df3.to_csv('Visualising_Netflix.csv') - and then downloaded it to my computer so that i could work on excel. I loaded it using PowerQuery, because it was a CSV file.

The steps i took here were:

1. Removed the first column (as this was the index column, unneccessary on excel
2. Adjusted the width of the cells
3. Split the 'Genre' column using ',' delimeter
4. Noticed that some 'Start Year' values were in roman numerals e.g. 'V'. When looking at Original data, some of the dates were cut out by the splicing (indexing) done in the previous python cleaning. SO i manually inputted the necessary data in, as Excel was not allowing em to directly copy and past.
5. Split the STARS column into Actor and Director Using 1 as a delimeter
6. Used Replace function to remove unnecessary words
7. Noticed that some cells still had the word 'Directors:' in it, so removed that using the replace function
8. Split the Actor/ Director Cells into multiple columns using ',' as a delimeter
9. Renamed 'Movie' Column as "Name"

At the end of this, Dataframe has 18 columns and 8174 rows

Have decided not to use this dataframe for Project!
