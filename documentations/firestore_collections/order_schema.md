## Firestore Schema - Orders collection

### Orders

Orders Documents (path: `orders/{orderId}`, represented by `OrderModel`), stores basic account
information of this order. This document is public. This document contains one sub-collection
`chats`.

#### Pickup Order

```
orders (collection)
    $orderId
        orderId (string)
        createdAt (timestamp)
        orderStatus (OrderStatus)
        orderStatusToTime (map) 
            unpaid (timestamp?)
            submitted (timestamp?)
            accepted (timestamp?)
            ready (timestamp?)
            picked (timestamp?)
            arrived (timestamp?)
            completed (timestamp?)
            rated (timestamp?)
            cancelled (timestamp?)
        orderType (string)
        userId (string)
        contactName (string)
        phoneNumber (string)
        restaurantLocation (map)   
            shortName (string)
            streetAddress (string)
            latitude (number)
            longitude (number)
        restaurantId (string)
        restaurantName (string)
        restaurantPhotoUrl (string)
        orderNote (string?)
        takeCutlery (bool)
        receiveTime (timestamp)
        foods (List<map>)
          foodId (string)
          foodName (string)
          quantity (number)
          singlePrice (number)
          foodNote (string)
          topping (string)
        foodSubtotal (number)
        taxFee (number)
        shippingFee (number)
        applicationFee (number)
        tips (number)
        discount (number)
        totalFee (number)
        userPickupCode (string)
        
    orderStatus: 'unpaid', 'submitted', 'accepted', 'ready', 'picked', 'arrived', 'completed',
    'rated', 'cancelled'
    orderStatusToTime: instance of OrderStatusToTimeModel, Map each order status with a time
    orderType: equal to 'pickUp'
    restaurantLocation: instance of LocationModel, it's attributes should not be null
    recieveTime: expect Pickup time
    foods: List of FoodInOrderModel
    userPickupCode: 4-digits code used for user verification
```

#### Delivery Order

```
orders (collection)
    $orderId
        orderId
        createdAt (timestamp)
        orderStatus (string)
        orderStatusToTime (map)
            unpaid (timestamp?)
            submitted (timestamp?)
            accepted (timestamp?)
            ready (timestamp?)
            picked (timestamp?)
            arrived (timestamp?)
            completed (timestamp?)
            rated (timestamp?)
            cancelled (timestamp?)
        driverStatus (string) 
        driverStatusToTime (map) 
            invalid (timestamp?)
            submitted (timestamp?)
            accepted (timestamp?)
            ready (timestamp?)
            picked (timestamp?)
            arrived (timestamp?)
            completed (timestamp?)
        orderType (string)
        deliveryLocation (map)
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
        userId (String)
        driverId (String?)
        restaurantLocation (map)     
            shortName (string)
            streetAddress (string)
            latitude (number)
            longitude (number)
        restaurantId (string)
        restaurantName (string)
        restaurantPhotoUrl (string)
        orderNote (string?)
        takeCutlery (bool)
        receiveTime (timestamp)
        foods (array of FoodInOrderModel) 
          foodId (string)
          foodName (string)
          quantity (number)
          singlePrice (number)
          foodNote (string)
          topping (string)
        foodSubtotal (number)
        taxFee (number)
        shippingFee (number)
        applicationFee (number)
        tips (number)
        discount (number)
        totalFee (number)
        userPickupCode (String)
        driverPickupCode (String)
        
    orderStatus: 'unpaid', 'submitted', 'accepted', 'ready', 'picked', 'arrived', 'completed',
    'rated', 'cancelled'
    orderStatusToTime: instance of OrderStatusToTimeModel, Map each order status with a time
    driverStatus: 'invalid', 'submitted', 'accepted', 'ready', 'picked', 'arrived', 'completed'
    driverStatusToTime: instance of OrderStatusToTimeModel, Map each order status with a time
    orderType: equal to 'delivery'
    receiveTime: expect Delivery (Receive) time
    restaurantLocation: instance of LocationModel, it's attributes should not be null
    deliveryLocation: instance of UserAddressModel
    foods: List of FoodInOrderModel
    userPickupCode: 4-digits code used for user verification
    driverPickupCode: 4-digits code used for driver verification
```

#### GrabAndGo Order

```
orders (collection)
    $orderId
        orderId (string)
        createdAt (timestamp)
        referenceId (string)
        pickupLocationId (string)
        orderStatus (string)
        orderStatusToTime (map)
            unpaid (timestamp?)
            submitted (timestamp?)
            accepted (timestamp?)
            ready (timestamp?)
            picked (timestamp?)
            arrived (timestamp?)
            completed (timestamp?)
            rated (timestamp?)
            cancelled (timestamp?)
        orderType (string)
        userId (String)
        contactName (String)
        phoneNumber (String)
        restaurantLocation (map)      
            shortName (string)
            streetAddress (string)
            latitude (number)
            longitude (number)
        restaurantId (string)
        restaurantName (string)
        restaurantPhotoUrl (string)
        orderNote (string?)
        takeCutlery (bool)
        receiveTime (timestamp)
        foods (array of FoodInOrderModel) 
          foodId (string)
          foodName (string)
          quantity (number)
          singlePrice (number)
          foodNote (string)
          topping (string)
        foodSubtotal (number)
        taxFee (number)
        shippingFee (number)
        applicationFee (number)
        tips (number)
        discount (number)
        totalFee (number)
        userPickupCode (String)
                        
    referenceId: reference to grabAndGo, other common shared data. Referece Id follows
    "restaurantId + pickupLocationId + receiveTime"
    pickupLocationId: pick up location
    orderStatus: 'unpaid', 'submitted', 'accepted', 'ready', 'picked', 'arrived', 'completed',
    'rated', 'cancelled'
    orderStatusToTime: instance of OrderStatusToTimeModel, Map each order status with a time
    orderType: equal to 'grabAndGo'
    restaurantLocation: instance of LocationModel, it's attributes should not be null
    recieveTime: expect Pickup time
    foods: List of FoodInOrderModel
    userPickupCode: 4-digits code used for user verification
```    
    
### Chats

Chats Documents (path: `orders/{orderId}/chats/{chatType}`, represented by `ChatModel`), stores 
basic chat information. This document is public. This document contains one sub-collection
`messages`.

```
chats (collection)
   $chatType
       orderId (string)
       chatType (string) 
       primaryUserId (string)
       primaryUserPhotoUrl (string)
       primaryUserName (string)
       secondaryUserId (string)
       secondaryUserPhotoUrl (string)
       secondaryUserName (string)
       lastMessage (string)
       onSection (bool)
        
   chatType: in format of primarySecondary (userDriver, userRestaurant, driverRestaurant)
   onSection: Whether this chat session is active
```


### Message

Messages Documents (path: `orders/{orderId}/chats/{chatType}/messages/{messageId}`, represented by 
`MessageModel`), stores message information. This document is public. This document contains no
sub-collection.

```
messages (collection)
    $messageId
        messageId (string)
        createdAt (timestamp)
        messageType (string)
        messageData (string)
        messageSource (string)
    
    messageType: text, image
    messageData: string of text, or string of image URL
    messageSource: user, driver, restaruant, admin
```