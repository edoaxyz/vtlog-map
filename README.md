# VTLog Map
This repository contains all the necessary files for running an interactive ETS2/ATS map, similar to the one hosted in [map.vtlog.net](https://map.vtlog.net).
This is an old version of the original map that I keep functional because it's easier for new people in the world of ETS2/ATS development and JavaScript.
The missing features from the live one are:
 - The animations by the players in their movements
 - The orientation of players so all players are showed as dots
 - The event system (specific of VTLOG)
 - The more-VTC system (specific of VTLOG)

### Handled GET parameters
These one below can be used in every map, even in map.vtlog.net.
```
follow:
    value: steam_id
    use: focus immediately on a user with the indicated steam_id, if online
    example: ets2.html?follow=76561198212562517
mode:
    value: 
        frame -> draw controls are hidden
        minimal -> hides everything
    example: ets2.html?mode=frame
zoom:
    value: 0 <= integer <= 8
    use: set the initial zoom of map that goes from 0 to 8 where 0 is the minimum zoom
    example: ets2.html?zoom=4
draggable:
    value: 
        false -> prevent map dragging
    example: ets2.html?draggable=false
zoomable:
    value:
        false -> prevent map zooming
    example: ets2.html?zoomable=false
```
These one below can be used only in the actual map.vtlog.net website.
```
realtime:
    value:
        false -> prevent map to load livetracker data (so dots won't be showed)
    example: ets2.html?realtime=false
job:
    value: job_id
    use: this will load the events of the provided job and will show them with their location
    example: ets2.html?job=577276
vtc:
    value: vtc_id
    use: shows only people of a certain vtc
    example: ets2.html?vtc=11
```

**Want to have the map of your VTC in your website using VTLOG?**
You can put an iframe in your website linking to the map with these URLs:
 - `https://map.vtlog.net/ets2?vtc=<your_vtc_id_here>` for ETS2
 - `https://map.vtlog.net/ats?vtc=<your_vtc_id_here>` for ATS

You can find your vtc_id in the URL of the VTC's home page with the format `https://<your_vtc_id_here>.vtlog.net`. If you have any problem in retrieving your vtc_id you can contact us on our Discord server.

Obviously you can append many parameters using the standards of the Query Strings. Example: `ets2.html?vtc=11&mode=frame`

### Player data format
This represent how JS expect to receive a request following the format of VTLog's tracker.
```
{
    "response": {
        "clients": [{
            "steamid": 99999999999999999,
            "data": {
                "job": {
                    "destination_city": "Le Mans",
                    "source_city": "Cassino"
                },
                "trailer": {
                    "wear": {
                        "chassis": 0.0209917742758989
                    }
                },
                "truck": {
                    "brand": "DAF",
                    "fuel": 325.123107910156,
                    "name": "XF",
                    "position": {
                        "x": -34914.2133712769,
                        "z": 8721.51288986206
                    },
                    "speed": 87.0046539306641,
                    "wear": {
                        "cabin": 0.0135743953287601,
                        "chassis": 0.0169679969549179,
                        "engine": 0.011621574871242,
                        "transmission": 0.00822832621634007,
                        "wheels": 0.0234782714396715
                    }
                },
                "username": "edo.g"
            }
        }]
    }
}
```

