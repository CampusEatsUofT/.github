## Firestore Schema - Grab And Go Schedule collection

### Grab And Go Schedule

Grab And Go Schedule Documents (path: `grabAndGoSchedules/{locationId}`, represented by
`GrabAndGoScheduleModel`), stores pre-defined schedule. This document is public.
This document contains no sub-collection.

```
grabAndGoSchedule
    $date (document)
        day (string)
        date (string)
        h11 (map)
            restaurants (List<string>)
            isValid (bool) 
        h12 (map)
        h13 (map)
        h17 (map)
        h18 (map) 
        
    date: in MM.DD format
    restaurants: List of restaurantId
    isValid: whether user can order (before deadline)
```