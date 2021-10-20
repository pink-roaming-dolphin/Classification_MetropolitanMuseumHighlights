## Prediction Met's Strategy for Highlighting Objects on their Website ## 

**Question / Use Case** 

 - Can I predict whether an object will be a highlight at the Met’s museum website using different classification problems?

- The goal is to help the Met see what kinds of categories they highlight the most (is it predictable) and possibly diversify their selection more broadly by tuning their parameters more in line with the museum’s mission. 

**Data** 
- Each observation is an object from the Met’s collection. 
- The target will be the column “Is Highlight” 
- Features include: 
       ['Object Number', 'Is Highlight', 'Is Public Domain', 'Object ID',
       'Department', 'Object Name', 'Title', 'Culture', 'Period', 'Dynasty',
       'Reign', 'Portfolio', 'Artist Role', 'Artist Prefix',
       'Artist Display Name', 'Artist Display Bio', 'Artist Suffix',
       'Artist Alpha Sort', 'Artist Nationality', 'Artist Begin Date',
       'Artist End Date', 'Object Date', 'Object Begin Date',
       'Object End Date', 'Medium', 'Dimensions', 'Credit Line',
       'Geography Type', 'City', 'State', 'County', 'Country', 'Region',
       'Subregion', 'Locale', 'Locus', 'Excavation', 'River', 'Classification',
       'Rights and Reproduction', 'Link Resource', 'Metadata Dte',
       'Repository'] 
- From domain knowledge, initial Features to zoom in on would be: 
Department, Period, Dynasty, Artist Role, Nationality, Object Date, Medium, Credit Line, Classification, Country, Geography
Acquired from Kaggle, but available on Met Open Access: 


**MVP Goal** 
- Build a baseline model (doing the EDA in order to decide which model might make the most sense as a baseline model here) 
