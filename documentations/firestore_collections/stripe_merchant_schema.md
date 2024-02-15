## Firestore Schema - Stripe Merchants collection

### Stripe Merchants

Stripe Merchant Documents (path: `stripeMerchants/{restaurantId}`, represented by 
`StripeMerchantModel`), stores the test and live stripe connect account ID of given seller. 
This document is private. This document contains no sub-collection.

```
stripeMerchants
    $sellerId
        sellerId (string)
        accountId (string)
        accountTestId (string)
        accountVerified (bool)
        accountTestVerified (bool)
        
    accountVerified: whether seller has complete onboarding on his live connect account
    accountTestVerified: whether seller has complete onboarding on his test connect account
```