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
- Which species belong to each tank and date (A1 - Juncus)

Plant Types: 
Juncus effesus
Pontederia cordata
Panicum virgatum

Scatterplot of root and shoot lengths:
ggplot used to create a variety of plots based on the data provided from the dataframe. In this case it was created using the shoot length data (in cm) sorted by which tank it came from. Root length is being used in the graph following this one. The data is arranged from smallest length to largest with a scatterplot of data points sorted by a single line of the tank. ggplot was used due to its ability to easily change different aspects of the graph with different lines of code. I was able to give the graph a title using the command ggtitle as well as changing the text size using element_text(size=). Changing the size of the text allowed for all the points to be easily readable along the x-axis. 

Boxplots: 
-Boxplots were chosen to see how the data were spread out. The advantage in using the boxplot was that I was able to see the distribution fo the data without taking up as much space with something such as a histogram which was useful because I was able to compare multiple datasets within the same graph. -With the boxplot we could observe where the majority of the data lie as well as outliers due ot the use of the five number summary. 
We can see that the pontederia data is skewed towards zero, which makes since due to plants dying off early resulting in that being most of the data. Without outliers present, panicum offers the most centralized dataset. Both juncus and panicum have data with a large number of outliers (juncus with most outliers in the upper quartile and panicum having it spread out amongst first and third quartile). 
-Shoot length tells a different story than root lenth. Median value of the data were larger due to roots generally being shorter than shoots. Pontederia still has skewed data with the median approaching and the minmimum at the zero value. Pancicum's median favors the upper end of the spectrum and juncus has the median placed at the lower end with a more even spread of the data values. Panicum has the only outlier in the graph. 

