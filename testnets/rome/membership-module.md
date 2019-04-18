
# Members Module

## Table Of Content

- [Overview](#overview)

# Overview

Manages the set of current members, their profile, status.

# Constants

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

# State Variables

| Name                                | Type                                                    | Genesis                    | Default                             |
| :---------------------------------- |:------------------------------------------------------- |:--------------------------:|:-----------------------------------:|
| `first_member_id`                   | `T::MemberId`                                           | `Yes`                      | `DEFAULT_FIRST_MEMBER_ID` |
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

# WIP: Peer Module Dependencies

The following list of peer modules, are relied upon to be in the same runtime.

- **xxx:**. A
- xxx-
- xxx

# State Invariants

1. `xxxx`
2. `xxxx`

# Events

- `MemberRegistered(MemberId, AccountId)``
- `MemberUpdatedAboutText(MemberId)`
- `MemberUpdatedAvatar(MemberId)`
- `MemberUpdatedHandle(MemberId)`

# Transactions

## `buy_membership`

- **Description:** hjaklfdjklfjklødsjlfø
- **Parameters:**
  1. `origin: Origin ?`
  2. `paid_terms_id: T::PaidTermId`
  3. `user_info: UserInfo`
- **Pre-condition:** `xxx`  
- **Post-condition:** `xxxx`
- **Events:** xxx
  - xx
  - xx
- **Errors:** xxx

## `change_member_about_text`

- **Description:** hjaklfdjklfjklødsjlfø
- **Parameters:**
  1. `origin: Origin ?`
  2. `text: Vec<u8>`

## `change_member_avatar`

- **Description:** hjaklfdjklfjklødsjlfø
- **Parameters:**
  1. `origin: Origin ?`
  2. `uri: Vec<u8>`

## `change_member_handle`

- **Description:** hjaklfdjklfjklødsjlfø
- **Parameters:**
  1. `origin: Origin ?`
  2. `handle: Vec<u8>`

## `update_profile`

- **Description:** hjaklfdjklfjklødsjlfø
- **Parameters:**
  1. `origin: Origin ?`
  2. `user_info: UserInfo`

## `add_screened_member`

- **Description:** hjaklfdjklfjklødsjlfø
- **Parameters:**
  1. `origin: Origin ?`
  2. `new_member: T::AccountId`
  3. `user_info: UserInfo`

## `set_screening_authority`

- **Description:** hjaklfdjklfjklødsjlfø
- **Parameters:**
  1. `authority: T::AccountId`
