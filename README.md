# Supermarket Store Branches Sales Excel Project - Data Analytics

### **ABOUT THE PROJECT**  

This is my first data analysis project using Microsoft Excel. In here I have used the dataset from Kaggle: Supermarket Store Branches Sales <br>[Click the Kaggle link here](https://www.kaggle.com/datasets/surajjha101/stores-area-and-sales-data)

I have decided to create this project to become my first-ever built project for my Data Analyst journey. I exhibited here my newly attained Microsoft Excel knowledge. This first project will serve as my strong foundation, as I will look back at this again and again to check my progress in my journey.

To further observe what Excel skills I have unlocked I asked ChatGPT to formulate questions about my dataset.<br>
Here are the generated questions:

> **Performance Analysis**:
> 1. Which store generates the highest and lowest sales? 
> 2. What is the average store sales across all stores? 
>
> **Customer Behavior**:
> 1. Is there a correlation between daily customer count and store sales? 
> 2. How does the number of items available affect 
>    the daily customer count or store sales? 
>
> **Store Characteristics**:
> 1. Does store area influence the daily customer count or store sales? 
> 2. Which stores have the highest efficiency (sales per square foot)? 
>
> **Trends and Patterns**:
> 1. Are larger stores consistently associated with higher 
>    sales or customer traffic? 
> 2. What is the relationship between items available and sales? 
>
> **Segmentation**:
> 1. Can stores be grouped into high-performing, average, and 
>    low-performing categories based on sales or customer count? 
>
> **Optimization**:
> 1. What store characteristics (e.g., size, items available) maximize sales or 
>    customer count? 
> 2. Could specific changes (e.g., increasing store area or inventory) improve performance for 
>    underperforming stores?

### **DATASET INFORMATION** 
First of all my dataset has a columns:<br>
#### **Dataset Columns**  
- **Store ID**: This serves as identification of the stores.  
- **Store_Area**: Physical area of the store in square yards.  
- **Items_Available**: Number of different items available in the corresponding store.  
- **Daily_Customer_Count**: Average number of customers who visited the stores over a month.  
- **Store_Sales**: Sales (in US $) that the stores made.

The dataset also has a total number of 897 rows.


### **SOLVING THE *PERFORMANCE ANALYSIS* QUESTIONS**
The first question is: *Which store generates the highest and lowest sales?*<br>
The second question is: *What is the average store sales across all stores?*<br>
What I did in this question is that I've created a simple table with 3 columns and 3 rows.<br>
- Column 1 is Metric (Highest Sales, Lowest Sales, Average Store Sales)<br>
- Column 2 is Store ID (To identify which store holds the highest or lowest sales.)
- Column 3 is Sales (Putting the amount of revenue collected by that store.)

Here is the image of the table:

<p align="center">
  <img src="https://github.com/JoshCO11/Supermarket_Store_Branches_Sales_Excel_Project-Data_Analytics/blob/7d6883e0c3e667e5b2a11284fd37ea8895735365/images/Question%201/Performance_Analysis_1.PNG" alt=" Performance Analysis #1" width="800"
</p>

What I did here is that I searched for the highest and lowest sales first and put it the rows aligned to *Sales* column.<br>
The formula that I've used are the following:<br>
For the highest sales:
```
=MAX(Table1[Store_Sales])
```
For the lowest sales:
```
=MIN(Table1[Store_Sales])
```
In finding the average store sales I've used median formula here instead of average to avoid outliers.
```
=MEDIAN(Table1[Store_Sales])
```

After finding the sales, I now started looking for Store ID. The formula that I've used is the following:<br>
This formula is for finding the Store ID of the highest sales:
```
=INDEX(Table1[[Store ID ]], MATCH(MAX(Table1[Store_Sales]), Table1[Store_Sales], 0))
```
This formula is for finding the Store ID of the lowest sales:
```
=INDEX(Table1[[Store ID ]], MATCH(MIN(Table1[Store_Sales]), Table1[Store_Sales], 0))
```

That is how I've answered the questions in *Performance Analysis*.<br>
Let's go now into the second set of questions. 


### **SOLVING THE *CUSTOMER BEHAVIOR* QUESTIONS**
The first question is: *Is there a correlation between daily customer count and store sales?*

In this part I need to know if there are relationships between the two feature. So I've used the correlation formula in Excel. Then I've also used the data analysis toolpak to gather more information about the two feature relationship. After that I also created a scatter plot to visualize the relationship.

The formula in finding correlation in Excel is:
```
=CORREL(Table1[Daily_Customer_Count], Table1[Store_Sales])
```
To further understand the relationship here is the regression analysis:
<p align="center">
  <img src="https://github.com/JoshCO11/Supermarket_Store_Branches_Sales_Excel_Project-Data_Analytics/blob/e20ff4e5ee8b5f0bfde5dc41fa409b6bf68c2d17/images/Question%202/Customer_Behavior_Corr1.1.PNG" alt=" Customer Behavior #1.1" width="800"
</p>

What's important to understand in this confusing set of numbers is the Multiple R, R Square, Significance F, Coefficients, and P-value.

- **Multiple R** is just the same as the =CORR formula in Excel.
- **R Sqaure** is the proportion of the variance in the dependent variable that is predictable from the independent variables, also known as the coefficient of determination.
- **Significance F** is the overall significance of the independent variable to dependent variable. If the result is below 0.05 that means its a good model.
- **Coefficients** is the estimated values of the regression equation that quantify the relationship between each independent variable and the dependent variable.
- **Intercept** is the representation predicted value of the dependent variable when all independent variables are equal to zero.
- **P-value** When the value is less than 0.05 that means the coefficient is working and you should disregard the null hypothesis.
- **X Variable** is the independent variable. You can put the name of the column here when you included the label header in your list.

Well as you can see in this image the Multiple R is low that conveys low relationship between the two. The Significance F is about *.80* meaning it is not working well. Then for P-value the intercept value is less than 0.05 which means it is good while the variable is much higher also almost *.80* indicating no relationship, proving the null hypothesis.

Some people understand it more when it is presented visually so here is the scatter plot:
<p align="center">
  <img src="https://github.com/JoshCO11/Supermarket_Store_Branches_Sales_Excel_Project-Data_Analytics/blob/e20ff4e5ee8b5f0bfde5dc41fa409b6bf68c2d17/images/Question%202/Customer_Behavior_Corr1.PNG" alt=" Customer Behavior #1" width="800"
</p>

The almost flat trendline means there is no correlation between the Daily Customer Count and Store Sales. Probably that is because the people going in-and-out the store doesn't buy and only goes for window shopping. Also maybe the store is themed like for seasonal events, like christmas season, halloween, etc. where people doesn't neccesarily buy and use in normal days.

Now let's take a look more analysis by answer the second question: *How does the number of items available affect the daily customer count or store sales?*

In this part I've also did the same process in the number one, the only difference is the feature used. 

I checked first the correlation between the number of items and daily customer count using the formula:
```
=CORREL(Table1[Items_Available], Table1[Daily_Customer_Count])
```

Here is the regression analysis:
<p align="center">
  <img src="https://github.com/JoshCO11/Supermarket_Store_Branches_Sales_Excel_Project-Data_Analytics/blob/e20ff4e5ee8b5f0bfde5dc41fa409b6bf68c2d17/images/Question%202/Customer_Behavior_Corr2.1.PNG" alt=" Customer Behavior #2.1" width="800"
</p>

It has low Multiple R suggesting no correlation. The significance f is again greater than 0.05. The intercept p-value is the only thing that beaten the null hypothesis because the independent variable has a *0.22* significance, greater than 0.05 which is needed to suggest good correlation.

Here is the scatter plot visualization:
<p align="center">
  <img src="https://github.com/JoshCO11/Supermarket_Store_Branches_Sales_Excel_Project-Data_Analytics/blob/51193e1245b3cf39635aadf47e77a16a49f720a7/images/Question%202/Customer_Behavior_Corr_Problem2.1.PNG" alt=" Customer Behavior #2" width="800"
</p>

The low correlation relationship between the number of items available and daily customer count is not correlated because of the possibility of poor desicion making into ordering stocks of items which is not really selling that store location. That is because probably the customer is looking for something specific that cannot be found in that store. Another example also of seasonal stores which are not visited often when its not holiday. 

Here is for the correlation between the number of items and store sales.<br>
Correlation using the formula:
```
=CORREL(Table1[Items_Available], Table1[Daily_Customer_Count])
```
Here is the regression analysis:
<p align="center">
  <img src="https://github.com/JoshCO11/Supermarket_Store_Branches_Sales_Excel_Project-Data_Analytics/blob/51193e1245b3cf39635aadf47e77a16a49f720a7/images/Question%202/Customer_Behavior_Corr2.2.PNG" alt=" Customer Behavior #2.2" width="800"
</p>

It also has low Multiple R suggesting no correlation. However the significance f is under 0.05 suggesting good model. Also both intercept and independent value is under 0.05 showing that it is useful.

Here is the visual of scatter plot between number of items available and store sales:
<p align="center">
  <img src="https://github.com/JoshCO11/Supermarket_Store_Branches_Sales_Excel_Project-Data_Analytics/blob/51193e1245b3cf39635aadf47e77a16a49f720a7/images/Question%202/Customer_Behavior_Corr_Problem2.2.PNG" alt=" Customer Behavior #2.2" width="800"
</p>

The visualization show a trendline that is looks like there is somewhat a upward slope but very little, that is because of the positive significance f, which indicates good model. However its also almost flat indicating low to no correlation between the two features. 

Does that mean the store is having poor performance? The answer is no, that is because maybe the store is not related to people. Just like what I've mentioned earlier, probably the store is dedicated for seasonal events, and people don't often buy products in that store if its only regular days. Another reason is the difference between of demand and supply. The people might not buy items because of the quality of the product and miss decision of restocking tons of items instead of focusing to quality can result to this low correlation. Suggesting to avoid overstocking.













