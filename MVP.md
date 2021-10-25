## Predicting Highlighting (of Objects) at the Met

**Features**

Original EDA was done to figure out which features might have special importance in the model. The target (highighted or not) ratio was -  
target_ratio: 0.004147674156576373
Below are some initial plots with that ratio also shown: 
![Artist Nationality vs  Ratio in Collection](https://user-images.githubusercontent.com/81533137/138774419-8c8fb296-bc85-458a-9d1f-7bff3b6c9449.png)
![Artist Role vs  Ratio in Collection](https://user-images.githubusercontent.com/81533137/138774436-baecf602-5a9c-43a4-ab7a-dbaab0c98b5e.png)
![Classification vs  Ratio in Collection](https://user-images.githubusercontent.com/81533137/138774451-2b51142f-bf89-4cc0-a0f3-f87a9ff48d10.png)
![Object Year vs  Count in Collection](https://user-images.githubusercontent.com/81533137/138774470-9bfeac09-034c-4780-862b-a8c05bd8471e.png)

Possible features/plots included: Artist Nationality, Artist Role, Classification, Country, Culture, Department, Medium, Object Name, Object Year

After inital analysis, it was found that the 20 different departments collected data separately (with different features completely null), so the dataset was divided into 4. 

**Modern Section** 
Data was cleaned and features were engineered to get dummies for the top occuring values in each feature. The plots were done to see which values in a certain feature would make
more of an appearance in the 'highlighted' class. 

![Department Counts in Modern](https://user-images.githubusercontent.com/81533137/138775354-ff0a3d59-2885-4968-b3c9-baea322186e2.png)
![Department Ratios in Highlighted](https://user-images.githubusercontent.com/81533137/138775324-4e8d44f3-c1d2-4889-9a2f-7182153a76a6.png)
![Classification in Highlighted Modern](https://user-images.githubusercontent.com/81533137/138775081-e5c0fb14-b0e7-43a3-809d-23344efad2cc.png)
![Object Year Counts in Modern Collection](https://user-images.githubusercontent.com/81533137/138775103-812c096c-5a9d-444b-862d-9e81240d1b88.png)
Other features/plots include: 'Department', 'Object Name', 'Artist Role', 
'Artist Nationality', 'Object Date', 'Medium', 'Classification'.

**MVP** 
Features were fitted to a logistic regression model. 
Metric to look out for was selected as: PRECISION (It's fine if we predict wrong and then the object becomes a highlight; collector will be happy. 
What we don't want is predict highlighted and then get a no-highlight. aka. we like FN, we don't like FP)

Below are the initial graphs looking at precision and recall: 

![Logreg Confusion Matrix for Modern Met](https://user-images.githubusercontent.com/81533137/138776316-9509bf65-75c9-4e5b-b844-a944d9332b66.png)
![Precision and Recall Curves for Modern Met](https://user-images.githubusercontent.com/81533137/138776137-862f7913-8d15-44c1-b2c5-4df5e1d1202c.png)
![Precision-Recall Curve for Modern Met](https://user-images.githubusercontent.com/81533137/138776139-fe05db78-0a8b-4bdc-9883-86ca58b03bee.png)
![ROC curve for predicting higlighting at the Met Modern Section](https://user-images.githubusercontent.com/81533137/138776140-6a089a6f-5fea-499d-812a-6a7bd6c50250.png)

The scores are as following: 

Train score: 0.9972814588538074, Test score: 0.9970785995826571

Precision score: 1.0, Recall score: 0.1870967741935484, F1 score: 0.31521739130434784

ROC - AUC score: 0.9404540524310834



The same workflow was done to the Ancient Section, and a model was fitted as well - but at this point there is not too much of a difference between the two to report back home about yet. 

