# productivity-tracker
It calculates average task rate and work availability for individuals, groups or teams of employees for a given date range, and the number of employees needed to complete a series of tasks in a given amount of time at a calculated rate of productivity.

### **CASE COUNT LOG**

User login/ password authentication (group permission).

User inputs:

	shiftDate   <input type=”date”>
	shiftStart    <input type=”time”>
	shiftEnd    <input type=”time”>
	categoryStart   <input type=”time”>
	categoryEnd   <input type=”time”>
	stockCount    <input type=”number”>

Variable Assignments:

	let categoryTime = categoryEnd - categoryStart
	let stockingRate = stockCount ÷ [60 minutes]
	let shiftTime = shiftEnd – shiftStart
	let stockingTime = shiftTime – [breaks, lunches, routine tasks]
	categoryEnd   <input type=”time”>
	stockCount    <input type=”number”>

Data stored to SQL server.


### **PRODUCTIVITY LOG**

User login/password authentication (owner permission).

User Inputs:

	deliveryDate		<input type=”date”>
	deliveryTime		<input type=”time”>
	categoryName		<input type=”text”>		*//ex. “BME”, “CSBB”*
	cat0StockRecvd	<input type=”number”>	*//attach to invoice*

Variable Assignments:

	let totalStockRecvd = cat1StockRecvd + cat2StockRecvd, ...

Data stored to SQL server.


### **CASE COUNT TRACKER**

Function...

	...defines teams of user(s) (dropdown select any/all)
	...sorts user(s) records by date range (any selected)
	...calculates avgCaseRate for user(s) per date range(s)
	...calculates avgWorkAvail for user(s) per date range(s)

*It should sort individuals, scheduled TMs, or whole team*
*It should show 1 day, 7 days or 28 days*


### **AVAILABILITY CALCULATOR**


Variable assignments:

	truckAvail = shiftEnd – deliveryTime
	if truckAvail < avgWorkAvail,		*//truck is late*
	  employeesRequired = totalStockRecvd ÷ avgCaseRate ÷ truckAvail
	else		*//truck is on time or early*
	  employeesRequired = totalStockRecvd ÷ avgCaseRate ÷ avgWorkAvail

*It should calculate team members needed to complete truck throwing for a given arrival time and average case throwing rate for a given team*
