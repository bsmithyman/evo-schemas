import OverlineWithVersion from '@theme/OverlineWithVersion';
import SchemaUri from '@theme/SchemaUri';
import FlatProperties from './_generated/flatmd/objects/experimental-variogram-1.0.0.md';

<OverlineWithVersion title="Geoscience Objects" version="1.0.0" badge="techPreview" />

# variogram

<SchemaUri uri="schema/objects/experimental-variogram/1.0.0/experimental-variogram.schema.json" />

The experimental-variogram object is used to capture spatial variability of univariate data acorss an area of interest. Spatial variability is described by direction and summarized per each lag in a direction. 

The experimental variogram is calculated a part of a standard variography workflow and is precursor to variogram modeling. An experimental variogram is a key input to fitting a variogram model.

## Required Data

To construct an experimental variogram object the following information is required.

* `data_variance` (number): The variance of the source data

* `generator` (string): Identifier for the calculation engine/software

* `lags` (object): Table describing individual lags

    * `data`(binary blob): Table with columns: direction_id, lag_number, lag_distance, lag_tolerance, start, end, value, num_pairs.
    * `length` (integer): Total number of lag bins
    * `width` (const): Must be 4
    * `data_type` (const): Must be "float64/float64/float64/uint64"
    * `directions` (object): Contains:

* `directions` (object): Table describing geometry and type ("directional", "omnidirectional" or "downhole") of each direction for which lags exist.
    * `data` (binary blob): Table with columns: direction_id, direction_type, nlags, azimuth, dip, azimuth_tolerance, dip_tolerance, bandwidth, bandheight.
    * `length` (integer): Number of directions
    * `width` (const): Must be 10
    * `data_type` (const): Must be "float64/float64/uint64/uint64/float64/float64/float64/*float64/float64/float64"

## Optional fields include:

* `description` (string)
* `domain` (string): The domain the variogram is calculated for
* `attribute` (string): The attribute the variogram is calculated for
* `variogram_type` (string, default: "variogram"): Type of calculation performed Both lags and directions can also have optional additional attributes through the  attribute-list-property component.

The schema enforces unevaluatedProperties: false, meaning no additional properties beyond those defined are allowed.
## Properties

<FlatProperties />

::mermaid[_generated/uml/experimental-variogram-1.0.0.mmd]
