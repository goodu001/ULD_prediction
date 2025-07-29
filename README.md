# ULD_prediction
A mockup data set and do a Python prediction .

## Step 1 Complete: ULD_Details Parsed
parsed ULD_Details into individual columns:

| FlightID | Aircraft | Origin | Destination | P1P | RKN | AKE | AMJ | PMC |
| -------- | -------- | ------ | ----------- | --- | --- | --- | --- | --- |
| RG559    | B737     | DXB    | SIN         | 12  | 0   | 17  | 0   | 0   |
| RG891    | B787     | LAX    | SYD         | 0   | 9   | 0   | 0   | 0   |
| ...      | ...      | ...    | ...         | ... | ... | ... | ... | ... |


## Step 2: Forecasting Total_ULDs

Clean and convert Total_ULDs into numeric.

Select features: aircraft, origin, destination, ULD types.

Encode categorical variables.

Train a regression model (e.g., RandomForestRegressor).

Evaluate with metrics.
