## Firestore Schema - Grab And Go Location collection

### Grab And Go Location

Grab And Go Location Documents (path: `grabAndGoLocations/{locationId}`, represented by 
`GrabAndGoLocationModel`), stores pre-defined grab and go location. This document is public. 
This document contains no sub-collection.

```
grabAndGoLocations
    $locationId (document)
        inUse (bool)
        locationId (String)
        location (map)    
            shortName (string)
            streetAddress (string)
            latitude (number)
            longitude (number)
    
    locationId: unique meaningful string to represent the string
```
