
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

- **Delete|Undelete a category**: Only possible if empty, that is there are no subcategories or threads. Is avoided for non-empty categories both for safety from both mistakes and malicious opportunists, and the possibly long time it may take to recursively execute on non-empty categories.

- **Delete a post in a thread**: Requires leaving some sort of rationale.

- **Delete a thread**: 

Requires leaving some sort of rationale in place of the thread, which should be gone from the state, along with all posts.

## Name

`Forum`

## Dependencies

- `ForumUserRegistry`: An external module which holds actual user state, allowing it to be queried based on a corresponding account, and recovering some representation of a user.

## Concepts

- `ForumUser`: Represents an actual forum user, which is provided by `ForumUserRegistry` dependency.

- `ForumSudoId`: Identifies a forum sudo authority.

- `ModerationAction`: Represents a moderation action on either a post or a

- `Post`: Represents a thread post, and includes initial text, moderation status, a vector of identifiers for `PostTextEdit` instances ordered chronologically by edit time, creation date and identifier of `ForumUser` creator.

- `PostTextEdit`: Represents a revision of the text of a `Post`, includes new text and revision date.

- `ModeratedPost`: Represents a post which was moderated by forum sudo, and includes a moderation date, original creation date of post, identifier of original `ForumUser` creator, a hash of the moderated body text, a text rationale for the moderation action and the `ForumSudoId` of moderator.

- `ThreadEntry`: Represents the presence of a post, or a moderated post, in a thread. Includes an instance of a `Post` or `ModeratedPost` - but not both, identifier for the corresponding `Thread` and an entry position. Is identified with an integer which is unique across all instances in all categories and threads.

- `Thread`: Represents a thread, and includes a title, number of `ThreadEntry` instances in the thread, creation date and identifier of `ForumUser` creator.

- `ModeratedThread`: Represents a thread which was moderated by forum sudo, and includes a moderation date,
original creation date of thread, identifier of original `ForumUser` creator, title of the thread and a text rationale for the moderation action and the `ForumSudoId` of moderator.

<!--
- `ParentCategoryId`: Represents an identifier for the parent of a `Category`. Is either an identifier for a `Category` when the parent is not the root category, otherwise it represents the root category.
-->

- `CategoryEntry`: Represents the presence of a thread, a moderated thread or a subcategory, in a category. Includes one, and only one, instance of a `Thread`, `ModeratedThread` or `ChildCategory`, identifier for the corresponding `ParentCategoryId` and an entry position. Is identified with an integer which is unique across all instances in all categories.

- `ChildCategory`: ... number of threads, total number of `CategoryEntry` instances, parent is set to identifier of `Category`

- `TopCategory`: ...






- `Category`: Represents a forum category, and includes a title, number of subcategories, creation date, `ForumSudoId` of creator and short topic description text. Is identified with an integer which is unique across all instances in all categories.

## State

- `rootCategories`

- `categoryById`: Map `Category` identifier to corresponding instance.

- `nextCategoryId`: Identifier to be used for the next `Category` created.

- `threadById`: Map `Thread` identifier to corresponding instance.

- `nextThreadId`: Identifier to be used for next `Thread` in `threadById`

- `threadEntryById`: Map `ThreadEntry` identifier to corresponding instance.

- `nextThreadEntry`: Identifier to be used for next in `ThreadEntry` created.

- `threadEntryIdsByThreadId`: Map `Thread` identifier to vector if `ThreadEntry` identifiers, ordered by entry position. **Note: This is here to make it fast to look up all entries in a given thread in a thread deletion scenario.**

- `forumSudo`: `ForumSudoId` of forum sudo.

## Events

- `CategoryCreated`: A category was introduced with a given identifier.
- `CategoryDeleted`: A category, with a given identifier, was removed.
- `ThreadCreated`: A thread was created with a given identifier.
- `ThreadDeleted`: A thread, with a given identifier, was removed.
- `ThreadModerated`: A thread, with a given identifier, was moderated.
- `PostAdded`: A post was introduced with a given identifier.
- `PostModerated`: A post, with a given entry position an `Thread` identifier, was moderated.
- `EditPostText`: A post, with a given identifier, had the post text edited.
- `PostDeleted`: A post, with a given identifier, was removed.

## Dispatchable Methods

### `create_category`

#### Payload

- `parent`: `ParentCategoryId` of parent
- `title`: text title
- `description`: description text

#### Description

Add a new category.

#### Errors

- Bad signature
- `forumSudo` does not match signature
- `parent` does not exist
- `title` invalid
- `description` invalid

#### Side effect(s)

- `categoryById` extended with new `Category` under new unique identifier.
- `nextCategoryId` updated
- if `parent` is not root, then subcategory count

#### Event(s)

- `CategoryCreated`

### `delete_category`

#### Payload

- `categoryId`: id of `Category` to remove.

#### Description

Delete a category.

#### Errors

- Bad signature
- `forumSudo` does not match signature
- Category not empty, has threads and/or subcategories

#### Side effect(s)

- `categoryById` no longer has category with identifier `categoryId`.
- parent of category identified by `categoryId`, if not root, has number of subcategories decremented.

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

#### Side effect(s)

- `threadById` extended with new `Thread`, which
- increment thread count of category with identifier `categoryId`

#### Event(s)

- `ThreadCreated`

### `delete_thread`

#### Payload

- `threadId`: identifier of `Thread` to delete

#### Description

Delete thread.

#### Errors

- Bad signature
- `forumSudo` does not match signature
- `threadId` not valid
- ``

#### Side effect(s)

- `threadById` no longer has `Thread` identified with `threadId`
-

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

#### Side effect(s)

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

#### Side effect(s)

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

#### Side effect(s)

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

#### Side effect(s)

- ...

#### Event(s)

- ...
