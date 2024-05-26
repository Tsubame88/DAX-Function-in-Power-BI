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



