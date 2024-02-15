## Firestore Schema - Sellers collection

### Sellers

Sellers Documents (path: `sellers/{sellerId}`, represented by `SellerModel`), stores basic account
information of this seller. This document is public. This document contains sub-collection
including `notifications`, and `orders`.

```
sellers (collection) [UserModel]
    $uid (document)
        uid (string)
        createdAt (timestamp)
        name (string)
        email (string)
        photoUrl (string?)
        phoneNumber (string?) 
        birthday (string?)
        gender (string?)
        fcmToken (string)
        
    fcmToken: Firebase Cloud Messaging Tokens of this user's device
```

### Sellers's Orders (OrderStates Documents, not Order Documents)

Seller Order States Documents (path: `sellers/{sellerId}/orders/{orderId}`, represented by
`OrderStateModel`), stores all order status information of this seller. This document is private.
This document contains no sub-collection.

```
orders (collection)
    $orderId (document)
        orderId (string)
        orderStatus (string)
        driverStatus (string?)
        
    orderStatus: one of the OrderStatus
    driverStatus: null if this isn't delivery order. one of the DriverStatus
```

### Seller's Notification

Sellers Notification Documents (path: `sellers/{sellerId}/notifications/{notificationId}`, 
represented by `NotificationModel`), stores all notifications of this seller. This document is 
private. This document contains no sub-collection.

```
notifications (collection)
    $notificationId (document)
        notificationId (string)
        type (string)
        title (string)
        message (string)
        createAt (timestamp)
        hasRead (bool)
        
    type: notification type: orderUnpaid, orderSubmitted, orderAccepted, driverAccepted, driverReady,
    orderReady, orderPickedUp, orderArrived, orderCompleted, orderRated, chat, custom.
```

