# Data-Driven Offensive Insights: Using Analytics to Improve Offensive Success Rates

The goal for my Senior Year Experience is to evaluate my teams’ offensive success rates 
using both exploratory statistics, logistic regression analysis, classification trees, 
bagging, and random forest to improve our offensive eﬀiciency. By studying the play 
by play data from both past and current seasons, I will be able to find patterns in 
both our play calling tendencies, our eﬀiciency in specific situations, and potentially 
develop a program that simulates our drives. Throughout this paper, I will use the term 
SUCCESS as the response variable. The variable SUCCESS refers to whether or not the 
offensive football play was successful or not. 

This research will directly help the team as identifying our tendencies and eﬀiciency
levels will tell us our strengths and weaknesses, improving our play designs, playbook, 
and player development. By using our different model methods, along with our exploratory 
research, we will be able to build future models that can be updated as the season 
moves on to see if our changes are working. This will help our coaching staff handle 
uncertainties when trying to game plan for the game.

For more information on this project and the findings, please check my full [paper.](file:///C:/Users/Clayton/Desktop/SYEProject/FinalDraft.pdf)

##Method 1: Logistic Regression

Model: glm(SUCCESSFUL ~ RP + DIST + DN)

Classification Rate: 0.602

##Method 2: Logistic Regression with Interaction

Model: glm(SUCCESSFUL ~ RP + DIST + DN + PERSONNEL + RP:DIST)

Classification Rate: 0.616

##Method 3: Classification Trees

Model: train(SUCCESSFUL ~ RP + DIST + DN + PERSONNEL, method = "rpart")

Classification Rate: 0.665 

##Method 4: Bagging and Random Forest

Bagging Model: train(SUCCESSFUL ~ RP + DIST + DN + PERSONNEL, method = "treebag")

Classification Rate: 0.723

Random Forest Model: train(SUCCESSFUL ~ RP + DIST + DN + PERSONNEL, method = "ranger")

Classification Rate: 0.667

##Comparing the Four Methods

![Classification Rate Comparison Graph][C:/Users/Clayton/Downloads/Screenshot_18-12-2025_141630_localhost.jpeg]

As you can see, the far away best model we built was our bagging model. We notice
that logistic regression, with or without interaction, were the worst two models. 
This isn't because GLM models are not as good as bagging and random forest, but 
instead means that the data is not best fit for a linear model. Because we have 
a strong interaction between RP and DIST, as well as non-linear patterns in the 
log-odds for success, a linear model like our logistic regression model does not 
best fit our data. Instead, re-sampling methods like classification trees, bagging, 
and random forest will have more success capturing the complexities of our data.

##Conclusion

Throughout this model, we see time and again Distance be the strongest predictor 
of success. This makes a ton of sense as a shorter distance to go is much more 
obtainable than a longer distance to go. While this project is done based on a 
single team's data, Dist should be the strongest or one of the strongest predictors 
of success with whatever school you applied this research to. We also saw downs, 
specifically 3rd down, be one of the stronger predictors of success. 3rd downs are
a pivotal part of a game, as third downs can either extend your drives and bring 
more chances for successful drives, or end your drives and kill the momentum. A model
built using bagging had the greatest success of predicting success. With its re-sampling
and simulation ability, the bagging model better fit the data strongly outperformed
the others. The model correctly predicted 72.4% of the plays, which is a very successful
rate. Using this model and my research, I hope to communicate with the coaches of 
the team about a plan for next season to incorporate our findings. As a staff, the
team needs to find a way to focus on creating short down situations, especially on
3rd downs.