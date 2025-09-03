# ESteps Calibration

When installing or setting up a new extruder one of the steps we need to do is calibrate the number of ESteps
This setting determines how far the filament will travel through the extruder given the number of steps provided by the stepper motor.

This is something we normally only do once so that when we ask for 10mm of filament to travel through the extruder 10mm is passed through.
In cases where filament needs additional or less flow, this is best done via the seperate filament settings instead within the slicer.

## Measuring off

Normally I mark the filament with some tape using a ruler.
Approx 200mm up from the entry of the extruder (the longer the better although 200mm is more than enough)

![ESteps1.jpg](images/ESteps1.jpg)

## Checking the measurement

Then it's a case of

  * Heating up the extruder
  * Extruding 25mm at a time
  * Checking with the ruler after each extrusion to see if it's actually moved 25mm

Any inaccuracies over a long distance will add up over 200mm's worth
