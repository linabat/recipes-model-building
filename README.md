<h1>Model Building ~ Recipies and Average Ratings </h1>	
<h4 id="creators">By: Lina Battikha & Nicole Reardon </h4>
<h5><em> The datasets that were used throughout this project can be found here: <a href = "https://dsc80.com/project3/recipes-and-ratings/food.com">food.com</a></em></h5>

<h5> Our exploratory data analysis on this dataset can be found</h5> <a href = "https://nicolereardon.github.io/Recipe-Ratings-Over-Time-EDA/"><strong>here</strong></a>.

<h1>Problem Prediction</h1>
<p> We decided that the focus of this project will inferential analysis. We did so by using a regression model with average rating as our response variable. We chose this response variable as we wanted to see which predictor variable had the biggest impact on the response variable. Furthermore, we believe that Average Rating provides a good numerical summary of the recipe as a whole because it's a direct indication of how favored a recipe is. Since this is an inferential analysis project, we are not limited to a  "time of prediction" and will have all predictor variables available to us to incorporate in our model.</p>

<p>The metric we used to evaluate our inferential analysis is R-squared. This is because R-squared provides a numerical number that tells us how well the predictor variables that we were using in the model explains the variation in the response variable. We chose this metric over Root Mean Squared Error (RMSE) because R-squared provides a direct numerical indication of how well the predictor variables can be explained our response variable of average rating.</p>

<h1>Baseline Model</h1>

<p>The model that we chose to use is a Linear Regression model. </p>

<p>The features that we included in our baseline model are the number of ingredients, the number of steps, and the number of minutes for each recipe. All of these features are quantitative values. We made no transformations to these features for this baseline model. 
</p>

<p>The results of our baseline model for both training and test sets are below. </p>
<ul>
	<li> <strong>RMSE of training set = 0.637</strong></li>
	<li> <strong>R-Squared of training set = 4.901 * <var>10<sup>-5</sup></var></strong></li>
	<li> <strong>RMSE of test set = 0.651</strong></li>
	<li> <strong>R-Squared of test set = -4.259 * <var>10<sup>-6</sup></var></strong></li>
</ul>

<p>We do believe this mode is good because of the incredibly small R-squared values that we got for both training and test sets. Also, for this model we looked at RMSE and for both training and test sets, we received a relatively high number. However, since the RMSE numbers for both training and test are very close, this indicates that our model was not overfitted on training data. </p>





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


	/*  .page {
        @include container;
    }*/


</style>
