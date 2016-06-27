# RelationSim
Simulates a population trying to pair up with ideal mates with the possibility of breaking off and trying again.

=Basic Theory=

This model places the personality spectrum of the population on a loop with an even distribution. The ideal match for each individual is someone similar to themselves. Therefore, there is no universally prefered individual, and there are two optimised groupings One has odd numbered individials pair to their left and even inividuals pair to their right (on the personality loop). The other is a mirror image of the first (this assumes an even number of individuals within the population).

Individauls will have a positive or negative loyalty once in a relationship. Negative loyalty represents a "The grass is always greener" mentality - the individial will abandon a better partner for a worse one. The more negative their loyalty is, the more they are willing to lose in terms of partner compatability. Individuals with a positive loyalty will overestimate their current partner's compatability when comparing them to other partners. The degree to which they overestimate the compatability of their current relationship will be equal to their loyalty.

During each step of the simulation it takes one member from the population and places them in a small group. The individual then considers pairing with the most compatible individual in this small group.

Individuals have a heartbreak threshold. After a partner has left them this many times, they will not be interested in any new relationship.

The simulation is attempting to group people optimally based on these factors. Thus, it rates individuals who were not able to find a partner and individuals who reached the heartbreak threshold quite poorly. The final output will be a measurement of the final happiness of the population at the end of the time period. The happiness of the population is defined as the average compatability for the pairs and a penalty for the percent of the population that has been left unpaired.

=Variables=

Population: The number of individuals. This number is a positive integer >= 2

Group Size: The number of individauls in the randomly composed small groups when one is seeking a mate. This number is a positive                 integer >= 2

Burnout: The heartbreak threshold. If the individual has been left this many times, they will not accept furture partners.

Loyalty: A buffer that overestimates or underestimates the compatability of their current relationship

Lonely Penalty: How badly should we penalize unpaired individuals?

Max Time: How many times should we randomly select an individual and give them a chance to select a partner for ONE SIMULATION

Average: How many times should we run the simulation to form an average?


=Basic Process=

1. Loops over the Average

2. Loops over the Max Time

3. Primary Process
  3a. Select one individual at random and select a small group at random
  3b. The individual looks for the best possible match in the group
  3c. If the individual is already paired, they will break off their current relationship if the prospective partner is estimated (adding in Loyalty here) to be a better match. The partner left behind will gain one burnout.
  3d. If the original individual is still paired at this point, skip to step 4.
  3e. If the target partner is already paired, they will estimate the value of the relationship they are currently in against the approaching partner (just like the approaching partner went through). If the approaching partner is estimated to be a better match (adding in Loyalty), the target individual will break off their relationship. The partner left behind will gain one burnout.
  3f. If both the original individual and the target individual are free, they will be paired together.

4. Repeat step 3 until the Max Time has been exceeded.

5. Calculate the Happiness of the Population

6. Repeat step 2 until the Average has been exceeded

7. Output the average Happiness in a matlab/octave document

=Expanded Features=

-Stepping over a range of Loyalty has been added, outputing an average happiness for each Loyalty
-Stepping over a range of Burnout Thresholds has been added, outputing an average happiness for each Burnout Threshold
