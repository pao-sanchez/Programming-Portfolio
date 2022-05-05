# Programming Portfolio

# Variables, Operators, Types, Expressions
Compund Interest

### Input
principal = 10000
rate = 0.15
compoundings = 4
time = 35

### Processing
amount = principal * (1+ (rate/compoundings))^ (compoundings * time)

### Output
print (amount)

### Result:
<img width="100" alt="Compound Interest" src="https://user-images.githubusercontent.com/98184898/166986211-d65867a8-af08-4e1d-a6f0-19dff4eb8058.png">

This example calculates compund interest using vairables, operators, and expressions





# File Input/Output
Net Income

### Input
netIncomeDataFrame = read.csv("data/Sanchez-Paola-Net-Income.csv")
revenue = netIncomeDataFrame$revenue
expenses = netIncomeDataFrame$expenses

### Processing
netIncome = revenue - expenses

### Output
print (netIncome)
netIncomeSolutionDataFrame = data.frame(
  revenue = revenue,
  expenses = expenses,
  netIncome = netIncome
)
write.csv(netIncomeSolutionDataFrame, "data/Sanchez-Paola-Net-Income-Solution.csv")

### Result:
<img width="192" alt="Net Income" src="https://user-images.githubusercontent.com/98184898/166986812-bfabea60-80e8-464d-8497-c008ead18aad.png">

This is an example using File output/input (File O/I) and data frames to calculate net income


# Conditionals
Amortized loan payment

### Input
amountBorrowed = 250000
periodicInterestRate = 0.004167
numberOfPayments = 360

### Processing
amortizedLoanPayment = (amountBorrowed* periodicInterestRate) / (1-(1+ periodicInterestRate)^-numberOfPayments)

### Output
print (amortizedLoanPayment)
if (amortizedLoanPayment<1000) {
  print ("very affordable")
} else if (amortizedLoanPayment>=1000 && amortizedLoanPayment<=2000) {
  print ("affordable")
} else if (amortizedLoanPayment>2000) {
  print ("expensive")
}

### Result:
<img width="157" alt="Amortized Loan Payment" src="https://user-images.githubusercontent.com/98184898/166985568-70e4d557-3d82-4bf1-a251-fdbf293ab3c8.png">

This example calculates amortized loan payment using conditionals


# Loops
While loop

```{r}
correctAnswer = FALSE
print ("The Guess Taylor Swift's age")
while (correctAnswer == FALSE) {
  answer = readline (prompt="Guess Taylor Swift's age");
  answerAsNumber = as.numeric(answer)
  if (answerAsNumber == 32) {
    cat("\n\nRIGHT!!! How'd you guess?\n")
    cat("GAME OVER")
    correctAnswer = TRUE
  } else if (answerAsNumber<32) {
    cat ("Too low\n")
    cat ("Try again\n\n")
  } else {
    cat ("Too high\n")
    cat ("Try again\n\n")
  }
}
```

### Result:
<img width="300" alt="Taylor's age" src="https://user-images.githubusercontent.com/98184898/166987205-ee561930-46ed-4ade-8e6a-cccf1651b93d.png">

This is a guess Taylor Swift's age, game using while loop



# Functions
Present Value

### Processing
calcPresentValue = function (futureValue, rateOfReturn, time) {
  presentValue = futureValue / (1+rateOfReturn)^time
  return (presentValue)
}

### Input
ans = calcPresentValue (10057, 0.15, 5)

### Output
print (ans)

### Result:
<img width="121" alt="Present Value" src="https://user-images.githubusercontent.com/98184898/166987703-b036d5ba-0ae6-4f2c-ae9b-11affc2ce463.png">

This example calculates present value using functions




# Data Wrangling
HPE STOCK PRICES 2021

```{r}
dfRaw = read.csv("HPE.csv")
dateColumnName = "Date"
closeColumnName = "Close"
volumeColumnName = "Volume"
columns = c(dateColumnName, closeColumnName, volumeColumnName)
startDate = as.Date("1/1/21", format="%m/%d/%y")
endDate = as.Date("12/31/21", format="%m/%d/%y")
rows = which(as.Date(dfRaw$Date, format="%m/%d/%y") >= startDate & as.Date(dfRaw$Date, format="%m/%d/%y") <= endDate)
dfWrangle = dfRaw [rows,columns]
filename = "HPE-2021.csv"
write.csv(dfWrangle, filename, row.names=F, fileEncoding = "UTF-8")
colnames(dfWrangle) = gsub("Date", "date", colnames(dfWrangle))
colnames(dfWrangle) = gsub("Close", "close", colnames(dfWrangle))
colnames(dfWrangle) = gsub("Volume", "volume", colnames(dfWrangle))
write.csv(dfWrangle, filename, row.names = F, fileEncoding = "UTF-8")
```


This is an emxample of data wrangling for HEP stock prices only in the year 2021


# Bar Chart
Japan Covid

```{r}
dataFrame = read.csv ("time_series_covid19_confirmed_global.csv")
country = "Japan"
japanRow = which (dataFrame$Country.Region==country)
japanAllData = dataFrame [japanRow,]
startRow = 1
startColumn = 5
endColumn = ncol (japanAllData)
japanData = japanAllData [startRow, startColumn:endColumn]
japanDataNumeric = as.numeric (japanData[1,])
names (japanDataNumeric) = colnames(japanData)
names(japanDataNumeric) = gsub("X", "", names(japanDataNumeric))
barplot(japanDataNumeric, xlab = "Date", ylab = "# of deaths")
title ("Japan's Deaths")
japanDailyData = sapply (2:length (japanDataNumeric), function (i) {
  japanDataNumeric[i]-japanDataNumeric[i-1]
})
barplot(japanDailyData, xlab = "Date", ylab = "Daily deaths")
title ("Japan's Daily Deaths")
```

### Result:
Cumulative:
<img width="663" alt="Cumulative" src="https://user-images.githubusercontent.com/98184898/166991365-25d3c669-6a1d-48d0-8929-18d6cc9b84c5.png">

Daily:
<img width="685" alt="Daily" src="https://user-images.githubusercontent.com/98184898/166991487-e5aeb949-97e4-40ac-ae59-410aa2abbde0.png">

This is an example of a Bar chart for the number of deaths in Japan that occured during Covid, both cumulative and daily


# Line graphs
Line graph: ADM stock prices 2020

```{r}
dfRaw = read.csv("AMD.csv")
dateColumnName = "Date"
closeColumnName = "Close"
volumeColumnName = "Volume"
columns = c(dateColumnName, closeColumnName, volumeColumnName)
startDate = as.Date("1/1/20", format="%m/%d/%y")
endDate = as.Date("12/31/20", format="%m/%d/%y")
rows = which(as.Date(dfRaw$Date, format="%m/%d/%y") >= startDate & as.Date(dfRaw$Date, format="%m/%d/%y") <= endDate)
dfWrangle = dfRaw [rows,columns]
filename = "AMD-2020.csv"
write.csv(dfWrangle, filename, row.names=F, fileEncoding = "UTF-8")
head(dfWrangle)
dateNumbers = 1:length (dfWrangle$Date)
plot (dateNumbers, dfWrangle$Close, type="l", col="blue", xaxt="n",
      xlab = "Date", ylab = "Stock Prices", cex.lab = 1.3, col.lab = "darkblue")
axis(side=1, 1:length(dateNumbers), dfWrangle$Date, las=1)
title("ADM Stock Prices 2020",
      cex.main = 1.5, col.main = "navy"
)
```

### Result:
<img width="681" alt="AMD" src="https://user-images.githubusercontent.com/98184898/166992657-98e5419b-e82c-45ef-8617-6d8152d3e16f.png">

This is an example of a line graph from AMD stock prices in 2020


# Dashboard

```{r}
library(shiny)

ui <- fluidPage(

    titlePanel("Stock Visualizer"),

    sidebarLayout(
        sidebarPanel(
          selectInput("seDataSet", "Data Set:", NULL),
          dateRangeInput("seDateRange", "Select Dates:", startview="year"),
          radioButtons("rbSymbols", "Point Shape:", 
                       choiceNames = c("square", "circle", "triangle", "diamond"),
                       choiceValues = c(15, 16, 17, 18)),
          radioButtons("rbLineType", "Line Type:", 
                       choices = c("blank", "solid", "dashed", "dotted"))
        ),

        mainPanel(
           plotOutput("stockPlot")
        )
    )
)

server <- function(input, output, session) {
  observeEvent(input$seDataSet, {
    file = input$seDataSet
    if (file=="") {
      folder = "data"
      updateSelectInput(session, "seDataSet", choices=list.files(folder))
    } else {
      folder = "data"
      fullPath = sprintf("%s/%s", folder, file)
      df = read.csv(fullPath, encoding = "UTF-8")
      nDates = length(df$Date)
      dfDate1 = df$Date[1]
      dfDateN = df$Date[nDates]
      updateDateRangeInput(session, "seDateRange", start=dfDate1, end=dfDateN, min=dfDate1, max=dfDateN)
    }
  })

    output$stockPlot <- renderPlot({
      file = input$seDataSet
      if (file == '') return()
      
      folder = "data"
      fullPath = sprintf("%s/%s", folder, file)
      df = read.csv(fullPath, encoding = "UTF-8")
      
      startDate = input$seDateRange[1]
      endDate = input$seDateRange[2]
      if (startDate>=endDate) return()
      wrangleRows = which (as.Date(df$Date) >= startDate & as.Date(df$Date) <= endDate)
      dfWrangle = df[wrangleRows,]
      
      plot(1:length(dfWrangle$Date), dfWrangle$Close,xlab = "", ylab = "", col = "lightgreen", cex = 1.75,
           pch = as.numeric(input$rbSymbols))
      lines(1:length(dfWrangle$Date), dfWrangle$Close, col = "lightgreen",
            lty = input$rbLineType)
      title(
        "Stock Visualizer", 
        xlab = "Date", ylab = "Close", 
        cex.main = 2, cex.lab = 1.5,
        col.main = "maroon", col.lab = "navy"
      )
    })
}

shinyApp(ui = ui, server = server)
```

### Result: 
<img width="1440" alt="Dashboard" src="https://user-images.githubusercontent.com/98184898/166994075-6812bf4e-b29c-4bf8-9add-8a9790eb885e.png">

This an example of a dashboard demonstrating stock prices from both AMD and HPE
