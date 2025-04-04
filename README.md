# Mobile Sales Dashboard Report

### Dashboard file : [Mobile Sales Dashboard](https://github.com/nikitanpatil1/Mobile-Sales/blob/main/Mobile_Sales_Dashboard.pbix)

## Problem Statement

This **Mobile Sales Dashboard** is designed for business decision-makers in the mobile phone industry—likely for a retailer, distributor, or brand analyzing sales performance. It helps in *Sales Performance Tracking*, gives *Regional Insights*, performs *Time Based Analysis*, helps in analyzing *Customer Behavior*.


### Steps followed 

- **Step 1 : Data Loading**
  
    Load data into Power BI Desktop, dataset is a excel file.
  
- **Step 2 : Data Transforming**
  
   Open power query editor & using the ETL tools for Data cleaning and processing.
  
- **Step 3 : Data Cleaning and Processing**

  It was observed that some columns needed modifications. Following modifications were done:
     
  - **Day, Month, and Year columns**
    
    These terms were allocated different column each but the analysis demanded them to be combined and hence it was done using *merge column* option.

     ![Image](https://github.com/user-attachments/assets/d8aaa5f3-2eab-4c89-9b9d-c0ac5b241552)
  
     ![Image](https://github.com/user-attachments/assets/1fa4d3d0-20e2-4b60-a3cd-9bd7eab6a0a0)

   - **Day Name column**

     This column had some mix data form, which could be processed using *Replace Values* or even *Date* option but it would just show the *Day Name* for only those dates which are present in the data.
     But for analysis each and every day from those 4 years were needed. So to deal with it Custome calender table was made.
  
      ![Image](https://github.com/user-attachments/assets/68013721-8309-4256-96f9-d859ead37b3e)
	 
    - **Custome Calender Table**
  
      It was made so that we can get the Day Name for each and every date present in that particular year.
      
      Following formula was used to get that info and later on it was converted into the column:
  
          = List.Dates(#date(2021,1,1),1461,#duration(1,0,0,0))
  
      ![Image](https://github.com/user-attachments/assets/3d56d1ad-4f14-46ef-ba73-20e4a41981c8)
 

 - **Step 4 : Data Modeling**

   i.e Relationship was created between two tables.
   
      ![Image](https://github.com/user-attachments/assets/3937402a-7ac9-4eb1-b658-2d73a3c8c459) 
		  
		  
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

  ![Image](https://github.com/user-attachments/assets/01bbdfbb-f119-483d-a66c-ff4717381b34)

 
 # Final Dashboard Snapshots

 ### Dashboard Snapshot
   
   ![Image](https://github.com/user-attachments/assets/41fc63a8-3afc-4bd0-bfc8-ba3f33deaa80)
   
 ### Month To Day (MTD) Dashboard Snapshot
   
   ![Image](https://github.com/user-attachments/assets/9cf47024-0ac1-44dd-bd6f-05b98af5051c)
	
 ### Same Period Last Year Dashboard Snapshot
   
   ![Image](https://github.com/user-attachments/assets/c806732c-e015-4121-aef6-e2b1d74167d6)



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
	   
	  - Peak Months: Based on the line graph, sales peaked in April & July.
    
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


