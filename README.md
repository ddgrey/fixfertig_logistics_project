**Not coming from my Notion portfolio? Start with the full project disclosure [here](https://dvyemchuk.short.gy/fixfertig_logistics_notion_page) for full context.**

# **Project Background**

FixFertig, a German e-commerce marketplace founded in 2019, connects sellers worldwide with customers, specializing in home goods and lifestyle products.

Partnering with the Logistics Manager, I examined whether product characteristics—size, weight, and category—contribute to delivery delays and if these delays impact product review scores, potentially revealing unexpected customer tolerance and preferences. He had noticed inconsistencies between shipping times and product ratings but sought clarity on underlying dependencies.

<p align="left">
  <img src="https://drive.google.com/uc?export=view&id=18kyIT-wuedLrCMb-c6SPuD1wlfcx3zEG" alt="FixFertig Dataset ERD (Entity Relationship Diagram)" width="550">
</p>

---

### **Stakeholder Request Operationalization**

> **Operationalization** is the process of *defining* abstract concepts (e.g. happiness) to make them measurable and testable (e.g. physiological indicators), ensuring precise evaluation and valid conclusions.

</aside>

- **Request**: "We need to understand if larger products receive worse reviews when delivery dates slip, or if customers are more forgiving with certain product categories regarding shipping delays."
- **Operationalized Version**: "Determine whether delayed delivery negatively affects the review scores of large-sized and heavyweight products. Additionally, analyze review scores across different product categories to compare customer tolerance for delayed deliveries."

---

### **Hypothesis Formulation**

**Delivery Status Hypothesis**
  - **Null Hypothesis** (H₀) **A**: Delivery status (delayed vs. on-time) has no effect on product review scores.
  - **Alternative Hypothesis** (H₁) **A**: Delayed delivery leads to lower review scores compared to on-time delivery.
      - **Independent variable**: Delivery status (delayed, on-time)
      - **Dependent variable**: Product review scores
<br>

**Product Characteristic Hypotheses**
    
  > **What is essentially being tested:**
  "Does the impact of delivery delays on customer satisfaction vary by product characteristics (size, weight, category)?"
  
  - **Null Hypothesis** (H₀) **B**: The distribution of review scores is the same across all product weight groups for delayed deliveries.
  - **Alternative Hypothesis** (H₁) **B**: At least one product weight group has a different distribution of review scores for delayed deliveries.
      - **Independent variable**: Product weight (among delayed deliveries)
          - **Product weight groups**: light, medium, heavy, extra-heavy
      - **Dependent variable**: Product review scores

<br>
  
  - **Null Hypothesis** (H₀) **C**: The distribution of review scores is the same across all product size groups for delayed deliveries.
  - **Alternative Hypothesis** (H₁) **C**: At least one product size group has a different distribution of review scores for delayed deliveries.
      - **Independent variable**: Product size (among delayed deliveries)
          - **Product size groups**: small, medium, large, extra-large
      - **Dependent variable**: Product review scores

<br>
  
  - **Null Hypothesis** (H₀) **D**: The distribution of review scores is the same across all product categories for delayed deliveries.
  - **Alternative Hypothesis** (H₁) **D**: At least one product category has a different distribution of review scores for delayed deliveries.
      - **Independent variable**: Product category (among delayed deliveries)
          - **Product categories**: multiple; of medium-high demand
      - **Dependent variable**: Product review scores

---

### **Analytical Methods**

- **Visualization** of product review scores and order distributions across product characterstics (size, weight and category) via box and bar plots
- **Brunner-Munzel test** (two-group comparison)
    - Choice reasoning
        1. Product review scores are ordinal data (relevance of non-parametric methods)
        2. Scores likely have different distribution shapes by delivery status (violated assumption of the Mann-Whitney U test). This test is tailored for such cases and is often the default over the M-W test
        3. It naturally handles ties (repeated values), preventing a loss of statistical power (inflated false-negative rates). The scoring nature and its narrow range (1-5) imply a decent number of ties
- **Kruskal-Wallis H test** (multiple-group comparison)
    - Choice reasoning
        1. Product review scores are ordinal data
        2. Scores likely have simillar distribution shapes across product characterstics among delayed deliveries, thereby satisfying the test assumption
  
---

# **Executive Summary**

1. **Delayed products receive lower scores**. We are 95% confident products delivered on time in 78% of cases receive higher review scores compared to delayed delivery (On-time: [median 5, IQR 4–5]; Delayed: [median 2, IQR 1–4]). Despite being on time, remaining 22% of deliveries receive scores as low as delayed ones, indicating other factors like product/service quality affect ratings.
2. **Large/heavy products are ordered the least often**. Most ordered products are small or light (~40%) and medium-sized or weighted (~50%), leaving ~10% of large/heavy products.
3. **Size/weight does not impact scoring**. The score distribution for both characteristics in delayed deliveries is nearly the same (median 2, IQR 1–4), indicating no strong relationship between product size/weight groups and scoring. Statistical testing further supports this finding, with non-significant results (p-values: 0.34 for weight and 0.69 for size; effect size: <0.000 each (no effect)).
4. **5 most in-demand product categories**. Bed, Bath and Table (9.9%), Health & Beauty (8.6%), Sports Leisure (7.7%), Furniture Decor (7.4%) and Computers Accessories (7%) are the most popular categories (40.6% total).
5. **Customers do not tolerate delays in product categories**. Medium-high demand products (low-demand ones were excluded) receive nearly the same scores when delayed across categories (medium 2, IQR 1-4), indicating no customer tolerance for delay. Statistical testing further supports this finding, with non-significant result (p-value: 0.11; effect size: 0.001 (no effect)).
