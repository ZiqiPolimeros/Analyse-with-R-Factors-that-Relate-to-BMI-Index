



<h1 style="text-align:center;">Analysis with R: Factors That Relate to Body Mass Index</h1>

Ziqi Polimeros<br>

April 3rd 2022<br>

!["BMI_Race"](https://github.com/ZiqiPolimeros/Analyse-with-R-Factors-that-Relate-to-BMI-Index/blob/main/pictures/obesity.jpg?raw=true)
<br>[13]

<br>
<a href="#1">Introduction</a><br />
  <a href="#3">Data Sources and Methods</a><br />
  <a href="#4">Feature Selections and Data Cleansing</a><br />
  <a href="#5">Data Analysis and Visualization</a><br />
  
  <ol id = "toc">
  <a href="#5.1">Discussion 1</a><br />
  <a href="#5.2">Discussion 2</a><br />
  <a href="#5.3">Discussion 3</a><br />
  <a href="#5.4">Discussion 4</a><br />
  
  </ol>
  
  <a href="#6">Summary</a><br />
  
  <a href="#7">References</a><br />


<h1 style="background-color:#e5f5f7;"><a id="1"> Introduction</a> </h1>


The problem of obesity has increased significantly in this century. In the United States, obesity grew from 30.5% to 42.4% and severe obesity jumped from 4.7% to 9.2% from  1999 to 2018,[1] as indicated by increased body mass index(BMI) in the population.
That poses a serious health risk in light of the fact that
obesity is correlated with various diseases, such as high blood pressure, diabetes, heart attacks etc. To address the health risk, we have to look at the causes of high BMI and what we can do to prevent obesity. To that end, we searched the internet for information and found the National Health and Nutrition Examination Survey (NHANES).[2]

NHANES is an annual survey taken by the Centers for Disease Control and Prevention(CDC). The survey is a program that is designed to assess the health and nutritional status of adults and children in the United States. The program takes a nationwide  sample of about five thousand persons each year. Data collected includes demographics, dietary and health related questions and laboratory tests results. Analysis from the survey can be used to determine the risk factors for diseases.


<h1 style="background-color:#e5f5f7;"><a id="3"> Data Sources and Methods</a></h1>

For this project, we used NHANES 2017 - March 2020 Pre-Pandemic Data[3] There are 82 data sets in the survey. Most of the data sets have about 15 thousand observations and dozens of features. We chose blood pressure, blood glucose, insulin and cholesterol data sets as known factors to examine our methods. We chose diet behavior data sets from  NHANES 2011, 2013, 2015 and NHANES 2017 - March 2020 Pre-Pandemic Data as unknown factors to analyze. 

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

<h4><i> Body Measures  </h4></i> 

There is a children's BMI category feature in the data, but no adult BMI category. The method we used to classify adult BMI is from National Heart, Lung, and Blood Institute.[8]

<h4><i> Demographics </h4></i>

We chose seven features, including age, gender, race, marital, and education. 

!["BMI_Race"](https://github.com/ZiqiPolimeros/Analyse-with-R-Factors-that-Relate-to-BMI-Index/blob/main/pictures/1_BMI_Race.png?raw=true)


<br><h3><b><a id="5.1"> Discussion 1</a> </b></h3><br>

Asian group is very prominent in the graph. 
The percentage of obesity is lower than 25% in the Asian group while around 50% in other races. Also, the percentage of healthy weight in Asian group is about two times of other race groups.
Are Asians healthier than other race groups? Some Asian Americans are in normal weight range, but have less muscle and more body fat.[9] That's another factor that impact the accuracy of BMI.


<h4><i> Insulin and Blood Glucose</h4></i>

We created a new feature, diabetes that is based on blood glucose.[10]
We also apply the same method on it.

!["BMI_insulin"](https://github.com/ZiqiPolimeros/Analyse-with-R-Factors-that-Relate-to-BMI-Index/blob/main/pictures/6_BMI_insulin.png?raw=true)

<br><h3><b><a id="5.2"> Discussion 2 </a></b></h3><br>

The graph shows that there's a moderate relationship between BMI and Insulin. But blood glucose and diabetes have a weak relationship with BMI. However, the indicator of relationship between BMI and age is 0.2 which means there's no relationship! 



<h4><i>Total Cholesterol, High Density Cholesterol and Blood Pressure</h4></i>

We added a new feature, cholesterol ratio.[11] In the Blood Pressure data set, both systolic and diastolic were taken three times. We took the average values of each.

!["BMI,Blood Pressure and Chotesterol"](https://github.com/ZiqiPolimeros/Analyse-with-R-Factors-that-Relate-to-BMI-Index/blob/main/pictures/7_heatmap_BMI_BPC.png?raw=true)
<br><h3><b><a id="5.3"> Discussion 3 </a></b></h3><br>



From the graph you can tell that BMI has a weak relationship with cholesterol ratio and blood pressure. But even more bizarre, the indicator of relationship between BMI and age soared from 0.2 to 0.34. Since these are laboratory and examination data, we didn't over-process the data. The big change was dropping missing values. Is this the problem? We decided to add more observations and see what the result will be.



<h4><i>Diet Behaviors</h4></i>

As we mention before, we chose NHANES 2011, 2013, 2015 and NHANES 2017 - March 2020 Pre-Pandemic Data to analyze diet behaviors. 


!["BMI,Blood Pressure and Chotesterol"](https://github.com/ZiqiPolimeros/Analyse-with-R-Factors-that-Relate-to-BMI-Index/blob/main/pictures/8_BMI_diet.png?raw=true)


<br><h3><b><a id="5.4"> Discussion 4 </a></b></h3><br>


In this sample, we examine diet behaviors, which included the following: <br> 
<ol id = "toc">
How healthy is your diet? <br>
How much milk did you consumed in the past 30 days? <br>
How many not-home-prepared meals did you consume in the past seven days?<br>
How many of your meals in the past seven days were from fast food or pizza place?<br>
How many of your meals in the past 30 days were from grocery stores(Ready_to_eat_foods)?<br>
How many frozen meals/pizzas did you consume in past 30 days? <br>

  </ol>
<br>

In this graph, the correlation coefficient between age and BMI is 0.15. Since it's from a bigger dataset, which combined four datasets, we believe that 0.15 is more accurate. 

From the heatmap you can tell that most of the indicators of these factors are close to zero. The lowest number is from "How healthy is your diet", negative 0.22, which still considered no relationship. We couldn't find any relationship between BMI and the diet behaviors above.

As we all know that what we eat, and drink directly impact our weight. Before analyzed the dataset, we expected to build a predictive model based on some diet behaviors. However, we couldn't find any proof that the diet behaviors from The survey impact BMI. We are of the opinion that those questions didn't relate to body weight. Diets relate to body weight because the calories that you consume. If the calories that you consume is less than the calories that the body need to maintain it’s weight, you will lose weight, and vice versa. However, in the survey questions were how often you had fast food or frozen food. It didn't count the amount of food that you had. The calories that you intake was uncertain. If we want to measure the relationship between BMI and diet behaviors, we need to ask more specific questions, such as how much calories do you consume daily, the proportion of protein in your diet, etc.


<h1 style="background-color:#e5f5f7;"><a id="6"> Summary </a> </h1>



<table style="width:100%">
  <tr>
  <th> Factors</th>
  <th>	Correlation Coefficient with BMI</th>
  <th>	Strength of relationship</th>
  </tr>
  
  <tr>
    <td>Weight</td>
    <td>0.81 or 0.9</td>
    <td>Strong relationship</td>

  </tr>
  
  <tr>
    <td>Age</td>
    <td>o.15, 0.2 or o.34</td>
    <td>No relationship or Weak relationship</td>

  </tr>
  
  <tr>
    <td>Blood glucose</td>
    <td>0.32</td>
    <td>Weak relationship</td>

  </tr>
  
  <tr>
    <td> Insulin</td>
    <td> 0.57</td>
    <td>Moderate relationship</td>

  </tr>
  
  <tr>
    <td> Diabetes</td>
    <td> 0.29</td>
    <td>Weak relationship</td>

  </tr>
  
  <tr>
    <td>Cholesterol ratio</td>
    <td> 0.4</td>
    <td>Weak relationship</td>

  </tr>
  
  <tr>
    <td>Systolic</td>
    <td>0.27</td>
    <td>Weak relationship</td>

  </tr>
  
  <tr>
    <td>Diastolic</td>
    <td>0.4</td>
    <td>Weak relationship</td>

  </tr>
  
  <tr>
    <td>How healthy is your diet?</td>
    <td> -0.22</td>
    <td>No relationship</td>

  </tr>
  
  <tr>
    <td>How much milk did you consumed in the past 30 days? </td>
    <td>-0.03</td>
    <td>No relationship</td>

  </tr>
  
  <tr>
    <td>How many not-home-prepared meals did you consume in the past seven days?</td>
    <td> 0</td>
    <td>No relationship</td>

  </tr>
  
  <tr>
    <td>How many of your meals in the past seven days were from fast food or pizza place?</td>
    <td>0.05</td>
    <td>No relationship</td>

  </tr>
  
  <tr>
    <td>How many of your meals in the past 30 days were from grocery stores(Ready_to_eat_foods)?</td>
    <td> 0.03 </td>
    <td>No relationship</td>

  </tr>
  
  <tr>
    <td>How many frozen meals/pizzas did you consume in past 30 days? </td>
    <td> -0.02</td>
    <td>No relationship</td>

  </tr>
  
  
  
</table>





<h1 style="background-color:#e5f5f7;"><a id="7"> References</a> </h1>

[1] 
<a href="https://www.cdc.gov/obesity/data/adult.html#:~:text=From%201999%20%E2%80%932000%20through%202017,and%20certain%20types%20of%20cancer">Obesity is a common, serious, and costly disease</a>  <br>


[2] 
<a href="https://www.cdc.gov/nchs/nhanes/about_nhanes.htm">NHANES - About the National Health and Nutrition Examination Survey</a>  <br>


[3] 
<a href="https://wwwn.cdc.gov/nchs/nhanes/continuousnhanes/default.aspx?cycle=2017-2020">NHANES 2017 - March 2020</a>  <br>

[4] 
<a href="https://www.cdc.gov/nccdphp/dnpao/growthcharts/training/bmiage/page5_2.html">Calculating BMI using the English System</a>  <br>

[5] 
<a href="https://www.runningshoesguru.com/content/how-bmi-impacts-sports-and-how-much-you-should-depend-on-it/#:~:text=The%20American%20Exercise%20Council%20on,height%20than%20long%2Ddistance%20runners">How BMI Impacts Sports and How Much You Should Depend on It</a>  <br>

[6] 
<a href="https://www.statisticshowto.com/probability-and-statistics/correlation-coefficient-formula">Correlation Coefficient: Simple Definition, Formula, Easy Steps</a>  <br>

[7] 
<a href="https://www.statology.org/what-is-a-strong-correlation">What is Considered to Be a “Strong” Correlation?</a>  <br>

[8] 
<a href="https://www.nhlbi.nih.gov/health/educational/lose_wt/BMI/bmicalc.htm">Calculate Your Body Mass Index</a>  <br>

[9] 
<a href="https://www.cdc.gov/diabetes/library/spotlights/diabetes-asian-americans.html">Diabetes and Asian Americans</a>  <br>

[10] 
<a href="https://www.cdc.gov/diabetes/basics/getting-tested.html">Tests for Type 1 Diabetes, Type 2 Diabetes, and Prediabetes</a>  <br>

[11] 
<a href="https://www.healthline.com/health/cholesterol-ratio">Understanding the Cholesterol Ratio: What It Is and Why It’s Important</a>  <br>

[12] 
<a href="https://www.health.harvard.edu/staying-healthy/preserve-your-muscle-mass#:~:text=After%20age%2030%2C%20you%20begin,risk%20of%20falls%20and%20fractures">Preserve your muscle mass</a>  <br>

[13]
<a href="https://www.cdc.gov/obesity/data/prevalence-maps.html#overall">Overweight & Obesity</a>  <br>

