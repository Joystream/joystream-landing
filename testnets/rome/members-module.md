
# Members Module

## Table Of Content

- [Overview](#overview)
- [State Variables](#state-variables)
- [State Invariants](#state-invariants)
- [Events](#events)
- [Module Dependencies](#module-dependencies)
- [Transactions](#transactions)
  - [buy_membership](#buy_membership)
  - [change_member_about_text](#change_member_about_text)
  - [change_member_avatar](#change_member_avatar)
  - [change_member_handle](#change_member_handle)
  - [update_profile](#update_profile)
  - [add_screened_member](#add_screened_member)
  - [set_screening_authority](#set_screening_authority)

## Overview

Manages the set of current members, their profile, status.
<!--
## Constants

| Name                                  | Type                 | Value                             |
| :------------------------------------ |:--------------------:| :--------------------------------:|
| `DEFAULT_FIRST_MEMBER_ID`             | `u64`                | `1`                               |
| `FIRST_PAID_TERMS_ID`                 | `u64`                | `1`                               |
| `DEFAULT_PAID_TERM_ID`                | `u64`                | `0`                               |
| `DEFAULT_PAID_TERM_FEE`               | `u64`                | `100`                             |
| `DEFAULT_PAID_TERM_TEXT`              | `String`             | `Default Paid Term TOS...`        |
| `DEFAULT_MIN_HANDLE_LENGTH`           | `u32`                | `5`                               |
| `DEFAULT_MAX_HANDLE_LENGTH`           | `u32`                | `40`                              |
| `DEFAULT_MAX_AVATAR_URI_LENGTH`       | `u32`                | `1024`                            |
| `DEFAULT_MAX_ABOUT_TEXT_LENGTH`       | `u32`                | `2048`                            |

 ## Parametric Types

These are types which are instantiated by the runtime in which this module is being instantiated.

- `MemberId`
- `AccountId`
- `PaidTermId`
-->

## State

### Variables

### `first_member_id`

- **Type:** [MemberId](README.md#type-MemberId)
- **Genesis:** `Yes`
- **Default:** `1`

### `next_member_id`

- **Type:** [MemberId](README.md#type-MemberId)
- **Genesis:** `No`
- **Default:** `1`

### `account_id_by_member_id`

- **Type:** *map* [MemberId](README.md#type-MemberId) => [AccountId](README.md#AccountId)
- **Genesis:** `No`
- **Default:** -


### `member_id_by_account_id`

- **Type:** *map* [AccountId](README.md#AccountId) => Option< [MemberId](README.md#type-MemberId) >
- **Genesis:** `No`
- **Default:** -

### `member_profile`

- **Type:** *map* [MemberId](README.md#type-MemberId) => Option<Profile<T>>
- **Genesis:** `No`
- **Default:** -

### `handles`

- **Type:** map Vec<u8> => Option< [MemberId](README.md#type-MemberId) >
- **Genesis:** `No`
- **Default:** -

### `next_paid_membership_terms_id`

- **Type:** `PaidTermId`
- **Genesis:** `No`
- **Default:** `1`

### `paid_membership_terms_by_id`

- **Type:** map [PaidTermId](README.md#PaidTermId) => Option<PaidMembershipTerms<T>>
- **Genesis:** `No`
- **Default:** `1`

### `next_paid_membership_terms_id`

- **Type:** Vec< PaidTermId >
- **Genesis:** `No`
- **Default:** `vec![0]`

### `active_paid_membership_terms`

- **Type:** Vec< PaidTermId >
- **Genesis:** `No`
- **Default:** `vec![0]`

### `new_memberships_allowed`

- **Type:** bool
- **Genesis:** `No`
- **Default:** `true`

### `screening_authority`

- **Type:** `Option<T::AccountId>`
- **Genesis:** `No`
- **Default:** -

### `min_handle_length`

- **Type:** u32
- **Genesis:** `No`
- **Default:** `5`

### `max_handle_length`

- **Type:** u32
- **Genesis:** `No`
- **Default:** `40`

### `max_avatar_uri_length`

- **Type:** u32
- **Genesis:** `No`
- **Default:** `1024`

### `max_about_text_length`

- **Type:** u32
- **Genesis:** `No`
- **Default:** `2048`

### Invariants

1. `xxxx`
2. `xxxx`

## Module Dependencies

The following list of peer modules, are relied upon to be in the same runtime.

- [**Actors**](#actors-module.md)
- [**Currency**](#)

## Events

### `MemberRegistered`
- **Payload:** (MemberId, AccountId)
- **Description:** (MemberId, AccountId)

### `MemberUpdatedAboutText`

#### Payload

1. [MemberId](runtime-types.md#MemberId) `id`
2. [MemberId](runtime-types.md#MemberId) `id_2`

#### Description

The about text on member `id` was altered to `x`

### `MemberUpdatedAvatar`

_fill in_

### `MemberUpdatedHandle`

_fill in_

## Extrinsics

### `buy_membership`

#### Payload

```Rust
p: PaidTermId, u: UserInfo
```


#### Description

Establish new membership through payment.

#### Errors

| # | Message | Precondition |
|:-: |:---------|:----------|
| 0 | ? | `[ensure_signed](runtime-types.md#ensure_signed)(**origin**) |
| 1 | new members not allowed | \![new_memberships_allowed](#new_memberships_allowed) |


#### Side effects

##### Membership established

Let

  - **terms** = `[paid_membership_terms_by_id](#).get(**p**)`
  - **profile** =
```Rust
Profile {
            id: new_member_id,
            handle: user_info.handle.clone(),
            avatar_uri: user_info.avatar_uri.clone(),
            about: user_info.about.clone(),
            registered_at_block: <system::Module<T>>::block_number(),
            registered_at_time: <timestamp::Module<T>>::now(),
            entry: entry_method,
            suspended: false,
            subscription: None,
};
```

then

  - **Precondition:** `NO_ERROR`
  - **Side effect(s):**
    - `let member_id = Self::insert_member(&who, &user_info, EntryMethod::Paid(paid_terms_id))`
    - `[Currency](#)::balance(**who**) == [Currency](#)::balance<sup>pre</sup>(**who**) - **terms**.fee`
    - `<MemberIdByAccountId<T>>::insert(who.clone(), new_member_id);`
    - `<AccountIdByMemberId<T>>::insert(new_member_id, who.clone());`
    - `<MemberProfile<T>>::insert(new_member_id, profile);`
    - `<Handles<T>>::insert(user_info.handle.clone(), new_member_id)`
    - `<NextMemberId<T>>::mutate(|n| { *n += T::MemberId::sa(1); });`
  - **Result:** Ok([next_member_id](#next_member_id)<sup>pre</sup>)
  - **Event(s):** MemberRegistered(member_id, who.clone())

<!--
#### Termination(s)

1. **Bad signature**
   - **Precondition:** \![ensure_signed](runtime-types.md#ensure_signed) (`origin`)
   - **Side effect(s):** _none_
   - **Result:** `Err(<what here?>)`
   - **Event(s):** _none_   
2. **Closed for new memberships**
    - **Precondition:** `!precondition(1) && !new_memberships_allowed`
    - **Side effect(s):** _none_
    - **Result:** `Err("new members not allowed")`
    - **Event(s):** _none_
3. **Account has existing membership**
    - **Precondition:** `!precondition(2) && member_id_by_account_id.exists(x)`
    - **Side effect(s):** _none_
    - **Result:** `Err("account already associated with a membership")`
    - **Event(s):** _none_
4. **Key already used for role**
    - **Precondition:** `!precondition(3) && Actors.actor_by_account_id.exists(ensure_signed(origin))`
    - **Side effect(s):** _none_
    - **Result:** `Err(“role key cannot be used for membership”)`
    - **Event(s):** _none_
5. **Terms are not active**
    - **Precondition:** `!precondition(4) && !active_paid_membership_terms.iter().any(|x| x == p.id)`
    - **Side effect(s):** _none_
    - **Result:** `Err(“paid terms id not active”)`
    - **Event(s):** _none_
6. **Terms don't exist** <= _This is a bug_
    - **Precondition:** `!precondition(5) && !paid_membership_terms_by_id.exists(p.id)`
    - **Side effect(s):** _none_
    - **Result:** `Err(“paid terms id not active”)`
    - **Event(s):** _none_
7. **Insufficient funds for membership**
    - **Precondition:** `precondition(6) && !Currency.can_slash(ensure_signed(origin), p.fee)`
    - **Side effect(s):** _none_
    - **Result:** `Err("not enough balance to buy membership")`
    - **Event(s):** _none_
8. **Invalid user information: missing handle**
9. **Invalid user information: handle too short**
10. **Invalid user information: handle too long**
11. **Invalid user information: avatar uri too long**
12. **Handle occupied**
13. **Membership established**
    - **Precondition:** `precondition(2) && member_id_by_account_id.exists(x)`
    - **Side effect(s):**
      - `let member_id = Self::insert_member(&who, &user_info, EntryMethod::Paid(paid_terms_id))`
      - `let _ = T::Currency::slash(&who, terms.fee);`
    - **Result:** `Ok(member_id)`
    - **Event(s):** `MemberRegistered(member_id, who.clone())`
-->

### `change_member_about_text`

_fill in_

### `change_member_avatar`

_fill in_

### `change_member_handle`

_fill in_

### `update_profile`

_fill in_

### `add_screened_member`

_fill in_

### `set_screening_authority`

_fill in_
