# Helios.AI

Helios.AI is an MVP for 6-hour solar flare risk prediction using Aditya-L1 payload data.  
The current MVP uses HEL1OS as the primary X-ray source and SUIT as the supporting payload, with an XGBoost baseline model and a dashboard-style output.  

## MVP Flow

Aditya-L1 data → Preprocessing → Feature Engineering → XGBoost → 6-hour Risk Prediction → Dashboard

## Pipeline Overview

1. **Aditya-L1 Data**
   - Source: PRADAN / ISSDC
   - MVP payloads:
     - HEL1OS (primary)
     - SUIT (supporting)

2. **Preprocessing**
   - Load raw payload data
   - Clean missing or invalid values
   - Align timestamps across payloads
   - Build a unified time-series dataset

3. **Feature Engineering**
   - Rolling statistics
   - Lag features
   - Trend and change-rate features
   - Basic domain-specific indicators from HEL1OS and SUIT

4. **Model**
   - Baseline model: XGBoost
   - Target: 6-hour solar flare risk prediction

5. **Prediction Output**
   - Risk level: Low / Medium / High
   - Probability score
   - Top contributing factors
   - Timestamp of latest prediction

6. **Dashboard**
   - Current 6-hour flare risk
   - Probability score
   - Key contributing factors
   - HEL1OS and SUIT activity snapshot

## Fixed Prediction Output Format

```json
{
  "risk": "HIGH",
  "probability": 0.78,
  "window": "6H",
  "top_factors": [
    "X-ray Flux (HEL1OS)",
    "UV Brightness (SUIT)"
  ],
  "updated_at": "YYYY-MM-DD HH:MM:SS"
}
```

## MVP Success Condition

The MVP is successful when the system runs end-to-end from Aditya-L1 input data to a visible dashboard prediction output.
