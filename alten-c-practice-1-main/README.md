# alten-c-practice-1
Github repository:
https://github.com/jquk/alten-c-practice-1

This document describes the main high level requirements.

# Main idea
- A csv file shall contain a set of GPS coordinates.
- An input manager, to open and read a csv file.
- A module to consume the csv data, process the data, add some fields.
- A module to generate another csv file with output data.

# State machines:
All modules shall have the main typical states that include: powerOnSequence, initialization, idle, normalOperationalMode, failSafe, powerOffSequence.

# The main processing shall consist on:
## inputManager, for [ Sandrina ]:
- Extracting the latitude and longitude coordinates from the string.
String example: $GPGGA,181908.00,3404.7041778,N,07044.3966270,W,4,13,1.00,495.144,M,29.200,M,0.10,0000*40

See this GPS references:
- https://www.gpsworld.com/what-exactly-is-gps-nmea-data/
- https://web.fe.up.pt/~ee95080/NMEA%20data.pdf

## directionCalculationManger, for [ Francisco ]:
- Calculate direction, for each coordinate, based on the previous coordinate.

## directionPredictionManager, for [ Aravind ]:
- Predict the next coordinate, based only on the calculated direction and current position.
## outputManager, for [ Jose ]:
- Compare the estimation of the next coordinate with the actual data for the next point.
- The output of the processing shall be the list of original coordinates side by side with the estimations and error.

# Code structure:
- Each module (manager) will be in a separate folder.
- Each module shall have the prototype declarations in the header file (<module>Manager.h).
- **Module configuration management:** We will try to think on some configurable parameters that will be configured in the <module>Manager_cfg.h / .c, and they will have to be loaded into the main module in the pointers of the initialization function.
