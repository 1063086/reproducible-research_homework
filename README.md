# Reproducible research: version control and R

\# INSERT ANSWERS HERE #

Questions 1,2,3 can be found here: https://github.com/nadiaangelab/logistic_growth

4) 
a) A: 
The function **random walk** generates a random walk with a specified number of steps (**`n_steps`**). It will create a data frame **`df`** to store x and y coordinates for each step. The walk starts at the origin (0,0) and will change coordinates based on a random angle and step size (**`h`**). The code uses the function **`random_walk`** twice to generate two sets of random walks (**`data1`** and **`data2`**). This creates separate plots (**`plot1`** and **`plot2`**) for each set of random walks using ggplot2. Each point in the plot is colour-coded based on the step number (**`time`**). We can observe that the paths of the two random walks are different due to the randomness involved in selecting the angle at each step. The colour gradient in the plots represents the progression of time (steps) along the paths.
  

b) A: Random seeds are used to ensure that results are reproducible. Using them makes sure that anyone who re-runs the code will get the exact same outputs - since setting a particular random seed allows you to produce the same sequence of random numbers each time you run the program.
They work since computers can't generate truly random numbers, instead the use  of algorithms called pseudo-random number generators (PRNGs) are employed. These algorithms create sequences of numbers that seem random but are entirely determined by an initial value, known as the seed. When you set a random seed, you're specifiying a start point in the PRNG. If you use the same seed, you'll always get the same sequence of pseudo-random numbers. This is important for making sure others can reproduce work in scientific experiments or simulations, which is crucial for scientific applications. By setting a random seed, this ensures that the random parts of the code will stay the same each time you run it. This is especially important when doing experiments, testing ideas, or analyzing data and means that others both check and continuing working on a project by using the same seed.

   - Edit the script to make a reproducible simulation of Brownian motion. Commit the file and push it to your forked `reproducible-research_homework` repo. (10 points)
   - Go to your commit history and click on the latest commit. Show the edit you made to the code in the comparison view (add this image to the **README.md** of the fork). (5 points)
     
A: <img width="1422" alt="Screenshot 2023-12-07 at 05 25 49" src="https://github.com/nadiaangelab/reproducible-research_homework/assets/150149096/4737fa9b-5357-45dc-9667-a50f14c92fc4">

5)(**30 points**) In 2014, Cui, Schlub and Holmes published an article in the *Journal of Virology* (doi: https://doi.org/10.1128/jvi.00362-14) showing that the size of viral particles, more specifically their volume, could be predicted from their genome size (length). They found that this relationship can be modelled using an allometric equation of the form **$`V = \beta L^{\alpha}`$**, where $`V`$ is the virion volume in nm<sup>3</sup> and $`L`$ is the genome length in nucleotides.

   - Import the data for double-stranded DNA (dsDNA) viruses taken from the Supplementary Materials of the original paper into Posit Cloud (the csv file is in the `question-5-data` folder). How many rows and columns does the table have? (3 points)

  A: 13 columns, 33 rows

   - What transformation can you use to fit a linear model to the data? Apply the transformation. (3 points)
     
A: To linearise the data we can take logs; 
log(V)=log(β)+α⋅log(L)

In R this could be carried out as followed;

```R
Logarithmic transformation
log_V <- log(V)
log_L <- log(L)

Linear model
linear_model <- lm(log_V ~ log_L)
```
   - Find the exponent ($\alpha$) and scaling factor ($\beta$) of the allometric law for dsDNA viruses and write the p-values from the model you obtained, are they statistically significant? Compare the values you found to those shown in **Table 2** of the paper, did you find the same values? (10 points)

Exponent (alpha): 1.515228 
Scaling factor (beta): 1181.807 

P-values: 2.279645e-10 (for beta) and  6.438498e-10 (for alpha)

The scaling factor in Table 2 of the paper is 1,182, presumably this has been rounded, therefore it is essentially the value. The same can be said for the exponent, which in the paper is 1.52, and the same could be attained from my values once rounded. Given the standard significance level of 0.05, any p-value smaller than 0.05 is considered statistically significant. In this case, both p-values are significantly smaller than 0.05. Therefore we can reject the null hypothesis and conclude that there is strong evidence against the null hypothesis in favor of the alternative hypothesis. In this case, we accept the alternative which suggests that there is a significant relationship between virion volume and genome length, indicating that the size of the viral particles varies in relation to the genome length.

   - Write the code to reproduce the figure shown below. (10 points)
Code can be found in:  https://github.com/nadiaangelab/reproducible-research_homework/question-5-data/scatterplotcode
  <p align="center">
     <img src="https://github.com/josegabrielnb/reproducible-research_homework/blob/main/question-5-data/allometric_scaling.png" width="600" height="500">
  </p>

  - What is the estimated volume of a 300 kb dsDNA virus? (4 points)

**Bonus** (**10 points**) Explain the difference between reproducibility and replicability in scientific research. How can git and GitHub be used to enhance the reproducibility and replicability of your work? what limitations do they have? (e.g. check the platform [protocols.io](https://www.protocols.io/)).

A: While reproducibility will refer to the fact that re-run the same analysis or experiment using the same data and code and should obtain the same results, replicability instead is the principle of doing the same study again but with new data or under different conditions to see if the findings hold. The former emphasises the consistency of the results within the same study, while the latter assesses the robustness of the results and findings across different applications or datasets.

Git allows you to track changes in your code and documents over time. This version control helps in maintaining a history of modifications, making it easier to trace back and understand the evolution of your work. Each commit represents a snapshot of your project, promoting transparency and reproducibility.
GitHub facilitates collaboration and sharing. By hosting your project on GitHub, others can easily access, contribute, and collaborate. It enhances transparency and reproducibility by providing a centralized global platform for sharing both code and data.

However limitations include the fact that Git and GitHub rely on external servers. If these platforms experience downtime or if your project relies on external factors that may change over time, it can introduce challenges for reproducibility. In addition to this GitHub has limitations on the size of files and repositories. Large datasets or binary files might be impractical to store directly on GitHub. Furthermore while GitHub provides collaboration features, work is made public by default, so if sensitive data is involved in the study, alternative methods of sharing might need to be considered.



