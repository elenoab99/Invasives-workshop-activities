# Revised DEP Invasive Tree Species Workshop — Activities 4–10

These notebooks are adapted directly from the structure of the uploaded
`Fiji_cordia_2.0_prediction_Vanuatu.ipynb` workflow and simplified for beginner participants.

## Sequence

04. Sentinel-2 STAC Search  
05. Pre-process Sentinel-2 and calculate NDVI  
06. Field Data to Training Array  
07. Train Random Forest  
08. Predict Invasive Classes  
09. Class Coverage Statistics  
10. Field Validation and Accuracy  

## Core workflow

AOI
→ Sentinel-2 STAC search
→ cloud masking
→ reflectance scaling
→ NDVI
→ median composite
→ field training points
→ spectral extraction
→ Random Forest
→ whole-image prediction
→ class coverage
→ independent field validation

## Instructor preparation

Create these folders beside the notebooks:

- AOI/
- Training_Data/
- Validation_Data/
- Results/

Expected files include:

- AOI/EfateAOI.geojson
- Training_Data/Merged_CleanV3.geojson
- Validation_Data/validation_points.geojson

The training and validation layers should contain the numeric class field used by the model
(e.g. `randomforest`).

Before Activity 9, confirm the true class-ID legend for values 1–9. Do not guess class names.

## Important differences from the original working notebook

1. STAC bbox is explicitly generated from an EPSG:4326 AOI.
2. Prediction is limited to pixels with finite predictor values so cloud/NoData pixels do not
   cause `RandomForestClassifier.predict()` failures.
3. Predictor order is explicitly preserved between training and whole-image prediction.
4. A held-out training/test split is included for teaching.
5. The final accuracy activity is designed for truly independent field validation points.
6. The random-array NDWI/NDBI/NDBaI demonstration in the original notebook is not included
   in the core beginner workflow because it is not connected to the actual Sentinel-2 composite.
   It can be added later as an advanced masking activity.
