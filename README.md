# clv

In most cases, customer lifetime value (or CLV) represents how much a customer is worth (maybe in USD) over their entire lifetime with the company. Some companies will assign a single, average value to represent the CLV of all of their customers. By doing this, those companies are assuming every customer behaves and is worth the same.

Typically, companies will make sure their cost of acquiring a customer (or CAC) is less than that customer's lifetime value. For example, a company could say *"I know the CLV of each customer for my business is $100, so that's the most I can spend to acquire them."* However, the obvious reasons for why this statement is wrong include the following:
- Since customers behave differently, not all customers should have the same CLV
- Since CLV is a forward-looking estimate, we should include confidence intervals for our CLV estimates
- Since current sales have already happened, we should be interested in the future spend of a customer
- Since CLV is an estimate, we should be estimating the future cost of acquiring a customer too

Regarding the first principle, an average CLV shouldn't be generalized across all customers. There is plenty of [evidence of customer heterogeneity](http://brucehardie.com/papers/022/fader_hardie_mksc_10.pdf), meaning we shouldn't assume customers are all the same. In other words, we shouldn't assume each customer's CLV is equal to the same average. Instead, we should assume they all have different values.

For example, customer 1 and customer 2 have very different purchasing behaviors based on their order recency and frequency in the illustration below. Notice, customer 2 has a much higher likelihood of churning compared to customer 1. If we have the power of looking into the future at each customer's actual purchases, then we'll see customer 1 should have a higher estimated CLV compared to customer 2. This point should help illustrate how each customer should be treated differently with a different estimated CLV.

![CLV Illustration 1](https://raw.githubusercontent.com/dkharazi/customer-centricity/main/clv1.svg)

Regarding the third principle, estimating the value of our customers solely based on historical sales shouldn't be our main focus. Instead, it's more interesting to focus on CLV, since it's a future-looking estimate of spend, instead of historical sales. To illustrate this point, notice how customer 1 and customer 2 have different order recencies in the illustration below. More specifically, customer 1 has more purchases compared to customer 2 historically, but customer 2 has purchased more frequently and recently compared to customer 1. Even though both of these customers may be considered high value customers, customer 2 has a higher CLV if we regained our power to look into the future at each customer's actual purchases.

![CLV Illustration 2](https://raw.githubusercontent.com/dkharazi/customer-centricity/main/clv2.svg)

If our CLV estimates are accurate enough, we can use those CLV estimates to measure the value of our acquired customers across their lifetimes, rather than the hisorical spend of our customers. This is an important concept for determining whether our acquired customers should be considered high-value or low-value customers. For example, [Peter Fader](https://www.youtube.com/watch?v=0iLQCNYdNb4&ab_channel=TalksatGoogle) and [Daniel McCarthy](https://twitter.com/d_mccar/status/1376564874713702408) have both mentioned Wayfair's acquisitions are growing too fast without retaining repeat buyers or high-value customers. In other words, they're acquiring a lot of low-value customers, and they haven't established enough of a base of repeat buyers, who they can rely on when their acquisitions level off.

Since the start of the COVID-19 pandemic, competitors have removed their furniture supply from the market [by either closing their brick-and-mortar stores or declaring bankruptcy](https://www.cnbc.com/2020/04/06/wayfair-shares-surge-37percent-as-coronavirus-drives-sales-of-office-furniture.html), leading to even greater levels of acquired customers for Wayfair. However, this doesn't solve their problem with retaining high-value customers and only allows them to put off confronting this ongoing issue. Since 2019, Wayfair has [admitted to growing too fast in the past](https://www.bostonglobe.com/2020/02/28/business/wayfair-stock-takes-another-hit-amid-sales-slowdown/) and has carried out large-scale layoffs, while [raising increasing amounts of debt](https://chainstoreage.com/analysis-wayfair-has-failed-turn-over-new-leaf-net-loss-continues-rise) to fund their operating losses. For every growing company, acquisition must reach a peak and level off at some point. When that time comes, these companies must rely on its base of repeat buyers (or high-value customers) make decreases in acquisition seem unnoticeable.

![Wayfair Model Forecast](https://raw.githubusercontent.com/dkharazi/customer-centricity/main/clv2.svg)

For most successful companies, there's enough of an established base of ongoing, repeat buyers after acquisitions level off. As an example, Amazon acquired and developed enough of their buyers to be high-value and repeat buyers, so slight decreases in their customer acquisition didn't impact their revenue.

Refer to [these slides from Roberto Medri](http://cdn.oreillystatic.com/en/assets/1/event/85/Case%20Study_%20What_s%20a%20Customer%20Worth_%20Presentation.pdf) for a deeper, high-level explanation about customer lifetime value. For a lower-level understanding of CLV models and how they're built, refer to [this talk at Wharton by Peter Fader](https://www.youtube.com/watch?v=guj2gVEEx4s&ab_channel=FirstMarkCapital). Or, refer to [this talk at Google by Peter Fader](https://www.youtube.com/watch?v=0iLQCNYdNb4&ab_channel=TalksatGoogle) for illustrations of how we can target and apply separate customer targeting tactics on different CLV segments of customers.

# Applications of CLV

There are many use-cases for CLV to be used across any type of business. The following are only a few use-cases that can provide immediate impact to a company:
- More effective reporting
- More meaningful segmentation
- More accurate testing
- More effective customer targeting for premium offerings and loyalty programs

# Modeling CLV

- Most of CLV modeling can be achieved stochastically using RFM features
  - In most cases, recency most important, then frequency, then monetary
  - CLV consists of two estimates using two different models
  - BG/NBD for order frequency estimates
  - Gamma-Gamma for average spend estimates
- ML algorithms, like boosting and RF, can do just as good of a job, but may offer less functionality
- Accuracy chart illustations

# Segmenting with CLV

- Most customer segments should be segmented based on RFM features, churn estimates, or clv estimates
- Then, profiled later (e.g. channel profiles) to determine different channels with different purchasing behavior
- Shouldn't really ever be done the other way around
- [Google Talk about Segmenting CLV](https://www.youtube.com/watch?v=0iLQCNYdNb4&ab_channel=TalksatGoogle)
- Pic of cohorting by year customers were acquired
- Cross-sell vs up-sell
- Minute 25:50 for Tactical Approach vs. Targeted Customers
