
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

## Parametric Types

These are types which are instantiated by the runtime in which this module is being instantiated.

- `MemberId`
- `AccountId`
- `PaidTermId`

## State

### Variables

| Name                                | Type                                                    | Genesis                    | Default                             |
| :---------------------------------- |:------------------------------------------------------- |:--------------------------:|:-----------------------------------:|
| `first_member_id`                   | [MemberId](README.md#type-MemberId)                                           | `Yes`                      | `DEFAULT_FIRST_MEMBER_ID` |
| `next_member_id`                    | `T::MemberId`                                           | `No`                       | `DEFAULT_FIRST_MEMBER_ID`  |
| `account_id_by_member_id`           | `T::MemberId => T::AccountId`                           | `No`                       | - |
| `member_id_by_account_id`           | `map T::AccountId => Option<T::MemberId>`               | `No`                       | - |
| `member_profile`                    | `map T::MemberId => Option<Profile<T>>`                 | `No`                       | - |
| `handles`                           | `map Vec<u8> => Option<T::MemberId>`                    | `No`                       | - |
| `next_paid_membership_terms_id`     | `T::PaidTermId`                                         | `No`                       | `FIRST_PAID_TERMS_ID`|
| `paid_membership_terms_by_id`       | `map T::PaidTermId => Option<PaidMembershipTerms<T>>`   | `No`                       | `FIRST_PAID_TERMS_ID`|
| `next_paid_membership_terms_id`     | `Vec<T::PaidTermId>`                                    | `No`                       | `vec![DEFAULT_PAID_TERM_ID]`|
| `active_paid_membership_terms`      | `Vec<T::PaidTermId>`                                    | `No`                       | `vec![DEFAULT_PAID_TERM_ID]`|
| `new_memberships_allowed`           | `bool`                                                  | `No`                       | `true` |
| `screening_authority`               | `Option<T::AccountId>`                                  | `No`                       | - |
| `min_handle_length`                 | `u32`                                                   | `No`                       | `DEFAULT_MIN_HANDLE_LENGTH` |
| `max_handle_length`                 | `u32`                                                   | `No`                       | `DEFAULT_MAX_HANDLE_LENGTH` |
| `max_avatar_uri_length`             | `u32`                                                   | `No`                       | `DEFAULT_MAX_AVATAR_URI_LENGTH` |
| `max_about_text_length`             | `u32`                                                   | `No`                       | `DEFAULT_MAX_ABOUT_TEXT_LENGTH` |

### Invariants

1. `xxxx`
2. `xxxx`

## Module Dependencies

WIP:

The following list of peer modules, are relied upon to be in the same runtime.

- **xxx:**. A
- [**AccountIdByMemberId**](#AccountIdByMemberId)
- xxx

## Events

- `MemberRegistered(MemberId, AccountId)`
- `MemberUpdatedAboutText(MemberId)`
- `MemberUpdatedAvatar(MemberId)`
- `MemberUpdatedHandle(MemberId)`

## Transactions

### `buy_membership`

- **Description:** Establish new membership through payment.
- **Payload:** [PaidTermId](runtime-types.md#PaidTermId) p, [UserInfo](runtime-types.md#UserInfo) u
- **Code paths**:

| i     | Precondition                          | Postcondition                              | Result                     | Event(s)                  |
| :---: | :------------------------------------ |:-------------------------------------------|----------------------------|---------------------------|
| 0     | `.....`                               | `.....`                                    | `....`                     | `...`                     |
| 1     | `.....`                               | `.....`                                    | `....`                     | `...`                     |
| 2     | `.....`                               | `.....`                                    | `....`                     | `...`                     |


### `change_member_about_text`

- **Description:** hjaklfdjklfjklødsjlfø
- **Payload:** `text: Vec<u8>`

### `change_member_avatar`

- **Description:** hjaklfdjklfjklødsjlfø
- **Payload:** `uri: Vec<u8>`

### `change_member_handle`

- **Description:** hjaklfdjklfjklødsjlfø
- **Payload:** `handle: Vec<u8>`

### `update_profile`

- **Description:** hjaklfdjklfjklødsjlfø
- **Payload:** `user_info: UserInfo`

### `add_screened_member`

- **Description:** hjaklfdjklfjklødsjlfø
- **Payload:** `new_member: T::AccountId`, `user_info: UserInfo`

### `set_screening_authority`

- **Description:** hjaklfdjklfjklødsjlfø
- **Payload:** `authority: T::AccountId`
