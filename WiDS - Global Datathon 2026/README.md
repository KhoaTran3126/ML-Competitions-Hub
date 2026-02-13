# WiDS Global Datathon 2026 Competition
## About the Competition
When a wildfire ignites, emergency managers face an impossible question with incomplete information. Which fires will reach populated areas? How quickly? And which communities should prepare first?

This year's WiDS Global Datathon challenges participants to build survival models that answer these questions using only the earliest signals available. Your task is to predict the probability that a wildfire will threaten an evacuation zone within 12, 24, 48, and 72 hours, drawing on data from just the first five hours after ignition.

The goal is not a single prediction but a calibrated forecast across multiple time horizons. Emergency responders need both urgency rankings (which fires demand immediate attention) and probability estimates they can trust when making high-stakes decisions about evacuations, resource deployment, and public alerts.

This competition turns that operational need into a survival analysis challenge. You will generate calibrated probability forecasts across multiple time horizons to support real-world decisions.

#### This is right-censored survival analysis:

1. If a fire hits within the 72-hour window, event = 1 and time_to_hit_hours is the observed time from t0+5h.
2. If a fire does not hit within 72 hours, event = 0 and time_to_hit_hours is the last observed time in the window (<= 72).
3. Participants do not predict a single time. They submit survival probabilities that a hit occurs by 12h, 24h, 48h, and 72h. The strongest solutions will deliver two outcomes at once. They will rank fires correctly by urgency for triage and produce calibrated probabilities that can support threshold-based decisions.
## About the Dataset

## About the Metric
The competition's metric is **0.3\*C_index + 0.7\*(1 - Weighted Brier Score)**

1. **C_index**

    Measures how well fires are ranked by urgency (from 0.5 to 1.0, higher is better)

2. **Weighted Brier Score**
   
    Measures calibration at 24h, 48h, 72h
   
    Uses censor-aware evaluation:

        Hits: 1 if hit by horizon H, else 0
        Censored after H: 0
        Censored before H: excluded

   Final Weighted Average: **0.3\*Brier@24h + 0.4\*Brier@48h + 0.3*Brier@72h**

## Submission Details
1. Strict schema: event_id, prob_12h, prob_24h, prob_48h, prob_72h
2. IDs must match the test set exactly; no missing/extra/duplicate IDs
3. Probabilities must be in [0, 1]
4. Monotonicity enforced row-wise **(prob_12h <= prob_24h <= prob_48h <= prob_72h)**
