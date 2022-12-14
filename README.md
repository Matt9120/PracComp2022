# Practical Computing Fall 2022
## Matthew Barnes 
### 20220712

- Final project for PracComp 2022

Contributors: 
- Natasha Bell (ECU)
- Matthew Barnes (ECU)
- Dr. Rachel Gittman (ECU)
- Dr. Ariane Peratla (ECU)
- Dr. Steven Hall (NCSU)

Objectives: 
Project Goal: Remediate N and P from FTW tanks 
Project Objective: To observe whether remediation is additive, synergistic, or antagonistic 

Background Project Info: 
-Using data collected from first growing season of FTW projects to analyze plant root and shoot growth 
-Constructed two csv files to analyze data appropriately with gucplant being focused on tank by tank analsys and gucplant.Aseries being focused on whole species analysis
-Data originally collcted using tape measure from root/shoot line to tip of longest root and shoot and written down in a notebook the day of
-Imported into a excel file, converted into csv
-Brought into RStudio as csv which was then converted into a data frame for ease of use

Variables Used to Describe the Data: 
- Root Length of each individual species (Juncus effesus, Pontederia cordata, and Panicum virgatum)
- Shoot Length of each individual species (Juncus effesus, Pontederia cordata, and Panicum virgatum)
- Date of which the sample was collected
- Which species belong to each tank and date (A1 - Juncus - 06/26/2022 -> 09/26/2022)

Plant Types: 
Juncus effesus
Pontederia cordata
Panicum virgatum

Data Source: 
gucplant = "~/Desktop/Practical Computing /PracCompFinal/MTB_GUC_Plant Measurements_PracComp.csv"
gucplant.Aseries = ""~/Desktop/Practical Computing /PracCompFinal/MTB_GUC_Plant Measurements_PracComp-BREWER.csv"

Scatterplot of root and shoot lengths:
ggplot used to create a variety of plots based on the data provided from the dataframe. In this case it was created using the shoot length data (in cm) sorted by which tank it came from. Root length is being used in the graph following this one. The data is arranged from smallest length to largest with a scatterplot of data points sorted by a single line of the tank. ggplot was used due to its ability to easily change different aspects of the graph with different lines of code. I was able to give the graph a title using the command ggtitle as well as changing the text size using element_text(size=). Changing the size of the text allowed for all the points to be easily readable along the x-axis. 

Boxplots: 
-Boxplots were chosen to see how the data were spread out. The advantage in using the boxplot was that I was able to see the distribution fo the data without taking up as much space with something such as a histogram which was useful because I was able to compare multiple datasets within the same graph. -With the boxplot we could observe where the majority of the data lie as well as outliers due ot the use of the five number summary. 
We can see that the pontederia data is skewed towards zero, which makes since due to plants dying off early resulting in that being most of the data. Without outliers present, panicum offers the most centralized dataset. Both juncus and panicum have data with a large number of outliers (juncus with most outliers in the upper quartile and panicum having it spread out amongst first and third quartile). 
-Shoot length tells a different story than root lenth. Median value of the data were larger due to roots generally being shorter than shoots. Pontederia still has skewed data with the median approaching and the minmimum at the zero value. Pancicum's median favors the upper end of the spectrum and juncus has the median placed at the lower end with a more even spread of the data values. Panicum has the only outlier in the graph. 

Species by Species ANOVA and Tukey Calculations:
Anova was the next form of data to calculate. This is useful for testing three or more variables at a time, which in this case we have three plant species so this is perfect. This is similar to a two sample t-test, but with ANOVA we are likely to have fewer type 1 errors than the t-test. Within the anova shoot length was tested by species to see if the data is statistically significant from one another. Based on the p-value the data does come back as statistically significant but with ANOVA, it cannot give specifics as to which set of data it is, which is why a Tukey test was run next to compare datasets. 

Welch's T-Test Using ggbetweenstats:
-ggbetween stats was used to make a publication ready plots along with relavent statistical analysis of the species by species comparison of root and shoot data of the gucplant.Aseries dataframe. Along the x axis for both graphs is the species of the plants (Juncus, Panicum, and Pontederia) and alonng the y axis is the lengths of the roots and shoots. The data within the plot is displayed in a violin plot esque fashion showing the distribution of the points. Within the graph itself it can also tell us all the relavent statistical data we could use to infer whether or not to reject the null hypothesis (p-value, r, r squared, f-value, and confidence interval). 

ggplot for Shoot/Root Length Across Growing Season: 
ggplot was ran again for a comparison of the overall growth of the roots and the shoots of all species within each tank. For the tanks with multiple plant species the plant species were singled out for individual analysis of their performance in the tanks. geom_point() draws the points defined by the x and y variables previously defined and can give them specifics on how they are presented on the graph. Within geom point we can give the points color (color=), tell it how big to make the points (linewidth=), annd the opacity of the points on a scale from 0-1 (alpha=). Within the ggpubr library we get the ggarrange function which allows for the graphs to be placed within a single page to be displayed at the same time. rremove allowed for the removal of the x labels that would have otheriwse been to jumbled to read. The label function gives a name to each graph (tank 1 is "a", tank 2 is "b" and tank 3 is "c") on the page while the ncola and nrow lays out the grid of how the graphs show up. In this case it is a 2x2 pattern. 


Conslusions: 
For the ggplot scatterplots, I feel as though the scatterplots that show the progress across the growing season offer the best information to inform on plannt performance. With these graphs, they were able to chart growth across time instead of just purely the distribution of the data. We can infer growth changes, unfavorable weather, and the beginning of fall from the progress of the plants. 

The data from the t-tests of the tank by tank analysis had more interesting results that previously thought when they were wrongfully conducted as ANOVA's. Initially in the t-test usage, the tanks were tested against similar tanks; A1 was compared to A2 and A3, B1 to B2 and B3, etc.). Within the single species tanks, 4 of the possible 18 analyses from the tanks came back statistically significant. Nothing associated with Pontederia cordata (so all the tanks with "B" in the tank name) came back statistically significant. Mainly I think them all dying off after week 4 of the trial is the reason for this result. The two species tanks with comparisons being made from the juncus plants of the two species present had 7 of the 12 analyses come back as statiscally significant. From this we can fail to reject the null hypothesis that the tanks behave differently from another within the same treatment. 

Within the tank by tank analysis of the data where I compared different tanks (A1 to C1, AB2 to BC3, etc.), the majority of the data came back as statistically significant. Most of the p-values were low enough below the 0.05 threshold that they could be counted as "really significant". The data shows signs that the tanks were behaving differently than one another with hints of synergism within the species, but more data will be needed to further these results. Data presented from the lachat in the near future that will have reduction amounts will provide a better picture of what this data really means. 

Within the welchs t-test performed using the ggbetweenstats, we were able to see that per species, the shoots were stastically significant from one another as well as the roots apart from juncus-panicum. However, for the roots the ANOVA test told a different story. After running the ANOVA test, followed by a Tukey analysis, it was concluded that the juncus-panicum species was the only statistically significant data produced. When the plant tissue analysis is ran here in the coming months, we'll be able to see how this translated into the amount of nitrogen and phosphorus stored in the plant throughout the growing season. 

Here within the coming months of the research project we will be running lachat data to see how much nitrogen and phosphorus was remediated from the tanks themselves. The data will be analyzed alongside the data provided for the final project to understand what we have produced. We will also be performing a spring analysis to see how the plant behave at the beginnning of the growing season in terms of remediation, storage, and growth. The tools used here will be used again to analyze the data we gather then and I look forward to seeing how they compare to one another. 
