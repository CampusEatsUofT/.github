## Firestore Schema - Grab And Go Order Reference collection

### Grab and Go Order Reference

Grab And Go Order Reference Documents (path: `grabAndGoOrderReferences/{reference}`), stores 
common shared information of this grab and go order. This document is public. This document 
contains no sub-collection.

```
grabAndGoOrderReference
    $referenceId
        referenceId (string)
        restaurantId (string)
        pickupLocationId (string)
        receiveTime (timestamp)
        driverId (string)
        driverStatus (string)
        driverStatusToTime (map)
            invalid (timestamp?)
            submitted (timestamp?)
            accepted (timestamp?)
            ready (timestamp?)
            picked (timestamp?)
            completed (timestamp?)
        driverPickupCode (string)
        orders (List<string>)
```