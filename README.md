<h1>Model Building ~ Recipies and Average Ratings </h1>	
<h4 id="creators">By: Lina Battikha & Nicole Reardon </h4>
<h5><em> The datasets that were used throughout this project can be found here: <a href = "https://dsc80.com/project3/recipes-and-ratings/food.com">food.com</a></em></h5>

<h5> Our exploratory data analysis on this dataset can be found<a href = "https://nicolereardon.github.io/Recipe-Ratings-Over-Time-EDA/"><strong>here</strong></a>.</h5>


<h1>Framing the Problem</h1>
<p> We decided that the focus of this project will inferential analysis. We did so by using a regression model with average rating as our response variable. We chose this response variable as we wanted to see which predictor variable had the biggest impact on the response variable. Furthermore, we believe that Average Rating provides a good numerical summary of the recipe as a whole because it's a direct indication of how favored a recipe is. Since this is an inferential analysis project, we are not limited to a  "time of prediction" and will have all predictor variables available to us to incorporate in our model.</p>


<p>To continue with our analysis, we decided to only keep data points that were up until the 95% percentile for the columns of protein, sugar, minutes, soidum, and calories. This is because  the values that were of the higher extremes in this columns were likely due to unfaithful data. If we had kept these values, it is likely the our analysis would have been incorrect. 

In addition to this, we also added in a new column into our dataset that counted the number of reviews for each recipe as we believe that knowing the number of reviews per recipe can help our inferential analysis. 
</p>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>id</th>
      <th>minutes</th>
      <th>n_steps</th>
      <th>n_ingredients</th>
      <th>average_rating</th>
      <th>calories (#)</th>
      <th>total fat (PDV)</th>
      <th>sugar (PDV)</th>
      <th>sodium (PDV)</th>
      <th>protein (PDV)</th>
      <th>saturated fat (PDV)</th>
      <th>carbohydrates (PDV)</th>
      <th>rating</th>
      <th>n_tags</th>
      <th>review_count</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>333281</td>
      <td>40</td>
      <td>10</td>
      <td>9</td>
      <td>4.0</td>
      <td>138.4</td>
      <td>10.0</td>
      <td>50.0</td>
      <td>3.0</td>
      <td>3.0</td>
      <td>19.0</td>
      <td>6.0</td>
      <td>[4,5] rating</td>
      <td>14</td>
      <td>1.0</td>
    </tr>
    <tr>
      <td>453467</td>
      <td>45</td>
      <td>12</td>
      <td>11</td>
      <td>5.0</td>
      <td>595.1</td>
      <td>46.0</td>
      <td>211.0</td>
      <td>22.0</td>
      <td>13.0</td>
      <td>51.0</td>
      <td>26.0</td>
      <td>[4,5] rating</td>
      <td>9</td>
      <td>1.0</td>
    </tr>
    <tr>
      <td>306168</td>
      <td>40</td>
      <td>6</td>
      <td>9</td>
      <td>5.0</td>
      <td>194.8</td>
      <td>20.0</td>
      <td>6.0</td>
      <td>32.0</td>
      <td>22.0</td>
      <td>36.0</td>
      <td>3.0</td>
      <td>[4,5] rating</td>
      <td>10</td>
      <td>4.0</td>
    </tr>
    <tr>
      <td>286009</td>
      <td>120</td>
      <td>7</td>
      <td>7</td>
      <td>5.0</td>
      <td>878.3</td>
      <td>63.0</td>
      <td>326.0</td>
      <td>13.0</td>
      <td>20.0</td>
      <td>123.0</td>
      <td>39.0</td>
      <td>[4,5] rating</td>
      <td>20</td>
      <td>1.0</td>
    </tr>
    <tr>
      <td>475785</td>
      <td>90</td>
      <td>17</td>
      <td>13</td>
      <td>5.0</td>
      <td>267.0</td>
      <td>30.0</td>
      <td>12.0</td>
      <td>12.0</td>
      <td>29.0</td>
      <td>48.0</td>
      <td>2.0</td>
      <td>[4,5] rating</td>
      <td>10</td>
      <td>2.0</td>
    </tr>
  </tbody>
</table>


<p>The metric we used to evaluate our inferential analysis is R-squared. This is because R-squared provides a numerical number that tells us how well the predictor variables that we were using in the model explains the variation in the response variable. We chose this metric over Root Mean Squared Error (RMSE) because R-squared provides a direct numerical indication of how well the predictor variables can be explained our response variable of average rating.</p>

<h1>Baseline Model</h1>

<p>The model that we chose to use is a Linear Regression model. </p>

<p>The features that we included in our baseline model are the number of ingredients, the number of steps, and the number of minutes for each recipe. All of these features are quantitative values. We made no transformations to these features for this baseline model. 
</p>

<p>The results of our baseline model for both training and test sets are below. </p>
<ul>
	<li> <strong>RMSE of training set = 0.6397</strong></li>
	<li> <strong>R-Squared of training set = 2.2709 * 10<sup>-5</sup></strong></li>
	<li> <strong>RMSE of test set = 0.6437</strong></li>
	<li> <strong>R-Squared of test set = 9.3928 * 10<sup>-10</sup></strong></li>
</ul>

<p>We believe this model is not good because of the incredibly small R-squared values that we got for both training and test sets. Also, for this model we looked at RMSE and for both training and test sets, we received a relatively high number. However, since the RMSE numbers for both training and test are very close, this indicates that our model was not overfitted on training data. </p>

<h1>Final Model</h1>


<p>The features we used and why we used each feature in our final model are listed below</p>
<ul>
<li><strong>Sugar, Sodium, Calories, Carbohydrates, and Protein - </strong>  We decided to use these features because they are the most popular nutritional categories that people generally focus on the most when trying a recipe. </li>
<li><strong>Number of Steps, Ingredients, Minutes - </strong> These features can indicate the overall length and difficulty, which can influence people’s willingness to try and thus rate the recipe. The longer a recipe takes or the more steps and ingredients it requires can discourage some from trying the recipe. Quantile Transformer was applied to minutes as there is still a wide range of times, even excluding the outliers. Because Quantile Transformer spreads out the most frequent values and reduces the impact of outliers, it was used along with GridSearchCV to optimize the accuracy the best.</li>
<li><strong>Number of Tags - </strong> This feature can widely impact how reachable it is. More tags likely increase the access people have to it, and thus increase the interaction the recipe gets. A Binarizer was used on this feature because there is likely a small marginal difference for the inclusion of another tag. Because of this GridSearchCV was applied to its threshold to optimize the prediction accuracy.</li>
<li><strong>Review Count - </strong> We decided to create this feature from the Interactions dataset as having the number of reviews per recipe could impact the average rating. If there are only a few reviews for a recipe, then the average rating can be skewed to either high or low. Also,  a recipe with more reviews would tend to have higher reviews as more people are trying it out and it’s more popular, which can be an indication that people like the recipe. </li>
</ul>


<h4>Our Plots that Led to the Transformation of Some Features</h4>
<p><strong>Before</strong></p>
<iframe src="review_count.html" width=800 height=600 frameBorder=0></iframe>
<p><strong>After</strong></p>
<iframe src="review_count_log.html" width=800 height=600 frameBorder=0></iframe>



<p>The model that we used for our analysis is a Linear Regression Model. We decided to use this model because after creating scatter plots with average rating on the y-axis and the different features we chose on the x-axis, we found that we can perform transformations on different features to create linear patterns. The hyperparameters that worked best for our model are listed below. </p>
<ul>
<li><strong>threshold</strong> for the Binarizer of Number of Tags:  4</li>
<li><strong>n_quantiles</strong> for the QuantilieTransformer of Number of Minutes:  17</li>
</ul> 
<p>To find these best hyperparameters, we used GridSearchCV. Our final model R-squared valued value improved by 457%. Our RMSE values sayed our relatively the same numbers of our baseline model. </p>
<h5>The results of our final model for both training and test sets are below. </h5>
<ul>
<li> <strong>RMSE of training set = 0.6279</strong></li> 
<li> <strong>R-Squared of training set = 0.01320</strong></li>
<li> <strong>RMSE of test set = 0.6345</strong></li>
<li> <strong>R-Squared of test set = 0.01322</strong></li>
</ul>


<h1>Fairness Analysis</h1>

<p>For our fairness analysis:</p>
<ul>
<li><strong>Group 1: </strong> Recipes that had a review count = 1</li>
<li><strong>Group 2: </strong> Recipes that had a review counts > 1</li>
<li><strong>Evaluation Metric: </strong> R-Squared</li>
<li><strong>Null Hypothesis: </strong>Our model is fair. There is no difference in R-Squared values between recipes with more than one interaction and recipes with only one interaction.</li>
<li><strong>Alternate Hypothesis: </strong>Our model is unfair.  There is a difference in R-Squared values between recipes with more than one interaction and recipes with only one interaction.</li>
<li><strong>Test Statistic: </strong>The difference between R-Squared of recipes with just one review and recipes with more than 1 review.</li>
<li><strong>Significance Level: </strong>0.05</li>
<li><strong>Observed Test Statistic:</strong> 0.2716</li>
<li><strong>P-value: INSERT</strong></li>
<li><strong>Conclusion: </strong>We fail to reject the null hypothesis. There is not enough evidence to support that there is a significant difference between R-squared  values of our two groups.</li>




<style> 
	table{ 
		table-layout: fixed; 
		border-collapse: collapse;
		width: 150%;
        margin-right:60%;
        overflow: scroll;
		/*width: 100; 
		height:350px;*/ 
	 }
	 th{
	 	width:150%;
	 	overflow: auto;
  	white-space: nowrap;
	 }
     /* tr{
         page-break-inside: avoid;
     } */

	 td{ 
	 	overflow: auto;
	 	white-space: nowrap;
    word-wrap: break-word;
	 	width: 200%;

	 	/*width:60%;
	 	overflow: hidden;*/
/*    	white-space:nowrap;*/
	  }
	  body{
	  	font-family: Helvetica, Sans-Serif;

	  }
    h1{
      font-family: Helvetica, Sans-Serif;
      color:#4B7A5C;
     }
    h4{
      color:#699A7B;

    }
    #creators{
      color: black;
    }

	sup {
	        vertical-align: super;
	        font-size: small;
	    }


</style>
