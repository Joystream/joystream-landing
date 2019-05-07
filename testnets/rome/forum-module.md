
# Forum Module

## Table Of Content

- [Design](#design)
- [Dependencies](#dependencies)
- [Name](#name)
- [Concepts](#concepts)
- [State](#state)
- [Events](#events)
- [Dispatchable Methods](#dispatchable-methods)

- [Non-dispatchable Methods](#non-dispatchable-methods)


## Design

### Motivation

....

### Structure

The structure of the forum is hierarchical, where each level of the forum is referred to as a topic category.

The root category simply includes other child categories, nothing else. It exists from the genesis of the forum, and can never be removed.

All other categories have an explicit name and explicit subject matter topic. Within such a category there may be other subcategories, and also threads, which are sequences of posts under some headline title and initial post made by the author of the thread. Such categories can be added and removed.

### Posts and threads

A thread is a sequence of posts, in a given topic category, which has some initial post from the original author, and title. A post exists in the context of a thread, and has some position in thread post sequence, as well as a body text. Both threads have a corresponding author and creation date. The text in a post can be edited by any time by the original author, however the history of all texts are available in the state.

### Users

Forum users can create threads in categories, and post to existing threads. A post s

### Forum SUDO

### Moderator??? forumsudo



## Forum
This covers the experience of users across Pioneer, the command line.

### Member
As a member I can create a new thread in a category, with a title and text.
As a member I can compose a post in markdown and submit to a thread.
As a member I can reply to a prior post in a thread by getting a quote of the prior post in my composer.
As a member I can edit the text of a post.
As a member I can learn how to become moderator in a given category. <= OUT!
As a member I can become a top level moderator by contacting Sudo (some how?). <= OUT!
As a member I can become a non-top level moderator by contacting the moderator of the parent category. <= OUT!

### Moderator <== OUT
As a moderator I can pin and unpin a post at the top of a category.
As a moderator I can create a subcategory of my category.
As a moderator I can archive and unarchive a subcategory of my category.
As a moderator I can lock and unlock a thread in my category. <== OUT!
As a moderator I can make/remove someone a moderator in a subcategory of my category. <== OUT!
### Forum Sudo
As forum sudo create a subcategory.
As forum sudo I can delete a post.
As forum sudo I can delete a category.

### Sudo
As sudo I can make a member a forum sudo.
As sudo I can remove a forum sudo.

As sudo I can alter the moderator set in any topic category <== OUT!
As sudo I can change key forum constraint variables on mutating/creating posts, threads, etc. <== OUT!




## Name

`Forum`

<!--

## Dependencies

- `Currency`: An external currency module which supports altering balances and total issuance.

## Concepts

- `Profile`: Describes core properties and status of a membership, like a unique handle and avatar URI. Is identified with unique integer identifier, called _member id_.

- `PaidMembershipTerms`: Terms for becoming a member, like price and terms. Is identified with a unique integer identifier called a _paid terms id_.

- `UserInfo`: Information required to establish a new profile.

## State

- `NextMemberId`: Unique identifier for next member, should equal total number of members ever created.

- `AccountIdByMemberId`: Maps member id to an account id.

- `MemberIdByAccountId`: Maps account id to optional member id.

- `MemberProfile`: Maps member id to `Profile` of member.

- `Handles`: Maps handle to corresponding memberid.

- `NextPaidMembershipTermsId`: Next paid membership terms id.

- `PaidMembershipTermsById`: Maps paid terms id to actual terms.

- `ActivePaidMembershipTerms`: Set of active paid term ids.

- `NewMembershipsAllowed`: Whether new memberships can currently be established.

- `ScreeningAuthority`: Optional account of screener.

- `MinHandleLength`, `MaxHandleLength`, `MaxAvatarUriLength`, `MaxAboutTextLength`: Mutable constraint variables

## Events

- `MemberRegistered`: A member was registered with a given id and account.
- `MemberUpdatedAboutText`: A member, with given id, had text updated.
- `MemberUpdatedAvatar`: A member, with given id, had avatar URI updated.
- `MemberUpdatedHandle`: A member, with given id, had handle updated.

## Dispatchable Methods

### `buy_membership`

#### Payload

- `paid_terms_id`: Id of terms
- `user_info`: UserInfo

#### Description

Establish new membership through payment.

#### Errors

- Bad signature.
- New members not allowed.
- Account already associated with a membership.
- Role key cannot be used for membership.
- Paid terms id not active.
- Not enough balance to buy membership.
- Missing handle.
- Handle too short.
- Handle too long.
- Avatar URI too long.
- Handle occupied.

#### Side effects

##### Membership established

###### Precondition

`NO_ERROR`

###### Side effect(s)

- `Currency` has decreased primary account balance and total issuance by terms fee.
- `MemberIdByAccountId` extended.
- `AccountIdByMemberId` extended.
- `MemberProfile` extended with new profile created with payload values.
- `Handles` extended with handle.
- `NextMemberId` incremented.

###### Event(s)

- `MemberRegistered` for new member

### `change_member_about_text`

#### Payload

- `text`: New about text

#### Description

Change about text on membership.

#### Errors

- Bad signature.
- No member id found for accountid.
- Not primary account.
- Member profile not found.

#### Side effects

##### About text updated

###### Precondition

`NO_ERROR`

###### Side effect(s)

- The text of profile of member corresponding to origin account is set to truncated `text`


###### Event(s)

- `MemberUpdatedAboutText`

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

## Non-dispatchable Methods

### `is_active_member`

_fill in_

### `lookup_member_id`

_fill in_

### `lookup_account_by_member_id`

_fill in_

-->
