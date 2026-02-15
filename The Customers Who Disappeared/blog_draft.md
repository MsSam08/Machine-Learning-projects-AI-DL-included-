# The Customers Who Disappeared

No one sent a goodbye email.

No angry complaint.

No dramatic exit.

They just… stopped showing up.

That’s the uncomfortable reality of customer churn in e-commerce. One day a customer is browsing, clicking, maybe even purchasing. A few weeks later, silence. By the time revenue dips, the damage is already done.

- I wanted to know: *Can we catch the warning signs before customers disappear?*

Using a small dataset of 50 customers, I explored behavioral signals such as visits in the last 30 days, time spent on the site, number of purchases, and support tickets. About 38% had churned. Not enough to ignore, but not obvious either.
At first glance, nothing screamed, **“This is why they left.”** Correlation analysis showed that no single variable strongly explained churn. That surprised me. I expected something dramatic, maybe customers who left barely visited or never purchased. But churn wasn’t loud. It was subtle.

That changed how I approached the modeling. Since patterns weren’t linear, I chose a Random Forest model to capture more complex relationships. I cleaned the data, encoded categorical features, scaled the variables, and, most importantly, removed the UserID column. That small decision mattered more than I expected. When I removed UserID, the ROC-AUC score jumped from 0.35 to 0.71. It was a reminder that irrelevant data can quietly sabotage performance.

Feature importance told a clearer story. Visits in the last 30 days accounted for 40% of predictive power. Time on site followed at 31%, and purchase count at 22%. Together, engagement metrics made up over 90% of the model’s influence. Support tickets barely mattered.

![Feature importance](https://github.com/MsSam08/Machine-Learning-projects-AI-DL-included-/blob/main/The%20Customers%20Who%20Disappeared/feture%20importance.png)


The real turning point came when I adjusted the classification threshold. At the standard 0.5 cutoff, the model caught only 25% of churners. That’s not helpful in the real world. When the threshold was lowered to 0.2 and recall reached 100%, every at-risk customer in the test set was identified. Yes, false positives increased. However, in a real e-commerce setting, this would allow the company to intervene immediately by offering targeted discounts, loyalty incentives, or personalized re-engagement emails before customers fully disengage.

If even half of those flagged customers were successfully retained, the financial impact could be significant. Retaining existing customers is far cheaper than acquiring new ones. Instead of spending heavily on ads to replace lost customers, the company could protect recurring revenue through strategic retention campaigns.
More importantly, this model shifts the company from reactive to proactive decision-making. Rather than analyzing churn after revenue declines, the business can act early, reduce lifetime value loss, and strengthen long-term customer relationships.

The dataset was small, so this isn’t production-ready. But the lesson was clear: churn doesn’t happen suddenly. It is usually a slow decline in engagement. If businesses monitor those signals early, they can intervene before revenue slips away.

Customers rarely announce their departure.
But their behavior does.
And now, we know how to listen.

