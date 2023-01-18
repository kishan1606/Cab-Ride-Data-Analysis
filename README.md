# Cab-Ride-Data-Analysis
**ABSTRACT**

Uber and Lyft have dominated the ride-sharing market during the past few years. Convenience is the key to Uber and Lyft's success. They offer their customers on-demand rides to any location for a fair price and within a short period of time. It is obvious that each company has a different pricing plan because charges for each trip change depending on several aspects including the type of service, travel distance, pickup location, etc. In this project, we'll use a dataset from Uber and Lyft, which we'll analyze to better understand the dynamics of pricing and the differences between the two companies' way of calculating rates. Through this project, we will learn about a variety of sophisticated processes used in data visualization. enable us to identify the patterns in this large organization's data. We are going to use a technique to preprocess the data and then train the model to predict the prices.

 **INTRODUCTION**

Personal transportation can be a helpful feature in the hectic life of city dwellers. The use of taxicab services has grown significantly recently. Its market expansion has been quite domineering. Traditional taxis have long been a dependable mode of transportation, but it appears that new online ride-sharing services, such as Uber, Lyft, and others, are beginning to gain traction and may eventually displace traditional taxi services. Several factors are causing people to switch to online ride-sharing services. You can't reserve a traditional cab for a specific time when trying to hail one. To ensure that it will arrive on time, you must phone a reasonable amount of time in advance. The option to schedule your pick-up in advance is one of the useful features of online taxi services. By being closer to the pickup location when you need it, this increases the driver's dependability. However, the primary factor driving people to online taxi services is the fact that they are less expensive than a taxi. Additionally, they have a predetermined flat rate, so if the travel takes longer than anticipated, the price won't increase. Additionally, the "share my ETA" feature allows others who have been granted access by the passenger to view the precise route that is being taken in real time. These qualities are causing these taxi services to expand more quickly. These businesses generate a large amount of data daily due to their online operations. In this project, we'll utilize a basic dataset of Uber and Lyft trips from 11-26-2018 to 12-18-2018 to evaluate the dynamics of pricing and the differences between Uber and Lyft's special rates. To eliminate unnecessary data and increase the dependability of the data, we have performed data preprocessing. Then, after preprocessing the data, we built a model based on the data, and we discovered the accuracy of the model that had performed the best.

**PROBLEM STATEMENTS**

Some of the problem statements that we are going to answer in this modeling evaluation are as follows-

- Which features are most relevant?
- Are any features correlated with one another?
- Performance comparison across models.
- Which company offers the most rides?
- Most common pickup locations?
- Most common drop up locations?
- When do most rides occur during the day?
- What are the minimum and maximum ride prices?
- What are the average costs for all

**DATA PROCESSING**
1. **Data Sources**

  [Link for Dataset](https://www.kaggle.com/datasets/brllrb/uber-and-lyft-dataset-boston-ma)

    The dataset contains Uber & Lyft trips from 11-26-2018 to 12-18-2018, which I will analyze to understand the factors affecting the dynamic pricing and the  difference   between Uber and Lyft's special prices.The datasets used in this project have been imported from Kaggle. The dataset contains 693071 rows and 57 columns.

  ![Aspose Words fb767b01-769e-4ff6-8d4e-d3e79b1d4572 001](https://user-images.githubusercontent.com/57938757/213277714-de69d1c1-e244-4a43-ab97-b016179afbd9.png)


2. **Issues in data and changes made**
- Rideshare Dataset:
  - There are a lot of missing values and column label mismatch among the files in the dataset.
  - There are a lot of missing values for source and destination names.
  - Date Time formats are different among different files.
  - Same features had different data type values in different files.
  - Changes made:
    - Renamed columns among all files to common labels
    - Dropped features that were not present among all files (SunriseTime, SunsetTime, MoonPhase etc)
    - Used values of latitude longitude to populate missing source and destination values among the files.
    - Used started time and ended time of the trip to calculate trip duration and added it wherever it was missing.
    - Formatted date time and other feature values in all files to have a single standard format.
    - Added additional columns with Day of the week from the date field.
- Weather Data:
- The date format is different from the datasets.
- Changes made:
- Date format has been changed to reflect the same format as dataset.

![Aspose Words fb767b01-769e-4ff6-8d4e-d3e79b1d4572 002](https://user-images.githubusercontent.com/57938757/213277938-9bfd01dc-5bcf-4008-9ce4-357633fa2a48.png)

3. **Observations**
- Data gathering and manipulation takes a lot of time and effort to identify differences among different files formats and column names, missing data. Most of the time in this project has been spent on this step.
- So far we never faced bottlenecks with the laptops we had but as soon as the data size increases, we have to be really careful about the code to make these data manipulations. We wanted to optimize this and rewrote the script using pandas and treating the columns as vectors
4. **Final Data Description**
- We ended up with the following 23 features after all of the data cleansing and preparation.



|Features selected|
| - |
|distance|
|surge\_multiplier|
|Fri|
|Sat|
|Sun|
|Shared|
|Lyft XL|
|Lux Black XL|
|LUX|
|Lux Black|
|Mostly Cloudy|
|Drizzle|
|UberPool|
|UberXL|
|Black|
|Black SUV|
|WAV|
|Possible Drizzle|
|Rain|
|Partly Cloudy|
|Overcast|
|Light Rain|
|Foggy||

**EXPLORATORY DATA ANALYTICS**

**1 Visualizations**

- Who offers the most rides, Uber or lyft?

  ![Aspose Words fb767b01-769e-4ff6-8d4e-d3e79b1d4572 003](https://user-images.githubusercontent.com/57938757/213279277-043cd134-19f9-4bd7-bac4-a50f4dcd64b4.jpeg)

  As we can observe from the above graph more than 50% of the rides were for uber and the rest are from lyft.

- Lyft: Per Surge Multiplier - Total Rides vs Hour of the Day

  ![Aspose Words fb767b01-769e-4ff6-8d4e-d3e79b1d4572 004](https://user-images.githubusercontent.com/57938757/213279580-fdf66c0f-13cf-4427-bccc-1d4bdc1094bf.jpeg)

  This plot examined the total number of Lyft rides per day of the week and their respective surge multiplier. Regardless of surge multiplier, the highest number of rides occurred on Tuesday and Wednesday.

- Top 10 most Popular Stations

  The below plot examines the maximum number of times a cab was booked (Uber and Lyft) for a particular source to a particular destination.

  As we can see from the graph, the trip from Financial District to South Station has the highest number of cab bookings.

  ![Aspose Words fb767b01-769e-4ff6-8d4e-d3e79b1d4572 005](https://user-images.githubusercontent.com/57938757/213279666-6993ace6-367e-4226-a026-ec46e70d7754.jpeg)

- Weather affects the rides

  It's very obvious that there is a relationship between weather condition and the number of rides, The number of rides when the weather is (overcast, clear, mostly and partly cloudy) is significantly different than when the weather is (rain,foggy, possible drizzle and drizzle), the number of rides when the weather is (overcast, clear, mostly and partly cloudy) is much higher than when the weather is (rain,foggy, possible drizzle and drizzle)

  ![Aspose Words fb767b01-769e-4ff6-8d4e-d3e79b1d4572 006](https://user-images.githubusercontent.com/57938757/213279739-01f85d83-b733-4e3a-8351-00c1fbfc27bf.jpeg)

  The corpus of the column named “long summary” is as follows-

  ![Aspose Words fb767b01-769e-4ff6-8d4e-d3e79b1d4572 007](https://user-images.githubusercontent.com/57938757/213279763-636e9b8c-6330-402b-a7a7-6395d574c4ed.png)

- Temperature affects the ride's price

  Similar to the above graph and comparison, the number of rides fluctuate with the temperature. This fluctuation is realized in the graph below.

  ![Aspose Words fb767b01-769e-4ff6-8d4e-d3e79b1d4572 008](https://user-images.githubusercontent.com/57938757/213280060-8234b547-9e99-4572-912e-b66721aeeab2.jpeg)

- Time division on basis of hour

  The below Treemap shows the cab booking interval in a 24 hour time period. Darker the shade of blue, more the number of rides were booked in that 1 hour interval.

  ![Aspose Words fb767b01-769e-4ff6-8d4e-d3e79b1d4572 009](https://user-images.githubusercontent.com/57938757/213280090-a1e9051c-9edf-482e-84a7-b00e8246a8b2.jpeg)

- Price range between Uber and Lyft

  The Price range for Uber and Lyft rides were then plotted, using a Boxplot and a Histogram. The results of the plottings are as follows-

  - Boxplot

    ![Aspose Words fb767b01-769e-4ff6-8d4e-d3e79b1d4572 010](https://user-images.githubusercontent.com/57938757/213280134-bec150e4-a37d-4448-aa56-d1bed92b714c.jpeg)

    As we can see that there are pretty distinct differences in the pricing of both Uber and Lyft, and both the plots have some outliers.

  - Histogram

    ![Aspose Words fb767b01-769e-4ff6-8d4e-d3e79b1d4572 011](https://user-images.githubusercontent.com/57938757/213280303-7e0f81b1-7801-4fe9-8de2-a723bbe52794.jpeg)

  This graph displays the price range for Uber and Lyft based on how frequently they occur. In this graph, Lyft's data are represented by the green color, whereas UBER's data are represented by the blue color. Lyft's minimum price is 2.5, whereas Uber's is 4.5. And the maximum price for Lyft is 97.5 and for Uber is 89.5.

   - Heatmap for specific location and hours

    ![Aspose Words fb767b01-769e-4ff6-8d4e-d3e79b1d4572 012](https://user-images.githubusercontent.com/57938757/213280355-a1a1aad6-0f4d-4d62-9999-b69518c2b0f6.jpeg)

  For Lyft, the price of “Share” products does not change with Hours. However, for “Normal” products, the price at 1pm is slightly higher than other hours. For “SUV” , 5am is higher and for “Lux”, 1–2pm is higher. For “Lux SUV”, 10am is higher. There is no consistent pattern in Lyft so that certain hours have higher prices for all types of products. Therefore, the relationship between hours and price may not have an universal rule but depends on specific circumstances for Lyft. As for Uber, the price of “Share” products is higher at night from 10pm to 12am. For “Normal” products, the price at 10am, 1pm, and 3pm are higher than other hours, and it is interesting to see that the price at 1pm is also higher for “SUV”, “Lux”, and “Lux SUV”.


**DATA MODELLING**

1. **Linear Regression Model**

Linear regression analysis predicts the value of one variable depending on the value of another. The variable you wish to forecast is referred to as the dependent variable. The variable you are using to forecast the value of the other variable. In the below mentioned scatter plot, we have the residual vs fitted plot which is the result of removing a few predictors based on p-values. We choose to predict prices with predictors as temperature, wind,snow, day of the week, year, rain. We analyzed that the R-Squared value for the predictors is 0.9365.

  ![Aspose Words fb767b01-769e-4ff6-8d4e-d3e79b1d4572 013](https://user-images.githubusercontent.com/57938757/213280727-77b5925c-1b66-4476-b8c1-33aa70502a79.jpeg)

  ![Aspose Words fb767b01-769e-4ff6-8d4e-d3e79b1d4572 014](https://user-images.githubusercontent.com/57938757/213280756-1bbdc961-aa70-43bb-9981-ff264446409b.jpeg)


2. **Decision Tree**

A decision tree is a specific kind of flowchart that illustrates a direct route to a choice. It is a kind of algorithm for categorizing data that uses conditional "control" statements. A decision tree begins at a single node (or "node") and branches out in two or more ways from there. Each branch presents various potential results, combining a range of choices and unforeseen circumstances until a decisive result is reached. Because they divide complex data into more digestible pieces, decision trees are very helpful for data analytics and machine learning.

Decision Tree model for Uber -

  ![Aspose Words fb767b01-769e-4ff6-8d4e-d3e79b1d4572 015](https://user-images.githubusercontent.com/57938757/213280866-762c7844-5a27-41b8-abb4-4c07c3eea4d6.png)

Decision Tree model for Lyft -

  ![Aspose Words fb767b01-769e-4ff6-8d4e-d3e79b1d4572 016](https://user-images.githubusercontent.com/57938757/213280891-a3697453-3421-4c2b-b59b-59017fb49712.png)

3. **Random Forest**

We applied a random forest model on our data to make it like a baseline model to compare our linear models against. The algorithm would make splits to decrease the overall error rate and hence would ideally fit the data more closely and would serve as a good baseline model to compare the above models too.

The Random Forest model was applied to the dataset and various parameters were evaluated.

We got the below results -

  ![Aspose Words fb767b01-769e-4ff6-8d4e-d3e79b1d4572 017](https://user-images.githubusercontent.com/57938757/213280947-4b0d4f6f-f9ee-4fc8-93de-3f1212b9aa4d.png)

  ![Aspose Words fb767b01-769e-4ff6-8d4e-d3e79b1d4572 018](https://user-images.githubusercontent.com/57938757/213280974-f9808c41-7bba-46c1-ba09-e676acfa41aa.png)


**MODEL EVALUATION**

We use several assessment criteria to measure the prediction outcomes of these diverse strategies in handling the trip prediction problem in order to evaluate their performance. Below mentioned are the statistics –

For Linear Regression -

  ![Aspose Words fb767b01-769e-4ff6-8d4e-d3e79b1d4572 019](https://user-images.githubusercontent.com/57938757/213281042-8b5c0713-1da2-4fd9-9762-6d34262e91b3.png)

For Random Forest -

  ![Aspose Words fb767b01-769e-4ff6-8d4e-d3e79b1d4572 020](https://user-images.githubusercontent.com/57938757/213281076-526b366f-4094-45a4-927f-888a1b44ee65.png)

For Decision Tree -

  ![Aspose Words fb767b01-769e-4ff6-8d4e-d3e79b1d4572 021](https://user-images.githubusercontent.com/57938757/213281099-82681153-ed6e-4ca4-865a-ead080fe2f25.png)

Best Score models -

![Aspose Words fb767b01-769e-4ff6-8d4e-d3e79b1d4572 022](https://user-images.githubusercontent.com/57938757/213281144-ba482cb8-05b3-4bfc-83b8-dc298fc8a8d2.png)

As we can observe from the above table that the best score for UBER data is achieved by the Linear regression model by 88.089834 and that for the LYFT is achieved by the Random Forest model by 86.733867. The overall accurate model is Random Forest.

Based on different metrics, we can conclude that the Random Forest model is the best model and thus we could consider this as our final model.


**OBSERVATIONS & CONCLUSION**

From the exploratory data analysis, we noticed that:

- We have performed EDA to understand the data well.
- For both Uber and Lyft, the overall model, as well as all predictors used were statistically significant.
- For Lyft, our model explained 91.31% of the variability in Log(Fare) while for Uber, our model explained 80.67% of the variability in Log(Fare).
- Uber is more affordable, but Lyft also offers fair competition.
- Long distance travel is more expensive, but not linearly so. However, a spike may change the price depending on the time and demand.
- Lyft's base pricing for shared cabs are cheaper than those for its premium "Black" and "Black XL" vehicles.
- The Random Forest's altered results ended up being the best.


**PLANNED FUTURE WORK**

This issue can be approached in a variety of ways and from different angles. The models may be improved to increase forecast precision. For instance, we could think about the interactions between the variables, like the predictors for distance and cab types. With the ideal values for the parameters, we can also investigate various Random Forests prediction error rates. We intend to take into account extraneous data to include traffic conditions and times. We also plan to study why we saw large standard deviation of fares for a given source and destination. Using the knowledge gained from this project, we’d like to build an improved model with more useful features and try to use new data formats like Avro or Parquet so that the row/column operations happen more efficiently.


**REFERENCES**
- Srinivas, B. Ankayarkanni and R. S. B. Krishna, "Uber Related Data Analysis using Machine Learning," 2021 5th International Conference on Intelligent Computing and Control Systems (ICICCS), 2021, pp. 1148-1153, doi:10.1109/ICICCS51141.2021.9432347.
- Patil, M., Kumari, V., Patil, A., Ahire, L., & Mandawka, U. (2021, July 7). UBER DATA ANALYSIS USING GGPLOT. JES Publication. Retrieved from <https://jespublication.com/upload/2021-V12I759.pdf>.
- *ACM Digital Library*. (n.d.). ACM Digital Library. Retrieved December 4, 2022, from <https://dl.acm.org/doi/fullHtml/10.1145/3178876.3186134>
- Leo, M. S. (2021, January 24). *New York Taxi data set analysis*. Medium. Retrieved December 4, 2022, from <https://towardsdatascience.com/new-york-taxi-data-set-analysis-7f3a9ad84850>
- Liu, L., Qiu, Z., Li, G., Wang, Q., Ouyang, W., & Lin, L. (2019). Contextualized Spatial-Temporal Network for Taxi Origin-Destination Demand Prediction.
