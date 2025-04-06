# Mobile Sales Dashboard Report

#### Dashboard file : [Mobile_Sales_Dashboard](https://github.com/nikitanpatil1/Mobile-Sales/blob/main/Mobile_Sales_Dashboard.pbix) (View raw)

## Problem Statement

This **Mobile Sales Dashboard** is a **Power BI** report designed to analyze mobile phone sales performance for retailers and brands. It includes **data transformation**, **modeling**, **DAX calculations**, and **visualization** to track key metrics. It tracks **sales trends**, **regional performance**, **customer behavior**, and **payment insights**, with **MTD** and **YoY** comparisons. The dashboard helps optimize marketing, pricing, and promotions to drive better sales and business decisions.

## Steps followed 

- **Step 1 : Data Loading**
  
    Load data into Power BI Desktop, dataset is a excel file.
  
- **Step 2 : Data Transforming**
  
   Open power query editor & using the ETL tools for Data cleaning and processing.
  
- **Step 3 : Data Cleaning and Processing**

  It was observed that some columns needed modifications. Following modifications were done:
     
  - **Day, Month, and Year columns**
    
    These terms were allocated different column each but the analysis demanded them to be combined and hence it was done using *merge column* option.

     ![Image](https://github.com/user-attachments/assets/abb2a9a4-478c-498e-9952-0055f9ecab7e)
  
     ![Image](https://github.com/user-attachments/assets/069b06dd-404a-4868-b06f-a54a8d176637)

   - **Day Name column**

     This column had some mix data form, which could be processed using *Replace Values* or even *Date* option but it would just show the *Day Name* for only those dates which are present in the data.
     But for analysis each and every day from those 4 years were needed. So to deal with it Custome calender table was made.
  
      ![Image](https://github.com/user-attachments/assets/9f0a7fd1-cee1-4e22-a9ee-75dd38212bdb)
	 
    - **Custome Calender Table**
  
      It was made so that we can get the Day Name for each and every date present in that particular year.
      
      Following formula was used to get that info and later on it was converted into the column:
  
          = List.Dates(#date(2021,1,1),1461,#duration(1,0,0,0))
  
      ![Image](https://github.com/user-attachments/assets/704c3d95-7ee8-4fa7-86f4-cabb22eec561)
 

 - **Step 4 : Data Modeling**

   i.e Relationship was created between two tables.
   
      ![Image](https://github.com/user-attachments/assets/ac24ab02-c4f7-4ab9-bffe-5c81121f871a)
		  
		  
- **Step 5 : Doing required DAX calculations**
  
   New Measure where added:
            
   **(a) Total_quantity**
		
		        Total_quantity = SUM(Sales_Data[units sold])
			 
   **(b) Total_sales** 
		   
		        Total_sales = SUMX(Sales_Data,Sales_Data[Units sold]*Sales_Data[Price Per Unit])
         
   **(c) Total_transactions**
		
		       Transactions = COUNTROWS(sales_Data)
			 
   **(d) Average_Price**

            Average_Price = AVERAGE(Sales_Data[Price Per Unit])

 - **Step 6 : Dash Board Creation**
   
   Dashboard was created using different charts, tables, cards, slicers, map, text box to get the insight regarding various terms.
   
  
  - **Step 7 : Month To Day (MTD) Calculation and Dashboard Creation**
    
    MTD for total sales was calculated using formula:
	    
		 MTD = TOTALMTD([Total_Sales],Custome_Calender[Date].[Date])
  
  
  - **Step 8 : Same Period Last Year Calculation and Dashboard Creation**
      
    To compare last year sales with this year using formula:
	  
	     Same Period Last Year = CALCULATE([Total_Sales], SAMEPERIODLASTYEAR(Custome_Calander[Date].[Date]))
		  
		  

# Snapshot of Dashboard (Power BI DESKTOP)

  ![Image](https://github.com/user-attachments/assets/ffbd7bab-0adc-479b-8e30-740b2cc558e2)

 
 # Final Dashboard Snapshots

 ### Dashboard Snapshot
   
   ![Image](https://github.com/user-attachments/assets/4329b418-b814-4ca7-a9b8-3750987d7844)
   
 ### Month To Day (MTD) Dashboard Snapshot
   
   ![Image](https://github.com/user-attachments/assets/9be3eb73-53f1-45e3-9065-944027795b36)
	
 ### Same Period Last Year Dashboard Snapshot
   
   ![Image](https://github.com/user-attachments/assets/3e26ef26-5915-45b1-9b63-969b8b8d5a2f)



# Insights

 This Mobile Sales Dashboard tracks and analyzes mobile phone sales performance for a retailer or brand. 

 Here's a quick summary of its key insights:

### [1] Sales Overview

    - Total Sales: 769M

    - Total Quantity Sold: 19K

    - Total Transactions: 4K

    - Average Price: 40.11K
           
### [2] Sales Trends & Key Insights

**a) Best & Worst Months for Sales**
	   
	  - Peak Months: Based on the line graph, sales peaked in July.
    
	  - Lowest Sales Months: February saw the lowest sales.
	
 **b) Best-Performing Cities**
	
	  - Cities like Mumbai, Delhi, Bangalore, and Chennai had high sales.

	  - Smaller cities like Ludhiana and Gorakhpur had lower sales contributions.
	   
 **c) Brand Performance**
	
	  - Apple leads in total sales, followed by OnePlus, Samsung, and Vivo.
    
	  - But Samsung has higher transactions, meaning it sells more units at a lower price.
	   
 **d) Payment Method Insights**
	
	  - UPI & Debit Cards dominate sales (both around 24-26%).
    
	  - Cash & Credit Cards are used less frequently.
	
 **e) Sales by Day of the Week**
	
	  - Monday, Friday, and Tuesday see the highest sales (~26.4M).
    
	  - Thursday has the lowest sales (~23.2M).
	   


 ### [3] Recommendations & Strategy
 
- **Boost Sales During Low Months** 
	
	   Introduce promotions during February & December.
 
 - **Leverage Digital Payments** 
	  
	   Offer cashback or discounts on UPI/Debit transactions.
 
 - **City-Based Targeting**
	
	   Focus marketing in high-performing cities & expand efforts in lower-tier cities.
	  
- **Enhance Mid-Tier Product Ratings**
	
	   Improve features based on customer feedback
	  
- **Day-Based Promotions**
	
	  Midweek sales (Tuesday-Thursday) can help balance out demand.




















