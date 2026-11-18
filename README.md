# Market Basket Analysis using the Apriori Algorithm

## Project Overview

This project applies **Market Basket Analysis** to retail transaction data using the Apriori algorithm. The objective is to identify products that frequently occur together in customer transactions and generate association rules that can help inform product placement, cross-selling, and promotional strategies.

The analysis is implemented using **Python and PySpark**, demonstrating distributed data processing, frequent itemset generation, and association-rule generation.

## Dataset

- **Dataset:** Market Basket Optimisation (`transactions.csv`)
- **Number of transactions:** 7,501
- **Number of unique items:** 119
- **Transaction format:** Each row represents a customer transaction, with products listed across multiple columns.
- **Data preparation:** Extracted distinct products, removed null values and duplicate entries, and standardized item values by removing leading and trailing spaces.

Each transaction represents a basket of products purchased together. The analysis uses these baskets to identify recurring product combinations.

## Methodology

The project follows two main stages:

### 1. Frequent Itemset Generation

The Apriori algorithm is used to identify product combinations that occur frequently across transactions.

The implementation:
- Extracts all unique products from the transaction dataset.
- Generates candidate itemsets of increasing size.
- Calculates the support of each candidate itemset.
- Filters out itemsets that do not meet the minimum support threshold.
- Repeats the process until no further frequent itemsets can be generated.

**Minimum support threshold: 0.01 (1%)**

An itemset must appear in at least 1% of all transactions to qualify as frequent.

### 2. Association Rule Generation

Association rules are generated from the frequent itemsets to identify relationships between products.

A rule has the following structure:

`Antecedent → Consequent`

For example, a hypothetical rule could be:

`Product A → Product B`

The rule indicates that transactions containing Product A may also contain Product B.

The notebook calculates confidence using:

`Confidence = Support(A ∪ B) / Support(A)`

**Minimum confidence threshold: 0.099 (9.9%)**

Rules meeting or exceeding this threshold are retained by the implementation.

*Implementation note:* The notebook describes a limitation in its rule-generation approach: it generates rules with single-item antecedents. The resulting rules should therefore be interpreted within that scope.

## Selected Association Rules

The notebook saves the generated association rules to a CSV output, but the final rule table is not preserved in the uploaded notebook. The following table should be populated from the exported rule results.

| Association rule | Support | Confidence | Lift |
|---|---:|---:|---:|
| `[Antecedent] → [Consequent]` | `[Value]` | `[Value]` | `[Value]` |
| `[Antecedent] → [Consequent]` | `[Value]` | `[Value]` | `[Value]` |
| `[Antecedent] → [Consequent]` | `[Value]` | `[Value]` | `[Value]` |

**Metric interpretation:**
- **Support:** The proportion of all transactions containing both the antecedent and consequent.
- **Confidence:** The proportion of transactions containing the antecedent that also contain the consequent.
- **Lift:** Measures how much more likely the consequent is to occur when the antecedent is present, compared with its overall occurrence rate.

`Lift = Confidence(A → B) / Support(B)`

A lift greater than 1 indicates a positive association, a lift equal to 1 indicates no association beyond what would be expected by chance under independence, and a lift below 1 indicates a negative association.

*Note: Lift is an additional metric to calculate from the frequent-itemset support values; it is not calculated in the current notebook.*

## Business Recommendations and Practical Applications

The association rules can support the following business recommendations once the strongest rules have been validated:

1. **Product placement:** Products with strong positive associations can be positioned near one another to make complementary purchases more convenient.

2. **Cross-selling opportunities:** Products frequently purchased together can be recommended as complementary items during checkout or through online product recommendations.

3. **Bundling and promotions:** Product combinations with meaningful support and lift can be considered for bundle offers or targeted promotions.

4. **Marketing strategy:** High-confidence rules can help identify products that are commonly purchased together and inform targeted campaigns.

5. **Inventory planning:** Consistent product associations can provide additional context for understanding purchasing patterns and planning stock availability.

Recommendations should prioritize rules with meaningful support and lift, rather than relying on confidence alone. A high-confidence rule with very low support may apply to only a small number of transactions.

## Scope and Limitations

- The analysis focuses on descriptive market basket patterns and association rules.
- The Apriori algorithm is used to generate frequent itemsets and identify product associations.
- The minimum support threshold is 1%, and the minimum confidence threshold is 9.9%.
- The implemented rule-generation approach is limited to single-item antecedents, as described in the notebook.
- Lift and the final selected-rule metrics require an additional calculation and validation step.
- Association rules indicate co-occurrence, not causation. They do not establish that purchasing one product causes a customer to purchase another.
- The recommendations are intended to support business decisions and should be validated against commercial context, margins, inventory, and campaign performance.

## Tools and Technologies

- Python
- PySpark
- Apache Spark
- Jupyter Notebook
- Apriori Algorithm
- Association Rule Mining

## Project Outcome

This exercise demonstrates how transaction-level retail data can be processed to identify frequent product combinations and generate association rules. The resulting analysis provides a foundation for data-driven product placement, cross-selling, bundling, and marketing recommendations.

**Project type:** MBA coursework / guided assignment.rules are infrequent. This portion will be explained in more detail in the code demonstration of rule generation.
