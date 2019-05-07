
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
  - [edit_post_text](#edit_post_text)
  - [set_forum_sudo](#set_forum_sudo)
- [Non-dispatchable Methods](#non-dispatchable-methods)

## Design

### Motivation

This module holds the basic content and structure of a hierarchical topic based forum with trivial sudo based moderation. It allows a blockchain to have _direct_ assertible custody of the forum governance and function. Systems which depend critical on reliable and fair asynchronous public discourse will benefit from this functionality.

### Structure

The structure of the forum is hierarchical, where each non-root node is referred to as a category. The root simply includes other subcategories, nothing else. It exists from the genesis of the forum, and can never be removed. All other categories have an explicit name and explicit subject matter topic. Within such a category there may be other subcategories, and also threads, which are sequences of posts under some headline title and initial post made by the author of the thread. Such categories can be added and removed.

### Posts and threads

A thread is a sequence of posts, in a given category, which has some initial post from the original author, and title. A post exists in the context of a thread, and has some position in thread post sequence, as well as a body text. Both threads have a corresponding author and creation date. The text in a post can be edited by any time by the original author, however the history of all texts are available in the state.

### Users

Forum users can create threads in categories, and post to existing threads. This module does not maintain its own set of forum users, but rather depends on some external module for this. The rationale for this is to allow reuse of the module with a diversity of user management systems, without requiring that runtime developer must keep user set state in synch, or waste state space.

### Forum sudo

There will be a single account, called the _forum sudo_ account. This account is set by the Sudo of the runtime, and can

- **Create a category**: Requires specifying the parent category.

- **Delete a category**: Only possible if empty, that is there are no subcategories or threads. Requires leaving some sort of rationale in place of the category, which should be removed from state fully, including all corresponding threads and posts.

- **Delete a post in a thread**: Requires leaving some sort of rationale in place of the post, which should be gone from the state.

- **Delete a thread**: Requires leaving some sort of rationale in place of the thread, which should be gone from the state, along with all posts.

## Name

`Forum`

## Dependencies

- `ForumUserRegistry`: An external module which holds actual user state, allowing it to be queried based on a corresponding account, and recovering some representation of a user.

## Concepts

- `ForumUser`: Represents an actual forum user, which is provided by `ForumUserRegistry` dependency.

- `ForumSudoId`: Identifies a forum sudo authority.

- `Category`: Represents a forum category, and includes a title, creation date, `ForumSudoId` of creator, parent is set to identifier of `Category` - or not set at all if under root, and short topic description text. Is identified with an integer which is unique across all instances in all categories.

- `Thread`: Represents a thread, and includes a title, creation date and identifier of `ForumUser` creator. Is identified with an integer which is unique across all instances in all categories.

- `Post`: Represents a thread post, and includes a linked list of body texts, one entry per edit (chronologically ordered) - corresponding to edit history, initial body text (not in list to disqualify otherwise invalid empty list state), creation date and identifier of `ForumUser` creator.

- `ModeratedPost`: Represents a post which was moderated by forum sudo, and includes a moderation date, original creation date of post, identifier of original `ForumUser` creator, a hash of the moderated body text, a text rationale and the `ForumSudoId` of moderator.

- `ThreadEntry`: Represents the presence of a post, or a moderated post, in a thread. Includes an instance of a `Post` or `ModeratedPost` - but not both, a thread identifier and a thread position identifier representing position in thread. Is identified with an integer which is unique across all instances in all categories and threads.

## State

- `categoryById`: Map `Category` identifier to corresponding instance.

- `nextCategoryId`: Identifier to be used for the next `Category` in `categoryById`

- `threadById`: Map `Thread` identifier to corresponding instance.

- `nextThreadId`: Identifier to be used for next `Thread` in `threadById`

- `threadEntryById`: Map `ThreadEntry` identifier to corresponding instance.

- `nextThreadEntry`: Identifier to be used for next in `ThreadEntry` in `threadEntryById`.

- `forumSudo`: `ForumSudoId` of forum sudo.

## Events

- `CategoryCreated`: A category was introduced with a given identifier.
- `CategoryDeleted`: A category, with a given identifier, was removed.
- `ThreadCreated`: A thread was created with a given identifier.
- `ThreadDeleted`: A thread was removed, with a given identifier, was removed.
- `PostAdded`: A post was added,
- `EditPostText`: ...
- `PostDeleted`: ...

## Dispatchable Methods

### `create_category`

#### Payload

- `parentCategory`: blank if root, otherwise identifier of `Category`
- `title`: text title
- `description`: description text

#### Description

Add a new category.

#### Errors

- Bad signature
- Signature not matching `forumSudo`
- `parentCategory` does not exist
- `title` invalid
- `description` invalid

#### Side effects

- `categoryById` extended with new `Category` under new unique identifier.
- `nextCategoryId` updated

###### Event(s)

- `CategoryCreated`

### `delete_category`

#### Payload

-  `categoryId`: id of `Category` to remove.

#### Description

Delete a category.

#### Errors

- Bad signature
- Signature not matching `forumSudo`
-  not empty

#### Side effects

- `categoryById` no longer has the value corresponding to key `categoryId`

#### Event(s)

- `CategoryDeleted`

### `create_thread`

#### Payload

- `categoryId`: `Category` identifier of category where thread should be created
- `title`: thread title text
- `text`: text of initial post

#### Description

Create new thread in category.

#### Errors

- Bad signature
- Signer is not forum user
- `categoryId` not a valid category
- `title` not valid
- `text` not valid

#### Side effects

- ...

#### Event(s)

- `ThreadCreated`

### `delete_thread`

#### Payload

- ...

#### Description

...

#### Errors

- ...
- ...

#### Side effects

- ...

#### Event(s)

- `ThreadDeleted`

### `add_post`

#### Payload

- ...

#### Description

...

#### Errors

- ...
- ...

#### Side effects

- ...

#### Event(s)

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

- ...

#### Event(s)

- ...

### `edit_post_text`

#### Payload

- ...

#### Description

...

#### Errors

- ...
- ...

#### Side effects

- ...

#### Event(s)

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

- ...

#### Event(s)

- ...
