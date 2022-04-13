
<h1 style="text-align:center;">Analysis with R: Factors That Relate to Body Mass Index</h1>

Ziqi Polimeros<br>

April 3rd 2022<br>

!["BMI_Race"](https://github.com/ZiqiPolimeros/Analyse-with-R-Factors-that-Relate-to-BMI-Index/blob/main/pictures/obesity.jpg?raw=true)
<br>[18]

<br>
<a href="#1">Introduction</a><br />
  <a href="#2">Abstract</a><br />
  <a href="#3">Data Sources and Methods</a><br />
  <a href="#4">Feature Selections and Data Cleansing</a><br />
  <a href="#5">Data Analysis and Visualization</a><br />
  
  <ol id = "toc">
  <a href="#5.1">Discussion 1</a><br />
  <a href="#5.2">Discussion 2</a><br />
  <a href="#5.3">Discussion 3</a><br />
  <a href="#5.4">Discussion 4</a><br />
  <a href="#5.5">Discussion 5</a><br />
  </ol>
  
  <a href="#6">References</a><br />


<h1 style="background-color:#e5f5f7;"><a id="1"> Introduction</a> </h1>


The problem of obesity has increased significantly in this century. In the United States, obesity grew from 30.5% to 42.4% and severe obesity jumped from 4.7% to 9.2% from  1999 to 2018,[1] as indicated by increased body mass index(BMI) in the population.
That poses a serious health risk in light of the fact that
obesity is correlated with various diseases, such as high blood pressure, diabetes, heart attacks etc. To address the health risk, we have to look at the causes of high BMI and what we can do to prevent obesity. To that end, we searched the internet for information and found the National Health and Nutrition Examination Survey (NHANES).[2]

NHANES is an annual survey taken by the Centers for Disease Control and Prevention(CDC). The survey is a program that is designed to assess the health and nutritional status of adults and children in the United States. The program takes a nationwide  sample of about five thousand persons each year. Data collected includes demographics, dietary and health related questions and laboratory tests results. Analysis from the survey can be used to determine the risk factors for diseases.


<h1 style="background-color:#e5f5f7;"><a id="2"> Abstract</a> </h1>

For this project we used the R programming language to perform data cleansing, wrangling and visualization. Our main objective was to analyze different behaviors that impact BMI. We started the analysis on body measurements, demographics, insulin, blood glucose, cholesterol ration and blood pressure. We found a major problem that almost stopped the project. But later we found some interesting points. We demonstrated all the findings with bar graphs, proportion graphs and correlation heatmaps. 

<h1 style="background-color:#e5f5f7;"><a id="3"> Data Sources and Methods</a></h1>

For this project, we used NHANES 2017 - March 2020 Pre-Pandemic Data.[3] There are 82 data sets in the survey. Most of the data sets have about 15 thousand observations and dozens of features. We chose blood pressure, blood glucose, insulin and cholesterol data sets as known factors to examine our methods. We chose diet behavior data sets as unknown factors to analyze. 

There are two main methods in the project. 

<li><b>
Body Mass Index(BMI)
</li></b>
<p> $BMI = 703*\frac{weight(lb)}{[height(in)]^{2}}$  &nbsp;&nbsp;&nbsp; [4]</p>
As you can see, BMI is based on two simple factors - height and weight. It's a crude method to roughly estimate body fat. It's not suitable for athletes who might have high BMI with normal body fat or very little body fat. However, "BMI is commonly used by doctors to screen for health problems stemming from weight issues".[5] In this project, we still used BMI to indicate body fat and classify overweight and obesity.

<li><b>
Correlation Coefficient
</li></b>
Correlation coefficients are used to measure the strength of a relationship between two variables.[6] The value of correlation coefficient, r range between -1 and +1. The table below shows that the relationship between two variables based on the value of r:

<style>
table, td {
  padding-left: 60px;
  padding-top: 10px;
}
th{
  padding-top: 10px;
}
</style>
<body>

<table style="width:60%">
  <tr>
  <th>Absolute value of r</th>
  <th>	Strength of relationship</th>
    
  </tr>
  <tr>
    <td>r < 0.25</td>
    <td>No relationship</td>

  </tr>
  
  <tr>
    <td>0.25 < r < 0.5</td>
    <td>Weak relationship</td>

  </tr>
  
  <tr>
    <td>0.5 < r < 0.75</td>
    <td>Moderate relationship</td>

  </tr>
  
  <tr>
    <td>r > 0.75</td>
    <td>Strong relationship</td>

  </tr>
  
</table>

[7]


<h1 style="background-color:#e5f5f7;"><a id="4"> Feature Selections and Data Cleansing </a></h1>

Our original data sets had missing information. We chose features with minimal missing data. As more features were added, the data set became smaller and smaller. The indicators of relationships between BMI and laboratory features changed alightly, but the indicator of BMI and age changed dramatically. We tried different approaches and addressed the problem.  


<h1 style="background-color:#e5f5f7;"><a id="5">  Data Analysis and Visualization</a></h1>

<h3> First data set: </h3>
<h4><i> Body Measures  </h4></i> 

There is a children's BMI category feature in the data, but no adult BMI category. The method we used to classify adult BMI is from National Heart, Lung, and Blood Institute.[8]

<h3> Second data set: </h3>
<h4><i> Demographics </h4></i>

We chose seven features, including age, gender, race, marital, and education. 

!["BMI_Race"](https://github.com/ZiqiPolimeros/Analyse-with-R-Factors-that-Relate-to-BMI-Index/blob/main/pictures/1_BMI_Race.png?raw=true)


<br><h3><b><a id="5.1"> Discussion 1</a> </b></h3><br>

Asian group is very prominent in the graph. 
The percentage of obesity is lower than 25% in the Asian group while around 50% in other races. Also, the percentage of healthy weight in Asian group is about two times of other race groups.
Are Asians healthier than other race groups? Some Asian Americans are in normal weight range, but have less muscle and more body fat.[9] That's another factor that impact the accuracy of BMI.


<h3> Third and Fourth Data set: </h3>
<h4><i> Insulin and Blood Glucose</h4></i>

We created a new feature, diabetes that is based on blood glucose.[10]
We also apply the same method on it.

!["BMI_insulin"](https://github.com/ZiqiPolimeros/Analyse-with-R-Factors-that-Relate-to-BMI-Index/blob/main/pictures/6_BMI_insulin.png?raw=true)

<br><h3><b><a id="5.2"> Discussion 2 </a></b></h3><br>

The graph shows that there's a moderate relationship between BMI and Insulin. But blood glucose and diabetes have a weak relationship with BMI. However, the indicator of relationship between BMI and age is 0.2 which means there's no relationship! 
We didn't know what's wrong. In this data set we only dropped some missing values, which is the requirement of performing the method. We wanted to find another material to do the analysis, but it's really difficult to find a data set that contains such comprehensive information and detailed explanation of features. We continued the analysis and hoped the problem can be avoided or addressed.

<h3> Fifth, Sixth and Seventh Data set: </h3>
<h4><i>Total Cholesterol, High Density Cholesterol and Blood Pressure</h4></i>

We added a new feature, cholesterol ratio.[11] In the Blood Pressure data set, both systolic and diastolic were taken three times. We took the average values of each.

!["BMI,Blood Pressure and Chotesterol"](https://github.com/ZiqiPolimeros/Analyse-with-R-Factors-that-Relate-to-BMI-Index/blob/main/pictures/7_heatmap_BMI_BPC.png?raw=true)
<br><h3><b><a id="5.3"> Discussion 3 </a></b></h3><br>



From the graph you can tell that BMI has a weak relationship with cholesterol ratio and blood pressure. But even more bizarre, the indicator of relationship between BMI and age soared from 0.2 to 0.34. Since these are laboratory and examination data, we didn't over-process the data. The big change was dropping missing values. Is this the problem? We went over the first data set and only chose two features, weight and age, that avoid dropping to much missing information. See the heatmap below:


!["BMI_age"](https://github.com/ZiqiPolimeros/Analyse-with-R-Factors-that-Relate-to-BMI-Index/blob/main/pictures/3_heatmap_BMI_age.png?raw=true)



<br><h3><b><a id="5.4"> Discussion 4 </a></b></h3><br>

The indicator of relationship between Age and BMI violently rose to about 0.6. We have three options for the relationship between Age and BMI. Which one is correct? We did some research on it. An article from Harvard Medical School describes that "The amount of body fat goes up steadily after age 30".[12] Above age 30, people tend to lose 3% to 5% muscle per decade, as well as bones density and organ cells, but gain body fat. This is the aging process. Based on the study, we judged that 0.6 is more accurate.

Why did the indicator of age change so dramatically? We speculate that the missing information causes the sample to become biased. Another reason is that the one year sample is still not big enough to represent the U.S. population. We purposely chose a survey that included three years information which is the biggest survey in NHANES, but we still encountered this problem. To solve the problem, we need to analyze data information from each year. 

 


<h3> Eighth Data set: </h3>
<h4><i>Diet Behaviors</h4></i>

Since the sample is biased, it's not necessary to show more analysis, but we found something interesting.


!["BMI,Blood Pressure and Chotesterol"](https://github.com/ZiqiPolimeros/Analyse-with-R-Factors-that-Relate-to-BMI-Index/blob/main/pictures/8_BMI_diet.png?raw=true)


<br><h3><b><a id="5.5"> Discussion 5 </a></b></h3><br>



In this sample, we examine ten diet behaviors, which included the following: <br> 
<ol id = "toc">
How healthy is your diet? <br>
How much milk did you consumed in the past 30 days? <br>
How many not-home-prepared meals did you consume in the past seven days?<br>
How many of your meals in the past seven days were from fast food or pizza place?<br>
How many of your meals in the past 30 days were from grocery stores?<br>
How many frozen meals/pizzas did you consume in past 30 days? <br>
Have you heard of My Plate? <br>
Are you the main meal planner/preparer? <br>
Did you Share meal planning/preparing duty? <br>
Are you the main food shopper? <br>
Did you Share food shopping duty? <br>
  </ol>
<br>

From the heatmap you can tell that most of the indicators of these factors are close to zero. The highest number is from "How healthy is your diet", 0.24.(We wondered if we analyze over 10 years of information, would this number go up?) Although it's considered no relationship, we checked the percentage of people that heard of My Plate or tried My Plate. It's really low, 13% and 4.4%, respectively. 

The concept of a healthy diet is changing. We grew up with food pyramid[13], which is  about 40% grains or breads, about 20% vegetables, 15% fruits, about 10% meat, 10% dairy, with fat making up less than 8%. This diet can be easily switched to high carbohydrate diet, which is over 60% of total dietary energy that is from carbohydrates.  With 40% gains or breads in your meal, if you choose potato,sweet potato,corn, pumpkins, taro, or yams as vegetables, your meal become high carbohydrate. This diet increase cholesterol and insulin resistance, having the greatest impact on insulin-resistant states, such as type 2 diabetes.[14] Asian people are in low percentage of obesity, but in high risk of diabetes.[15] Diet probably plays a Huge role here. We wish CDC do more publicity of my plate plan [13] and improve people's awareness of healthy diets to prevent obesity.





<h1 style="background-color:#e5f5f7;"><a id="6"> References</a> </h1>

[1] Centers for Disease Control and Prevention.<br>
Obesity is a common, serious, and costly disease. <br>
https://www.cdc.gov/obesity/data/adult.html#:~:text=From%201999%20%E2%80%932000%20through%202017,and%20certain%20types%20of%20cancer. <br>

[2] Centers for Disease Control and Prevention. <br>
NHANES - About the National Health and Nutrition Examination Survey. <br>
https://www.cdc.gov/nchs/nhanes/about_nhanes.htm <br>
Date published September 15, 2017 <br>


[3] Centers for Disease Control and Prevention. <br>
NHANES 2017 - March 2020 <br>
https://wwwn.cdc.gov/nchs/nhanes/continuousnhanes/default.aspx?cycle=2017-2020

[4] Centers for Disease Control and Prevention. <br>
Calculating BMI using the English System.<br>
https://www.cdc.gov/nccdphp/dnpao/growthcharts/training/bmiage/page5_2.html

[5] Running Shoes Guru.<br>
How BMI Impacts Sports and How Much You Should Depend on It.<br>
https://www.runningshoesguru.com/content/how-bmi-impacts-sports-and-how-much-you-should-depend-on-it/#:~:text=The%20American%20Exercise%20Council%20on,height%20than%20long%2Ddistance%20runners.<br>

[6] Statistics How To <br>
Correlation Coefficient: Simple Definition, Formula, Easy Steps. <br>
https://www.statisticshowto.com/probability-and-statistics/correlation-coefficient-formula/ <br>

[7] Statology. <br>
What is Considered to Be a “Strong” Correlation?. <br>
https://www.statology.org/what-is-a-strong-correlation/. <br>

[8] National Heart, Lung, and Blood Institute. <br>
Calculate Your Body Mass Index. <br>
https://www.nhlbi.nih.gov/health/educational/lose_wt/BMI/bmicalc.htm <br>

[9]  Centers for Disease Control and Provention. <br>
Diabetes and Asian Americans <br>
https://www.cdc.gov/diabetes/library/spotlights/diabetes-asian-americans.html.<br>

[10] Centers for Disease Control and Provention. <br>
Tests for Type 1 Diabetes, Type 2 Diabetes, and Prediabetes. <br>
https://www.cdc.gov/diabetes/basics/getting-tested.html<br>

[11] Healthine.<br>
Understanding the Cholesterol Ratio: What It Is and Why It’s Important.<br>
https://www.healthline.com/health/cholesterol-ratio<br>

[12] Harvard Health Publishing. <br>
Preserve your muscle mass. <br>
https://www.health.harvard.edu/staying-healthy/preserve-your-muscle-mass#:~:text=After%20age%2030%2C%20you%20begin,risk%20of%20falls%20and%20fractures. <br>

[13]A Brief History of USDA Food Guides <br>
https://myplate-prod.azureedge.us/sites/default/files/2020-12/ABriefHistoryOfUSDAFoodGuides.pdf <br>

[14] ScienceDirect. <br>
High Carbohydrate Diet. <br>
https://www.sciencedirect.com/topics/agricultural-and-biological-sciences/high-carbohydrate-diet#:~:text=High%2Dcarbohydrate%20diets%20(%3E%2060,type%202%20diabetes%20or%20pregnancy.<br>

[15] Harvard School of Public Health Department of Nutrition.<br>
Why are Asians at Higher Risk?<br>
https://asiandiabetesprevention.org/what-is-diabetes/why-are-asians-higher-risk <br>

[18] Centers for Disease Control and Prevention. <br>
Overweight & Obesity<br>
https://www.cdc.gov/obesity/data/prevalence-maps.html#overall <br>
