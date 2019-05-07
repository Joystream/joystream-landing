
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

- `ForumSudoId`: Identifies a forum sudo authority.

- `TopicCategory`: Represents a subcategory, and includes a title, creation date, `ForumSudoId` of creator, parent category is set to identifier of `TopicCategory` - or not set at all if under root, and short topic description text. Is identified with an integer which is unique across all instances in all categories.

- `Thread`: Represents a thread, and includes a title, creation date and `ForumUserId` of creator. Is identified with an integer which is unique across all instances in all subtopics.

- `Post`: Represents a thread post, and includes a linked list of body texts, one entry per edit (chronologically ordered) - corresponding to edit history, initial body text (not in list to disqualify otherwise invalid empty list state), creation date and `ForumUserId` of creator.

- `ModeratedPost`: Represents a post which was moderated by forum sudo, and includes a moderation date, original creation date of post, `ForumUserId` of original creator, a hash of the moderated body text, a text rationale and the `ForumSudoId` of moderator.

- `ThreadEntry`: Represents the presence of a post, or a moderated post, in a thread. Includes an instance of a `Post` or `ModeratedPost` - but not both, a thread identifier and a thread position identifier representing position in thread. Is identified with an integer which is unique across all instances in all subtopics and threads.

## State

- `topicCategoryById`: Map `TopicCategory` identifier to corresponding instance.

- `nextTopicCategoryId`: Identifier to be used for the next `TopicCategory` in `topicCategoryById`

- `threadById`: Map `Thread` identifier to corresponding instance.

- `nextThreadId`: Identifier to be used for next `Thread` in `threadById`

- `threadEntryById`: Map `ThreadEntry` identifier to corresponding instance.

- `nextThreadEntry`: Identifier to be used for next in `ThreadEntry` in `threadEntryById`.

- `forumSudo`: `ForumSudoId` of forum sudo.

## Events

- `TopicCategoryCreated`: A topic category was introduced with a given identifier.
- `TopicCategoryDeleted`: A topic category, with a given identifier, was removed.
- `ThreadCreated`: A thread was created with a given identifier.
- `ThreadDeleted`: A thread was removed, with a given identifier, was removed.
- `PostAdded`: ...
- `EditPostText`: ...
- `PostDeleted`: ...

## Dispatchable Methods

### `create_category`

#### Payload

- `parentCategory`: blank if root, otherwise identifier of `TopicCategory`
- `title`: text title
- `description`: description text

#### Description

Adds a new `TopicCategory`.

#### Errors

- Bad signature
- Signature not matching `forumSudo`
- `parentCategory` does not exist
- `title` invalid
- `description` invalid

#### Side effects

##### Category created

###### Precondition

`NO_ERROR`

###### Side effect(s)

- `TopicCategoryById` extended with new `TopicCategory` under new unique identifier.
- `nextTopicCategoryId` updated

###### Event(s)

- `TopicCategoryCreated`

### `delete_category`

#### Payload

-  `topicCategoryId`: id of `TopicCategory` to remove.

#### Description

Deletes a `TopicCategory`.

#### Errors

- Bad signature
- Signature not matching `forumSudo`
- Subcategory not empty

#### Side effects

##### Category deleted

###### Precondition

`NO_ERROR`

###### Side effect(s)

- `TopicCategoryById` no longer has the value corresponding to key `topicCategoryId`

###### Event(s)

- `TopicCategoryDeleted`

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

##### [...]

###### Precondition

`NO_ERROR`

###### Side effect(s)

- ...

###### Event(s)

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

##### [...]

###### Precondition

`NO_ERROR`

###### Side effect(s)

- ...

###### Event(s)

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
