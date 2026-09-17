MARKET BASKET ANALYSIS:


The first step of the algorithm is to identify distinct items in the given set of transactions. Let’s say these are ({A}, {B}, {C}, {D}).

Once you have different items, your next step would be to calculate the support of each of these items. Items with support values less than the minimum support are removed from the distinct items list.

The next step is to create higher-order itemsets by merging the existing itemsets. This can be done using the candidate generation technique. We will cover this concept in detail while implementing the generation of higher item sets on code.

Using the 1 itemsets ({A}, {B}, {C}, {D}) and assuming that only A, B and C are frequent, we generate itemsets {A, B}, {A, C} and {B, C}. Note that none of the 2-item sets contains the item D. This is because we have applied the Apriori principle. Since D is infrequent, any item set containing D, e.g., {A, D}, {C, D} and {B, C, D} will automatically become infrequent.

Once you have the higher-order itemsets, you can calculate the support for these item sets and again remove the itemsets that do not qualify the minimum support criteria.

This ( n-1 ) -item sets then become inputs for the generation of n-item sets, and once again the item sets that do not satisfy the minimum support criteria are removed. This process continues until no new itemsets can be generated.

Rule Generation in the Apriori Algorithm:

Once you have all the frequent itemsets, we can proceed with the rule generation process. We begin with 2-itemsets and generate all the possible rules.

For each rule, we check the corresponding confidence value and return the rule only if its confidence is above the minimum confidence level.

In order to avoid generating redundant rules, we utilise confidence-based pruning. Using this, we eliminate the generation of higher-order rules if their corresponding lower-order rules are infrequent. This portion will be explained in more detail in the code demonstration of rule generation.
