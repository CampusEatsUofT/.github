## Firestore Schema - Drivers collection

### Drivers

Drivers Documents (path: `drivers/{driverId}`, represented by `DriverModel`), stores basic account
information of this driver. This document is public. This document contains sub-collection
including `notifications`, and `orders`.

```
drivers (collection)
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

### Driver's Orders (OrderStates Documents, not Order Documents)

Driver Order States Documents (path: `drivers/{driverId}/orders/{orderId}`, represented by
`DroverOrderStateModel`), stores all order status information of this driver. This document is
private. This document contains no sub-collection.

```
orders (collection)
    $orderId (document)
        orderId (string)
        orderStatus (string)
        driverStatus (string?)
        transferStatus (string)
        expectedEarning (number)
        
    transferStatus: invalid, pending, done     
    orderStatus: one of the OrderStatus
    driverStatus: null if this isn't delivery order. one of the DriverStatus
```

### Driver's Notification

Drivers Notification Documents (path: `driver/{driverId}/notifications/{notificationId}`,
represented by `NotificationModel`), stores all notifications of this driver. This document is
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

