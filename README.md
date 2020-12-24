<h1>1. Software description</h1>
<br />
<h2>1.1 Objective</h2>
The objective of the software is to build a predictive model based on the number of deaths recorded in Italy from 2015 to 2019.
The prediction of the year 2020 obtained is in turn compared with the number of deaths from COVID-19 confirmed and disseminated by the Italian Civil Protection in order to estimate the possible number of COVID-19 deaths not recorded by official sources.
<br />
<h2>1.2 Components</h2>
The software is divided into four modules: “Analysis of complete ISTAT data”, “Data analysis of 7.357 municipalities”, “Complete provinces analysis” and “Region analysis”. 
Each module will be described individually below, making known the function it performs through the explanation of each script that composes it.
<br />
<h3>1.2.1 Analysis of complete ISTAT data</h3>
The first module: "Analysis of complete ISTAT data" has the purpose of estimating the possible number of COVID-19 deaths not registered for the total number of municipalities present in the official dataset released by ISTAT on 4 June 2020, which includes, from 1 January 2015 to 31 December 2019, the deaths registered in 7.903 Italian municipalities, while, in the first four months of 2020, the deaths registered in 7.270 municipalities. Figure 1.1 shows the structure, while Figure 1.2 shows how the module works. 
The following are the scripts that make it up.
<br/>


![](img/str-1-eng.png?raw=true)

Figure 1.1: structure of the model "Analysis of the complete ISTAT data"

![](img/fun-1-eng.png?raw=true)

Figure 1.2: operation of the module “Analysis of complete ISTAT data"

<b>Creation of time series of daily deaths</b>
<br/>
It processes the dataset released by ISTAT in order to return the related time series containing the daily deaths for the same period.

<b>Input </b>
- deaths.csv: ISTAT dataset relating to deaths registered from 1 January 2015 to 31 December 2019 in 7.903 municipalities, while from 1 January 2020 to 30 April 2020 in 7.270 Italian municipalities.

<b>Output</b>
- deaths_tot.csv: time series of the daily total deaths registered in Italy according to the ISTAT data sets from 1 January 2015 to 30 April 2020.

<b>Creation of time series COVID-19 confirmed deaths</b>
<br/>
It processes the dataset representing an increase in daily issued by Civil Protection of confirmed deaths due to COVID-19 and returns the time series containing the number of daily deaths due to COVID-19 from 24 February to 30 April 2020.

<b>Input</b>
- covid19.csv: dataset released by the Italian Civil Protection which shows the daily increase in deaths occurred for COVID-19 nationwide.

<b>Output</b>
- deaths_covid19.csv: time series of the total number of daily deaths for COVID-19 in Italy from 22 February to 30 April 2020.

<b>ARIMA model</b>
<br/>
It elaborates the time series relative to the daily total deaths and creates a predictive model ARIMA in order to return the prediction of the daily total deaths obtained from the model for the year 2020.

<b>Input</b>
- deaths_tot.csv: time series of the daily total deaths registered in Italy according to the ISTAT data sets.

<b>Output</b>
- predictions_daily_ARIMA.csv: time series relating to the result of the prediction of daily deaths obtained from the ARIMA predictive model.

<b>Comparison of confirmed COVID-19 deaths with ARIMA model prediction</b>
<br/>
It processes the time series of total daily deaths and confirmed daily deaths for COVID-19. It compares the two time series with the daily prediction obtained from the ARIMA predictive model in order to estimate the possible number of unrecorded COVID-19 deaths in the period from 24 February to 30 April 2020.

<b>Input </b>
- deaths_tot.csv: time series relating to deaths daily totals recorded in Italy according to the ISTAT dataset.
- Deaths_covid19.csv: time series of the number of daily deaths occurred in Italy from 22 February to 30 April 2020.
- predictions_daily_ARIMA.csv: time series relating to the result of the prediction of daily deaths obtained from the ARIMA predictive model.

<b>Output</b>
- The estimate of the possible total number of COVID-19 deaths predicted by the ARIMA model from February 24 to April 30, 2020 throughout Italy.
- The estimate of the possible number of deaths due to COVID-19 not registered according to the ARIMA model from 24 February to 30 April 2020 2020 on all Italian soil.

<b>SARIMA monthly model</b>
<br/>
It elaborates the time series of the daily deaths, converts it into a monthly time series and creates a predictive model SARIMA in order to return the prediction of the monthly total deaths obtained from the model for the year 2020.

<b>Input</b>
- decessi_tot.csv: time series relating to the total daily deaths recorded in Italy according to the ISTAT dataset.

<b>Output</b>
- predictions_SARIMA.csv: time series relating to the result of the prediction of monthly deaths obtained from the SARIMA predictive model.
- predictions_SARIMA_lower.csv: time series relating to the minimum limit of the confidence interval of the SARIMA model prediction.
- predictions_SARIMA_upper.csv: time series relating to the upper limit of the confidence interval of the SARIMA model prediction.

<b>Monthly comparison of confirmed COVID-19 deaths with SARIMA model prediction</b>
<br/>
It processes the time series of total daily deaths and confirmed daily deaths for COVID-19, converts them into monthly time series and compares them with the monthly prediction obtained from the SARIMA predictive model in order to estimate the possible number of deaths due to COVID-19 not registered in the months of March and April 2020.

<b>Input</b>
- deaths_tot.csv: time series relating to the total daily deaths recorded in Italy according to the ISTAT dataset.
- Decessi_covid19.csv: time series of the number of daily deaths occurred in Italy from 22 February to 30 April 2020.
- predictions_SARIMA.csv: time series relating to the result of the prediction of monthly deaths obtained from the SARIMA predictive model.
- predictions_SARIMA_lower.csv: time series relative to the minimum limit of the confidence interval of the model prediction.
- predictions_SARIMA_upper.csv: time series relating to the upper limit of the confidence interval of the model prediction.

<b>Output</b>
- The estimate of the possible minimum, average and maximum number of the total COVID-19 deaths predicted by the SARIMA model for the months of March and April 2020 throughout Italy.
- The estimate of the possible minimum, average and maximum number of deaths due to COVID-19 not registered according to the SARIMA model for the months of March and April 2020 throughout Italy.

<h3>1.2.2 Data analysis 7.357 municipalities</h3>
<br/>
The second module “Data analysis 7.357 municipalities” aims to estimate the possible number of deaths due to unregistered COVID-19 relating to 7.357 Italian municipalities out of a national total of 7.903 municipalities. Figure 2.1 shows the structure, while Figure 2.2 shows how the module works. 
Below are the scripts that make it up.


![](img/str-2-eng.png?raw=true)

Figure 2.1: structure of the module "Data analysis 7.357 municipalities"


![](img/fun-2-eng.png?raw=true)

Figure 2.2: operation of the module "Data analysis 7.357 municipalities"

<b>Creation of time series of deaths (7.357 municipalities)</b>
<br/>
It processes the dataset which includes, from 1 January 2015 to 30 June 2020, the relative deaths to 7.357 municipalities in Italy in order to return the relative time series containing the daily deaths of 7.357 municipalities.

<b>Input</b>
- deaths_istat_7.357municipalities.csv: ISTAT dataset relating to deaths registered from 1 January 2015 to 30 June 2020 in 7.357 municipalities out of a total of 7.903 Italian municipalities.

<b>Output</b>
- time_series.csv: time series of the daily total deaths registered in Italy in 7357 seconds the ISTAT common dataset from January 1, 2015 to June 30, 2020.

<b>Creation of time series COVID-19 confirmed deaths</b>
<br/>
It elaborates the dataset released by the Civil Protection alleging '' daily increase in confirmed deaths due to COVID-19 and returns the time series containing the number of daily deaths due to COVID-19 from 24 February to 30 June 2020.

<b>Input</b>
- deathspc_covid_30june.csv: dataset released by the Italian Civil Protection where the increase is reported number of deaths from COVID-19 nationwide.

<b>Output</b>
- deaths_covid19_30june.csv: time series of the total number of daily deaths due to COVID-19 occurred in Italy from 22 February to 30 June 2020.

<b>ARIMA model</b>
<br/>
It processes the time series relating to the total daily deaths of the 7.357 municipalities of Italy in order to create the ARIMA predictive model and return the prediction of total daily deaths for the year 2020.

<b>Input</b>
- time_series.csv: time series relating to total daily deaths recorded in Italy in 7.357 municipalities according to the ISTAT dataset from 1 January 2015 to 30 June 2020.

<b>Output</b>
- predictions_daily_ARIMA_7357comuni: time series relating to the result of the prediction of daily deaths obtained from the ARIMA predictive model for the 7.357 municipalities.

<b> of confirmed COVID-19 deaths with ARIMA model prediction</b>
<br/>
Processes the time series of total daily deaths of 7.357 municipalities in Italy and confirmed daily deaths for COVID-19 and compares them with the daily prediction obtained from the ARIMA predictive model in order to estimate the possible number of deaths due to COVID-19 not registered by 7.357 municipalities in Italy in the period from 24 February to 30 June 2020.

<b>Input</b>
- time_series.csv: time series relating to the total daily deaths recorded in Italy in 7.357 municipalities according to the ISTAT dataset from 1 January 2015 to 30 June 2020.
- deaths_covid19_30june.csv: time series of the total number of daily deaths from COVID-19 which occurred in Italy from 22 February to 30 June 2020.
- predictions_daily_ARIMA_7357comuni: time series relating to the result of the prediction of daily deaths obtained from ARIMA predictive model for 7.357 municipalities.

<b>Output</b>
- The estimate of the possible total number of COVID-19 deaths predicted by the ARIMA model from 24 February to 30 June 2020 for 7.357 municipalities out of a total of 7.903 Italian municipalities.
- The estimate of the possible number of deaths due to COVID-19 not registered according to the ARIMA model from 24 February to 30 June 2020 for 7.357 municipalities out of a total of 7.903 Italian municipalities.

<b>SARIMA monthly model</b>
<br/>
It elaborates the time series relating to daily deaths of 7.357 municipalities of Italy, converts it into a monthly time series, elaborates it and creates the SARIMA predictive model. The script returns the forecast of the total monthly deaths obtained from the model for the year 2020.

<b>Input</b>
- time_series.csv: time series relating to the total daily deaths recorded in Italy in 7.357 municipalities according to the ISTAT dataset from 1 January 2015 to 30 June 2020.

<b>Output</b>
- predictions_SARIMA_7357comuni.csv: time series relating to the result of the prediction of monthly deaths obtained from the SARIMA predictive model for 7.357 Italian municipalities.
- predictions_SARIMA_lower.csv: time series relating to the minimum limit of the confidence interval of the prediction of the SARIMA model for 7.357 Italian municipalities.
- predictions_SARIMA_upper.csv: time series relating to the maximum limit of the confidence interval of the prediction of the SARIMA model for 7.357 Italian municipalities.

<b>Monthly comparison of confirmed COVID-19 deaths with SARIMA model prediction</b>
<br/>
It processes the time series of the total daily deaths of the 7.357 municipalities of Italy and of the confirmed daily deaths of COVID-19, converts them into monthly time series and compares them with the monthly prediction obtained from the model SARIMA predictive in order to estimate the possible number of deaths due to COVID-19 not registered in the months of March, April, May and June 2020.

<b>Input</b>
- time_series.csv: time series relating to the total daily deaths registered in Italy in 7.357 municipalities according to the dataset ISTAT from 1 January 2015 to 30 June 2020.
- deaths_covid19_30june.csv: time series of the total number of deaths per day due to COVID-19 which occurred in Italy from 22 February to 30 June 2020.
- predictions_SARIMA_7357municipalities.csv: time series relating to the result of the prediction of deaths obtained from the SARIMA predictive model for 7.357 Italian municipalities.
- predictions_SARIMA_lower.csv: time series relating to the minimum limit of the confidence interval of the prediction of the SARIMA model for 7.357 Italian municipalities.
- predictions_SARIMA_upper.csv: time series relating to the maximum limit of the confidence interval of the prediction of the SARIMA model for 7.357 Italian municipalities.

<b>Output</b>
- The estimate of the possible minimum, average and maximum number of the total COVID-19 deaths predicted by the SARIMA model for the months of March, April, May and June 2020 in 7.357 municipalities out of a total of 7.903 Italian municipalities.
- The estimate of the possible minimum, average and maximum number of deaths due to COVID-19 not registered according to the SARIMA model for the months of March, April, May and June 2020 in 7.357 municipalities out of a total of 7.903 Italian municipalities.

<h3>1.2.3 Data analysis complete provinces</h3>
<br/>
The third module: "Complete provinces data analysis" has the purpose of estimating the possible number of deaths due to unregistered COVID-19 relating to the provinces for which, in the ISTAT dataset which includes 7.357 municipalities, the total daily deaths of each municipality in the province.
Figure 3.1 shows the structure, while figure 3.2 shows how the module works. 
Below are the scripts that compose it.


![](img/str-3-eng.png?raw=true)

Figure 3.1: structure of the module "Data analysis complete provinces"


![](img/fun-3-eng.png?raw=true)

Figure 3.2: operation of the module "Data analysis complete provinces"

<b>Research complete provinces</b>
<br/>
It processes the dataset of daily totals 7.357 deaths related to the municipalities of Italy and compares it to the dataset released by ISTAT which includes the total daily deaths from 1 January 2015 to 31 December 2019 relating to the total number of Italian municipalities which amounts to 7.903. The purpose of the research is to find the municipalities that diverge from the two datasets and bring them back to the province to which they belong, in order to eliminate the incomplete provinces of each municipality from the analysis. Finally, the script releases the dataset containing the information relating to the remaining complete provinces.

<b>Input</b>
- deaths_istat_7.357municipalities.csv: ISTAT dataset relating to deaths registered from 1 January 2015 to 30 June 2020 in 7.357 municipalities out of a total of 7.903 Italian municipalities.
- deaths.csv: ISTAT dataset relating to deaths registered from 1 January 2015 to 31 December 2019 in 7.903 municipalities, while from 1 January 2020 to 30 April 2020 in 7.270 Italian municipalities.

<b>Output</b>
- missing_monicipalities_provinces.csv: dataset containing information relating to 547 common, namely the number of municipalities that differ from the two datasets placed on the input.
- df_complete_municipalities.csv: dataset relating to deaths registered from 1 January 2015 to 30 June 2020 in the municipalities of the complete provinces.

<b>Creation of complete provinces time series</b>
<br/>
It processes the dataset containing the data of the complete provinces found and returns the time series of daily deaths from 1 January 2015 to 30 June 2020.

<b>Input</b>
- df_complete_municipalities.csv: dataset relating to deaths registered from 1 January 2015 to 30 June 2020 in the municipalities of the complete provinces.

<b>Output</b>
- time_series_8provinces.csv: time series relating to the total daily deaths recorded from 1 January 2015 to 30 June 2020 in the municipalities of the complete provinces.

<b>Creation of time series of deaths COVID-19 confirmed complete provinces</b>
<br/>
It processes the dataset containing the daily increase in deaths for COVID-19 of the complete provinces and returns the time series of daily deaths from March 22 to May 22, 2020.

<b>Input</b>
- deaths_covid_provinces.csv: dataset relating to the increase in daily deaths from COVID-19 recorded from March 22 to May 22 in the complete provinces.

<b>Output</b>
- death_covid19_8provinces.csv: time series relating to the number of daily deaths from COVID-19 recorded from March 22 to May 22 in the complete provinces.

<b>ARIMA model</b>
<br/>
It elaborates the time series of daily deaths recorded in the municipalities of the complete provinces, creates the ARIMA predictive model and returns the prediction of total daily deaths for the year 2020 obtained from the model.

<b>Input</b>
- time_series_8provinces.csv: time series relating to the total daily deaths recorded from 1 January 2015 to 30 June 2020 in the municipalities of the complete provinces.

<b>Output</b>
- predictions_daily_ARIMA_8provinces.csv: time series relating to the result of the prediction of daily deaths obtained from the ARIMA predictive model for the complete provinces.
 
<b>Comparison of confirmed COVID-19 deaths with ARIMA model prediction</b>
<br/>
It elaborates the time series of total daily deaths and daily deaths for COVID-19 of the complete provinces and compares them with the daily prediction obtained from the ARIMA model in order to estimate the possible number of deaths for COVID-19 not registered in the complete provinces from 22 March to 22 May 2020.

<b>Input</b>
- time_series_8provinces.csv: time series relating to the total daily deaths recorded from 1 January 2015 to 30 June 2020 in the municipalities of the complete provinces.
- deaths_covid19_8provinces.csv: time series relating to the number of daily deaths from COVID-19 recorded from 22 March to 22 May in the complete provinces.
- predictions_daily_ARIMA_8provinces.csv: time series relating to the result of the prediction of daily deaths obtained from the ARIMA predictive model for the complete provinces.

<b>Output</b>
- The estimate of the possible total number of deaths from COVID-19 foreseen by the ARIMA model for the complete provinces in the period from March 22 to May 22, 2020.
- The estimate of the possible number of deaths from COVID-19 not registered according to the ARIMA model for the complete provinces in the period from March 22 to May 22, 2020.

<b>SARIMA monthly model</b>
<br/>
It processes the time series of daily deaths recorded in the municipalities of the complete provinces, converts it into a monthly time series and creates the SARIMA monthly predictive model. Finally, it returns the forecast of the total monthly deaths obtained from the model for the year 2020.

<b>Input</b>
- time_series_8provinces.csv: time series relating to the total daily deaths recorded from 1 January 2015 to 30 June 2020 in the municipalities of the complete provinces.

<b>Output</b>
- predictions_SARIMA_7357municipalities.csv: time series relating to the result of the prediction of monthly deaths obtained from the SARIMA predictive model for the complete provinces.
- predictions_SARIMA_lower.csv: time series relating to the minimum limit of the confidence interval of the prediction of the SARIMA model for the complete provinces.
- predictions_SARIMA_upper.csv: time series relating to the upper limit of the confidence interval of the SARIMA model prediction for complete provinces.

<b>Monthly comparison of confirmed COVID-19 deaths with SARIMA model prediction</b>
<br/>
It processes the time series of total daily deaths and deaths from COVID-19 of the complete provinces, converts them into monthly time series and compares them with the monthly prediction obtained from the SARIMA model in order to estimate the possible number of unrecorded COVID-19 deaths in the complete provinces in April 2020.

<b>Input</b>
- time_series_8provinces.csv: time series relating to the total daily deaths recorded from 1 January 2015 to 30 June 2020 in the municipalities of the complete provinces.
- deaths_covid19_8provinces.csv: time series relating to the number of daily deaths from COVID-19 recorded from 22 March to 22 May in the complete provinces.
- predictions_SARIMA_7357comuni.csv: time series relating to the result of the prediction of monthly deaths obtained from the SARIMA predictive model for the complete provinces.
- predictions_SARIMA_lower.csv: time series relating to the minimum limit of the confidence interval of the prediction of the SARIMA model for the complete provinces.
- predictions_SARIMA_upper.csv: time series relating to the upper limit of the confidence interval of the SARIMA model prediction for complete provinces.

<b>Output</b>
- The estimate of the possible minimum, average and maximum number of total COVID-19 deaths predicted by the SARIMA model in April 2020 for the complete provinces.
- The estimate of the possible minimum, average and maximum number of deaths from COVID-19 not registered according to the SARIMA model in April 2020 for the complete provinces.

<h3>1.2.4 Data analysis by regions</h3>
<br/>
The fourth and last module: “Analysis by regions” has the purpose of estimating the possible number of deaths from COVID-19 not registered for each Italian region. Figure 4.1 shows the structure, while Figure 4.2 shows how the module works. Below are the scripts that make it up.


![](img/str-4-eng.png?raw=true)

Figure 4.1: structure of the module "Data analysis by regions"


![](img/fun-4-eng.png?raw=true)

Figure 4.2: operation of the module “Data analysis by regions"

<b>Creation of regional time series of total deaths</b>
<br/>
It processes the dataset relating to the total daily deaths of the 7.357 Italian municipalities in order to return the monthly time series of total deaths for every region of Italy. The reference period runs from January 2015 to June 2020.

<b>Input</b>
- deaths_istat_7.357municipalities.csv: ISTAT dataset relating to deaths registered from 1 January 2015 to 30 June 2020 in 7.357 municipalities out of a total of 7.903 Italian municipalities.

<b>Output</b>
- regions /region_name.csv: time series relating to the number of total monthly deaths recorded in the region from January 2015 to June 2020.  

<b>Creation of regional time series of confirmed COVID-19 deaths</b>
<br/>
It processes the dataset relating to the increase in deaths for COVID-19 issued by the Civil Protection and creates the monthly time series of deaths for each region of Italy. The reference months are: March, April, May and June 2020. Subsequently, the time series of each region is multiplied by the percentage of regional coverage of the municipal data released by ISTAT and returned as output.

<b>Input</b>
- table_coverage_istat.xlsx: table for each Italian region the percentages of completeness of the data relating to the total daily deaths issued by ISTAT on a municipal basis as of 31 May 2020.
- covid19_regions.csv: dataset issued by the Italian Civil Protection relating to the increase of daily deaths from COVID-19 at the regional level.

<b>Output</b>
- regions_weights/region_name.csv: time series relating to the number of deaths from COVID-19 recorded in the region in the months of March, April, May and June 2020. The time series has been multiplied by the percentage of completeness of the data relating to total daily deaths present in the coverage_table_istat.xlsx.

<b>Region name - SARIMA monthly</b>
<br/>
It elaborates the time series of the total monthly deaths of the reference region and creates the SARIMA model in order to return the forecast of the total monthly deaths of the region obtained from the model for the year 2020.

<b>Input</b>
- regions /region_name.csv: time series relating to the number of total monthly deaths recorded in the region from January 2015 to June 2020. 

<b>Output</b>
- predictions_SARIMA_name-region.csv: time series relating to the result of the prediction of monthly deaths obtained from the SARIMA predictive model for the region.
- predictions_SARIMA_name-region._lower.csv: time series relating to the minimum limit of the confidence interval of the regional prediction of the SARIMA model.
- predictions_SARIMA_name-region_upper.csv: time series relating to the maximum limit of the confidence interval of the regional prediction of the SARIMA model.

<b>Region name comparison</b>
<br/>
It processes the time series of total monthly deaths and deaths from COVID-19 related to the region under consideration and compares them with the forecast of monthly deaths for the year 2020 obtained from the SARIMA predictive model in order to estimate the possible number of unrecorded COVID-19 deaths in March, April, May and June 2020 in the aforementioned region.

<b>Input</b>
- regions /region-name.csv: time series relating to the number of total monthly deaths recorded in the region from January 2015 to June 2020. 
- weighted regions/region-name.csv: time series relating to the number of deaths due to COVID- 19 recorded in the region in the months of March, April, May and June 2020. The time series has been multiplied by the percentage of completeness of the data relating to the total daily deaths present in the table_copteggio_istat.xlsx.
- predictions_SARIMA_region-name.csv: time series relating to the result of the prediction of monthly deaths obtained from the SARIMA predictive model for the region.
- predictions_SARIMA_region-name._lower.csv: time series relating to the minimum limit of the confidence interval of the regional prediction of the SARIMA model.
- predictions_SARIMA_region-name_upper.csv: time series relating to the maximum limit of the confidence interval of the regional prediction of the SARIMA model.

<b>Output</b>
- The estimate of the possible minimum, average and maximum number of total COVID-19 deaths predicted by the SARIMA model in March, April, May and June 2020 for the region.
- The estimate of the possible minimum, average and maximum number of deaths from unrecorded COVID-19 according to the SARIMA model in March, April, May and June 2020 for the region.

