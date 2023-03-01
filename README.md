# Niyo-Final-Project
Final project dataset, analysing Netflix Movies and TV shows scrapped from IMDB.
This data frame had 9 columns ('MOVIES', 'YEAR', 'GENRE', 'RATING', 'ONE-LINE', 'STARS', 'VOTES', 'RunTime', 'Gross') and 9999 rows.

*PART 1 - DATA CLEANING USING PYTHON* 

Initial-Data-Cleaning-using-Python file

I started Data cleaning with Python on Google colab and mainly used pandas to clean up the dataset.

I imported the necessary dataframe and assigned it to a variable, df2. From initial analysis of the data, I noticed a few things:

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
