# clv

In most cases, customer lifetime value (or CLV) represents how much a customer is worth (maybe in USD) over their entire lifetime with the company. Some companies will assign a single, average value to represent the CLV of all of their customers. By doing this, those companies are assuming every customer behaves and is worth the same.

Typically, companies will make sure their cost of acquiring a customer (or CAC) is less than that customer's lifetime value. For example, a company could say *"I know the CLV of each customer for my business is $100, so that's the most I can spend to acquire them."* However, the obvious reasons for why this statement is wrong include the following:
- Since customers behave differently, not all customers should have the same CLV
- Since CLV is a forward-looking estimate, we should include confidence intervals for our CLV estimates
- Since current sales have already happened, we should be interested in the future spend of a customer
- Since CLV is an estimate, we should be estimating the future cost of acquiring a customer too

Regarding the first principle, an average CLV shouldn't be generalized across all customers. There is plenty of [evidence of customer heterogeneity](http://brucehardie.com/papers/022/fader_hardie_mksc_10.pdf), meaning we shouldn't assume customers are all the same. In other words, we shouldn't assume each customer's CLV is equal to the same average. Instead, we should assume they all have different values.

![CLV Illustration 2](https://raw.githubusercontent.com/dkharazi/customer-centricity/main/clv2.svg)

Why it's important to rely on CLV instead of historical sales:

![CLV Illustration 2](https://raw.githubusercontent.com/dkharazi/customer-centricity/main/clv2.svg)

Refer to [these slides from Roberto Medri](http://cdn.oreillystatic.com/en/assets/1/event/85/Case%20Study_%20What_s%20a%20Customer%20Worth_%20Presentation.pdf) for a deeper, high-level explanation about customer lifetime value. For a lower-level understanding of CLV models and how they're built, refer to [this talk at Wharton by Peter Fader](https://www.youtube.com/watch?v=guj2gVEEx4s&ab_channel=FirstMarkCapital). Or, refer to [this talk at Google by Peter Fader](https://www.youtube.com/watch?v=0iLQCNYdNb4&ab_channel=TalksatGoogle) for illustrations of how we can target and apply separate customer targeting tactics on different CLV segments of customers.

# Applications of CLV

There are many use-cases for CLV to be used across any type of business. The following are only a few use-cases that can provide immediate impact to a company:
- More effective reporting
- More meaningful segmentation
- More accurate testing
- More effective customer targeting for premium offerings and loyalty programs

# Modeling CLV

- Most of CLV modeling can be achieved stochastically using RFM features
  - CLV consists of two estimates using two different models
  - BG/NBD for order frequency estimates
  - Gamma-Gamma for average spend estimates
- ML algorithms, like boosting and RF, can do just as good of a job, but may offer less functionality
- Accuracy chart illustations

# Segmenting with CLV
- Most customer segments should be segmented based on RFM features, churn estimates, or clv estimates
- Then, profiled later (e.g. channel profiles) to determine different channels with different purchasing behavior
- Shouldn't really ever be done the other way around

# CLV with RFM Analysis
- [Wharton Talk about Computing CLV with RFM Features](https://www.youtube.com/watch?v=guj2gVEEx4s&ab_channel=FirstMarkCapital)

# CLV and Segmentation
- [Google Talk about Segmenting CLV](https://www.youtube.com/watch?v=0iLQCNYdNb4&ab_channel=TalksatGoogle)
- Cross-sell vs up-sell
- Minute 25:50 for Tactical Approach vs. Targeted Customers
