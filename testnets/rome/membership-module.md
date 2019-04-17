
# Members Module

# Overview

`Describe purpose of module`

## Constants


| Name                        | Type          | Value                |
| --------------------------- |:-------------:| --------------------:|
| `DEFAULT_PAID_TERM_ID`      | `u64`         | 0                    |
| `DEFAULT_PAID_TERM_FEE`     | `u64`        | 100                    |
| `DEFAULT_PAID_TERM_TEXT`    | `String`        | Default Paid Term TOS...   |

## State Variables



| Name                       | Type                   | Genesis                          | Default               |
| --------------------------- |:---------------------:|:--------------------------------:|:--------------------:|
| `first_member_id`           | `T::MemberId`         | TYes`                                | `DEFAULT_FIRST_MEMBER_IDE` |
| `next_member_id`     | `T::MemberId`                 | 100                              |  `DEFAULT_FIRST_MEMBER_IDE`  |
| `DEFAULT_PAID_TERM_TEXT`    | `String`              | Default Paid Term TOS...         | |

```Rust

get(first_member_id) config(first_member_id): T::MemberId = T::MemberId::sa()

) build(|config: &GenesisConfig<T>| config.first_member_id): T::MemberId = T::MemberId::sa(DEFAULT_FIRST_MEMBER_ID)

account_id_by_member_id) : map T::MemberId => T::AccountId

member_id_by_account_id) : map T::AccountId => Option<T::MemberId>

member_profile) : map T::MemberId => Option<Profile<T>>

handles) : map Vec<u8> => Option<T::MemberId>

next_paid_membership_terms_id) : T::PaidTermId = T::PaidTermId::sa(FIRST_PAID_TERMS_ID)

paid_membership_terms_by_id) build(|config: &GenesisConfig<T>| {
            // This method only gets called when initializing storage, and is
            // compiled as native code. (Will be called when building `raw` chainspec)
            // So it can't be relied upon to initialize storage for runtimes updates.
            // Initialization for updated runtime is done in run_migration()
            let mut terms: PaidMembershipTerms<T> = Default::default();
            terms.fee = config.default_paid_membership_fee;
            vec![(terms.id, terms)]
        }) : map T::PaidTermId => Option<PaidMembershipTerms<T>>

active_paid_membership_terms) : Vec<T::PaidTermId> = vec![T::PaidTermId::sa(DEFAULT_PAID_TERM_ID)]
new_memberships_allowed) : bool = true
screening_authority) : Option<T::AccountId>
min_handle_length) : u32 = DEFAULT_MIN_HANDLE_LENGTH
max_handle_length) : u32 = DEFAULT_MAX_HANDLE_LENGTH
max_avatar_uri_length) : u32 = DEFAULT_MAX_AVATAR_URI_LENGTH
max_about_text_length) : u32 = DEFAULT_MAX_ABOUT_TEXT_LENGTH
```
## WIP: Peer Module Dependencies

The following list of peer modules, are relied upon to be in the same runtime.

- **xxx:**. A
- xxx-
- xxx

## State Invariants

1. `xxxx`
2. `xxxx`

## Events

- `added_member(String s, PublicKey s)`
- `added_member(String s, PublicKey s)`
- `added_member(String s, PublicKey s)`

## Transactions

### `add_member`

- **Description:** hjaklfdjklfjklødsjlfø
- **Parameters:**
  1. `PublicKey s`: xxx
  2. `String s`: xxxx
- **Pre-condition:** `xxx`  
- **Post-condition:** `xxxx`
- **Events:**
  - xx
  - xx
