# What is Casual Inference?
- When you implement a policy $\alpha$, casual inference indicates the relation between a target number and the effect from the policy. In other word, you can measure change amount of the target $x$. 
- Let's say you are a member of marketing department and you need to measure an ad impact on conversion. 
- However,it is not easy to directly measure it because there may be other causes to change the conversion, such as social tred.
- Casual Inference can assumes the change amount of the ad.

# Way of thinking
- Using the sample case above, when you use casual inference, you will measure the impact by thinking that the difference of change amount between the case when you implement the policy and the case when you would not implement the policy. How do you assume the change amount when you would not implement the policy? Well, that is exactly what casual inference does.
- The case when you implement the policy is fact and the other case is not fact, which is called <b>counterfactural</b>.
- Moreover, the actual change amount of the fact case is called an outcome variable, whereas, the imaginary change amount of the counterfactual is called a potentila outcome variable.

# Difference between causal relationship and correlation
- Causual relationship means a variable Y becomes larger when you make another variable Z larger.
- Correlation means a variable Y becomes larger when another variable Z became larger.

# Cofounding Factor
- Imagine there is a target variable X. You want to make it beggier to operate another variable Y. Also, there is the other variable Z that you cannot control but it has an impact on X. In this case, you cannot measure how much impact the Y has on X because uncounsiously variable Z effects on X. In that case, X is called a cofounding factor.

# spurious correlation
- case 1: you thought variable Z has an impact on the tagert variable Y. However, actually it is oppositie.
- cofounding factor
- When two interindependent variables are sum to a total. $E(Y_1|Z = 1) - E(Y_0| Z = 0)$ This is called Selection Bias.

# Individual Treatment Effect(ITE)
- When it comes to an individual effect, such as training  program effect on an individual is called Individual Treatment Effect(ITE)
- ITE has two variables. When you think of an outcome variable, it is denoted $Y_1^i$ On the other hand, of a potential outcome variable, it is denoted $Y_0^i$

# Average Treatment Effect(ATE)
-This is an antonyms against individual treatment effect, that is a group effect, such as a training program effect on all employess who took the program.
- ATE is denoted $E(Y_1 - Y_0) = E(Y_1) - E(Y_0) = \frac{1}{N}\sum^N_{i = 1}(Y_1^i) - \frac{1}{N}\sum^N_{i = 1}(Y_0^i)$ 

# Average Treatment effect on the Treated(ATT)
- This is an Avearge Tretment Effect fo cases treated, which means fact.
- $E(Y_1 - Y_0|Z= 1)$
- $Z$ means a binary flag of an explanatory variabel.

# Average Treatment effect on the Untreated.(ATU)
- This is an Average Treatment Effect on cases not treated, which means being couterfact.
- $E(Y_1 - Y_0|Z= 0)$
- Let's say your boss did not take a training program and you need to evaluate your boss related to content of the training. How much evaluation was and how much it would be if your boss had taken the training? This difference is Average Treatment effect on the Untreated.

# Conditional Average Treatment Effect(CATE)
- This is an Average Treatment Effect under a specific condition.
- $E(Y_1 - Y_0|x)$

# Intervation
- The operation to change a variable $Z$. 
- For example, yor are trying to measure an TV effect(ATE) on ladies. $E(Y_1 - Y_0|Z= 1)$
- Intervation is to change the assumption as ladies to boys. $E(Y_1 - Y-0|do(Z= 0))$
- Intervation is denoted by $do(Z= 1)$ Its argument is called a do operator
- ATT is not same as $E(Y_1 - Y-0|do(Z= 0))$ but intervation is same as $ATE$. Imagine there are 100 records of questionnier that you conducted. 30 are answered by men and the rest of it was done by women. ATT is an Average Treatment Effect of 30 men(or 70 women). Intervation is to force 30 men become a woman and calculate 100 women's Average Treatment Effect(or, vice vasa.)
- Using intervation can solve spurious correlation problem.

# Adjustment formula
- The advantage of using this formula is to enable to demote intervation with a mathmatical formula.

$P(Y = y|do(Z= Z)) = \sum{}_{x}P(Y = y|Z = z,X= x)P(X=x)$

m# Structual equation model(SEM)
- SEM is an algorithm to denote causual relationships to equations.
- SEM does not treat the case of having impact on itself because it doesn't converge.
- If variable x and z has the following relationship, it is called 循環グラフ. Whereas,the other is called acylic Graph.
- If a relationship is directed and acylic, is is called Directed Acylic Graph(DAG)
- If there is three variables;x,y,z in a causual relationship, they can be expressed as follows with error variable e, which is unknown variables that may have impact.

$x = f(y,z,e)$

$y = f(x,z,e)$

$z = f(x,y,e)$

- The kind of equations like above is called Linear Structual Model.
- SEM is useful because it can technically express a causual relationship. However, it is difficult when there are many variables.

# Causal diagram
- It is a graph to express a casual relationship with a graph.
- When there are two variables in whose relationship is that one effects on the other, that is the relationship can be an arrow like $Z→X$, it is called being directed. On the other hand, if the relationship is pretty unkonwn except for that A has impact on B. This relationship is called being undirected.
- Variables can be observed is called an observed variable whereas, the other is called an unobserbed.

# backdoor criterion, backdoor bapth, D separation
- When you wan to examine the degree of impact of variable Y on variable Z, there must be other variables which might affect on variable Z. This case, you should know what variables you need to deal with as variables to have impact on variable Z. 
- In other words, you need to decside which variables you need to leave or ignore.
- The variables you leave is called a covariate.
- How you decisde that? Well, there are some specific variables which you can ignore or you need to do something

## bacidoor
- Imagine there are variables Z, Y and a. When you want to measure the imact of Z on Y, do you need to leave the variabe a too? In this case, you do not because variabe a indirectly effects on variable Y from the variable Z, which is called a backdoor path. Besides, the variable a is called an intermediate variable.

## A factor meets the backddor criterion
- The other case where you need to go thorough is the following case. When variable X has impact on variable Z as well as variable Y, and variable Z effects on variabe Y, the variable X is a cofounding factor that causing a spurious correlation. This case variable X is called a factor meets the backdoor criterion and interveration is executed to delete the impact of variable x to variable Z

## Other cases where you should ignore
- For the case where you measure the impact of variable Z on variable Y all the variables which are directed from variable Y must be ignored.
- Moreover, all the variables which are intersections and direct to variable Z must be ignored

## D separetion
- This is an operation to change a causal diagram by ignoring some variables and intervation.

## Randomized controlled Trials
- When you do intervation, you decide values of variable Z randomly. This operation is called Randomized controlled Trials(RCT).