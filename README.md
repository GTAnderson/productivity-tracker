# productivity-tracker
It calculates average task rate and work availability for individual, subset or full set of employees for a given date range, and the number of employees needed to complete a series of tasks in a given amount of time at a calculated rate of productivity.

### **CASE COUNT LOG**

User login/ password authentication (group permission).

User inputs:
```
shiftDate   	<input type=”date”>
shiftStart    	<input type=”time”>
shiftEnd    	<input type=”time”>
categoryStart	<input type=”time”>
categoryEnd	<input type=”time”>
stockCount    	<input type=”number”>
```
Variable Assignments:
```
let categoryTime = categoryEnd - categoryStart
let stockingRate = stockCount ÷ [60 minutes]
let shiftTime = shiftEnd – shiftStart
let stockingTime = shiftTime – [breaks, lunches, routine tasks]
```
Data stored to SQL server.


### **PRODUCTIVITY LOG**

User login/password authentication (owner permission).

User Inputs:
```
deliveryDate			<input type=”date”>
deliveryTime			<input type=”time”>
categoryName			<input type=”text”>	//ex. “BME”, “CSBB”
stockReceived.CategoryName	<input type=”number”>	//attach to invoice, use data collections
```
Variable Assignments:
```
let totalStockReceived = stockReceived.Category1 + stockReceived.Category2 ...
```
Data stored to SQL server.


### **CASE COUNT TRACKER**

Function...
```
...defines team of employee(s) (dropdown select any/all)
...sorts employee(s) records by date range (any selected)
...calculates averageTaskRate for employee(s) per date range(s)
...calculates averageWorkAvailability for employee(s) per date range(s)
```
*It should sort by individual, subset or full set of employees.*

*It should show 1 day, 7 days or 28 days*


### **AVAILABILITY CALCULATOR**


Variable assignments:
```
deliveryAvailability = shiftEnd – deliveryTime
if deliveryAvailability < averageWorkAvailability,	//delivery is late
  employeesRequired = totalStockReceived ÷ averageTaskRate ÷ deliveryAvailability
else							//delivery is on time or early
  employeesRequired = totalStockReceived ÷ averageTaskRate ÷ averageWorkAvailability
```
*It should calculate subset of employees needed to complete total stock received for a given arrival time and average task rate for a full set of employees.*
