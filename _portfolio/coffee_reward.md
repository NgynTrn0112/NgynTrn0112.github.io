---
title: "Coffee Promotion Campaign"
category: "analysis"
tools: ["Python","PosgreSQL","GoogleSheet"]
excerpt: "The mid-sized coffee shop chain launched a new membership reward program. An investigation to engagement performance and demographic drivors."
header: 
  image: "/assets/images/coffee_reward/coffee_background.jpg"
  teaser: "/assets/images/coffee_reward/coar_house_logo.png"
---

[![View on GitHub](https://img.shields.io/badge/GitHub-View_on_GitHub-blue?logo=GitHub)](https://github.com/NgynTrn0112/BA_portfolio/tree/main/coffee_reward)
## Table of Contents
1. [Project Background](#project-background)
2. [Business Objectives](#business-objectives)
3. [Executive Summary](#executive-summary)
4. [Insight Deep-dive](#insight-deep-dive)
    - [Informational offers](#informational-offers)
    - [Promotional offers: BOGO & Discount](#promotional-offers)
    - [Demographic Drivers](#demographic-drivers)
5. [Recommendations](#recommendations)
6. [Techinical Deep-dive](#technical-deep-dive)
---

## Project Background
The Coar House is a mid-sized coffee shop chain generating an average monthly revenue of approximately $1.5 million. To strengthen customer engagement and increase sales, the company recently launched a membership rewards program. Under this program, registered members receive promotional offers on a recurring basis, typically every few days.

These offers vary in format and intent:
- Informational offers: promotional messages highlighting new or seasonal menu items.
- Discount offers: price reductions when reaching a total purchase value.
- Buy One, Get One (BOGO): bundled deals designed to drive volume and attract groups.

The program funnel follows these stages:

1. Customers receive the offers
2. Customers view the offers
3. Customers complete/make transaction before deadline

Given the competitive landscape of the coffee retail industry, The Coar House seeks to understand how these different types of offers influence customer behavior, such as view and transaction/completion rates. The metrics can be calculated:

  $$\text{View rate} = \frac{\text{Number of viewed offers}}{\text{Number of offers sent}}$$
  $$\text{Completion rate} = \frac{\text{Number of offers redeemed}}{\text{Number of offers sent}}$$
  $$\text{Transaction rate} = \frac{\text{Number of offers followed by a transaction}}{\text{Number of offers sent}}$$

This analysis will provide data-driven insights into the effectiveness of the membership program, helping the company refine its promotional strategy and improve customer loyalty.

## Executive Summary

The analysis of 306k events in a span of 30-days shows a 7% stronger conversion of Discount over BOGO offers, notably with a same threshold, Discount yield 15% higher completion rate than BOGO though rewarding lower value. Promotion threshold plays a significant role in incentivise customer completing the offers where lower requirement return 5%-10% more completion rate. 

Customers from diverse demographics display variety of behaviours, yet the order in completion rate of the offers remains consistent amongst the different cohort. The Coar House can capitalise this piece of intelligence by profiling customers, optimising bundle, and enhance customer onboarding experience to increase customer lifetime value. 

<div align="center">
    <img src="/assets/images/coffee_reward/coffee_reward_erd.png">
    <figcaption>The Coar House Datasets ERD</figcaption>
</div>

## Business Objectives

We formulate the analysis to mainly answer the following areas:
- Informational:
    - How many offers were followed by transactions?
    - What is the completion rate?
- BOGO & Discount:
    - How many offers were completed?
    - What is the completion rate at each stage of each type?
    - What is the highest completion rate?
- Customer demographics:
    - Are there any underlying patterns in the offer completion?
    - What are the difference at each group?

## Insight Deep-dive:
### Informational advertisement:
There are a total of **15k** advertisements sent throughout the period, with a view rate of **51.3%** and transaction rate of **28.5%**. In other words, roughly **4.3k** informational offers were followed up with a transaction.

<div align="center">
    <img src="/assets/images/coffee_reward/informational_funnelchart.png" alt="Informational Funnel Chart">
</div>

Although, sharing similar number of offers, having slightly higher transaction/view statistic and longer expiry duration, *4-days* informational offers resulted in **800** transaction-followed offers gap to *3-days*, due to significant lower view rate **(40% to 62%)**.

The difference can partially be contributed to the different in engaging channel:
- 4-days: web, mobile, email
- 3-days: web, mobile, social

**Social channel driver**: This suggest the channel mix plays a role in shaping customer awareness and responsiveness, with *social* potentially generating **broader reach** and almost **same level conversion**.

<div>
    <img src="/assets/images/coffee_reward/informational_table.png" alt="Informational Summary Table" >
</div>

### Promotional Offers:
Generally, promotional offers yield significant higher view and completion(transaction) rate.

A total of **61k** were published during the period, with **76.8%** view and **55%** completion rate.

However, there is still outlier as 5 dollar *20-5 discount* offers generated only **34.7%** of view but **44.6%** of completion rate. The contradicting higher completion rate and low yield can be contributed to communicating channels: web and email. Customers received the offers in-place without noticing the on-going promotion.

<img src="/assets/images/coffee_reward/promotional_table.png" alt="Promotional Summary Table" style="max-width:100%; height:auto;">

- **Discount offers act as a stronger sales driver**: Despite haring similar number of offers and having higher views, BOGO-offer generated **2.3k** fewer transactions. However, the lower view rate is mainly driven by low statistics of *20-5 discount* offers.
- **Lower difficulty increases completion rate**: Lower purchase value required(difficulty) achieved higher completion rate within same offer type. 
    - Applied for BOGO, though BOGO 5-5 achieved 10% higher completion but 16% lower view rate than BOGO 10-10

### Demographic Drivers:
- **completion rate gradually increases as age reaching 50 and declines afterward**: Graph and Regression model suggest a Quadratic relation of completion rate and Age, while the model indicate the turning point at 50 years old.

<img src="/assets/images/coffee_reward/age_completionrate.png" alt="completion rate by Age" style="max-width:100%; height:auto;">

- **Higher income drives higher completion rate**: Graph and Regression model indicates a positive association of Income and completion rate. The model suggests that **2.7** times increase in *income* raises the *likelihood* by  *1.3* times.

<img src="/assets/images/coffee_reward/income_completionrate.png" alt="completion rate by Income" style="max-width:100%; height:auto;">

- **Female customers are more likely to redeem the offers**:
    - Female customers are more likely to complete the offers by 1.7 times compared to male
    - Due to very few customers classified as Other gender, the different is not statistically significant

<img src="/assets/images/coffee_reward/gender_completionrate.png" alt="completion rate by Gender" style="max-width:100%; height:auto;">

- **New customers are not engaging with the program**:
    - completion rate association with Tenure year follows an inverted U shape, peak at 2-3 year tenure with the total rate above 75%
    - The completion rate of *new* customers is below 50%, with the total below 40%

<img src="/assets/images/coffee_reward/tenure_completionrate.png" alt="completion rate by Tenure" style="max-width:100%; height:auto;">

### Recommendations:
1. **:Optimise Channel Mix**:
    - **Leverage social channels for awareness**: The significant gap of informational offers highlights *social* as a more effective engagement driver compared to email. The Coar House should prioritise social media in the channel mix for time-sensitive campaigns.
    - **Resolve channel visibility gaps**: The low view rate suffer of 20-5 *discount* despite stronger completion rate suggests poor visibility on web/email channel. The brand should consider investigate integration of *personalised subject lines*, *send times*, and *segmented mailing list* to improve the customers' experience and engagement
2. **Refine Promotional Offer Strategy**::
    - **Prioritise discount offers over BOGO**: Discount promotions are delivering strong sales impact, indicating customer preference for flexible price savings over constrained product bundles. Future campaign should emphasise discount mechanics
    - **Balance accessibility with profit**: Lower purchase thresholds drive higher completion. Design promotions with achievable thresholds to leverage the lift without eroding margin.
3. **Tailor Campaigns by Demographics**:
    - **Age targeting**: With completion peaking at 50 years, campaigns can be segmented into:
        - Young (<35): prioritise flexible offers with low difficulty, epmhasising convenience, mobile-first channels, and lifestyle branding
        - Middle-age (35-55): prioritise value-driven offers
        - Old (>55): test simplified mechanics to counteract declining engagement
    - **Income segmentation**: Since higher income customers are more likely to redeem, premium upsell campaigns (Ex: specialyy coffee, food bundle) can be targeted to this group
    - **Gender-driven personalisation**: Female customers are 1.7x more likely to redeem offers, while the majority of the customer base is male.
        - Optimise messaging for *Male* engagement by testing theme resonate better with them
        - Continue leveraging *Female* responsiveness through value-driven campaigns
        - Inclusivity efforts should be mainted by piloting tailored campaigns for *Other* gender
    - **Re-engage new customers**: Low redemption among first-year members indicates onboarding weakness. Introduce more simple, frequent, highly visible offers to encourage habit formation

<img src="/assets/images/coffee_reward/demographic_distribution.png" alt="Demographic Distribution" style="max-width:100%; height:auto;">

## Technical Deep-dive
### Datasets Overview
The datasets consist of 3 tables:
- `offers`: dimensional data of offers
- `customers`: demographic data of customers
- `events`: Activity data of customers, with record of receive, view, complete offers and make transactions

For more metadata details, please view the [data_dictionary](!https://github.com/NgynTrn0112/BA_portfolio/blob/main/coffee_reward/data_dictionary.csv).
<div align="center">
    <img src="/assets/images/coffee_reward/coffee_reward_erd.png">
    <figcaption>The Coar House Datasets ERD</figcaption>
</div>

`events` can be divided into 3 types storing in semi-structured format. Each type of event store different details in `value`:
- offer received:
    - `offer_id`
- offer viewed:
    - `offer_id`
- offer completed:
    - `offer_id`
    - `reward`: value rewarded for completing the offer, identical with `offer` . `reward`
- transaction:
    - `amount`: total purchase value

Without having identification key like `event_id` or `transaction_id`, this pose challenge to match `transaction` to the related `offer` and the `offer_received` to `offer_completed`.

`customers` have the demographic details of 17k customers, with 2175, equivalent to **12.5%**, missing the data of age and income. Furthermore, the age of the missing customers are all set at 118. On the other hand, the remaining two are relatively clean

### Preprocessing
Due to only having `customer_id`, the data-missing customers are lacking the details to impute the missing data. Hence, regarding the demographic analysis, we remove the all of those customers.

However, for the overall trend, we retain those. This leads to a disparity of the total completion rate of the two datasets. Additionally, the data shows that this group of customers is disengaging, redeeming only 14.5% of the promotion offered. 

To prepare for the analysis, we segment the `events` into 4 subsets: `received`, `viewed`, `completed` and `transaction`. As only Discount and BOGO can be completed, only `received` and `viewed` were segmented into informational and promotional subsets. *ast* package is used to extract unstructured json data.

### Analysis - Python
The analysis is mainly carried out by dataframe manipulation and aggregation function via *pandas* and *numpy*, while the visualisations are generated by *seaborn* and *matplotlib.pyplot*.

### Logistics Regression
#### Preprocessing with SQL
To perform Logistics Regression, we need independent variable to be binary. However, as previously mentioned, `events` is lacking a primary, posing a challenge of matching of each stage in the funnel. Although having deadline as a validation, there are cases customers redeemed and claimed the same offers simultaneously.

We decide to use SQL to create the desired data set. The idea is to use SQL window function ROW_NUMBER() to partition the data by `customer_id` and `offer_id`. We, then, join the mutated `received` and `completed`by matching same `customer_id`, `offer_id` and the order. For more detail, please view [SQL script](!https://github.com/NgynTrn0112/BA_portfolio/blob/main/coffee_reward/sql_Tablegeneration.txt) for more details.

#### Descriptive
