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
What I did in this question is that I've created a simple table with 3 columns and 3 rows.<br>
- Column 1 is Metric (Highest Sales, Lowest Sales, Average Store Sales)<br>
- Column 2 is Store ID (To identify which store holds the highest or lowest sales.)
- Column 3 is Sales (Putting the amount of revenue collected by that store.)

Here is the image of the table:

<p align="center">
  <img src="https://github.com/JoshCO11/Supermarket_Store_Branches_Sales_Excel_Project-Data_Analytics/blob/6beb6ac7bd9ae7e79f775bb9aa045833bcb8199c/images/Question%201/Performance_Analysis_1.PNG" alt=" Performance Analysis #1" width="800"
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
Finding the average store sales is not included in the questions but its better to know it too. I've used median formula here instead of average to avoid outliers.
```
=MEDIAN(Table1[Store_Sales])
```





