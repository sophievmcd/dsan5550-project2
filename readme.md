# Stuck in Line: Machine Learning Analysis of U.S. Grid Interconnection Bottlenecks
AUTHOR: Sophie McDowall

CONTACT: svm37@georgetown.edu

DATE: April 15, 2026

CLASS: DSAN 5550 Data Science for Climate Change


### Problem:

In the last two decades, the growth of demand for electricity from the U.S. grid has been relatively low. However, in the last few years, it has spiked – driven by increased production and rapid growth of data centers (ICF). Power demand for data centers alone is projected to increase from 34.7 gigawatts in 2024 to 106 gigawatts by 2035, potentially adding millions of metric tons of CO2e (BloombergNEF). This demand also will place a strain on the energy grid, potentially increasing prices for customers. Despite the thousands of projects actively seeking grid interconnection, including many renewable projects, which represent a potential 1,400 gigawatts of generation and 890 gigawatts of storage, there are many barriers to project connection and the median duration of time for grid interconnection is around four years (LBL).


### Solution:

A large proportion of proposed interconnection projects are withdrawn, much more than are approved and connected to the grid. Understanding the factors and regions that see the most withdrawals can help policymakers identify potential areas to focus on expediting processes or providing further support. 


### Approach:

In this project, I use data from Lawrence Berkeley National Laboratory on the queue of project interconnection requests, which includes details about the types of power plant projects submitted to be interconnected to the national grid from 2000 through the end of 2024 (LBL). I perform feature engineering on the dataset to narrow to seven variables – the year the project entered the queue, the days spent waiting for a status update, interconnection agreement status, lead time for proposed project vs. online date/current date, project size in terms of megawatt capacity, energy type (ex. solar, oil, etc.), and queue congestion (number of projects that entered the queue the same year). Using the status of the project as a label – either withdrawn, accepted, or still active for potential interconnection – I will run multiple machine learning models to predict the status of a project based on the above variables. 

I run a logistic regression model as a baseline, three tree-based models (Decision Tree Classifier, Random Forest Classifier, and Gradient Boosting Classifier), and one neural network (MLP Classifier). I then compare the performance of each of these models using precision scores, recall scores, ROC/AUC scores, and Brier scores. For the logistic regression, I also run analysis to identify potential multicollinearity between variables since some of the engineered features rely on the same data points. For each model, I identify which features were the biggest predictors of withdrawal or acceptance for projects and which were most common as key predictors across models. 

Using these models, I visualize the data geospatially on a county, region, and state level (data which is included in the initial dataset from Berkeley Lab) to identify any trends in regional chokepoints for plant integration. I use the highest performing models to predict on the active plants to identify which appear most likely to be approved vs. withdrawn and identify what regions may benefit from policy steps to expedite processes. I also identify trends associated with energy type and the withdrawal rates for clean vs. dirty energy types across regions. 

Throughout my model training, testing, code refinement, and analysis, I use the CodeCarbon package to measure estimated carbon costs associated with the model training. Logged data on each test run can be found in the outputs/codecarbon_emissions.csv document. 

## Data Sources:

-	ICF – energy demand growth background (https://www.icf.com/insights/energy/impact-rapid-demand-growth-us) 
-	EIA – U.S. grid forecasts for data centers (https://www.eia.gov/pressroom/releases/press582.php)
-	EPA – Greenhouse gas equivalencies calculator (https://www.epa.gov/energy/greenhouse-gas-equivalencies-calculator-calculations-and-references#:~:text=Electricity%20used%20(kilowatt%2Dhours):)
-	Bloomberg NEF – Energy transition background (https://about.bnef.com/insights/clean-energy/the-us-transition-ahead-booming-energy-demand-shifting-mobility/)
-	Lawrence Berkeley National Laboratory – Queued Up: Characteristics of Power Plants Seeking Transmission Interconnection dataset (https://emp.lbl.gov/queues)

***Note:*** *I used Claude AI to help explore different topic ideas and to assess the feasibility of my ideas, as well as to build and debug code workflow.* 