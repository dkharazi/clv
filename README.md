# customer-centricity

In most cases, customer lifetime value (or CLV) represents the present value of
the future cash flows attributed to a customer relationship, or how much a customer is worth (maybe in USD) over their entire lifetime with a company. Marketing departments spend much of their attention on tactical initiatives, such as who to target in an upcoming seasonal email campaign or how to allocate marketing budget across channels, which can be solved by marketing mix modeling. However, these should be thought of as secondary initiatives, where the primary initiative or ultimate objective should be to increase the value of the firm by:
1. Improving the acquisition of new customers
2. Improving the CLV of new and existing customers
3. Decreasing the riskiness of the customer portfolio

Marketing departments shouldn't lose sight of these higher-level, fundamental objectives. Some companies will fail to address these objectives by assigning a single, average value to represent the CLV of all of their customers. By doing this, those companies are assuming every customer behaves and is worth the same.

# CLV Assumptions and Principles

Companies typically will make sure their cost of acquiring a customer (or CAC) is less than that customer's lifetime value. A company could say *"I know the CLV of each customer for my business is $100, so that's the most I can spend to acquire them."* However, the obvious reasons for why this statement is wrong relate to the following principles:
1. Since CLV is a forward-looking estimate, we should include confidence intervals for our CLV estimates
2. Since customers behave differently, not all customers should have the same CLV
3. Since current sales have already happened, we should be interested in the future spend of a customer
4. Since CLV is an estimate, we should be estimating the future cost of acquiring a customer too

To touch on the first principle, estimates of future revenue can be decomposed into four general components directly related to CLV estimates. Specifically, future revenue (or estimated CLV) can be decomposed into the following components:
- How many customers will we acquire?
- How long will those acquired customers stay with us?
- How many transactions will those customers make over that horizon?
- How valuable will those transactions be?

To be specific, calculating how long acquired customers will stay with us directly relates to [survival analysis](https://lifelines.readthedocs.io/en/latest/Survival%20Analysis%20intro.html). Then, calculating the number of orders made by customers during their lifetimes involves computing order frequency estimates using a Pareto/NBD or BG/NBD model. Lastly, calculating the value of customers over their lifetimes involves computing the average value of transactions using a Gamma-Gamma submodel. By adding up all of these components, we can calculate customer-level CLS estimates as the present value of the expected sum of discounted cash flows (DCF).

Regarding the second principle, an average CLV shouldn't be generalized across all customers. There is plenty of [evidence of customer heterogeneity](http://brucehardie.com/papers/022/fader_hardie_mksc_10.pdf), meaning we shouldn't assume customers are all the same. In other words, we shouldn't assume each customer's CLV is equal to the same average. Instead, we should assume they all have different values.

For example, customer 1 and customer 2 have very different purchasing behaviors based on their order recency and frequency in the illustration below. Notice, customer 2 has a much higher likelihood of churning compared to customer 1. If we have the power of looking into the future at each customer's actual purchases, then we'll see customer 1 should have a higher estimated CLV compared to customer 2. This point should help illustrate how each customer should be treated differently with a different estimated CLV.

![CLV Illustration 1](https://raw.githubusercontent.com/dkharazi/customer-centricity/main/clv1.svg)

Regarding the third principle, estimating the value of our customers solely based on historical sales shouldn't be our main focus. Instead, it's more interesting to focus on CLV, since it's a future-looking estimate of spend, instead of historical sales. To illustrate this point, notice how customer 1 and customer 2 have different order recencies in the illustration below. More specifically, customer 1 has more purchases compared to customer 2 historically, but customer 2 has purchased more frequently and recently compared to customer 1. Even though both of these customers may be considered high value customers, customer 2 has a higher CLV if we regained our power to look into the future at each customer's actual purchases.

![CLV Illustration 2](https://raw.githubusercontent.com/dkharazi/customer-centricity/main/clv2.svg)

# Wayfair: a CLV Case Study 

If our CLV estimates are accurate enough, we can use those CLV estimates to measure the value of our acquired customers across their lifetimes, rather than the hisorical spend of our customers. This is an important concept for determining whether our acquired customers should be considered high-value or low-value customers. For example, [Peter Fader](https://www.youtube.com/watch?v=0iLQCNYdNb4&ab_channel=TalksatGoogle) and [Daniel McCarthy](https://twitter.com/d_mccar/status/1376564874713702408) have both mentioned Wayfair's acquisitions are growing too fast without retaining repeat buyers or high-value customers. In other words, they're acquiring a lot of low-value customers, and they haven't established enough of a base of repeat buyers, who they can rely on when their acquisitions level off. As a result, their revenue is expected to drop once acquisitions reach their peak, which is illustrated in the following figure.

![Wayfair Acquisition Costs](https://raw.githubusercontent.com/dkharazi/customer-centricity/main/clv3.png)

![Wayfair Forecasted Revenues](https://raw.githubusercontent.com/dkharazi/customer-centricity/main/clv4.png)

Those forecasts didn't account for the occurrence of the pandemic, causing acquistions to continue to grow even more rapidly than expected. Since the start of the COVID-19 pandemic, competitors have removed their furniture supply from the market [by either closing their brick-and-mortar stores or declaring bankruptcy](https://www.cnbc.com/2020/04/06/wayfair-shares-surge-37percent-as-coronavirus-drives-sales-of-office-furniture.html), leading to even greater levels of acquired customers for Wayfair.

However, this doesn't solve their problem with retaining high-value customers and only puts off confronting this ongoing retention issue. Since 2019, Wayfair has [admitted to growing too fast in the past](https://www.bostonglobe.com/2020/02/28/business/wayfair-stock-takes-another-hit-amid-sales-slowdown/) and has carried out large-scale layoffs, while [raising increasing amounts of debt](https://chainstoreage.com/analysis-wayfair-has-failed-turn-over-new-leaf-net-loss-continues-rise) to fund their operating losses. For every growing company, acquisition must reach a peak and level off at some point. When that time comes, these companies must rely on its base of repeat buyers (or high-value customers) make decreases in acquisition seem unnoticeable.

For most successful companies, there's enough of an established base of ongoing, repeat buyers after acquisitions level off. As an example, Amazon acquired and developed enough of their buyers to be high-value and repeat buyers, so slight decreases in their customer acquisition didn't impact their revenue.

For a deeper understanding of the forecasts and underlying CLVs at Wayfair, refer to [McCarthy and Fader's paper](https://deliverypdf.ssrn.com/delivery.php?ID=217116104122089025069125121097076103121046070053091056099116021109091027113116024081057056103059050003021087120021001116093091000085032086058068011118113065000099106025080050118126124103092083099108005018031018083106115029070123004010092120067092069115&EXT=pdf&INDEX=TRUE). Refer to [these slides from Roberto Medri](http://cdn.oreillystatic.com/en/assets/1/event/85/Case%20Study_%20What_s%20a%20Customer%20Worth_%20Presentation.pdf) for a deeper, high-level explanation about customer lifetime value. For a lower-level understanding of CLV models and how they're built, refer to [this talk at Wharton by Peter Fader](https://www.youtube.com/watch?v=guj2gVEEx4s&ab_channel=FirstMarkCapital). Or, refer to [this talk at Google by Peter Fader](https://www.youtube.com/watch?v=0iLQCNYdNb4&ab_channel=TalksatGoogle) for illustrations of how we can target and apply separate customer targeting tactics on different CLV segments of customers.

# Applications of CLV

There are many use-cases for CLV to be used across any type of business. The following are only a few use-cases that can provide immediate impact to a company:
- Valuating channels or cohorts of customers by comparing average CLV against average CAC for a particular acquisition channel or cohort of customers
- Determine more meaningful customer segments based on unique purchasing behavior or CLV estimates
- Design more forward-looking tests for determining changes in CLV or future lifts for cohorts
- Applying more effective customer targeting strategies (i.e. premium offerings and loyalty programs) to low-value or high-value customers based on CLV
- Improving retention of future customer cohorts
- Improving acquisitions of customer cohorts
- Evaluating histogram of binned CLVs for recent customers relative to binned CLVs for long-time customers 

# Modeling CLV

Generating accurate revenue projections plays an important role at any business, and CLV should be included in these estimates, especially since every dollar of revenue that a company generates must come from its customers. Typically, financial professionals forecast business revenues and expenses using time-series models. This may be a sensible modeling methodology when customer data is unavailable to the firm. However, forecasting accuracy can be improved by decomposing customer-driven financial line items into their constituent components, estimating models and forecasting these parts into the future, then aggregating these components back together again to form projections of future customer-driven financial line items, rather than estimates based solely on historical sales. In the end, revenue forecasts should include these components whenever customer data is available.

In most cases, RFM features (recency, frequency, spend, and tenure) are sufficient in predicting CLV estimates stochastically for customers. From personal experience, a model with these RFM features will achieve a nearly identical accuracy compared to that same model including additional demographic, engagement, and other sets of features. Here, CLV is calculated using DCF as a combination of two estimates: estimated average spend of a customer and estimated number of orders over a customer's lifetime. The average spend of a customer is estimated using a BG/NBD model, and the order frequency of a customer is estimated using a Gamma-Gamma submodel.

Either the BG/NBD model or the Pareto/NBD model can be used to estimate the order frequency of a customer, and both models employ the same constraints and only require 3 features: recency, frequency, and tenure features. The primary difference between these two models is that the BG/NBD model maps the survivorship curve to a beta-geometric distribution instead of a Pareto distribution. Specifically, the time to *dropout* (or churn) is modeled using the Pareto (or beta-geometric) timing model. For both models, repeat-purchasing behavior while active is modeled using the NBD (or negative binomial) counting model.

Generally, both models are used to model non-contractual purchasing behavior of customers. The BG/NBD model slightly adjusts the assumptions of the Pareto/NBD model in order to speed up estimation drastically. In particular, the BG/NBD model has the following assumptions:
- Each active customer has their own Poisson distribution with transaction rate λ
  - Here, λ represents the expected number of transactions in a time interval
  - The number of orders made by a customer in a given time period (i.e. month, year, etc.) comes from this poisson distribution
- Each customer can have a different λ (i.e. transaction rates are heterogeneous across all customers)
  - Here, the heterogeneity in λ is assumed to follow a Gamma distribution
- After each purchase, each customer has an α probability of churning (i.e. never buying again)
  - Here, α is assumed to follow a Geometric distribution
  - Roughly, a customer's probability of churning decreases as a customer places more orders
- Each customer can have a different α (i.e. probabilities of churning are heterogenous across all customers)
  - Here, the heterogeneity in α is assumed to follow a Beta distribution

To help illustrate these parameters, let's imagine every customer (who are repeat purchases) has two coins. In particular, each customer flips a coin every day to see if they purchase or not (i.e. a purchase coin). After this first coin is flipped, each customer will flip their second coin. This second coin will decide whether they die or not (i.e. a drop-out coin). Once a customers flips heads on the die coin, then they will stop flipping both coins and exit the experiment.

To tie in the model parameters with our analogy, the number of times our first coin (i.e. purchase coin) landed on heads (or the customer purchased) in a given period (e.g. month, year, etc.) is our transaction rate λ, which determines the shape of their own Poisson distribution. The heterogeneity in transaction rates across different customers follows a Gamma distribution. Each customer's second coin has a different probability α of landing on heads, or the customer dropping out and never buying again. Each customer's chance of dropping out is represented by their own α parameter, which determines the shape of their own Geometric distribution. The heterogeneity in drop-out probabilities across different customers follows a Beta distribution.

The CLV of customers can be estimated using ML models, such as boosting methods, random forests, LSTMs, etc. However, the probabilistic models usually produce similar out-of-sample accuracies and do as good of a job at estimating our variables of interest, while requiring fewer features and customer data. As an additional point, keep in mind most ML models require labels. If we're truly interested in predicting CLVs for a non-contractual company, then it's impossible to ever retrieve actual CLVs for each customer, since we don't know when they actually churn.

Again, for a deeper dive into modeling customer behavior for both transactional and non-transactional businesses, refer to [McCarthy's dissertation](https://repository.upenn.edu/cgi/viewcontent.cgi?article=4247&context=edissertations). For high-level intuitions behind each parameter, refer to [this Medium article](https://towardsdatascience.com/predicting-customer-lifetime-value-with-buy-til-you-die-probabilistic-models-in-python-f5cac78758d9). For comprehensive descriptions of the parameters used in modeling CLV, refer to [Bruce Hardie's slides](http://www.brucehardie.com/talks/ho_cba_tut_art_09.pdf).

# Customer-Based Corporate Valuation Metrics

Corporate valuation is the process of determining the value of a company. Since every dollar of revenue generated by a company must come from its customers, it only makes sense for the valuation of a company to be centered around customer-based metrics. Notably, only a few customer-based corporate valuation (or CBCV) metrics are needed to accurately predict the worth of a company.

Very roughly, revenue comes from either acquired customers or retained customers. In general, companies that do a good job of retaining and developing their customers over time are positioning themselves to increase the worth of their companies in the long run. Specifically, there are six metrics reflecting a company's repeat-purchasing patterns:
- `AU:` Number of active users
- `HAU:` Number of heavy active users
- `F:` Average frequency of orders from active users
- `RR:` Rate of repeat customers
- `RBPO:` Percentage of orders from repeat buyers
- `RBPC:` Percentage of customers who are repeat buyers

Here, `AU` represents the number of customers who've placed at least 1 order in the current year, whereas `HAU` represents the number of customers who've placed at least 2 orders in the current year. Internally, these thresholds act as a good starting points across different types of companies, but could be adjusted based on what a company considers a *heavy active user*. Additionally, the `F` metric represents the average orders placed by active users in the current year.

The `RR` metric represents the percentage of the previous year's buyers who buy again in the current year, relative to all of the previous year's buyers. On a similar note, `RBPO` represents the percentage of the current year's orders from customers with an order in the previous year, relative to all of the current year's orders. Whereas, the `RBPC` metric represents the percentage of of the current year's buyers with an order in the previous year, relative to all of the current year's buyers. In a non-contractual setting, these metrics act as an observable workaround to *retention rate* metrics.

For more information about the accuracy of this small set of customer-based corporate valuation metrics, refer to [Dan McCarthy's slides from his presentation at Wharton](https://scientistcafe.com/CIRUG/2017_07_24ASA_TalkDanMcCarthy.pdf). For a deeper understanding of the math behind these metrics and examples of companies using these metrics in practice, refer to [McCarthy and Fader's paper](https://deliverypdf.ssrn.com/delivery.php?ID=217116104122089025069125121097076103121046070053091056099116021109091027113116024081057056103059050003021087120021001116093091000085032086058068011118113065000099106025080050118126124103092083099108005018031018083106115029070123004010092120067092069115&EXT=pdf&INDEX=TRUE). For a deeper dive into modeling customer behavior for both transactional and non-transactional businesses, refer to [McCarthy's dissertation](https://repository.upenn.edu/cgi/viewcontent.cgi?article=4247&context=edissertations).

# Implementing CLV Models

As a general rule, modeling aggregate customer behavior in a non-contractual setting is a solved problem if the modeler has access to individual-level customer data. If individual-level customer data isn’t available to the model for evaluating a non-contractual business, [Fader and McCarthy](https://deliverypdf.ssrn.com/delivery.php?ID=776114008100075122082093005101119014038018014015006038127117098011069080076116004007106099010022103035124021028124014107086028126008014016039097081012116113097098123041011057120102126103076114007028069126094121085068106006126005103099117092085113125069&EXT=pdf&INDEX=TRUE) recommend following a CBCV model (or using their 6 proposed customer metrics) instead. For a more in-depth analysis about the math behind their well-tested probabilistic models, refer to [Hardie and Fader's paper](http://www.brucehardie.com/papers/020/fader_et_al_mksc_10.pdf) about their proposed CLV models in a non-contractual setting.

```python
var u = 1
```
DERT = (expected orders from now) x (probability customer is alive at a given time) x (discount rate)
    - E[RLV] = (expected average spend per order) x DERT
    - E[PAV] = E[RLV] + (value of old orders)
    - E[CLV] = E[PAV] - CAC
    - CE = sum of all CLVs

For a clearer defintion about the differences between residual lifetime values, customer lifetime values, and other customer-based metrics, refer to [McCarthy's slides](https://www.dropbox.com/s/xjak7pezn6i9m06/CLV%20framework.pptx). For slides about the high-level components included in these probabilistic CLV models, refer to [Hardie and Fader's slides](http://www.brucehardie.com/talks/ho_cba_tut_art_09.pdf). For more intuition behind the mathematical componented included in the models, refer to [Hardie and Fader's paper](http://www.brucehardie.com/papers/020/fader_et_al_mksc_10.pdf).

