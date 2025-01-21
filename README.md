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

What's important to understand in this confusing set of numbers is the Multiple R, R Square, Significance F, Coefficients, and P-value. You can access this using Data Analysis Toolpak in Excel. 

- **Multiple R** is just the same as the =CORR formula in Excel.
- **R Sqaure** is the proportion of the variance in the dependent variable that is predictable from the independent variables, also known as the coefficient of determination.
- **Significance F** is the overall significance of the independent variable to dependent variable. If the result is below 0.05 that means its a good model.
- **Coefficients** is the estimated values of the regression equation that quantify the relationship between each independent variable and the dependent variable.
- **Intercept** is the representation predicted value of the dependent variable when all independent variables are equal to zero.
- **P-value** When the value is less than 0.05 that means the coefficient is working and you should disregard the null hypothesis.
- **X Variable** is the independent variable. You can put the name of the column here when you included the label header in your list.

Well as you can see in this image the Multiple R is low that conveys low relationship between the two. The Significance F is about *.80* meaning it is not working well. Then for P-value the intercept value is less than 0.05 which means it is good while the variable is much higher also almost *.80* indicating no relationship, proving the null hypothesis.

Some people understand it more when it is presented visually, so here is the scatter plot:
<p align="center">
  <img src="https://github.com/JoshCO11/Supermarket_Store_Branches_Sales_Excel_Project-Data_Analytics/blob/e20ff4e5ee8b5f0bfde5dc41fa409b6bf68c2d17/images/Question%202/Customer_Behavior_Corr1.PNG" alt=" Customer Behavior #1" width="800"
</p>

The almost flat trendline means there is no correlation between the Daily Customer Count and Store Sales. Probably that is because the people going in-and-out the store doesn't buy and only goes for window shopping. Also maybe the store is probably themed like store that is for seasonal events, like christmas season, halloween, etc. where people doesn't neccesarily buy items that can be used in normal days.

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

The low correlation relationship between the number of items available and daily customer count is not correlated because of the possibility of poor desicion making of the store owner into ordering stocks of items which is not really selling in that store location. That is because probably the customer is looking for something specific that cannot be found in that store. Another example also of seasonal stores which are not visited often when its not holiday. 

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

The visualization show a trendline that looks like there is somewhat a upward slope but very little, that is because of the positive significance f, which indicates good model. However, its also almost flat indicating low to no correlation between the two features. 

Does that mean the store is having poor performance because the items available is not showing high correlation to sales? The answer is no, that is because maybe the store is not relevant to people. Just like what I've mentioned earlier, probably the store is dedicated for seasonal events, and people don't often buy products in that store if its regular days. Another reason is the difference between of demand and supply. The people might not buy items because of the quality of the product, indicating there could be also wrong decision making of restocking tons of items instead of focusing to quality can result to this low correlation. Suggesting to avoid overstocking and monitor the store's selling products to avoid cost waste. 


Now we're done with second set of questions, let's go with the third set of questions.

### **SOLVING THE *STORE CHARACTERISTICS* QUESTIONS**

The first question is: *Does store area influence the daily customer count or store sales?*

On what I did here is that I also answered it by using the *=CORR* formula in Excel and then I've created a scatter plot with trendline to be able to understand it more visually.

I analyzed Store Area and Daily Customer Count relationship:
```
=CORREL(Table1[Store_Area],Table1[Daily_Customer_Count])
```
The result is *-0.04* meaning there is a negative correlation. This is not a good result because it means one variable increases while the other variable decreases. You can visualize it more with this image.

<p align="center">
  <img src="https://github.com/JoshCO11/Supermarket_Store_Branches_Sales_Excel_Project-Data_Analytics/blob/c6f84fe64d3687e855e02d23de6e0b21bd193f04/images/Question%203/Store_Characteristics_1.PNG" alt="Store Characteristics #1" width="800"
</p>

In this visualization we can see that when the Store Area increases the Daily Customer Count decreases. I can tell it that way because the slope is downward. It's decreasing greatly but still you can say that they are not greatly correlated and has no good relationship with each other. There could be different reasons why this is happening. 

First reason could be, the store is mainly not encouraging normal day-to-day customers. The items for sale might be too expensive for normal customers, hence, the reason of the store being large. Another reason could be, the store has only few items inside, this is also related to my first reason because probably the items are only specified for specific demographics. Indicating mismatching of target customers in the location area.

Let's now analyze correlation between Store Area and Store Sales. I also did the same process in here with the formula:
```
=CORREL(Table1[Store_Area],Table1[Store_Sales])
```
It's also low but this time it's not negative. Let's check the scatter plot.

<p align="center">
  <img src="https://github.com/JoshCO11/Supermarket_Store_Branches_Sales_Excel_Project-Data_Analytics/blob/c6f84fe64d3687e855e02d23de6e0b21bd193f04/images/Question%203/Store_Characteristics_1.1.PNG" alt="Store Characteristics #1.1" width="800"
</p>

The slope here is not in downward motion, its somewhat increased, showing an upward motion. As you can see most of the stores are around 1,200 to 1,800 size and the store sales is about $40,000 and $80,000. But to answer the question does store area influence store sales? The answer is somewhat yes. This is probably, larger stores are offering more expensive items. These expensive items could be branded items that you cannot find in local stores. Another reason is that larger stores offer more than selling products. Larger stores can offer satisfaction like playground for kids or other areas that could make the customer relaxed. Another reason could be the style of marketing of products in that store. Hooking more customers to buy instead of just going in-and-out of the store. 


That's all about the question no.1 in Store Characteristics. Let's now move into second question, which is: *Which stores have the highest efficiency (sales per square foot)?*

In this part I've decided to use pivot table to easily filter out and create a chart. I've created a simple table to put there the values of Store ID and the Efficiency of said store. But to be able to answer this question, I needed to create another column to my dataset, named *"Efficiency of (Sales per Square Foot)"*. This column will show the efficiency of each store efficiency by sales per square foot. To make this happen I've converted the yard square first into square foot, to get the expected answer by the question. So to convert it, you just simply multiply the yard square to 9. 

Here is the formula:
```
[Store_Area]]*9
```

Then to find the efficiency, I've divided the store sales to the square foot of store area. Here is the formula:
```
=[@[Store_Sales]]/([@[Store_Area]]*9)
```
Now that we have the new column made, we can now insert a pivot table. In the pivot table I will select the Store ID as rows and Efficiency of (Sales per Square Foot) as the values. Then I filtered the Efficiency of (Sales per Square Foot) by largest to smallest. Then I've filtered the Store ID into only top 10 because 897 rows is too many.

<p align="center">
  <img src="https://github.com/JoshCO11/Supermarket_Store_Branches_Sales_Excel_Project-Data_Analytics/blob/c6f84fe64d3687e855e02d23de6e0b21bd193f04/images/Question%203/Store_Characteristics_2.1.PNG" alt="Store Characteristics #2.1" width="800"
</p>

Here is now the pivot table. After that I've inserted a pivot chart, specifically a clustered column chart to visualize the result.

<p align="center">
  <img src="https://github.com/JoshCO11/Supermarket_Store_Branches_Sales_Excel_Project-Data_Analytics/blob/c6f84fe64d3687e855e02d23de6e0b21bd193f04/images/Question%203/Store_Characteristics_2.PNG" alt="Store Characteristics #2" width="800"
</p>

As you can see here, the highest efficiency is $10.70 USD and the lowest efficiency is at $1.23 USD. Which means the Store ID 557 is earning $10.70 USD per square foot in the store space. This could be a result of effective store layout. The products could be placed perfectly where the customer will be able to see it as quickly as possible. Not giving the customer a hard time finding the product he or she needs. Another possibility is that there is a lot of customer going inside the store. Maximizing the store area. Another reason could be, it has a great marketing strategy into promoting the products inside. It could be also because of the great customer service inside the store.


So those are the analysis answer for the third set of questions. Let's now move to the fourth set of questions.

### **SOLVING THE *TRENDS AND PATTERNS* QUESTIONS**

The only question in this is: *Are larger stores consistently associated with higher sales or customer traffic?*

In this part I've first checked first if there is any outlier in the Store Area. That is why I've gathered the basic description of the Store Area. 

<p align="center">
  <img src="https://github.com/JoshCO11/Supermarket_Store_Branches_Sales_Excel_Project-Data_Analytics/blob/53412f6283ecdd8f25e5d229f8514ef22cc9c48c/images/Question%204/Trends_and_Patterns_1.PNG" alt="Trends and Patterns 1" width="800"
</p>

I can see in here that the average is slightly higher than median by a very small margin. It's likely that's the distribution of store area is slightly right-skewed. I also created a visualization to understand it more easily. 

<p align="center">
  <img src="https://github.com/JoshCO11/Supermarket_Store_Branches_Sales_Excel_Project-Data_Analytics/blob/53412f6283ecdd8f25e5d229f8514ef22cc9c48c/images/Question%204/Trends_and_Patterns_1.1.PNG" alt="Trends and Patterns 1.1" width="800"
</p>

Just like what I have mentioned earlier the difference between the average and the median is very small, because of that the visualization of the chart is not showcasing right-skewed, its like a perfect bell shape size. This chart made me continue my analysis without further cleaning and removing outliers in my dataset.<br><br>
I now proceeded to answer the question if there is an associated relationship between the larger stores and higher sales. To answer this question, I need to set a threshold where the larger store distinction will start. For that I've used *1 Standard Deviation above the Mean* <br><br>
The formula to achieve this is:
```
=median + standard deviation
```
I was able to do this because I have displayed the store area description, where I was able to check all the nessecesary information about the store area.

Then after that, knowing the threshold for the larger store, I began discretize the store area that is greater than or equal to the threshold. Here is the result:

<p align="center">
  <img src="https://github.com/JoshCO11/Supermarket_Store_Branches_Sales_Excel_Project-Data_Analytics/blob/8ab35e59bd5a426011a24eed0d5abe8605b36483/images/Question%204/Trends_and_Patterns_L_SA_bin.PNG" alt="Trends and Patterns Large Store Area bin" width="800"
</p>

With that I was able to create this plot showing if whenever the larger stores helps with the store sales.

<p align="center">
  <img src="https://github.com/JoshCO11/Supermarket_Store_Branches_Sales_Excel_Project-Data_Analytics/blob/8ab35e59bd5a426011a24eed0d5abe8605b36483/images/Question%204/Trends_and_Patterns_1.2.PNG" alt="Trends and Patterns 1.2" width="800"
</p>

As you can see in this visualization the larger the store become, the lesser it gets with total sales. That is because the larger stores are not effectively displaying their product for selling to the customer. There is also a chance that probably the store is not in a good area for their target customers. Maybe there marketing strategy is not good enough, that doesn't convince people to buy. But it's good to know that large store area doesn't necessarily means high profit. What about the stores that has a store area less than the threshold?

Here is the plot of that:
<p align="center">
  <img src="https://github.com/JoshCO11/Supermarket_Store_Branches_Sales_Excel_Project-Data_Analytics/blob/8ab35e59bd5a426011a24eed0d5abe8605b36483/images/Question%204/Trends_and_Patterns_1.3.PNG" alt="Trends and Patterns 1.3" width="800"
</p>

This is not part of the question, in finding the less than the large store area. However, I've included it for better understanding, to find an answer if size of store area is really relevant. Well, according to the image, it took a rising action from the smallest size until it reaches the size of around *1,455 - 1,494*, indicating that this size is accumulating good amount of sales, much higher than the most of larger store area. Also, as you can see, other small store area is earning much higher than the larger store area. What could be the reason behind this? The possible reason behind this is an effective way of selling product to the mass. The store owner probably aware of what products are in-demand in his or her area. Providing those items for sale to the mass of customers. Another reason is the right location for their specific service. For example, a scuba-diving or beach store located in a beach, would sell a lot because that is the right store the person would go to whenever he is around the beach area. That is probably why it's generating a much higher value of total sales than a larger store area.

I've also analyzed the association between the larger store area and daily customer count. To also to that I've used the discretized bin for larger store area. Then I've plotted the chart to visualize it.

<p align="center">
  <img src="https://github.com/JoshCO11/Supermarket_Store_Branches_Sales_Excel_Project-Data_Analytics/blob/8ab35e59bd5a426011a24eed0d5abe8605b36483/images/Question%204/Trends_and_Patterns_1.4.PNG" alt="Trends and Patterns 1.4" width="800"
</p>

Well, just like the relationship of large store area with daily customer count, it's showing a decline whenever the store reach a larger store area. The reason is probably because of the store is selling products that is expensive and not aiming for the mass of customers. The store is probably set for a specific demographics which does not scope the regular citizen around his location. That is an examples of why it is gaining less traction with daily customer traffic. The correlation also shows a negative value, indicating a decrease whenever one variable increases, mirroring the comment I have stated. How about the less than the larget store area threshold?

Here is the chart for that:
<p align="center">
  <img src="https://github.com/JoshCO11/Supermarket_Store_Branches_Sales_Excel_Project-Data_Analytics/blob/38861ed45fc891237a9c287ea9462fd3a2eb2107/images/Question%204/Trends_and_Patterns_1.5.PNG" alt="Trends and Patterns 1.5" width="800"
</p>

Just like the chart for store area and store sales, it's showing a rise at the top at the start of the smallest store area until it reaches the size of *1,415 - 1,454* size. Then it's seen to be on decline. What's the reason behind the larger traction of daily customer traffic than the larger store area. Well, that is probably because the smaller or at medium size store are is selling products that is highly in-demand in its location. The proximity of accessability to the store is greater than the larger store area. That is one of example why the smaller or medium size store area is gaining more customer traffic. Another reason is that, probably the store is selling products in much more affordable prices. This is a stragety where you will also sell a lot but only gain a little of profit, but the sale factor will be high because it is affordable in smaller change. If that's the case the customer traffic will be high because not all customers are rich to purchase items that is not in the capacity of their budget. And about the correlation status of the less than large store area and daily customer count is at negative also, showing that whenever the other variable goes to increase the other one is decreasing, that is probably why when it reached the peak of *1,415 - 1,454* size, it decreases. 

That is all for the set of fourth set of question about the trends and patterns. Let's now go to segmentation.

### **SOLVING THE *SEGMENTATION* QUESTIONS**

There is only one question in this set, that is: *Can stores be grouped into high-performing, average, and low-performing categories based on sales or customer count?*

I've assessed both the grouping on store sales and daily customer count. Here are the basic description of both store sales and daily customer count:
<p align="center">
  <img src="https://github.com/JoshCO11/Supermarket_Store_Branches_Sales_Excel_Project-Data_Analytics/blob/c0404f97d8c15dfb2c20514c7bd1870b88deff4f/images/Question%205/Segmentation_1.PNG" alt="Segmentation 1" width="800"
</p>

I've used this basic description to create two new column to my dataset page. The two columns are *Sales Performance Category* and *Customer Count Performance Category*. In this two new column I've used an Excel formula *=IFS* to distinguish whatever store category its fall to. The average category is the median, low-performaning is the stores less than 25th percentile, and high-performing is the stores greater than 75th percentile.

The exact formula is here.<br>
This is for the store sales category:
```
=IFS([@[Store_Sales]] < Segmentation!$C$4, "Low -performing", AND([@[Store_Sales]] >= Segmentation!$C$4, [@[Store_Sales]] <= Segmentation!$C$6), "Average", [@[Store_Sales]] > Segmentation!$C$6, "High-performing")
```

This is for the daily customer count category:
```
=IFS([@[Daily_Customer_Count]] < Segmentation!$F$4, "Low -performing", AND([@[Daily_Customer_Count]] >= Segmentation!$F$4, [@[Daily_Customer_Count]] <= Segmentation!$F$6), "Average", [@[Daily_Customer_Count]] > Segmentation!$F$6, "High-performing")
```
After that I've created a pie chart and column chart to visualize the category for both store sales and daily customer count.

This plots is for Store Sales category:
<p align="center">
  <img src="https://github.com/JoshCO11/Supermarket_Store_Branches_Sales_Excel_Project-Data_Analytics/blob/f3d8f2fe76077698edfdfc167746a2b0fa540613/images/Question%205/Segmentation_2.PNG" alt="Segmentation 2" width="800"
</p>

As you can see there is more average store sales than both low-performing and high-performing stores. This shows that in our dataset, it is more on about average stores.


This plot is for Daily Customer Count category:
<p align="center">
  <img src="https://github.com/JoshCO11/Supermarket_Store_Branches_Sales_Excel_Project-Data_Analytics/blob/f3d8f2fe76077698edfdfc167746a2b0fa540613/images/Question%205/Segmentation_3.PNG" alt="Segmentation 3" width="800"
</p>

For the daily customer count, the average is still the highest at *459* stores, while the high-performing is at *217* and for low-performing is at *220*. Indicating that, when it comes to daily customer count in our dataset, it is more on about the average range of values.


Now, we've finished the fifth set of questions. We will now move to the final question, which is *"Optimization"*.

### **SOLVING THE *OPTIMIZATION* QUESTIONS**

The first question is: *What store characteristics (e.g., size, items available) maximize sales or customer count?*

In this question I've created a correlation table where it shows the correlation of each feature to each other. Here is the table:

<p align="center">
  <img src="https://github.com/JoshCO11/Supermarket_Store_Branches_Sales_Excel_Project-Data_Analytics/blob/ed48dfc4dbe19fe649323bc0bb12f381de3da459/images/Question%206/Optimization_1.PNG" alt="Optimization 1" width="800"
</p>

As you can see there is no correlation that is high other than the equal feature or the same feature, and the feature of *Area * Items* which I have created just to check if it will put affect to the store sales, but as you can see it only has *0.102* correlation with store sales, which is pretty low. Why is this the result? The possible reason is that, the dataset doesn't include more important features. Remember this dataset is from kaggle, so this dataset is probably missing some columns but still, this dataset has a 700+ upvotes, so it's still a good dataset for project.

Now let's proceed to the last and second question in this final set of question: *Could specific changes (e.g., increasing store area or inventory) improve performance for underperforming stores?*

In this part what I did is I've added numerous new columns to my dataset to simulate an increase to the store area, items available, and daily customer count. They are increased by 50% and 100%. The formula I've used is this. By the way, the dataset I've used here are the only low-performing stores, and we've already covered that in the previous set of questions, so I've used it. 

For 50% raise:
```
=Column_Feature * 1.5
```

For 100% raise:
```
=Column_Feature * 2
```

After that I've used multiple regression analysis to finally simulate the increase to the store sales. Here is the result of the multiple regression analysis:

<p align="center">
  <img src="https://github.com/JoshCO11/Supermarket_Store_Branches_Sales_Excel_Project-Data_Analytics/blob/ed48dfc4dbe19fe649323bc0bb12f381de3da459/images/Question%206/Optimization_2.PNG" alt="Optimization 2" width="800"
</p>

I've disregard other values in the multiple regression analysis because the only thing I will use is this one, the values you can see in the image. 

After that I've created another set of new columns to present the store sales of the increased variables. The formula I used is this:
```
=Intercept + (Coefficient_1 * Variable_1) + (Coefficient_2 * Variable_2) + (Coefficient_3 * Increased_Variable_3)
```

This formula depends on what I'm simulating, for this example, let's say I'm increasing the *variable 3* that is why I've used the increased variable instead the original. The rest will be the original when you only want to check the simulated increase of that one variable.

After doing this in each new columns, I've created a table and also bar chart to understand if something really significant happens whenever there are changes with the present features in the dataset. Whether will it really increase the store sales or not. 

This is the table:
<p align="center">
  <img src="https://github.com/JoshCO11/Supermarket_Store_Branches_Sales_Excel_Project-Data_Analytics/blob/ed48dfc4dbe19fe649323bc0bb12f381de3da459/images/Question%206/Optimization_2.1.PNG" alt="Optimization 2.1" width="800"
</p>

In this table you will see the changes, and I made it easier to understand because of the column of percentage changes. The only thing that increased here is the correlation between the store area and store sales. The rest is at negative. What is the meaning of that? before we answer that question, here are the bar charts:

<p align="center">
  <img src="https://github.com/JoshCO11/Supermarket_Store_Branches_Sales_Excel_Project-Data_Analytics/blob/ed48dfc4dbe19fe649323bc0bb12f381de3da459/images/Question%206/Optimization_2.2.PNG" alt="Optimization 2.2" width="800"
</p>

Well, as you can see here there was a huge leap of store sales when the store area increased in the underperforming stores. This might probably because of enhanced/better storage capacity, making the stocks more and when people comes they are able to give what the customers are looking. Another reason is better display of products inside the store. They might also had an edge to their competitors because they've had an upgrade of store size, gaining attraction the customers around their area. This means that whenever the underperforming stores decided to increase their store size about *50% or 100%*5, the store sales will increase in significant in about *41% or 81%*.

<p align="center">
  <img src="https://github.com/JoshCO11/Supermarket_Store_Branches_Sales_Excel_Project-Data_Analytics/blob/ed48dfc4dbe19fe649323bc0bb12f381de3da459/images/Question%206/Optimization_2.3.PNG" alt="Optimization 2.3" width="800"
</p>

When it comes to the simulation of increasing the items available, there is a huge decrease to the total sales. The store sales decreases by *39% or 79%*, when you increase the items avaialable by *50% or 100%*. This is probably because the items added only costed the store and did not get the return of costs. This is probably because of poor decision making of restocking items that is not selling good in their location. Another reason is the location, the area probably not crowded with people.

<p align="center">
  <img src="https://github.com/JoshCO11/Supermarket_Store_Branches_Sales_Excel_Project-Data_Analytics/blob/ed48dfc4dbe19fe649323bc0bb12f381de3da459/images/Question%206/Optimization_2.4.PNG" alt="Optimization 2.4" width="800"
</p>

Lastly is when the simulated increase of daily customer count. This simulation also had a decrease to the total sales. When the daily customer count increased by *50%* the change of total sales dropped by *1%*. Then when the daily customer count increased by *100%* the total sales dropped by *2%*, so what is the meaning of this? This is probably the customers just stopped over the store, so even they count as addition to the daily count customer, the sales doesn't increased because the customers did not buy anything. They just did some window shopping or used the store as waiting location to someone. Another reason is that, people may tend to go inside the store to buy something not that significant to the overall total revenue of the store. For example buying a penny priced item, will not contribute a lot to the total sales. Another reason is the poor marketing strategy of the store. The customer service is probably also poor. The display of product is also probably poor, giving the customers hard time to buy whenever tons of customers come daily. 


That is the last set of answers to my analysis project.<br>

What I've learned from the analysis? I can say that the independent variables of the dataset does not affect the store sales (dependent variable) in a lot of ways. Maybe other aspects affect it more and it's not included in the dataset that was presented. But other than that, I can say that there is chance for underperforming stores to gain more sales. That is by increasing their store area. Investing to the quality of the store will get them more earnings than improving their marketing strategy to attract more traction of customers in daily basis. Also to avoid the overstocking of items. The owner should always check and be aware to the demand-supply situation of his or her store. Aiming to restock more items that is relevant to the store instead of ordering unnecessary items. 


### **CONCLUSION ABOUT THE PROJECT**  

This is my first project about data analysis using Excel. The skills I've showcased is just a the surface level of what a real data analyst can do. But this will serve as my stepping stone to improve my analysis in the future. I would to hear your reactions and comments to my analysis, either bad or good will help a lot to my progress. I'm planning to upload more projects here about datas using SQL, Python, Excel, Power BI, and other data related tools. 










