
# Members Module

## Table Of Content

- [Overview](#overview)
- [Constants](#constants)
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

<!-- ## Parametric Types

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
- **Default:** `DEFAULT_FIRST_MEMBER_ID`

### `next_member_id`

- **Type:** [MemberId](README.md#type-MemberId)
- **Genesis:** `No`
- **Default:** `DEFAULT_FIRST_MEMBER_ID`

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
- **Default:** `FIRST_PAID_TERMS_ID`

### `paid_membership_terms_by_id`

- **Type:** map [PaidTermId](README.md#PaidTermId) => Option<PaidMembershipTerms<T>>
- **Genesis:** `No`
- **Default:** `FIRST_PAID_TERMS_ID`

### `next_paid_membership_terms_id`

- **Type:** Vec< PaidTermId >
- **Genesis:** `No`
- **Default:** `vec![DEFAULT_PAID_TERM_ID]`

### `active_paid_membership_terms`

- **Type:** Vec< PaidTermId >
- **Genesis:** `No`
- **Default:** `vec![DEFAULT_PAID_TERM_ID]`

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
- **Default:** `DEFAULT_MIN_HANDLE_LENGTH`

### `max_handle_length`

- **Type:** u32
- **Genesis:** `No`
- **Default:** `DEFAULT_MAX_HANDLE_LENGTH`

### `max_avatar_uri_length`

- **Type:** u32
- **Genesis:** `No`
- **Default:** `DEFAULT_MAX_AVATAR_URI_LENGTH`

### `max_about_text_length`

- **Type:** u32
- **Genesis:** `No`
- **Default:** `DEFAULT_MAX_ABOUT_TEXT_LENGTH`

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

The about text on member `id` was alted to `x`

### `MemberUpdatedAvatar`

_fill in_

### `MemberUpdatedHandle`

_fill in_

## Extrinsics

### `buy_membership`

#### Payload

1. [PaidTermId](runtime-types.md#PaidTermId) `p`
2. [UserInfo](runtime-types.md#UserInfo) `u`

#### Description

Establish new membership through payment.

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
let terms = Self::ensure_active_terms_id(paid_terms_id)?;

5. **Insufficient funds for membership**
    - **Precondition:** `precondition(2) && ...`
    - **Side effect(s):** _none_
    - **Result:** `Err("....")`
    - **Event(s):** _none_

ensure!(T::Currency::can_slash(&who, terms.fee), "not enough balance to buy membership");

6. **Invalid user information**
    - **Precondition:** `precondition(2) && ...`
    - **Side effect(s):** _none_
    - **Result:** `Err("....")`
    - **Event(s):** _none_

let user_info = Self::check_user_registration_info(user_info)?;

7. **Handle occupied**
    - **Precondition:** `precondition(2) && ...`
    - **Side effect(s):** _none_
    - **Result:** `Err("....")`
    - **Event(s):** _none_

Self::ensure_unique_handle(&user_info.handle)?;

8. **Membership established**
    - **Precondition:** `precondition(2) && member_id_by_account_id.exists(x)`
    - **Side effect(s):**
      - `let member_id = Self::insert_member(&who, &user_info, EntryMethod::Paid(paid_terms_id))`
      - `let _ = T::Currency::slash(&who, terms.fee);`
    - **Result:** `Ok(member_id)`
    - **Event(s):** `MemberRegistered(member_id, who.clone())`

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
