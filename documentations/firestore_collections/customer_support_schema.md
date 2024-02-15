## Firestore Schema - Customer Support collection

### Customer Support

Customer Supports Documents (path: `customerSupports/{customerSupportId}`, represented by
`CustomerSupportModel`), stores different types of customer support data. This document is public.
This document contains no sub-collection.

#### UserOrderCustomerSupport

```
customerSupports (collection)
    $customerSupportId (document)
        customerSupportId (string)
        customerSupportType (string)
        createdAt (timestamp)
        priority (int)
        message (string)
        customerSupportStatus (string)
        adminId (string?)
        visibleDriverId (string?)
        visibleSellerId (string?)
        visibleUserId (string?)
        orderId (string)
        
    customerSupportType: 'websiteMessage', 'refundRequest', 'userOrder', 'restaurantOrder',
    equals to 'userOrder'
    priority: 1, 2, 3, less the more urgent
    customerSupportStatus: 'submitted', 'processing', 'completed'
    adminId: adminId which admins has processing this order. null if unaccepted
    visibleDriverId: driver who can see this customer support in his history
    visibleSellerId: seller who can see this customer support in his history
    visibleUserId: user who can see this customer support in his history
```

#### RestaurantOrderCustomerSupport

```
customerSupports (collection)
    $customerSupportId (document)
        customerSupportId (string)
        customerSupportType (string)
        createdAt (timestamp)
        priority (int)
        message (string)
        customerSupportStatus (string)
        adminId (string?)
        visibleDriverId (string?)
        visibleSellerId (string?)
        visibleUserId (string?)
        orderId (string)
        
    customerSupportType: 'websiteMessage', 'refundRequest', 'userOrder', 'restaurantOrder',
    equals to 'restaurantOrder'
    priority: 1, 2, 3, less the more urgent, eqauls to 1 in this case
    customerSupportStatus: 'submitted', 'processing', 'completed'
    adminId: adminId which admins has processing this order. null if unaccepted
    visibleDriverId: driver who can see this customer support in his history
    visibleSellerId: seller who can see this customer support in his history
    visibleUserId: user who can see this customer support in his history
```

#### WebsiteMessageCustomerSupport

```
customerSupports (collection)
    $customerSupportId (document)
        customerSupportId (string)
        customerSupportType (string)
        createdAt (timestamp)
        priority (int)
        message (string)
        customerSupportStatus (string)
        adminId (string?)
        visibleDriverId (string?)
        visibleSellerId (string?)
        visibleUserId (string?)
        email (string)
        name (string)
        phoneNumber (string)
        
    customerSupportType: 'websiteMessage', 'refundRequest', 'userOrder', 'restaurantOrder',
    equals to 'webstieMessage'
    priority: 1, 2, 3, less the more urgent, eqauls to 3 in this case
    customerSupportStatus: 'submitted', 'processing', 'completed'
    adminId: adminId which admins has processing this order. null if unaccepted
    visibleDriverId: driver who can see this customer support in his history
    visibleSellerId: seller who can see this customer support in his history
    visibleUserId: user who can see this customer support in his history
```



#### RefundRequestCustomerSupport

```
customerSupports (collection)
    $customerSupportId (document)
        customerSupportId (string)
        customerSupportType (string)
        createdAt (timestamp)
        priority (int)
        message (string)
        customerSupportStatus (string)
        adminId (string?)
        visibleDriverId (string?)
        visibleSellerId (string?)
        visibleUserId (string?)
        orderId (string)
        pushId (string)
        userId (string)
        paymentType (string)
        refundAmount (number)
        
    customerSupportType: 'websiteMessage', 'refundRequest', 'userOrder', 'restaurantOrder',
    equals to 'restaurantOrder'
    priority: 1, 2, 3, less the more urgent, eqauls to 1 in this case
    customerSupportStatus: 'submitted', 'processing', 'completed'
    adminId: adminId which admins has processing this order. null if unaccepted
    visibleDriverId: driver who can see this customer support in his history
    visibleSellerId: seller who can see this customer support in his history
    visibleUserId: user who can see this customer support in his history
    pushId: the pushId of the payment
    userId: the userId of user who pays this payment
    paymentType: 'order'

```



