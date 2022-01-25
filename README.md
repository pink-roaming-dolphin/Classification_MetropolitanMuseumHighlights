Blog post about project here: [Medium - Met Classification Project](https://medium.com/@zey-o/classification-project-7959901cc8ef)


## Predicting the Metropolitan Museum’s Highlighting Strategy

**Abstract** 
The goal of the project was to build a model predicting whether an object to be donated to the Metropolitan Museum of Art would be highlighted. 
The model’s use case is that it would allow a patron to assess the chances of an object that they are thinking about donating to be highlighted 
in the ‘Highlights of the Museum’ section, thereby achieving more visibility for the object (and of course, themselves). 
After trying initial models of KNN, Random Forest, CART, a Logistic Regression model was chosen, for the higher scores it yielded. 
But in the long run, we like the interpretability of this model as another possible use case would be for curators to assess 
the congruence of their curatorial choices with the overall mission of the museum. 

**Design**
The project proposes to predict the odds of being highlighted of an object that is donated to the Met. 
It focuses specifically on precision scores because a patron donating on the belief that on object will be highlighted 
would be very disappointed to find out that it is not. On the other hand, if they donate thinking that it is unlikely 
that it will get donated and yet it does, it would be a welcome surprise. So we concentrated on the reduction of FP’s to as minimum as possible. 
This meant that our TP numbers were quite low as well, so we did make slight adjustments in our thinking about our class imbalances (in the weighting) 
to bring the TP’s up a little bit. 

**Data**
The data was downloaded from [Kaggle](https://www.kaggle.com/metmuseum/the-metropolitan-museum-of-art-open-access); 
it is also readily available from the Met Museum Open Access CVS on GitHub. It has a total of 448,203 observations. 
After EDA, we found out that the 20 Departments at the Museum had different data collections systems within the departments, 
meaning the null values/ which features were filled out with data was very much dependent on the department. 
After analysis, we divided the dataset into 4 parts: 
1. Egyptian [Egyptian] - This is one department that needs a model onto itself. Department include: 'Egyptian Art'. Features include: Object ID', 'Department', 'Object Name', 'Culture', 'Country', 'Object Date', 'Medium', 'Dimensions', 'Geography Type', 'Region', 'Dynasty', 'Reign', 'Subregion', 'Locale', 'Locus', 'Excavation'.
2. Categorical [Type] - Departments include: 'American Decorative Arts', 'European Sculpture and Decorative Arts', 'Arms and Armor', 'Costume Institute', 'Islamic Art', 'Musical Instruments', 'Asian Art'. Features include: Object ID', 'Department', 'Object Name', 'Culture', 'Classification', 'Object Date', 'Medium', 'Dimensions', 'Artist Display Name' (might leave this one out eventually but let's look if there is anything here), 'Artist Role', 'Artist Nationality', 'City'.
3. Timewise Older [Ancient] - Departments include: 'Medieval Art', 'Arts of Africa, Oceania, and the Americas', 'Greek and Roman Art', 'Ancient Near Eastern Art', 'The Cloisters'. Features include: 'Object ID', 'Department', 'Object Name', 'Culture', 'Classification', 'Object Date', 'Medium', 'Dimensions'.
4. Timewise Modern [Modern]- Departments include: 'American Paintings and Sculpture', 'Modern and Contemporary Art', 'Drawings and Prints', 'Photographs', 'European Paintings', 'Robert Lehman Collection', 'The Libraries'. Features include: 'Object ID' , 'Department', 'Object Name', 'Artist Role', 'Artist Display Name' , 'Artist Nationality', 'Object Date', 'Medium', 'Classification'.

We decided to work with Group 4 (Modern) in order to build our model. This group had a total of 215,649 observations. The only numerical feature was Object Year, which had peculiar data entries, but was converted to object years assuming for example 1300 for 13th century. Our target class, “Is Highlight” was highlighly imbalance, with 750 Highlights & 214,899 Non-highlights. 
EDA was done to make sure that all the smaller values in each categorical feature was aggregated under on ‘other’ value. This selection was specifically done keeping in mind the representation in the Highlighted section, not in the overall Collection so that our model could train better. 
All the EDA was also applied to the Ancient Group and an initial baseline was run on this group. 

**Algorithms**
- KNN, Random Forest, CART and Logistic Regression models were compared. 
- Precision score was the main metric (F1 score was considered towards the end to get some extra TP); also confusion matrix & threshold curves were utilized during model tuning. 
- Class imbalances were handled both during model training through adjusting the class weights and after training but adjusting the threshold. Weight classes were tested to find the optimum class weight number. 
- Train_test_split while tuning, cross_val during model selection 

**Tools**
- Pandas & Numpy for EDA
- Matplotlib & Seaborn for Visualization 
- Scikit-Learn for Modeling

**Communication**
The project was presented with a slideshow in which the use case & model deployment were narrated. The presentation PDF can be found [here](https://github.com/zey-o/Classification_Metropolitan_Highlights/blob/main/presentation_Met_highlighting.pdf) 
