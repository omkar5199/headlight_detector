
# Headlight Detector

Can we detect vehicles parked / idling along the highway at night?  

This is a hardware and software project to test if this is possible via headlight emissions.

![](icon.png)

## Why?

For safety...  

Coincidentally, this might also detect speed traps (vehicles idling on a freeway).

## How does it work?
An car idling at low RPM is likely parked.  As the engine runs, it causes the battery voltage to fluctuate (both generating the spark for cylinders, and also due to the alternator not having perfect filters). Headlights are high-wattage transmitters.  Minor fluctuations in battery voltage should be detectable in the light output.  

## Does it work?
Piecewise, it seems to.  But it's a work in progress.  

## Sub-projects:
###Solar panel light detector
* A solar panel is used to maximize light collection.  
* Optionally, a second panel allows differential light collection, to reduce ambient signals.
* The solar panel is mounted on a metal enclosure (altoids tin) to block RF noise.
* The signal is transmitted as a differential pair, via a stereo headphone jack

Status: Working.  Tested at close range.  Circuit may need to change for long distance.

![Solar Panel Module](/doc/solar_panel.jpg)

###GnuRadio (software-defined radio) to detect the RPM signature(s)
* I was hoping for high frequency artifacts, but the most prominent signal is approximately 20 to 100 hz, corresponding to engine RPM.
* Signal is FM modulated. 
* Initial version detects RPM, but needs calibration and testing.
![](./doc/RPM_detector.grc.png)

Status: Signs of working, needs calibration and testing.  Was able to detect RPM variations and output a signal that should be proportional to RPM.  Didn't work as well in an urban environment (busy parking ramp).


###Optical 4F correlator for enhanced detection of headlights.
* This is a fancy add-on for better detection.
* All-optical image filter, performing fourier transforms with matched a filter.
* Octave / matlab scripts to test the math with images of cars
* Schematic of the actual optical system.  (Not built yet)
![Headlight_Detector_4F_Correlator](./doc/Headlight_Detector_4F_Correlator.png)

Status: Theoretical, simulated.  Implementation is conceptually simple, but likely difficult to get working properly.  

### Examples of headlight spectrum 
![Spectrum when turning lights off momentarily](doc/spectrum_lights_on_and_off.png)
![Overall spectrum](doc/spectrum_44khz.png)
![Overall spectrum](doc/spectrum_engine_rev_slight.png)
![Overall spectrum](doc/spectrum_engine_revs.png)



### Infrequently Asked Questions

#### Does it work with incandescent / halogen headlights?
Yes.  Traditional light bulbs warm and cool slowly (fractions of a second), but still transmit a surprising amount of RF noise, at least several khz.  

#### What about LEDs?
These might work even better than halogens, depending on how well they filter the power supply.  Car manufacturers reduce costs wherever possible.  

#### Xenon? Other types?
Maybe.  Requires testing.

#### Tail lights, turn signals, interior lights?
These should work the similar to headlights, but lower intensity.

#### Blue and Red strobe lights?
An interesting question.  Perhaps RPM can be extracted.  

#### What about just detecting colored strobe lights reflecting off clouds and haze?  Over the horizon?  
That would be another project...

#### Could this work from a satellite?
It's probably easier than most things done from space.

## Sub projects
### Optical 4F correlator:
![headlights_target](headlights_bothsizes.png)
![resulting filter](doc/filter_2000x2000.png)








