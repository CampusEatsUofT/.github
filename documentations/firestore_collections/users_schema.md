## Firestore Schema - Users collection

### Users

Users Documents (path: `users/{userId}`, represented by `UserModel`), stores basic account
information of this user. This document is public. This document contains sub-collection
including `shoppingCarts`, `addresses`, `vouchers`, `notifications` and `orders`.

```
users (collection) [UserModel]
    $uid (document)
        uid (string)
        createdAt (timestamp)
        name (string)
        email (string)
        photoUrl (string?)
        phoneNumber (string?) 
        birthday (string?)
        gender (string?)
        restaurantLikes (List<String>)
        fcmToken (string)
        
    restaurantLikes: List of restaurantId that this user likes
    fcmToken: Firebase Cloud Messaging Tokens of this user's device
```

### User's Shopping Carts and Cart Items

Shopping Carts Documents (path: `users/{userId}/shoppingCarts/{restaurantId}`, is a placeholder
documents for `cartItems` collection of `{restaurantId}`. This document is private.
This document contains one sub-collection `cartItems`.

```
shoppingCarts (collection)
    $restaurantId (document)
        restaurantId        
```

Cart Items Documents (path: `users/{userId}/shoppingCarts/{restaurantId}/cartItems/{cartItemId}`,
represented by `CartItemModel`), stores cart items of this user at `{restaurantId}`. This document
is private. This document has no sub-collection.

```
cartItems (collection)
    $cartItemId
        cartItemId (string)
        foodId (string)
        quantity (int)
        note (string)
        toppings (List<Map>)
            toppingSectionId (string)
            toppingId (List<string>)
            
    cartItemId: made up by foodId + random string
    toppings: represented by List<ToppingSectionInCartItemModel>
    toppingSectionId: the topping section that user has at least one selection
    toppingId: the value user selected under toppingSectionId
```

### User's Orders (OrderStates Documents, not Order Documents)

User Order States Documents (path: `users/{userId}/orders/{orderId}`, represented by
`OrderStateModel`), stores all order status information of this user. This document is private.
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

### User's Notification

User Notification Documents (path: `users/{userId}/notifications/{notificationId}`, represented by
`NotificationModel`), stores all notifications of this user. This document is private.
This document contains no sub-collection.

```
notifications (collection)
    notificationId (document)
        notificationId (string)
        type (string)
        title (string)
        message (string)
        createAt (timestamp)
        hasRead (bool)
        
    type: notification type: orderUnpaid, orderSubmitted, orderAccepted, driverAccepted, driverReady,
    orderReady, orderPickedUp, orderArrived, orderCompleted, orderRated, chat, custom.
```

### User's Addresses

User Addresses Documents (path: `users/{userId}/addresses/{addressId}`, represented
by `AddressModel`), stores delivery addresses information of this user. This document is public.
This document contains no sub-collection.

```
addresses (collection)
    $addressId (document)
        addressId (string)
        label (string)
        location (map)   
            shortName (string)
            streetAddress (string)
            latitude (number)
            longitude (number)
        buildingName (string)
        unitNumber (string)
        contactName (string)
        phoneNumber (string)
        
    location: represented by LocationModel
```

### User's Vouchers

User Vouchers Documents (path: `users/{userId}/vouchers/{voucerId}`, represented by abstract
`VoucherModel`), stores all vouchers of this user. This document is private. This document contains
no sub-collection.

#### Percentage Vouchers

```
vouchers (collection)
    $voucherId (document)
        voucherId (string)
        description (string)
        restaurantId (string?)
        restaurantPhotoUrl (string?)
        minPriceRequirement (double?)
        maxSale (double?)
        expiredAt (timestamp?)
        redeemed (bool)
        salePercentage (double)
        
    restaurantId: null if all restaurants can use
    minPriceRequirement: min price requirement to use this voucher, null if none
    maxSale: sales cap in dollars, null if none
    expiredAt: null if no expiration time
```

#### Regular Vouchers

```
vouchers (collection)
    $voucherId (document)
        voucherId (string)
        description (string)
        restaurantId (string?)
        restaurantPhotoUrl (string?)
        minPriceRequirement (double?)
        maxSale (double?)
        expiredAt (timestamp?)
        redeemed (bool)
        saleAmount (double)
        
    restaurantId: null if all restaurants can use
    minPriceRequirement: min price requirement to use this voucher, null if none
    maxSale: sales cap in dollars, null if none
    expiredAt: null if no expiration time
```
        