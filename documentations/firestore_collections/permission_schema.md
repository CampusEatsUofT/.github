## Firestore Schema - Permission collection

### SellerPermission

Seller Permission Documents (path: `sellerPermission/{sellerId}`), stores whether this seller has
the seller permission. This document is private. This document contains no sub-collection.

```
sellerPermissions (collection)
    $sellerId (document)
        sellerId (string)
        hasPermission (timestamp)
        email (string)
```

### AdminPermission

Admin Permission Documents (path: `adminPermission/{adminId}`), stores whether this admin has
the admin permission. This document is private. This document contains no sub-collection.

```
adminPermissions (collection)
    $adminId (document)
        adminId (string)
        hasPermission (timestamp)
        email (string)
```

### DriverPermission

Driver Permission Documents (path: `driverPermission/{driverId}`), stores whether this driver has
the driver permission. This document is private. This document contains no sub-collection.

```
driverPermissions (collection)
    $driverId (document)
        driverId (string)
        hasPermission (timestamp)
        email (string)
```