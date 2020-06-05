The genetic algorithm is a search-based optimization technique. It is frequently used to find the optimal or nearest optimal solution. It was introduced by John Holland. It is based on darwin's Natural Selection Theory. Before explaining how the genetic algorithm works let me first explain Darwin’s theory on natural selection. In his theory, he defined natural selection as the “principle by which each slight variation [of a trait], if useful, is preserved”. The concept was simple but powerful: individuals best adapted to their environments are more likely to survive and reproduce.[Wikipedia] Sometimes this theory is described as“ survival of the fittest”. Those who are fittest than others have the chance to survive in this evolution. The genetic algorithm is all about this. It mimics the process of natural selection to find the best solution.
In genetic we will use some biological terms such as population, chromosome, gene, selection, crossover, mutation. Now, first of all, let’s try to understand what these terms mean.
Population, Chromosome, Gene
At the beginning of this process, we need to initialize some possible solutions to this problem. The population is a subset of all possible solutions to the given problem. In another way, we can say that the population is a set of chromosomes. A chromosome is one of that solution to that current problem. And each chromosome is a set of genes.
For simplicity, We can describe a chromosome as a string. So, we can say that a population is a collection of some string(each character is a binary value, either 0 or 1 ). And each character of the string is a gene.

For starting the process of the genetic algorithm, we first need to initialize the population. We can initialize the population in two ways. The first one is random and the second one is heuristic. It is always better to start the algorithm with some random population.
Fitness Function
After initializing the population, we need to calculate the fitness value of these chromosomes. Now the question is what this fitness function is and how it calculates the fitness value.
As an example, let consider that we have an equation, f(x) = -x² + 5 .We need the solution for which it has the maximum value and the constraint is 0≤x≤31.
Now, let consider that we have a random population of four chromosomes like below. The length of our chromosome is 5 as 2⁵=32 and 0≤x≤31.

Our fitness function will calculate the functional value of each chromosome as stated in the problem statement :
For the 1st chromosome, 01110 means 14 in integer. So, f(x) = -(14*14) + 5 = -191.
For the 2nd chromosome, 10101 means 21 in integer. So, f(x) = -(21*21) + 5 = -436.
For the 3rd chromosome, 00011 means 3 in integer. So, f(x) = -(3*3) + 5 = -4.
For the 4th chromosome, 10111 means 23 in integer. So, f(x) = -(23*23) + 5 = -524.
Parent Selection
Parent selection is done by using the fitness values of the chromosomes calculated by the fitness function. Based on these fitness values we need to select a pair chromosomes with the highest fitness value.
There are many ways for fitness calculation like Roulette wheel selection, rank selection.
In Roulette wheel selection, the chromosome with the highest fitness value has the maximum possibility to be selected as a parent. But in this selection process, a lower can be selected.
In rank selection, chromosomes are ranked based on their fitness values from higher to lower. As an example, According to those fitness values calculated above, we can rank those chromosomes from higher to lower like 3rd>1st>2nd>4th. So, in the selection phase, 3rd and 1st chromosomes will be selected based on the fitness valued calculated from the fitness function.
Crossover
Crossover is used to vary the programming of the chromosomes from one generation to another by creating children or offsprings. Parent chromosomes are used to create these offsprings(generated chromosomes).
To create offsprings, there are some ways like a single-point crossover, two or multi-point crossover.
For a single point crossover, first, we need to select a point and then exchange these portions divided by this point between parent chromosomes to create offsprings. You can use the color combination for easy understanding.

For a two-point crossover, we need to select two points and then exchange the bits.

Finally, these new offsprings are added to the population.
Mutation
Mutation brings diversity to the population. There are different kinds of mutations like Bit Flip mutation, Swap mutation, Inversion mutation, etc. These are so so simple.
In Bit Flip mutation, Just select one or more bits and then flip them. If the selected bit is 0 then turn it to 1 and if the selected bit is 1 then turn it to 0.

In Swap Bit mutation, select two bits and just swap them.

In inverse mutation, just inverse the bits.

Implementation of Genetic Algorithm in Python
Let’s try to implement the genetic algorithm in python for function optimization.
Problem Statement
Let consider that we have an equation, f(x) = -x² + 5 . We need the solution for which it has the maximum value and the constraint is 0≤x≤31. To select an initial population use the probability 0.2.