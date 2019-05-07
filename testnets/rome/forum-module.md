
# Forum Module

## Table Of Content

- [Design](#design)
- [Dependencies](#dependencies)
- [Name](#name)
- [Concepts](#concepts)
- [State](#state)
- [Events](#events)
- [Dispatchable Methods](#dispatchable-methods)
  - [create_category](#create_category)
  - [delete_category](#delete_category)
  - [create_thread](#create_thread)
  - [delete_thread](#delete_thread)
  - [add_post](#add_post)
  - [delete_post](#delete_post)
  - [set_forum_sudo](#set_forum_sudo)
- [Non-dispatchable Methods](#non-dispatchable-methods)

## Design

### Motivation

This module holds the basic content and structure of a hierarchical topic based forum with trivial sudo based moderation. It allows a blockchain to have _direct_ assertible custody of the forum governance and function. Systems which depend critical on reliable and fair asynchronous public discourse will benefit from this functionality.

### Structure

The structure of the forum is hierarchical, where each level of the forum is referred to as a topic category. The root category simply includes other child categories, nothing else. It exists from the genesis of the forum, and can never be removed. All other categories, called _subcategories_, have an explicit name and explicit subject matter topic. Within such a category there may be other subcategories, and also threads, which are sequences of posts under some headline title and initial post made by the author of the thread. Such categories can be added and removed.

### Posts and threads

A thread is a sequence of posts, in a given topic category, which has some initial post from the original author, and title. A post exists in the context of a thread, and has some position in thread post sequence, as well as a body text. Both threads have a corresponding author and creation date. The text in a post can be edited by any time by the original author, however the history of all texts are available in the state.

### Users

Forum users can create threads in categories, and post to existing threads. This module does not maintain its own set of forum users, but rather depends on some external module for this. The rationale for this is to allow reuse of the module with a diversity of user management systems, without requiring that runtime developer must keep user set state in synch, or waste state space.

### Forum sudo

There will be a single account, called the _forum sudo_ account. This account is set by the Sudo of the runtime, and can

- **Create a subcategory**: Requires specifying the parent category.

- **Delete a subcategory**: Only possible if empty, that is there are no subcategories or threads. Requires leaving some sort of rationale in place of the category, which should be removed from state fully, including all corresponding threads and posts.

- **Delete a post in a thread**: Requires leaving some sort of rationale in place of the post, which should be gone from the state.

- **Delete a thread**: Requires leaving some sort of rationale in place of the thread, which should be gone from the state, along with all posts.


## Name

`Forum`

## Dependencies

- `ForumUserRegistry`: An external module which holds actual user state, allowing it to be queried based on some user identifier, and recovering some representation of a user.

## Concepts

- `ForumUserId`: Identifier used for forum user, which is used by `ForumUserRegistry` dependency.

- `ForumUser`: Represents an actual forum user, which is provided by `ForumUserRegistry` dependency.

- `ForumSudoId`: Identifies a forum sudo authority, is integer.

- `TopicCategory`: Represents a subcategory, and includes a title, creation date, `ForumSudoId` of creator, parent  category (if not root), and short topic description text. Is identified with an integer which is unique across all objects in all subtopics.

- `Thread`: Represents a thread, and includes a title, creation date and `ForumUserId` of creator. Is identified with an integer which is unique across all objects in all subtopics.

- `Post`: Represents a thread post, and includes a linked list of body texts, one entry per edit (chronologically ordered) - corresponding to edit history, initial body text (not in list to disqualify otherwise invalid empty list state), creation date and `ForumUserId` of creator. Is identified with an integer which is unique across all objects in all subtopics and threads.

- `ModeratedPost`: Represents a post which was moderated by forum sudo, and includes a moderation date, a hash of the moderated body text, post identifier, a text rationale and the `ForumSudoId` of moderator.

- `ThreadEntry`: Represents the presence of a post, or a moderated post, in a thread. Includes a reference to a `Post` or a `ModeratedPost` (but not both), a thread identifier and a thread position identifier representing position in thread. Is identified with an integer.

## State

- `TopicCategoriesById`: Map category identifier to corresponding `TopicCategory`.

- `ThreadById`: Map combined topic category identifier to corresponding `Thread`.

- `PostById`: Map post identifier to corresponding

## Events

WIP

## Dispatchable Methods

### `create_category`

#### Payload

- ...

#### Description

...

#### Errors

- ...
- ...

#### Side effects

##### [...]

###### Precondition

`NO_ERROR`

###### Side effect(s)

- ...

###### Event(s)

- ...

### `delete_category`

#### Payload

- ...

#### Description

...

#### Errors

- ...
- ...

#### Side effects

##### [...]

###### Precondition

`NO_ERROR`

###### Side effect(s)

- ...

###### Event(s)

- ...

### `create_thread`

#### Payload

- ...

#### Description

...

#### Errors

- ...
- ...

#### Side effects

##### [...]

###### Precondition

`NO_ERROR`

###### Side effect(s)

- ...

###### Event(s)

- ...

### `delete_thread`

#### Payload

- ...

#### Description

...

#### Errors

- ...
- ...

#### Side effects

##### [...]

###### Precondition

`NO_ERROR`

###### Side effect(s)

- ...

###### Event(s)

- ...

### `add_post`

#### Payload

- ...

#### Description

...

#### Errors

- ...
- ...

#### Side effects

##### [...]

###### Precondition

`NO_ERROR`

###### Side effect(s)

- ...

###### Event(s)

- ...

### `delete_post`

#### Payload

- ...

#### Description

...

#### Errors

- ...
- ...

#### Side effects

##### [...]

###### Precondition

`NO_ERROR`

###### Side effect(s)

- ...

###### Event(s)

- ...

### `set_forum_sudo`

#### Payload

- ...

#### Description

...

#### Errors

- ...
- ...

#### Side effects

##### [...]

###### Precondition

`NO_ERROR`

###### Side effect(s)

- ...

###### Event(s)

- ...


<!--

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

None.

-->
