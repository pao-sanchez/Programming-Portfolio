# Variables, Operators, Types, Expressions
compund Interest

### INPUT
principal = 10000
rate = 0.15
compoundings = 4
time = 35

### PROCESSING
amount = principal * (1+ (rate/compoundings))^ (compoundings * time)

### OUTPUT
print (amount)

### Result:
<img width="100" alt="Compound Interest" src="https://user-images.githubusercontent.com/98184898/166986211-d65867a8-af08-4e1d-a6f0-19dff4eb8058.png">

## This example calculates compund interest using vairables, operators, and expressions





# File Input/Output
Net Income

### INPUT
netIncomeDataFrame = read.csv("data/Sanchez-Paola-Net-Income.csv")
revenue = netIncomeDataFrame$revenue
expenses = netIncomeDataFrame$expenses

### PROCESSING
netIncome = revenue - expenses

### OUTPUT
print (netIncome)
netIncomeSolutionDataFrame = data.frame(
  revenue = revenue,
  expenses = expenses,
  netIncome = netIncome
)
write.csv(netIncomeSolutionDataFrame, "data/Sanchez-Paola-Net-Income-Solution.csv")

## Result:
<img width="192" alt="Net Income" src="https://user-images.githubusercontent.com/98184898/166986812-bfabea60-80e8-464d-8497-c008ead18aad.png">

### This is an example using File output/input (File O/I) and data frames to calculate net income



