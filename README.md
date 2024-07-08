# DAX-Function-in-Power-BI

## Measure and Calculated column 

![Measure and calculated Column](https://github.com/Tsubame88/DAX-Function-in-Power-BI/assets/156522557/f8aa060b-9587-46ec-8825-3e3dce003747)

## Context in Power BI 

![Row Context](https://github.com/Tsubame88/DAX-Function-in-Power-BI/assets/156522557/11660bff-3c33-45d1-8332-f29364e28048)
![Query Context](https://github.com/Tsubame88/DAX-Function-in-Power-BI/assets/156522557/93845adb-8980-4280-bb0c-add2d0e2ad44)
![Ex Query Context](https://github.com/Tsubame88/DAX-Function-in-Power-BI/assets/156522557/1e5babb0-b50f-4b33-901e-5338be348bc9)
![Filter Context](https://github.com/Tsubame88/DAX-Function-in-Power-BI/assets/156522557/1285a315-011d-4127-854e-f79815f684ae)
![Ex Filter Context](https://github.com/Tsubame88/DAX-Function-in-Power-BI/assets/156522557/204834ea-04a6-412e-9a9a-15d119b73482)
![Context in POwer BI](https://github.com/Tsubame88/DAX-Function-in-Power-BI/assets/156522557/85c5adfd-8614-4864-a1ce-67253ba7d0f4)

## Date Table

Dimentional date table are neccessary to ensure that calculations such as DAX time_intelligence fucntions have all available dates. This ensures there is no gap between dates so there is no error occur while perform these calculations. 
## SUNSTITUTE(data, old, new ) 

to replace a character by using DAX intead of performing in Power Query 

## RELATE( column ) 

to coppy a column from different table 

## IMPLICIT & EXPLICIT MEASURE

![Implicit _ Explicit Measure](https://github.com/Tsubame88/DAX-Function-in-Power-BI/assets/156522557/d14f7c9a-f933-40e4-9a45-38d0e6d4fc75)
![Implicit_Explicit_2](https://github.com/Tsubame88/DAX-Function-in-Power-BI/assets/156522557/b983d002-c00b-4883-95e9-2f79a0d1c8fe)

## Year Over Year Calculation 

is often used in financial comparision analysis to compare two or more events on an anualized basic

Sales YoY %  = 

VAR  SalePriorYear = CALCULATE([Sales], SAMEPERIODLASTYEAR(Dim_DeliveryDate[Delivery Date Key]))

RETURN 

DIVIDE(
    ( [sales] - SalePriorYear),
    SalePriorYear
)

## DATEADD()

Returns a table that contains a column of dates, shifted either forward or backward in time by the specified number of intervals from the dates in the current context.

### Syntax 

DATEADD( <dates>, <number_of_intervals>,<interval>) 

**Parameters** 
+ dates : A column that contains dates.
+ number_of_intervals :	An integer that specifies the number of intervals to add to or subtract from the dates.
+ interval : The interval by which to shift the dates. The value for interval can be one of the following: year, quarter, month, day


### Return value
A table containing a single column of date values.

### Example 

= DATEADD(DateTime[DateKey],-1,year)

## CALCULATED()

1. We have a measure that calculate the change YoY% of Avg retail price 
![Retail Price YoY%](https://github.com/Tsubame88/DAX-Function-in-Power-BI/assets/156522557/03734e74-e5fe-4262-933d-ce5a52ab1777)

2. then add a filter from Dim_Invoice table 
![Filter](https://github.com/Tsubame88/DAX-Function-in-Power-BI/assets/156522557/a3b040d7-4f0f-4e69-876a-270f8a68ca6f)

3. And when we click on year on filter our chart of YoY% was messed up
![YoY% changed by filter ](https://github.com/Tsubame88/DAX-Function-in-Power-BI/assets/156522557/85f83df3-6b19-4691-9251-13e092fb4138)

4. Add ALL() to override all the filter from Dim_Invoice Table
![Calculate_All](https://github.com/Tsubame88/DAX-Function-in-Power-BI/assets/156522557/8483e63d-7f46-42f4-9ca1-86eb89f8c1a5)

## CROSSFILTER()
Another way, can you Edit interaction under Format ribbon 

## INTERATING FUNCTION

![Sumx](https://github.com/Tsubame88/DAX-Function-in-Power-BI/assets/156522557/ec719a7e-d8e7-4ccd-a53c-c7543cf8a89c)
![Sumx2](https://github.com/Tsubame88/DAX-Function-in-Power-BI/assets/156522557/e1b67123-6c25-43e6-8ab6-eb2a98367401)
![rankx](https://github.com/Tsubame88/DAX-Function-in-Power-BI/assets/156522557/93299ff2-8be4-4a66-a10c-fd5b508ce235)

![operation in DAX](https://github.com/Tsubame88/DAX-Function-in-Power-BI/assets/156522557/25f0a12e-7a27-45c8-a2d9-bed864298047)

## HASONEVALUE()

Return TRUE / FALSE

## USEPRINCIPALNAME( ) 

## RLS 

is used to manage data access for given users or personalized dashboard.

The dashboard is presented as below. 
![dashboard_everyone](https://github.com/Tsubame88/DAX-Function-in-Power-BI/assets/156522557/007e8981-b2ce-4458-83c8-ffc5fb7b7a26)
Every chart presents the KPI made by all of employee in company, and every one can see the same dashboard.
Now we will implement Role RLS so that each salesperson can only see their KPI on dashboard. 

### Manage Role RLS
![manage role RLS](https://github.com/Tsubame88/DAX-Function-in-Power-BI/assets/156522557/e2636ef9-bbf3-490a-97d9-8d27cc3c1b8a)

1. Model Wiew >  Manage Role
2. Create a new role (Ex: Salesperson)
3. Select [Is Salesperson] column from Dim_Employee Table which return only TRUE/FALSE . This will allow only salesperson to see dashbord
4. Use USERPRINCIPALNAME () to personalize the dashboard so that each salesperson can only see their own dashboard, can not access to another person's dashboard.

### Test of Role RLS :  check how the dashboard be seen from employee name Lily Code 
1. Model View > View As
2. Check to
   - [x]Other Users
   - [x]Salesperson
3. Type the email adress of Lily Code in the white box :  lily.code@wwi.com   
![test role RSL](https://github.com/Tsubame88/DAX-Function-in-Power-BI/assets/156522557/dc0216bd-b3c1-4689-8188-12860341880b)

### Lily's dashboard 
Except for the "Distinct Count City" card every visual was changed and now just presents these KPIs related to Employee named LiLy Code.   
![sercurity filtering_lily](https://github.com/Tsubame88/DAX-Function-in-Power-BI/assets/156522557/1729da26-d42c-44f6-988d-ba6610548d4f)

## SECURITY FILTERING 
In this above example  "Distinct Count City" card  doesn't change when we conduct Role RLS.

That's because :
1.  "Distinct Count City" card has value from measure DISTINCTCOUNT(Dim_City[WWI City ID]), Dim_City and Fact_Sales has a relationship one way from Dim_City to Fact_Sales so this measure count the distinct city in Fact_sales table which locate in Dim_city table 
2. Above we setup the RLS from Dim_Employee table which has one way relationship to Fact_Sales table so it will filter the Fact_Sales Table but because there is no relationship from Fact_Sale to Dim_City, so there is no relation ship between Dim_Employee and Dim_City.

To present the correct information on the "Distinct Count City" card, we have to edit the relationship between Fact_Sales and Dim_City to Cross-filter dicrection & Apply security Filter to both direction 
![cross filter](https://github.com/Tsubame88/DAX-Function-in-Power-BI/assets/156522557/d39bae39-45a6-40fe-9152-1eb4e683a2cf)


## SUMMARIZE ()



