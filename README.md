# STAT 519 Term Project: Data Analysis of DKSH Dataset

### I. Introduction
In this paper, I will analyze the DKSH dataset, which contains weekly sales data of industrial cables from Dec. 2011 to Oct. 2014. The DKSH dataset was acquired through an industry-university joint research project initiated by the course Statistical Data Analysis for Business and Management in my junior year at National Taiwan University. DKSH is a market expansion services provider in the Asia-Pacific area that procures materials and supplies for its customers. To further reduce its transportation and storage costs, DKSH hoped to forecast its sales (demand of customers) more accurately based on this dataset. However, since statistical methods covered in the course Statistical Data Analysis for Business and Management included only regression analysis and categorical data analysis, I could not analyze this dataset efficiently at that time. Thus, the purpose of this paper is to revisit the DKSH dataset and forecast the sales based on time series analysis. I will first perform exploratory data analysis, propose several possible time series models, and then conduct diagnostic tests to see if these models are good fits for the data. Finally, the conclusion will be made based on the model that best fits the dataset.

### II. Data Exploration
The following figure shows the DKSH dataset.

<p align="center">
  ![image](https://github.com/tonychu-yw/STAT-519-Time-Series-Analysis/blob/master/fig1_ts.png)
  Fig1: DKSH time series
</p>

The most significant feature of this time series is that there are several spikes, or so-called bulk orders in business. These spikes may be crucial in terms of decision making in business, yet they might cause a serious impact on our analysis. I also conducted a Dickey-Fuller test to check whether this time series is stationary, and the result shows a p-value of 0.01. Therefore, we may conclude that this time series is stationary.
