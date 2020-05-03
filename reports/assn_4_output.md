# Predicting Pit Stop Times

_Note: This model isn't supposed to make sense, it was built to try out MLflow
for assignment 3. I wouldn't actually pick these features to predict pit stop times, or even actually predict pit stop times. Nevertheless, I try
here to make meaning of the model's results in a way that would make sense._

## Objective
We built a random forest model to predict the pit stop timings:
* Circuit
* Drivers
* Lap Number
* Stop Number

Our objective here is to discuss:
* The trends in pit stop times with regards to these features
* How well the model captures these trends in its predictions, with an eye
towards improving the model.

We do so with the aid of visualisations built using tableau, accessible from
[`src/visualisations`](`src/visualisations`) in this repo.

Only test set data is included in this dataset as this is where we have
predictions for data that the model was not trained on.

## Tracks
Sheet one shows the average predicted and actual pit stop times on different tracks.

* Pit stop times are around 20k ms for most tracks. Notable exceptions are
  - Azerbaijan Grand Prix
  - Brazilian Grand Prix
  - Australian Grand Prix
  - Japanese Grand Prix
* The model appears to predict pit times well, with the exception of
underpredicting the times for the Azerbaijan Grand Prix by a large
amount.
  - This may be due to the fact that the Azerbaijan Grand Prix is new - it only
  became an F1 race in 2017, the last year for which data is available - so
  there may not be enough data for the model to capture the particularities of
  pit times on this track.

## Drivers
Sheet two shows the average predicted and actual pit stop times for
different drivers.
* Pit stop times are slightly above 20k for most drivers, with significant
exceptions with much higher pit stop times - e.g.
 - Max Verstappen
 - Esteban Ocon
 - Felipe Massa
 - Romain Grosjean
* The model appears to predict pit stop times well, including for the
exceptions with longer lap times, although it tends to under-predict the pit
stop times of these exceptions.
 - This may be doe to drivers changing constructors, or the period where
refuelling during pit stops was allowed (increasing pit times). Including
constructor changes and refuelling as features may improve the model
predictions.

## Lap Number
Sheet 3 shows the average predicted and actual pit times for different
lap numbers.
* Pit stop times are around 20k for most laps, with notable exceptions at
laps 2, 9, 20, and 28.
* The model captures the data well, with exception of some under-predicting of
times when drivers pit at lap 20
  - Lap 20 may be a popular lap for refuelling during the years where it was
  permitted, which may have driven up times for those laps. Including this
  feature as was suggested with regards to drivers may help prediction.

## Pit Stop Number
Sheet 4 shows the average predicted and actual pit stop lap times for different
pit stop numbers.
* Pit times are higher for the second and third stops, and lower for the 4th
and subsequent stop
* The model does a good job at predicting actual pit times for the 1st, 5th, and 6th pit stops, but
  - Under-predicts times when drivers make stops 2 and 3
  - Over-predicts times for the 4th stop
* The under-prediction for stops 2 and 3 may be because of refuelling (see   
above), but it is not immediately clear to me why stop 4 is over-predicted by
such a dramatic amount.
