# customer-centricity

In most cases, customer lifetime value (or CLV) represents the present value of
the future cash flows attributed to a customer relationship, or how much a customer is worth (maybe in USD) over their entire lifetime with a company. Marketing departments spend much of their attention on tactical initiatives, such as who to target in an upcoming seasonal email campaign or how to allocate marketing budget across channels, which can be solved by marketing mix modeling. However, these factors should be thought of as secondary initiatives, where the primary initiative or ultimate objective should be to increase the value of the firm by:
1. Improving the acquisition of new customers (e.g. number of newly acquired customers)
2. Improving the CLV of newly, acquired customers
3. Improving the CLV of existing, retained customers
4. Decreasing the riskiness of the customer portfolio

Marketing departments shouldn't lose sight of these higher-level, fundamental objectives. Specifically, companies should invest in the three major customer-based strategies: customer acquisition, customer retention, and customer development. Some companies will fail to address these objectives by assigning a single, average value to represent the CLV of all of their customers. By doing this, those companies are assuming every customer behaves and is worth the same.

# CLV Assumptions and Principles

There is growing evidence that no customer is born the same, each with his or her own preferences, propensities, and potential. In the the [Customer Centricity Playbook](https://wsp.wharton.upenn.edu/book/customer-centricity-playbook/), Peter Fader describes this idea of *customer goodness*, which specifically ties into this assumption and thinking that each customer is born with his or her own set of inherent propensities to engage in a campaign, purchase a certain product, etc. This set of baked-in propensities manifest themselves into customer preferences and translate into a potential value. However, we should think of customer's only being born with baseline propensities. Meaning, these propensities can be developed, and mid-value customers may be developed into high-value customers. For example, customers' propensities for purchasing may increase if effective loyalty programs are implemented or the brand reputation receives a boost. In contrast, a poor customer experience may decrease a certain customer's propensities. By following this thinking, CLV can unlock many doors for a company, since we can start to understand how much a customer is likely to spend throughout their life cycle with our company.

In a non-contractual setting, a customer's true CLV is always unknown and unobservable, since a customer never declares when he or she wants to churn. As a result, it is necessary to estimate each customer's CLV, which includes estimating metrics like future revenue, orders, etc. Estimates of future revenue can be decomposed into four general components directly related to the *acquisition part* of CLV estimates. Specifically, future revenue (or estimated CLV) can be decomposed into the following components:
- How many customers will we acquire?
- How long will those acquired customers stay with us?
- How many transactions will those customers make over that horizon?
- How valuable will those transactions be?

Similarly, estimates of future revenue can be decomposed into nearly identical components directly related to the *retention part* of CLV estimates. Specifically, future revenue (or estimated RLV) can be decomposed into the following components:
- How must customers will be retained?
- How long will those retained customers stay with us?
- How many transactions will those customers make over that horizon?
- How valuable will those transactions be?

To be specific, calculating how long customers will stay with us directly relates to [survival analysis](https://lifelines.readthedocs.io/en/latest/Survival%20Analysis%20intro.html). Then, calculating the number of orders made by customers during their lifetimes involves computing order frequency estimates using a Pareto/NBD or BG/NBD model. Lastly, calculating the value of customers over their lifetimes involves computing the average value of transactions using a Gamma-Gamma submodel. By adding up all of these components, we can calculate customer-level CLS estimates as the present value of the expected sum of discounted cash flows (DCF).

Companies typically will make sure their cost of acquiring a customer (or CAC) is less than that customer's lifetime value. A company could say *"I know the CLV of each customer for my business is $100, so that's the most I can spend to acquire them."* However, the obvious reasons for why this statement is wrong relate to the following principles:
1. Since CLV is a forward-looking estimate, we should include confidence intervals for our CLV estimates
2. Since customers behave differently, not all customers should have the same CLV
3. When focusing on retention, we should be interested in the future spend of a customer, since current sales have already happened
4. When focusing on acquisition, we should be estimating the future cost of acquiring a customer, since CLV is an estimate as well in a non-contractual setting

Regarding the second principle, an average CLV shouldn't be generalized across all customers. There is plenty of [evidence of customer heterogeneity](http://brucehardie.com/papers/022/fader_hardie_mksc_10.pdf), meaning we shouldn't assume customers are all the same. In other words, we shouldn't assume each customer's CLV is equal to the same average. Instead, we should assume they all have different values.

For example, customer 1 and customer 2 have very different purchasing behaviors based on their order recency and frequency in the illustration below. Notice, customer 2 has a much higher likelihood of churning compared to customer 1. If we gained the power of being able to see into the future and look at each customer's actual purchases, then we'll see customer 1 should have a higher estimated CLV compared to customer 2. This point should help illustrate how each customer should be treated differently with a different estimated CLV.

![CLV Illustration 1](https://raw.githubusercontent.com/dkharazi/customer-centricity/main/clv1.svg)

Regarding the third principle, estimating the value of our customers solely based on historical sales shouldn't be our main focus. Instead, it's more interesting to focus on CLV, since it's a future-looking estimate of spend, instead of historical sales. To illustrate this point, notice how customer 1 and customer 2 have different order recencies in the illustration below. More specifically, customer 1 has more purchases compared to customer 2 historically, but customer 2 has purchased more frequently and recently compared to customer 1. Even though both of these customers may be considered high value customers, customer 2 has a higher CLV if we regained our power to look into the future at each customer's actual purchases.

![CLV Illustration 2](https://raw.githubusercontent.com/dkharazi/customer-centricity/main/clv2.svg)

# Wayfair: a CLV Case Study 

If our CLV estimates are accurate enough, we can use those CLV estimates to measure the value of our acquired customers across their lifetimes, rather than the hisorical spend of our customers. This is an important concept for determining whether our acquired customers should be considered high-value or low-value customers. For example, [Peter Fader](https://www.youtube.com/watch?v=0iLQCNYdNb4&ab_channel=TalksatGoogle) and [Daniel McCarthy](https://twitter.com/d_mccar/status/1376564874713702408) have both mentioned Wayfair's acquisitions are growing too fast without retaining repeat-buyers or high-value customers. In other words, they're acquiring a lot of low-value customers, and they haven't established enough of a base of repeat buyers, who they can rely on when their acquisitions level off. As a result, their revenue is expected to drop once acquisitions reach their peak, which is illustrated in the following figure.

![Wayfair Acquisition Costs](https://raw.githubusercontent.com/dkharazi/customer-centricity/main/clv3.png)

![Wayfair Forecasted Revenues](https://raw.githubusercontent.com/dkharazi/customer-centricity/main/clv4.png)

Those forecasts didn't account for the occurrence of the pandemic, causing acquistions to continue to grow even more rapidly than expected. Since the start of the COVID-19 pandemic, competitors have removed their furniture supply from the market [by either closing their brick-and-mortar stores or declaring bankruptcy](https://www.cnbc.com/2020/04/06/wayfair-shares-surge-37percent-as-coronavirus-drives-sales-of-office-furniture.html), leading to even greater levels of acquired customers for Wayfair.

However, this doesn't solve their problem with retaining high-value customers and only puts off confronting this ongoing retention issue. Since 2019, Wayfair has [admitted to growing too fast in the past](https://www.bostonglobe.com/2020/02/28/business/wayfair-stock-takes-another-hit-amid-sales-slowdown/) and has carried out large-scale layoffs, while [raising increasing amounts of debt](https://chainstoreage.com/analysis-wayfair-has-failed-turn-over-new-leaf-net-loss-continues-rise) to fund their operating losses. For every growing company, acquisition must reach a peak and level off at some point. When that time comes, these companies must rely on its base of repeat buyers (or high-value customers) make decreases in acquisition seem unnoticeable.

For most successful companies, there's enough of an established base of ongoing repeat-buyers after acquisitions level off. As an example, Amazon acquired and developed enough of their buyers to be high-value and repeat buyers, so slight decreases in their customer acquisition (after their peak) didn't impact their revenue.

For a deeper understanding of the forecasts and underlying CLVs at Wayfair, refer to [McCarthy and Fader's paper](https://deliverypdf.ssrn.com/delivery.php?ID=217116104122089025069125121097076103121046070053091056099116021109091027113116024081057056103059050003021087120021001116093091000085032086058068011118113065000099106025080050118126124103092083099108005018031018083106115029070123004010092120067092069115&EXT=pdf&INDEX=TRUE). Refer to [these slides from Roberto Medri](http://cdn.oreillystatic.com/en/assets/1/event/85/Case%20Study_%20What_s%20a%20Customer%20Worth_%20Presentation.pdf) for a deeper, high-level explanation about customer lifetime value. For a lower-level understanding of CLV models and how they're built, refer to [this talk at Wharton by Peter Fader](https://www.youtube.com/watch?v=guj2gVEEx4s&ab_channel=FirstMarkCapital). Or, refer to [this talk at Google by Peter Fader](https://www.youtube.com/watch?v=0iLQCNYdNb4&ab_channel=TalksatGoogle) for illustrations of how we can target and apply separate customer targeting tactics on different CLV segments of customers.

# Applications of CLV

There are many use-cases for CLV to be used across any type of business. The following are only a few use-cases that can provide immediate impact to a company:
- Valuating channels or cohorts of customers by comparing average CLV against average CAC for a particular acquisition channel or cohort of customers
- Targeting more meaningful customer segments based on CLV estimates or other unique purchasing behaviors
- Designing more forward-looking A/B tests by observing changes in CLV or future lifts for test and treatment groups
- Applying more effective customer targeting strategies (i.e. premium offerings and loyalty programs) to low-value or high-value customers based on CLV
- Create marketing strategies for certain customer cohorts based on CLV
- Develop customer segments based on CLV
- Apply targeting forecasting and customer evolution for particular customer segments based on CLV
- Create different communication, services and loyalty programs based on CLV
- Awake any *non-active* customers based on CLV
- Estimate total customer equity
- Improving retention of future customer cohorts
- Improving acquisitions of customer cohorts
- Evaluating histogram of binned CLVs for recent customers relative to binned CLVs for long-time customers

#### Types of Acquisition Strategies and Tactics

In order to grow the CLV of customers, a company must first acquire a sizable number of high-value customers. The *80:20 rule* states that 80% of a firm's future profits come from just 20% of their existing customers. There are slight deviations and exceptions to this rule, depending on a company's industry, stage in its lifecycle, and many other factors. For the most part, this rule seems to be seen in practice for more mature companies. Acquisition strategies are important because the company is then able to grow the size of their customer base, leading to an increase in the number of customers covered by this figure of 20%. Also, a company has the opportunity to decide who is included in that 20 percent of customers, and they likely will want to ensure high-value customers are included in this percentage of customers or even grow the CLV of this cohort of customers.

There are four general categories of tactics and strategies used for acquiring customers:
- Direct-broad acquisition approach
- Direct-selective acquisition approach
- Indirect-broad acquisition approach
- Indirect-selective acquisition approach

In general, a direct tactic simply involves a company reaching out to a known customer prospect directly and individually, whereas an indirect tactic involves a company reaching out to an unknown customer prospect indirectly. A broad strategy refers to a generalized approach for acquiring a customers, whereas a selective strategy refers to a more targeted approach. Said another way, an approach is broad when the strategy isn't meant to be targeted on a certain cohort of customers, whereas an approach is selective when the strategy is meant to be targeted on a certain cohort of customers. Today, firms are able to obtain and analyze more specific information about individual customers than ever before. Also, storing this information is incredibly cheap compared to previous years. As a result, the world is becoming more direct as time goes on.

A direct-broad acquisition approach will directly target individual customer leads in the broad customer audience, where some or very little information is known about them. For example, maybe the potential lead provided their phone number or email address in a previous email campaign. This approach aims to reach customers broadly through telemarketing, canvassing, Google marketing, etc.

A direct-selective acquisition approach will directly target individual customer leads in a particular segment of the customer audience, where some information is known about them. For example, a company may have little information on these potential leads, but the information would be enough to segment them and apply more targeted approaches through their preferred channel. Usually, this approach involves some customer segmentation or look-alike modeling to be done beforehand.

An indirect-broad acquisition approach will indirectly target customer leads in the broad customer audience, where almost no information is known about them. This approach usually involves coming up with generalized marketing messages for a more mainstream audience. In other words, a company is casting the widest net to reach as many unidentifiable customers as possible. Telivision ads, billboards, and word-of-mouth are all examples of indirect-broad acquisition approaches.

An indirect-selective acquisition approach will indirectly target customer leads in a particular segment of the customer audience, where almost no information is known about them. For example, this approach could include offering referrals to only high-value customers or other targeted customer cohorts. Offering referrals to any customer may be considered an indirect-broad aqcuisition approach, instead. 

Again, most of this research has been done by Peter Fader and Bryce Hardie, which is outlined in [Peter Fader's Customer Centricity Playbook](https://wsp.wharton.upenn.edu/book/customer-centricity-playbook/). For more details about customer-centric strategies, assumptions, and findings, refer to Fader's playbook.

#### Types of Retention Strategies and Tactics

Again, most of this research has been done by Peter Fader and Bryce Hardie, which is outlined in [Peter Fader's Customer Centricity Playbook](https://wsp.wharton.upenn.edu/book/customer-centricity-playbook/). For more details about customer-centric strategies, assumptions, and findings, refer to Fader's playbook.

# Sample CLV-Related Metrics
In the early stages of tracking customers' CLV, it's important to monitor certain metrics when focusing on customer acquisition, retention, and development. The following metrics are examples of useful metrics related to CLV, but there could be many more estimates:
- Propensity to be acquired
- Propensity to churn
- Propensity to develop into a higher value customer
- Propensity to refer others
- Propensity to respond to the right messages

# Implementing CLV Models

As a general rule, modeling aggregate customer behavior in a non-contractual setting is a solved problem if the modeler has access to individual-level customer data. If individual-level customer data isn’t available to the model for evaluating a non-contractual business, [Fader and McCarthy](https://deliverypdf.ssrn.com/delivery.php?ID=776114008100075122082093005101119014038018014015006038127117098011069080076116004007106099010022103035124021028124014107086028126008014016039097081012116113097098123041011057120102126103076114007028069126094121085068106006126005103099117092085113125069&EXT=pdf&INDEX=TRUE) recommend following a CBCV model (or using their 6 proposed customer metrics) instead. For a more in-depth analysis about the math behind their well-tested probabilistic models, refer to [Hardie and Fader's paper](http://www.brucehardie.com/papers/020/fader_et_al_mksc_10.pdf) about their proposed CLV models in a non-contractual setting.

In a non-contractual setting, CLV is unknown and unobservable when a customer is active, since customers don't raise their hand and alert a firm about when they're ready to churn. Note, we can only estimate CLV, since the true CLV values are unobservable. Mathematically, our expected values of CLV are denoted as E[CLV].

When calculating CLV estimates, we'll need to compute the [discounted expected residual transactions (or DERT) of a customer](https://www.rdocumentation.org/packages/BTYD/versions/2.4.2/topics/pnbd.DERT), which can be done in R using the BTYD package coauthored by both Peter Fader and Daniel McCarthy. DERT is an estimate dependent on two additional estimates: the estimated customer-level expected orders from now and the estimated probability of a customer being alive at a given moment. Mathematically, the formula for **DERT** is given below, where **EO** is the expected orders from now, **EPC** is the expected probability of a customer being alive at a given moment, and **DR** is the discount rate.

```
DERT = EO x EPC x DR
```

Once the estimates within the DERT computation are calculated and DERT is finally computed, then we can calculate the expected residual lifetime value (or RLV). To be clear, **RLV** is unobservable and unknown in a non-contractual setting when a customer is still active, so we'll need to calculate the E[RLV]. The formula for E[RLV] is given below, where **ESO** is the expected customer-level average spend per order:

```
E[RLV] = ESO x DERT
```

In general, the CLV metric is useful when focusing on acquisition, whereas the RLV metric is useful when focusing on retention. Since, RLV only includes future variable profits and excludes previous profits. CLV also includes the cost of acquiring the customer (or **CAC**). Specifically, the formula for the expected post aquisition value (or **PAV**) is given below, where **VO** is the value of old orders:

```
E[PAV] = E[RLV] + VO
```

In other words, PAV just refers to CLV before deducting CAC. In general, PAV determines the upper bound on how to spend on CAC. Then, a positive CLV indicates a given customer is profitable, whereas a negative CLV indicates a given customer isn't profitable and likely isn't worth acquiring. For monitoring purposes, typically it's more useful to track PAV, CLV, and CAC separately, since ratios can sometimes be misleading in this case. 

Lastly, **CLV** represents PAV minus costs of acquisition. Again, the CLV metric is useful when focusing on acquisition and less useful when focusing on retention, since the goal of retention strategies is to increase what remaining value can be extended. Hence, why we prefer RLV for retention strategies. Here, the sum of all customers' CLV is known and referred to as customer equity (or CE).

```
E[CLV] = E[PAV] - CAC
```

In many cases, firms use **CE** to represent financial value of the customer base, which typically is the most significant, if not entire, portion of a firm's worth. More specifically, CE is is a valuation measure that is an estimate of a company’s valuation in dollars. When calculating CE, it isn't entirely correct to incorporate the CLV of existing customers, since this adds the total historical value of those existing customers. In truth, any historical spend is already sunk. This issue is easily remedied by defining CE to be equal to the RLV of existing (or retained) customers plus the net present value of the CLV of all future customers who haven't been acquired yet. The formula for CLV is given below:

```python
CE = 0

for c in customers:
  if c.is_existing_customer:
    CE = CE + c.RLV
  else:
    CE = CE + c.CLV
```

For a clearer definition about the differences between residual lifetime values, customer lifetime values, and other customer-based metrics, refer to [McCarthy's slides](https://www.dropbox.com/s/xjak7pezn6i9m06/CLV%20framework.pptx). Also, refer to [his sample spreadsheet](https://www.dropbox.com/s/dv2epzyhktdtazo/CLV%20taxonomy.xlsx) or [his slides](https://www.dropbox.com/s/x7b7e1kq7gk9id1/summarizing%20buyer%20behavior%20in%20excel%20clean.pptx) for an example of how CLV can be calculated. For a granular summary and overview of customer equity and its relation to CLV, refer to [McCarthy's paper](https://deliverypdf.ssrn.com/delivery.php?ID=094105095110064008003086086022107024001033030064027066098109068088068009091005007071020045051127023056111099107027079081119064107001090050083103105083098093098104120036022056002073019080115123098125000029097094117122001072114003023119090007105085118119&EXT=pdf&INDEX=TRUE). For slides about the high-level components included in these probabilistic CLV models, refer to slides 65 and 148 in [Hardie and Fader's presentation](http://www.brucehardie.com/talks/ho_cba_tut_art_09.pdf). For an explanation of common misconceptions or misrepresentations of CLV, refer to [Hardie and Fader's paper](http://www.brucehardie.com/notes/033/what_is_wrong_with_this_CLV_formula.pdf) and [their other paper](http://brucehardie.com/notes/024/reconciling_clv_formulas.pdf) for a deeper dive into their definitions of CLV and its components. For more intuition behind the mathematical componented included in the models, refer to [Hardie and Fader's paper](http://www.brucehardie.com/papers/020/fader_et_al_mksc_10.pdf).

# Modeling CLV

Generating accurate revenue projections plays an important role at any business, and CLV should be included in these estimates, especially since every dollar of revenue that a company generates must come from its customers. Typically, financial professionals forecast business revenues and expenses using time-series models. This may be a sensible modeling methodology when customer data is unavailable to the firm. However, forecasting accuracy can be improved by decomposing customer-driven financial line items into their constituent components, estimating models and forecasting these parts into the future, then aggregating these components back together again to form projections of future customer-driven financial line items. Typically, using these forward-looking, customer-based estimates is better than using estimates based solely on historical sales. In the end, revenue forecasts should include these components whenever customer data is available.

In most cases, RFM features (recency, frequency, spend, and tenure) are sufficient in predicting CLV estimates stochastically for customers. From personal experience, a model with these RFM features will achieve a nearly identical accuracy compared to that same model including additional demographic, engagement, and other sets of features. Here, CLV is calculated using DCF as a combination of three estimates: estimated average spend of a customer, estimated probability of being alive for a customer, and estimated number of orders over a customer's lifetime. The average spend and churn probability of a customer is estimated using a BG/NBD model, and the order frequency of a customer is estimated using a Gamma-Gamma submodel.

Either the BG/NBD model or the Pareto/NBD model can be used to estimate the order frequency or churn probability of a customer, and both models employ the same constraints and only require 3 features: recency, frequency, and tenure features. The primary difference between these two models is that the BG/NBD model maps the survivorship curve to a beta-geometric distribution instead of a Pareto distribution. Specifically, the time to *dropout* (or churn) is modeled using the Pareto (or beta-geometric) timing model. For both models, repeat-purchasing behavior while active is modeled using the NBD (or negative binomial) counting model.

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

To help illustrate these parameters, let's imagine every customer (who are repeat purchases) has two coins. In particular, each customer flips a coin every day to see if they purchase or not (i.e. a purchase coin). After this first coin is flipped, each customer will flip their second coin. This second coin will decide whether going forward they die or not (i.e. a drop-out coin). Once a customer flips heads on the die coin, then they will stop flipping both coins and exit the experiment.

To tie in the model parameters with our analogy, the number of times our first coin (i.e. purchase coin) landed on heads (or the customer purchased) in a given period (e.g. month, year, etc.) is our transaction rate λ, which determines the shape of their own Poisson distribution. The heterogeneity in transaction rates across different customers follows a Gamma distribution. Each customer's second coin has a different probability α of landing on heads, or the customer dropping out and never buying again. Each customer's chance of dropping out is represented by their own α parameter, which determines the shape of their own Geometric distribution. The heterogeneity in drop-out probabilities across different customers follows a Beta distribution.

The CLV of customers can be estimated using ML models, such as boosting methods, random forests, LSTMs, etc. However, the probabilistic models usually produce similar out-of-sample accuracies and do as good of a job at estimating our variables of interest, while requiring fewer features and customer data. As an additional point, keep in mind most ML models require labels. If we're truly interested in predicting CLVs in a non-contractual company, then it's impossible to ever retrieve actual CLVs for each customer, since we don't know when they actually churn.

Again, for a deeper dive into modeling customer behavior for both transactional and non-transactional businesses, refer to [McCarthy's dissertation](https://repository.upenn.edu/cgi/viewcontent.cgi?article=4247&context=edissertations). For high-level intuitions behind each parameter, refer to [this Medium article](https://towardsdatascience.com/predicting-customer-lifetime-value-with-buy-til-you-die-probabilistic-models-in-python-f5cac78758d9). For sample implementations of BTYD models using the BTYD R package, refer to [this notebook and code sample](https://srepho.github.io/CLV/CLV). For comprehensive descriptions of the parameters used in modeling CLV, refer to [Bruce Hardie's slides](http://www.brucehardie.com/talks/ho_cba_tut_art_09.pdf).

