# VTLog Map
This repository contains all the necessary files for running an interactive ETS2/ATS map, the same one hosted in [map.vtlog.net](https://map.vtlog.net).
The only difference are that it has for the actual one is that all the specific functions and parts of code for handling VTCs stuff has been removed.

ETS2 Map + Promods not included because of it's deprecation.

### Handled GET parameters
- `follow` (type Number) the id of the player that needed to be followed by the view
- `export` (type String) used for importing external drawings
- `mode` (type String) specify if some parts of the UI needs to be hidden
	Available values:
	- `frame` hides drawing components
	- `minimal` leaves only the option for managing layers
- `mode` (type 0 ≤ Number ≤ 8) set zoom level to the one specified
- `draggable` (type String) map not draggable if fixed to `false`
- `zoomable`(type String) map not zoomable if fixed to `false`

### Player data format
This represent how JS expect to receive a request following the format of VTLog's tracker.
```
{
	"response": [{
		"userID": 61, 								// ID
		"username": "edo.g",						// Username
		"telemetry": {
			"trackerdata": {
				"location_x": "-20363.039276",		// X position
				"location_z": "23105.090950",		// Z position
				"speed": "74.282417",				// Speed
				"fuel": "940.156738",				// Fuel
				"truckdamage": "0.072582",			// Truck damage
				"trailerdamage": "0.035040",		// Trailer damage
				"trailer_attached": "1",			// Trailer attached or not
				"source_city": "Nürnberg",			// Trailer's source city
				"destination_city": "Montpellier",	// Trailer's destination city
				"truck_brand": "Scania",			// Truck brand
				"truck_name": "S"					// Truck name (model)
			}
		}
	}]
}
```
