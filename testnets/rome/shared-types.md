
# Shared Types

Here we list shared types which are used across multiple modules in the same runtime in various ways. Most, if not all, these types may eventually be dropped, as we make our modules more isolated, and define new stronger guidelines on runtime architecture, but for now its all listed here.

## GovernanceCurrency

```Rust
pub trait GovernanceCurrency: system::Trait + Sized {
    type Currency: Currency<Self::AccountId>
        + ReservableCurrency<Self::AccountId>
        + LockableCurrency<Self::AccountId, Moment = Self::BlockNumber>;
}
```
