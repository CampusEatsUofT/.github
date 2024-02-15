## Firestore Schema - Order Ratings collection

### Order Ratings

Order Ratings Documents (path: `orderRatings/{orderId}`, represented by `OrderRatingModel`), stores 
order ratings of this order. This document is public. This document contains no sub-collection.

```
orderRatings (collection)
    $orderId
        orderId (string)
        restaurantId (string)
        userId (string?)
        createdAt (timestamp)
        rating (number)
        userComment (string)
        reviewPhotos (List<string>)
        merchantResponse (string?)
        likeFoodId (List<string>)
```
