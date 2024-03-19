## Firestore Schema - Invites collection

### Invites

Invites Documents (path: `invites/{email}`, represented by `InviteModel`), stores
information of an invite. This document is public.

```
invites (collection) [InviteModel]
    email (document)
        email (string)
        inviterId (string)        
        createdAt (timestamp)
```