## Firestore Schema - Driver Locations collection

### Drivers Locations

Driver Locations Documents (path: `driverLocations/{driverId}`, represented by 
`DriverLocationModel`), stores location information of this driver. This document is public. 
This document contains no sub-collection.

```
driverLocations (collection)
    $driverId (document)
        driverId
        updatedAt (timestamp)
        location (map)     
            shortName (null)
            streetAddress (null)
            latitude (number)
            longitude (number)
            
    location: locationModel
    shortName: always null
    streetAddress: always null
```




