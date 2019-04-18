
# Types

These are all public types that are part of the runtime. They are public in the sense that they are parameters in transactions or events, or that they are part of some module state(s). Any other types that may appear in a particular implementation, for example generic types and traits/interfaces related to software engineering abstractions, are not included.


only public parts of struct.. and of course only public types

## MemberId

`u64`

## PaidTermId

`u64`

## PaidMembershipTerms

**struct**

```Rust
pub struct PaidMembershipTerms<T: Trait> {
    /// Unique identifier - the term id
    pub id: T::PaidTermId,
    /// Quantity of native tokens which must be provably burned
    pub fee: BalanceOf<T>,
    /// String of capped length describing human readable conditions which are being agreed upon
    pub text: Vec<u8>,
}
```

## CheckedUserInfo

**struct**

```Rust
struct CheckedUserInfo {
    handle: Vec<u8>,
    avatar_uri: Vec<u8>,
    about: Vec<u8>,
}
```

## EntryMethod

**enum**

- Paid(PaidTermId),
- Screening(AccountId)

## Profile

**struct**

| Field                                  | Type                              |
| :------------------------------------ |:----------------------------------|
| `id`                                  | [`MemberId`](#MemberId)   |
| `handle`                              | `Vec<u8>`                         |
| `avatar_uri`                          | `Vec<u8>`                         |
| `about`                               | `Vec<u8>`                         |
| `registered_at_block`                 | `T::BlockNumber`                  |
| `registered_at_time`                  | `T::Moment`                       |
| `entry`                               | `EntryMethod`                     |
| `suspended`                           | `bool`                            |
| `subscription`                        | `Option<T::SubscriptionId>`       |

## UserInfo

| Field                                  | Type                          |
| :------------------------------------ |:------------------------------|
| `handle`                              | `Option<Vec<u8>>`             |
| `avatar_uri`                          | `Option<Vec<u8>>`             |
| `about`                               | `Option<Vec<u8>>`             |
