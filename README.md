# STAT 519 Term Project: Data Analysis of DKSH Dataset



### I. Introduction
In this paper, I will analyze the DKSH dataset, which contains weekly sales data of industrial cables from Dec. 2011 to Oct. 2014. The DKSH dataset was acquired through an industry-university joint research project initiated by the course Statistical Data Analysis for Business and Management in my junior year at National Taiwan University. DKSH is a market expansion services provider in the Asia-Pacific area that procures materials and supplies for its customers. To further reduce its transportation and storage costs, DKSH hoped to forecast its sales (demand of customers) more accurately based on this dataset. However, since statistical methods covered in the course Statistical Data Analysis for Business and Management included only regression analysis and categorical data analysis, I could not analyze this dataset efficiently at that time. Thus, the purpose of this paper is to revisit the DKSH dataset and forecast the sales based on time series analysis. I will first perform exploratory data analysis, propose several possible time series models, and then conduct diagnostic tests to see if these models are good fits for the data. Finally, the conclusion will be made based on the model that best fits the dataset.

<br/>

### II. Data Exploration
The following figure shows the DKSH dataset.

<br/>
<p align="center"> <img src = "fig1_ts.png" width="60%" height="60%"> </p>
<div align="center"> Fig1: DKSH time series </div>
<br/>

The most significant feature of this time series is that there are several spikes, or so-called bulk orders in business. These spikes may be crucial in terms of decision making in business, yet they might cause a serious impact on our analysis. I also conducted a Dickey-Fuller test to check whether this time series is stationary, and the result shows a p-value of 0.01. Therefore, we may conclude that this time series is stationary.

To further explore this dataset, I plotted the lag plot of lag = 1, histogram of the dataset, and ACF and PACF. 

<br/>
<p align="center"> <img src = "fig2_explore1.png" width="60%" height="60%"> </p>
<div align="center"> Fig2: Preliminary data exploration </div>
<br/>

Both the lag plot and the histogram show that there are a few significant outliers, consistent with what we discovered in Fig1. The ACF and PACF plots also indicate that the outliers may have a significant impact on the correlations. For instance, the significant spike at lag = 19 may be caused by the correlation between t = 70 and t = 89, when there are two sales spikes in Mar. 2013 and Aug. 2013 with values of 12500 and 8780 respectively. Therefore, to better forecast this time series, I will replace these outliers with some other alternatives. However, as I mentioned earlier, please note that these spikes may be crucial in business decision making. For instance, in response to the outbreak of pandemic, retailers may want to prepare for unexpected sales increases to ensure that every customer has the items they need during home quarantine. Here I am replacing these outliers just to better estimate the rest of the sales that are considered as ordinary situations. 

I defined outliers as values that are three standard deviations away from the mean  and discovered the following four outliers: 
t = 32, t = 70, t = 89, and t = 129. I implemented Levinson-Durbin recursions to replace these outliers with one-step-ahead predictions. That is, for instance, for the outlier at t = 32, I replaced it with the prediction based on t = 1 to 31 through Levinson-Durbin recursions.  The following figure shows the time series with outliers being replaced. 

<br/>
<p align="center"> <img src = "fig3_tsnew.png" width="60%" height="60%"> </p>
<div align="center"> Fig3: DKSH time series with outliers replaced </div>
<br/>

Similarly, I plotted the lag plot of lag = 1, histogram, and ACF and PACF of the new time series.

<br/>
<p align="center"> <img src = "fig4_explore2.png" width="60%" height="60%"> </p>
<div align="center"> Fig4: Data exploration without outliers </div>
<br/>

The lag plot shows that there seems to be no significant correlation between X_(t+1) and X_t. The histogram shows that the time series may be approximately Gaussian but there is a significant bump on the right side of the distribution. The PACF plot shows that an AR(2) or AR(3) model may be a suitable choice; however, the ACF plot does not show an exponential decay which AR(p) models should have. Thus, an ARMA(p,q) may also be considered. 

<br/>

### III. 










