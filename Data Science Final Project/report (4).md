## **Title and Author**

**Project Title: Final Project- Macroeconomic Indicators and Economic Forecasting**

Prepared for UMBC Data Science Master Degree Capstone by Dr Chaojie (Jay) Wang

Author Name: Jonathan Rius

Fall 2023 Semester

Link to the author's GitHub profile https://github.com/jonnie763

Link to the author's LinkedIn profile https://www.linkedin.com/in/jonathan-rius-17612b207/

Link to your PowerPoint presentation file https://github.com/DATA-606-2023-FALL-MONDAY/Rius_Jonathan/blob/main/docs/Jonathan%20Rius_Final%20Presentation%20.pptx

Link to your YouTube video https://youtu.be/Oo_g2CpV0NM?si=nnLJqtQNIyDoQ7ek


## **Background**

**What are some macroeconomic metrics and why do they matter?**


There are many macroeconomic metrics but this project aims to investigate four metrics. This projects aims to investigate inflation,GDP percent change,
unemployment rate and federal interest rate. Why do economists put such emphasis on such figures? These indicators give social scientists a good indication
on the health of the economy. From here governments can take action and employ policy changes to improve these figures so that damage is mitgated. What 
do they do? They will generally increase government spending(like with unemployment insurance, called fiscal policy), lower taxes and regulations or will adjust 
the interest rate (monetary policy). In short, these metrics are some of the best infomation we have in gauging the health of the economy and using policy changes
to fix holes in the economy.


How can one define each metric? *Inflation* (as measured in the project by CPI)  is the general price level rise of goods and services in an economy. 
Too much inflation can mean the economy is overheating while very low inflation can be a harbinger of economic recession. What about *GDP*? GDP stands
for gross domestic product (GDP),it  provides the overall value of the goods and services that the economy produces and indicates whether it is growing 
or slowing. The *Unemployment rate* is the percentage of the labor force without a job. *The federal interest rate*  refers to the target interest rate 
range set by the Federal Open Market Committee (FOMC).


**Research Questions**

What will inflation, GDP, unemployment rate and the federal interest look like in the future?

Can indicators predict the other (like with regression analysis)?

What are some correlations between economic indicators, and what are some trends that occur when looking at the data?

What is the frequency of most of the data? 

How can economists use this data to make policy changes?


## **Description of Data Sources and Data Elements**

**Data Source**

The data uses several files to which they are combined. 

1. FEDFUNDS.csv
2. GDP (4).csv
3. CPIAUCSL (3).csv
4. UNEMPLOYMENT RATE.csv

**Data Size and Records**

The combined size of the files is 30 kb. The combined dataframe has 277 rows combined. 
The following data goes back to 1954 and ends in the year 2023. 

**Data Structure**

| Column Name  | Description                                        | Data Type |
|--------------|----------------------------------------------------|-----------|
| Date         | Date in year, day, and month                        | Date time  |
|Interest Rate | Federal Interest Rate                               | float 64   |
| Inflation    | CPI                                                 | float 64   |
| GDP          |GDP percent change                                   | float 64   |
| U.S Rate     | Unemployment Rate                                   | float 64   |



The data source was combined through pandas dataframe function. The data types had objects that needed to converted to 
float and the date needed to be converted to datatime in order for data exploation to begin. 

## **Results of EDA**

![image](https://github.com/DATA-606-2023-FALL-MONDAY/Rius_Jonathan/assets/70355050/3628edbb-54e9-4010-924b-98cc88b6adfe)

<div align="justify">

A simple line graph is used to explore trends, annotations were made to explore the effect recessions had on indicators. As you can see gdp and
unemployment were most affected by recessions. Sometimes the interest rate was effected, and inflation remained relatively stable. There were some notable deflations and 
inflations during some of the recessions. Recessions have a substantial impact on indicators. In some recessions a high interest rate 
was used to combat inflation, in others, a low interest rate was used to surge the economy. Deflation occured in two recessions but not the other. 

---

![image](https://github.com/DATA-606-2023-FALL-MONDAY/Rius_Jonathan/assets/70355050/a2e36a68-2dd1-4909-b307-213603e8e531)

<div align="justify">
Interest rate had the highest range of numbers, and inflation had the least. Values typically ranged from 0 to 5 except for unemployment 
which had values more concentrated between 5 and 10. Interest rates are more variable because they can be easily manipulated in order 
to aid the ecoonmy or to control inflation. GDP and unemployment have outliners that typically occur during recessions. Rarely are values below
zero except during recessions. 

--- 
![image](https://github.com/DATA-606-2023-FALL-MONDAY/Rius_Jonathan/assets/70355050/f8827dca-949e-4d51-a344-6c84a4a1904a)

<div align="justify">
Not a lot of notable correlations. Since inflation rate and interest rate has the highest correlation regression analysis will be run. In reality, 
the fed will increase interest rates when inflation is too high or low so this makes sense. GDP and inflation correlation also occurs in nature, 
but this shows a relatively moderate one. Many of economic theory suggests these correlation should be higher but the only significant one is 
interest rate and inflation. Surprising. 

---

## **Results of ML**

**Arima Models and Regression Analysis** 

ARIMA Model will be used for Time Series Forecasting 


ARIMA stands for autoregressive integrated moving average model and is specified by three order parameters: (p, d, q). Autoregressive integrated moving average (ARIMA) models predict future values based on past values. 
ARIMA makes use of lagged moving averages to smooth time series data. They are widely used in technical analysis to forecast future security prices,statistics, and econometrics. 


Because there is a correlation between interest rate and inflation( the Fed will often raises interest rate to slow inflation) predictive models such as linear regression, random forest, and extra tree will be used. The 
regression analysis will be used to see if the interest rate (the predictor variable and the dependent variable) predicts inflation (the independent variable and target variable). 

---
![image](https://github.com/DATA-606-2023-FALL-MONDAY/Rius_Jonathan/assets/70355050/7764815c-b359-4a1d-bd17-254a8ecff645)

<div align="justify">
The model has a means squared error of 2.22 which is pretty low and the forecast is realistic if no recessions occur. While the model does not take into 
account those recessions, the forecast of the percent change going between 0 and 2.5 is a realistic one. This combined with a low MSE means its a decent model.
If one were to look at the EDA section the box plot showed similar, in where, the values ranged mostly from zero to three. For the most part if one would to look
at the graph's past values values ranged from zero to three, the box plot states something similar. The forecast also continues this trend where gdp percent change values
go from zero to three. A overall respectable model. 

---
![image](https://github.com/DATA-606-2023-FALL-MONDAY/Rius_Jonathan/assets/70355050/bb0eec22-e72b-4735-956f-90613ee045ac)

<div align="justify">
This means squared error is almost 8 and the model is somewhat unrealistic. In a nature setting the interest rate changes according the economic landscape to induce or slow down borrowing.
This model shows an increase of the interest rate over many years and this just not economically feasible. Overall the interest rate is highly variable in a natural setting but very 
fixed and only increasing here. 

---

![image](https://github.com/DATA-606-2023-FALL-MONDAY/Rius_Jonathan/assets/70355050/df561ccb-3295-4d42-82d2-860c44e6bbcc)


<div align="justify">
This has a high means squared error of 24, the model is also highly questionable, if continued past ten years the unemployment is in the negatives. This is  impossible. The unemployment rate
changes greatly to economic contacting and recession like events. The MSE is very high and unemployment rate, based off the box plot, flucuates between five and ten. This is continuously 
a downward slope, not realistic and a mathematically poor model. 

---
![image](https://github.com/DATA-606-2023-FALL-MONDAY/Rius_Jonathan/assets/70355050/0c0f6712-74b9-43ad-8fad-24105287bbb8) ![image](https://github.com/DATA-606-2023-FALL-MONDAY/Rius_Jonathan/assets/70355050/5ea767ac-2c70-43e9-9344-e55b13235eba)

<div align="justify">
To put it briefly there was a correlation between the interest rate and inflation, and a model was produced. The model has R2 of .47, so the model is adequate
but not strong enough for the interest rate to predict the target variable of inflation. When thinking about the theory, the interest rate should be correlated
as the interest rate flucuates to control inflation, especially if there is deflation or rampant inflation. Overally, and suprisingly, the interest rate does not predict
inflation as well as first predicted in the background portion. 


---
## **Conclusion and Further research**

Let’s split the conclusion into several categories. 

**Trends**: Basic exploratory analysis reveals that recessions cause certain indicators to fluctuate and that the data going high or low is a result of outside economic forces. Thus effects all economic indicators. 


**Frequency**: Indicators showed most data was concentrated between values zero and five, except for unemployment rate (which was five to ten). Inflation had the shortest range and interest rate had the highest range 
(thats because its easier to change). This also gives an idea of where most of the the data in the forecasting should be at. 

**Correlations**: Only one correlation (inflation vs interest rate) was above .5. In many economic situations the interest rate is used to control inflation. It was used as a predictor variable for regression analysis. The other correlation
GDP and inflation was very moderate. 

**Arima modeling**: All models besides the gdp will unrealistic, the gdp is the only plausible scenario (if recessions occur). If one were to look at GDP percent change one has to keep in mind that recessions will change the forecast.

**Regression analysis**: With interest rate as the predictor variable and the inflation as the target variable, the model’s R2 score was too low to be considered good. Therefore the interest rate does not necessarily predict inflation.
The model was okay and the correlation was only a bit above .6. 

**Further research:**

There is a a lot to gather from the information above. There are several key points, one the models and forecast were not as strong as one would hope and the regression analysis and correlations showed very modest pearson's coefficients. Its 
well known that the Fed changes interest rates to control inflation and that GDP, and inflation are correlated but the actual correlations of this empirical data shows correlations that were not that strong and models that were not that
robust. The exception was the GDP percent change forecast, which showed a low MSE (means squared error) and data that looked like the range of values present in the box plot data (values ranging from zero to three). This forecast had a low
MSE, and similar looking data to the box plot but does not flucuate in any way that you were anticipate GDP would during recessions. All this data suggests certains things. One GDP percent change usually flucuates between zero and three. Correlations
between indicators are not as drastic as one would be thinking versus the economic theory. And three interest rate does not necessarily predict inflation well. 

  In the future if I were a policy maker I would look at the relatively low correlation values and the low R2 scores of the predictive models and state that other policies to be implemented besides monteary policy (changing the interest rate).
Policies should include fiscal policy. I think this is strong evidence that fiscal policy is needed to control inflation, and good evidence for controlling unemployment and GDP. Things like adjusting governement spending and adjusting taxes are a 
necessary step in controlling inflation, gdp,and the unemployment rate. For the future, one could consider putting the variables of tax rate and govenment spending in the data to see if stronger correlations for regression analysis exist. For the arima models
perhaps including more data about the span of hundred years in order for the model to take into account flucuations that occurs during depression and recessions. Including the great depression of the 1930's might be good the arima models for example. 
As far as the forcasts a policy maker might consider the GDP as decent but the others as inaccurate. In short, for the future I would consider adding the tax rate, and government spending to the data frame to seek correlations for analysis and
also add great depression era data. For a policy maker I think this proves that fiscal policy is still important for affecting the economy and that only the GDP forecasts is the only good forecasts here that might hint at the future because of its 
closeness to the rest of the past data. 



## **References**

https://www.investopedia.com/articles/personal-finance/020215/top-ten-us-economic-indicators.asp

https://www.investopedia.com/terms/f/federalfundsrate.asp

https://www.investopedia.com/terms/u/unemploymentrate.asp

https://www.clevelandfed.org/center-for-inflation-research/inflation-101/why-does-the-fed-care-start

https://www.investopedia.com/ask/answers/112814/why-does-inflation-increase-gdp-growth.asp#:~:text=GDP%20is%20the%20monetary%20value,demand%20and%2For%20reduced%20supply.

https://www.google.com/search?q=arima+models&rlz=1C1ONGR_enUS1005US1005&oq=arima+models&gs_lcrp=EgZjaHJvbWUyCQgAEEUYORiABDIHCAEQABiABDIHCAIQABiABDIHCAMQABiABDIHCAQQABiABDIHCAUQABiABDIHCAYQABiABDIHCAcQABiABDIHCAgQABiABDIHCAkQABiABKgCALACAA&sourceid=chrome&ie=UTF-8

https://www.investopedia.com/ask/answers/111314/what-methods-can-government-use-control-inflation.asp#:~:text=Monetary%20policy%20primarily%20involves%20changing,way%20to%20help%20reduce%20inflation.
