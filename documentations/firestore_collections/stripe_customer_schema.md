## Firestore Schema - Stripe Customers collection

### Stripe Customers

Stripe Customer Documents (path: `stripeCustomers/{userId}`, represented by `StripeCustomerModel`), 
stores the test and live stripe customer ID of given userId. This document is private. This document 
contains sub-collection including `paymentMethods`, and `payments`.

```
stripeCustomers
    $userId
        userId (string)
        customerId (string)
        customerTestId (string)
```

### Stripe Payment Methods

Stripe Customer's Payment Method Documents (path: 
`stripeCustomers/{userId}/paymentMethods/{paymentMethodId}`, represented by `PaymentMethodModel`),
stores the summary of payment methods of this stripe customer. This document is private. This 
document contains no sub-collection.

#### CardPaymentMethod

```
paymentMethods (collection)
    $paymentMethodId (doc)
        createdAt (timestamp)
        paymentMethodId (string)
        paymentMethodType (string)
        hasVerified (bool)
        isTest (bool)
        lastFour (string)
        expMonth (int)
        expYear (int)
        brand (string)
        billingName (string)
        billingEmail (string)
        
    paymentMethodType: instance of AppPaymmentMethodType: 'card', 'applePay'
    hasVerified: whether this payment method has been verifed (set up)
```


### Stripe Payments

Stripe Customer's Payments Documents (path:
`stripeCustomers/{userId}/payments/{pushId}`, represented by `PaymentModel`),
stores the summary of successful payments of this stripe customer. This document is private. This
document contains no sub-collection.

#### OrderPayment

```
payments (collection)
    $pushId
        pushId (string)
        createdAt (timestamp)
        paymentType (string)
        amount (int)
        currency (string)
        paymentMethodId (string)
        paymentIntentId (String)
        isTest (bool)
        
    paymentType: Instance of PaymentType, equals to 'order'
```