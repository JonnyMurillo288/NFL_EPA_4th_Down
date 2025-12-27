# NFL EPA 4th Down (2025 data)

## This analysis looks at the Expected Points of a team's 4th down attempt compared to their Actual Points scored. Attempting to find flaws in the Expected Points models
The image below shows that some teams are scoring above and some teams below EP for their 4th down attempts. However the good offenses seem to be scoring well above, while bad offenses are well below.

![image](https://github.com/JonnyMurillo288/NFL_EPA_4th_Down/blob/main/ep_vs_actual_pa_4th_down.png)

One of the key takeaways from the regression diagnostics is that the model contains a meaningful amount of **extreme behavior in the tails**. A small number of drives produce very large scoring swings, and these high-impact outcomes exert a disproportionate influence on the fit.

We checked this in multiple ways:

- **Robust regression** (which down-weights extreme points)
- **Quantile regression** (which focuses on median outcomes rather than the mean)

Across all approaches, we still find a **positive relationship between offensive strength and PA − EP** — teams with better offenses are more likely to score more than expected after 4th-down decisions.

However:

- the effect is **modest rather than dominant**
- the model’s **R² remains relatively low**
- much of the variation appears to come from
  **rare but high-leverage scoring sequences**

So the conclusion is necessarily cautious:

> There does seem to be a real effect, but 4th-down outcomes are highly volatile events, and a large portion of the story lies outside what this simple team-level model can explain.

---

### Where to Go Next

To better understand the unexplained variance, the next phase of the analysis will:

- shift from team-level aggregation to **individual drive outcomes**
- use **mixed-effects modeling** to incorporate:
  - team offensive strength, and
  - opponent defensive strength

We will also explore:

- **field position and context of the 4th-down attempt**

While EP already encodes conversion probability and expected scoring value, reconstructing those dynamics using interaction terms (e.g., distance, location, opponent quality) may reveal structure that the baseline EP model flattens out — and potentially lead to a richer, more interpretable model of 4th-down outcomes.
