## Data challenge - starter files

This part of the repository contains the starter files for your data challenge. Think of this as a stand-alone DS project to clone and use to solve your data challenges.

Data challenges are to be solved as team assignments (collabortion! collaboration! collaboration!). 
* designate a master repository for your data challenges among team members, and 
* use it to collaborate to solve the data challenge. 

To submit a data challenge, please 
* create a report file on your master GitHub, and 
* submit a pdf of your report to **Canvas**. 

The project structure is as follows:

```
data_challenges\

| -- src 
	| -- data 
			| -- Gather_ViolenceData_171220.R
			| -- LibraryInstaller.R
			| -- DefineFunctions.R

| -- data  
	| -- raw 
			| -- A-A.xlsx
			| -- A-E.xlsx
			| -- tabla9-A-A.xlsx
			| -- tabla9-A-E-xlsx

	| -- external 
			| -- ARCH535.csv
			| -- LookupAuthorityNames.csv

	| -- processed
			| -- AllViolenceData_171220.csv

| -- references  
			| -- README.md

```

A few things to note:

* `src/data/Gather_ViolenceData_171220.R` is the main script to shape the data. It makes use of `LibraryInstaller.R` which installs libraries if you don't already have them, and `DefineFunctions.R` which calls some processing functions to the main script
* `references/README.md` is the data dictionary for `data/processed/AllViolenceData_171220.csv`, which is your ready-to-use output file 
* all raw data is stored in `data/raw` and external sources in `data/external`


To do before out third class:

* make sure you can run the script [`Gather_ViolenceData_171220.R`](src/data/Gather_ViolenceData_171220.R) and you understand what's going on
* read the [data dictionary](references/README.md)
* start exploring the dataset `AllViolenceData_171220.csv`
* pose questions on the dataset in Slack if you have any (I'll be your sherpa on this one)


## Context on our dataset of choice for the next weeks...

Over a year ago, the New York Times published an [article](https://www.nytimes.com/2016/05/27/world/americas/mexican-militarys-high-kill-rate-raises-human-rights-fears.html?_r=1) detailing the "lethality" of Mexican armed forces in their fight against organized crime and drug cartels ongoing since 2006. Based on data that had been released by the Mexican Government until 2014, the article concludes that 

> Mexico’s armed forces are exceptionally efficient killers — stacking up bodies at extraordinary rates. [...] The Mexican Army kills eight enemies for every one it wounds. [...] For the nation’s elite marine forces, the discrepancy is even more pronounced: The data they provide says they kill roughly 30 combatants for each one they injure.

At the end of January 2017, the [Drug Policy Program (PPD)](http://www.politicadedrogas.org/) at CIDE, a public university in Mexico, released a dataset that allegedly expands on a database that the Mexican government released with data on executions, confrontations, and aggressions related to alleged members of organized crime that happened between 2006-2010. 

PPD claims that a lengthier and more detailed database was leaked anonymously to the Program, and that it is allegedly the original database for the government dataset. This new data released by PPD spans 11 additional months to cover drom December 2006 to November 2011, roughly 80% of the Administration of then President Felipe Calder&oacute;n. According to PPD, it also includes new variables that were not previously available in the original government datatset. 

Upon releasing this new data, PPD's director concludes that  

> 86.1% of dead civilians who presumably participated in confrontations with federal armed forces were killed in events of "perfect lethality" where there were only dead and no wounded. [...] Mexico has the terrible situation of having lethality indices of 2.6. The lethality index of the Federal Police is 2.6 dead for every wounded, the Navy's reaches 17.3 dead for every wounded, and the Army's is 9.1 dead for every wounded. 

We will be using this new behavioral dataset for a few weeks and a couple of data challenges. 


<!--


## Data Challenge 1 (due on 2/22 at 6PM)

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

This is a team assignment. Please create a file on your team GitHub repo where you answer the challenge, including links to your code, graphs. 



## Data Challenge 2 (due on 3/22 at 6PM)


1. Ask two (2) questions that might help you understand better the dynamics of violence contained on our datas et. Apply one algorithm per question and share your insights from each analysis. [50 pts]  Remember: a non-finding is also a finding! It tells you whether a question is worth pursuing further or not.
	* perform the necessary transformations in your data - if any are needed, and explain why you did that
	* show the output from your analysis in a consumable form
	* be explicit about the limitations of your anaylisis, due to estimation or to the data itself
	* did you find something interesting? what is that? does your finding suggest this question is worth pursuing further? why or why not?
	* if you did not find something interesting, explain why, and whether there is some additional information that would help in answering your question
	* provide your code, and a single visualization per question that summarizes your finding 
	* phrase your finding for each question in two ways: 
		* one sentence that summarizes your insight
		* one paragraph that reflects all nuance in your insight 
	* make sure to also include your code 




## Data Challenge 3 (due on 3/22 at 6PM)

1. Formulate two (2) conditional hypotheses that you seek to investigate with the data. One of your hypotheses should condition on two variables (as the example on the slides), and the other should condition on three variables. [50 pts]
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

This is a team assignment. Please create a file on your team GitHub repo where you answer the challenge, including links to your code, and graphs. 


 -->