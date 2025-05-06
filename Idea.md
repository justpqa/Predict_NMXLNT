Tried idea:
- Trial 1:
    + No outlier/zeros filter 
    + No Ho Tay/Vinh Niem (due to problematic data collection)
    + Used past COD, Temperature, TSS, PH, NH4
    + Used 4-8 hours
    + Model used: XGBoost
    => Baseline: 3.2, best model ~ 2.95 - 3.0
- Trial 2: 
    + Same as trial 1 but not use NH4 due to weird distribution in Yen So
    + Model used: XGBoost, LightGBM
    + Try both full model and reduced model (only past COD for XGBoost and 4 hours before features for LightGBM)
    => Baseline: 3.2, best model ~ 2.95 - 3.0
- Trial 3: 
    + Including time related features (hour, day, day of week, month)
    + Including CatBoost
    + Including lags from 4-12 hours
    => Baseline 3.2, best model ~ 2.9
- Trial 4:
    + Adding model of CatBoost with reduced feature sets
    + Filter for very high value of COD (based on rolling z-score) & zeros
    + Also tried to increase trees & add early stopping (not work well)
    => Baseline: 3.1, best model ~ 2.77
- Trial 5:
    + Use sine of time-related features
    + Use lags from 4-8 hours, with 30 min timestep
    + Removing filter of high values, still filters for COD = 0