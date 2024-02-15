## Firestore Schema - Restaurants collection

### Restaurants

Restaurants Documents (path: `restaurants/{sellerId}`, represented by `RestaurantModel`), stores
basic restaurant information. This document is public. This document contains sub-collections
including `sections` and `foods`.

```
restaurants (collection)
    $sellerId (document)
        sellerId (string)
        createAt (timestamp)
        restaurantCategory (List<string>)
        restaurantName (string)
        restaurantDescription (string)
        restaurantPhotoUrl (string)
        restaurantType (string)
        contactName (string)
        contactPhoneNumber (string)
        ratings (number)
        reviewNumbers (number)
        location (map)
            shortName (string)
            streetAddress (string)
            latitude (number)
            longitude (number)
        isOpen (bool)
        openHour (map)
            Sunday (map)
                openHour (int)
                openMinute (int)
                closeHour (int)
                closeMinute (int)
            Monday (map)
            TuesDay (map)
            Wednesday (map)
            Thursday (map)
            Friday (map)
            Saturday (map)
        restaurantDiscount (string)
    
    restaurantCategory: At most three categories
    restaurantType: "Food Truck" or "Restaurant"
    ratings: update every day, based on previous month
    reviewNumbers: update every day, based on previous month
    location: instance of LocationModel
    openHour: instance of OpenHour, Map of OpenTimeModel
    restaurantDiscount: TBD, defult 'none'
```

### Sections

Restaurant Sections Documents (path: `restaurants/{sellerId}/sections/{sectionId}`, represented by
`RestaurantSectionModel`), stores restaurant section information. This document is public. This
document contains no sub-collections.

```
sections (collection)
    $sectionId (document)
        sectionId
        sectionName (string)
        minSelection (number)
        maxSelection (number)
        restaurantDiscount
    
    minSelection: min number of selection under this section before user can create this order
    maxSelection: max number of selection under this section before user can create this order      
    restaurantDiscount: TBD, defult 'none'
```

### Foods

Restaurant Foods Documents (path: `restaurants/{sellerId}/foods/{foodId}`, represented by
`FoodModel`), stores restaurant foods information. This document is public. This
document contains one sub-collections `toppingSections`.

```
foods (collection)
    $foodId
        foodId (string)
        foodName (string)
        foodDescription (string)
        foodPrice (number)
        foodPhotoUrl (string)
        sectionId (string)
        foodLikes (string)
        foodSold (string)
        
    foodLikes: update every day, based on previous month
    foodSold: update every day, based on previous month  
```

### Topping Section

Topping Sections Under Food Documents
(path: `restaurants/{sellerId}/foods/{foodId}/toppingSections/{toppingSectionId}`, represented by
`ToopingSectionModel`), stores topping section information. This document is public. This
document contains one sub-collections `toppings`.

```
toppingSections (collection)
    $toppingSectionId
        toppingSectionId (string)
        sectionName (string)
        minSelection (number)
        maxSelection (number)
        
    minSelection: min number of selection under this section before user can create this order
    maxSelection: max number of selection under this section before user can create this order 
```

### Toppings

Toppings Under ToppingSections Under Food Documents (path:
`restaurants/{sellerId}/foods/{foodId}/toppingSections/{toppingSectionId}/toppings/{toppingId}`,
represented by `ToopingModel`), stores topping information. This document is public. This
document contains no sub-collections.

```
toppings (collection)
    $toppingId
        toppingId (String)
        toppingName (String)
        toppingPrice (number)
```


