
# Data Challenges

<!--

## Data Challenge 3 (due on 9/99 at 6PM)

Formulate two (2) conditional hypotheses that you seek to investigate with the data. One of your hypotheses should condition on two variables (as the example on the slides), and the other should condition on three variables. [50 pts]
    * formulate each one of your hypotheses explicitly in substantive terms (as opposed to statistical terms) using 2-3 lines at most
	* show exactly how each one of your hypotheses translates into the marginal effect that you will seek to estimate from the data 
	* show the output from your analysis in a consumable form
	* show all your computations to estimate the corresponding marginal effect and its standard error
	* be explicit in your assumptions
	* be explicit in the limitations of your inferences
	* phrase your finding for each question in two ways: 
		* one sentence that summarizes your insight
		* one paragraph that reflects all nuance in your insight 
	* make sure to also include your code 

**This is NOT a team assignment.** Please create a file on your **personal GitHub** repo where you answer the challenge, including links to your code, graphs. 

**Remeber:** there is a late delivery penalty: 10% of your grade per day of late delivery

-->


## Data Challenge 2 (due on 3/21 at 6PM)


Ask two (2) questions that might help you understand better the dynamics of violence contained on our dataset. One of them should be an **inferential** question, and one of them a **predictive** one. Apply one of the algorithms we've reviewed on each question and share your insights from each analysis. [50 pts]  Remember: a non-finding is also a finding! It tells you whether a question is worth pursuing further or not.

    * write each one of your questions explicitly, and not the approach (inferential or predictive) that you'll apply
	* perform the necessary transformations in your data - if any are needed, and explain why you did that
	* show the output from your analysis in a consumable form
	* be explicit about the limitations of your analysis. Are they due to estimation or to the data itself?
	* did you find something interesting? what is that? does your finding suggest this question is worth pursuing further? why or why not?
	* if you did not find something interesting, explain why, and whether there is some additional information that would help in answering your question
	* provide your code, and a single visualization per question that summarizes your finding 
	* phrase your finding for each question in two ways: 
		* one sentence that summarizes your insight
		* one paragraph that reflects all nuance in your insight 
	* make sure to also include your code 

**This is NOT a team assignment.** Please create a file on your **personal GitHub** repo where you answer the challenge, including links to your code, graphs. 

**Remeber:** there is a late delivery penalty: 10% of your grade per day of late delivery


## Data Challenge 1 (due on 2/14 at 6PM)


At the end of January 2017, the [Drug Policy Program (PPD)](http://www.politicadedrogas.org/) at CIDE, a public university in Mexico, released a dataset that allegedly expands on a database that the Mexican government released with data on executions, confrontations, and aggressions related to alleged members of organized crime that happened between 2006-2010. Upon releasing this new data, PPD's director concludes that  

> 86.1% of dead civilians who presumably participated in confrontations with federal armed forces were killed in events of "perfect lethality" where there were only dead and no wounded. [...] Mexico has the terrible situation of having lethality indices of 2.6. The lethality index of the Federal Police is 2.6 dead for every wounded, the Navy's reaches 17.3 dead for every wounded, and the Army's is 9.1 dead for every wounded. 

The lethality index is defined as the ratio of dead over wounded per event. 


With this new dataset, please address the following: 

1. Can you replicate the 86.1% number? the overall lethality ratio? the ratios for the Federal Police, Navy and Army? 
    * Provide a visualization that presents this information neatly. 
    * Please show the exact computations you used to calculate them (most likely than not, you'll need to do some additional munging in the data to get there)
    * If you could not replicate them, please show why and the difference relative to your own computations (also, include a neat graph that summarizes this)
	* Be very explicit: What are you assuming to generate these computations?

2. Now you know the data more intimately. Think a little bit more about it, and answer the following questions:
  * Is this the right metric to look at? Why or why not? 
  * What is the "lethality index" showing explicitly? What is it not showing? What is the definition assuming?
  * With the same available data, can you think of an alternative way to capture the same construct? Is it "better"? 
  * What additional information would you need to better understand the data?
  * What additional information could help you better capture the construct behind the "lethality index"

**This is NOT a team assignment.** Please create a file on your **personal GitHub** repo where you answer the challenge, including links to your code, graphs. 

**Remeber:** there is a late delivery penalty: 10% of your grade per day of late delivery
