# AntColony-SCP
An implementation of the Set Coverin Problem using Ant Colony Systems. More specifically, Min-Max Any System.

This algorithm was implemented using the following paper: **Riad Hadji, "Ant Colonies for the Set Covering Problem", ResearchGate, Jan 2000**.

### ANT ENVIRONMENT:
First we need to come up with a way to represent the problem with an environment: We assume that there are num_rows + 2 nodes placed on plain labeled start, end, and 1 to num_rows. Then ants should comeup with a path from the start node to the end node, possibly passing through some intermediary nodes on their way. If an ant passes through the i-th node, it means that in the corresponding solution to the set covering problem we want to include the i-th set. Since it doesn't matter what order the ants visit the nodes in, we assume that the do it lexicographically based on the indices. Thus a chromosome is a binary array of size num_rows, showing which nodes the ant took on its trip.

### PARAMETERE INITIALIZATION:
Now we need to initialize the variables, the initializataion is as follows:

number of ants and max population set empirically.

rho, alph, and beta set based on the criteria defined in the algorithm.

number of columns and number of rows set by the given problem.

pheromone values are initially one for every node, this is to avoid dividing by zero in *P_ij* function.

heuristic values are initially set to the number of elements each subset holds as well.

And finally a set of binary sets, that represent our solutions.

### FITNESS FUNCTION
Now we need to come up with a fitness function:
in this function we should keep in mind two main factors:
1. number of elements of U that this solution covers
2. number of elements of S that this solution includes

The first one should be maximized and the second one should be minimized. Our goal is to find a solution that covers ALL the members of num_columns and has the minirhom number of elements. It is also good to note, false answers could also appear in the form of a solution that covers all the members of num_columns and has a minimal number of members from S, however this minimality cannot be extended to minimization.

### P<sub>ij</sub> FUNCTION
Since we are implementing the MMAS algorithm here we should also come up with a P<sub>ij</sub> function as described in the algorithm.

## INFERENCE
Now we should iterate:

In order to solve this problem we're using the Max-Min Ant System with slight tweaks to get a response quicker.
