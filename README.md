# Reproducible research: version control and R

\# INSERT ANSWERS HERE #

Questions 1,2,3 can be found here: https://github.com/nadiaangelab/logistic_growth

4) 
A: 1. **Function `random_walk`:**
    - Generates a random walk with a specified number of steps (**`n_steps`**).
    - Initializes a data frame **`df`** to store x and y coordinates for each step.
    - Starts at the origin (0,0) and updates coordinates based on a random angle and step size (**`h`**).
2. **Creating and plotting two random walks:**
    - Calls **`random_walk`** twice to generate two sets of random walks (**`data1`** and **`data2`**).
    - Creates separate plots (**`plot1`** and **`plot2`**) for each set of random walks using ggplot2.
    - Each point in the plot is color-coded based on the step number (**`time`**).
3. **Observations:**
    - The paths of the two random walks are different due to the randomness involved in selecting the angle at each step.
    - The colour gradient in the plots represents the progression of time (steps) along the paths.
   - Investigate the term **random seeds**. What is a random seed and how does it work? (5 points)
   A: Random seeds are used to ensure that results are reproducible. Using this parameter makes sure that anyone who re-runs your code will get the exact same outputs - since setting a random seed allows you to produce the same sequence of random numbers each time you run the program.
It works since computers can't generate truly random numbers, they will use algorithms called pseudo-random number generators (PRNGs). These algorithms create sequences of numbers that seem random but are entirely determined by an initial value, known as the seed. When you set a random seed, your specifiying a start point in the PRNG. If you use the same seed, you'll always get the same sequence of pseudo-random numbers. This is important for making sure others can reproduce your work in scientific experiments or simulations, which is crucial for scientific applications. By setting a random seed, you make sure that the random parts of your work stay the same each time you run it. This is especially important when doing experiments, testing ideas, or analyzing data. Others can check and build on your work by using the same seed.

   - Edit the script to make a reproducible simulation of Brownian motion. Commit the file and push it to your forked `reproducible-research_homework` repo. (10 points)
   - Go to your commit history and click on the latest commit. Show the edit you made to the code in the comparison view (add this image to the **README.md** of the fork). (5 points)
A: <img width="1422" alt="Screenshot 2023-12-07 at 05 25 49" src="https://github.com/nadiaangelab/reproducible-research_homework/assets/150149096/4737fa9b-5357-45dc-9667-a50f14c92fc4">

5)(**30 points**) In 2014, Cui, Schlub and Holmes published an article in the *Journal of Virology* (doi: https://doi.org/10.1128/jvi.00362-14) showing that the size of viral particles, more specifically their volume, could be predicted from their genome size (length). They found that this relationship can be modelled using an allometric equation of the form **$`V = \beta L^{\alpha}`$**, where $`V`$ is the virion volume in nm<sup>3</sup> and $`L`$ is the genome length in nucleotides.

   - Import the data for double-stranded DNA (dsDNA) viruses taken from the Supplementary Materials of the original paper into Posit Cloud (the csv file is in the `question-5-data` folder). How many rows and columns does the table have? (3 points)

  A: 13 columns, 33 rows

   - What transformation can you use to fit a linear model to the data? Apply the transformation. (3 points)


   - Find the exponent ($\alpha$) and scaling factor ($\beta$) of the allometric law for dsDNA viruses and write the p-values from the model you obtained, are they statistically significant? Compare the values you found to those shown in **Table 2** of the paper, did you find the same values? (10 points)
   - Write the code to reproduce the figure shown below. (10 points)

  <p align="center">
     <img src="https://github.com/josegabrielnb/reproducible-research_homework/blob/main/question-5-data/allometric_scaling.png" width="600" height="500">
  </p>

  - What is the estimated volume of a 300 kb dsDNA virus? (4 points)

**Bonus** (**10 points**) Explain the difference between reproducibility and replicability in scientific research. How can git and GitHub be used to enhance the reproducibility and replicability of your work? what limitations do they have? (e.g. check the platform [protocols.io](https://www.protocols.io/)).

