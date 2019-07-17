# Table of contents

<!-- TOC START min:1 max:3 link:true asterisk:false update:true -->
- [Table of contents](#table-of-contents)
- [Planned Meetings](#planned-meetings)
  - [Release Plan Finalization Meeting](#release-plan-finalization-meeting)
    - [Agenda](#agenda)
    - [Minutes](#minutes)
  - [Release Checklist Meeting](#release-checklist-meeting)
    - [Agenda](#agenda-1)
    - [Minutes](#minutes-1)
  - [Lessons Learned](#lessons-learned)
    - [Agenda](#agenda-2)
    - [Minutes](#minutes-2)
- [Conducted Meetings](#conducted-meetings)
  - [Launch Meeting](#launch-meeting)
    - [Agenda](#agenda-3)
    - [Minutes](#minutes-3)
  - [User Stories Meeting](#user-stories-meeting)
    - [Agenda](#agenda-4)
    - [Minutes](#minutes-4)
<!-- TOC END -->

# Planned Meetings

## Release Plan Finalization Meeting

- **ID:** `Rome Release Plan Finalization Meeting`
- **Date:** `dd.mm.yy`
- **Starts:** `hh:mm GMT+2`
- **Scheduled Duration:** `min`
- **Venue:** `ZOOM`
- **Lead**: `NA`
- **Minutes**: `NA`
- **Participants**:
  - `name1`
  - ...

### Agenda
#### Item 1
...


### Minutes
**Started at:** `hh:mm GMT+2`
**Present:**
  - `name1`
  - ...

#### Item 1
...

**Other topics raised:**
...

**Ended at:** `hh:mm GMT+2`

---

## Release Checklist Meeting

- **ID:** `Rome Release Checklist Meeting`
- **Date:** `dd.mm.yy`
- **Starts:** `hh:mm GMT+2`
- **Scheduled Duration:** `min`
- **Venue:** `ZOOM`
- **Lead**: `NA`
- **Minutes**: `NA`
- **Participants**:
  - `name1`
  - ...

### Agenda
#### Item 1
1. Review the [Release Checklist](../../testnet#release-checklist) draft, and compare to the release plan.
2. Land a final Release Checklist, that contains all items, and sorted it in order of deployment.


### Minutes
**Started at:** `hh:mm GMT+2`
**Present:**
  - `name1`
  - ...

#### Item 1
...

**Other topics raised:**
...

**Ended at:** `hh:mm GMT+2`


---

## Lessons Learned

- **ID:** `Rome Lessons Learned`
- **Date:** `dd.mm.yy`
- **Starts:** `hh:mm GMT+2`
- **Scheduled Duration:** `min`
- **Venue:** `ZOOM`
- **Lead**: `NA`
- **Minutes**: `NA`
- **Participants**:
  - `name1`
  - ...

### Agenda
#### Item 1
...


### Minutes
**Started at:** `hh:mm GMT+2`
**Present:**
  - `name1`
  - ...

#### Item 1
...

**Other topics raised:**
...

**Ended at:** `hh:mm GMT+2`

# Conducted Meetings

## Launch Meeting

- **ID:** `Rome Launch Meeting`
- **Date:** `10.07.19`
- **Starts:** `11:30 GMT+2`
- **Scheduled Duration:** `45min`
- **Venue:** `ZOOM`
- **Lead**: `Martin`
- **Minutes**: `Martin`
- **Participants**:
  - `Alex`
  - `Bedeho`
  - `Martin`
  - `Mokhtar`

### Agenda
#### Item 1
Discuss draft Rome [release plan](../../testnets/rome).

#### Item 2
Discuss draft [release OKR](/okrs#release-okrs).

#### Item 3
Schedule [user stories meeting](#user-stories-meeting)

### Minutes
**Started at:** `11:30 GMT+2`
**Present:**
  - `Alex`
  - `Bedeho`
  - `Martin`
  - `Mokhtar`

#### Item 1
1. Went through the draft Release plan point by point
2. Points that were unclear, inaccurate, missing or wrong, was corrected or marked for change.

#### Item 2
1. Martin presented a draft OKR, with an emphasis on a proposed new way of making, tracking and grading the KRs using github issues, as discussed in the [Acropolis Lessons Learned Meeting](../acropolis#lessons-learned).
    - In practice, it meant breaking down each KR into tasks
    - The tasks would be sorted by the affected parties/repos, and a checkbox would accompany each task.
    - Each task could (optionally) be assigned a weighting, to get an objective tracking of the progress.
        - Each KR issue would also include an objective and pre-defined formulae for finally grading the KR. This would not necessarily be mapped to the same tasks.
    - Each Monday, all affected parties would have a meeting, evaluating progress and checking off completed tasks.
    - A summary of that weeks meeting, alongside a tracking grade, would be added as comment by the release manager.
    - This summary would be presented on the [Weekly All Hands](https://github.com/Joystream/joystream#monday-all-hands), which would be moved to Tuesday.

2. The general sentiment was that the concept seemed like an improvement in certain areas, but the presented draft was not sufficient to convince all attendees that it sufficiently addressed the problems with the old release OKR system.

3. Attendees shall present proposals to what the KRs should cover.


#### Item 3

This was not addresssed.

**Other topics raised:**
NA

**Ended at:** `15:00 GMT+2`

---

## User Stories Meeting

- **ID:** `Rome User Stories Meeting`
- **Date:** `16.07.19`
- **Starts:** `11:00 GMT+2`
- **Scheduled Duration:** `1h30min`
- **Venue:** `ZOOM`
- **Lead**: `Martin`
- **Minutes**: `Martin`
- **Participants**:
  - `Alex`
  - `Bedeho`
  - `Martin`
  - `Mokhtar`

### Agenda

Review and discuss Users Stories.
Note that during the meeting, it was decided to change the order of discussion due to time constraints. These changes are reflected below.

---

#### 1. General Signup

NB1: provider refers to either storage provider or distributor.

NB2: These stories are kind of hand wavy. Many of the stories may be better suited off chain, e.g. coordinated through a server run by conductor. But it remains to be seen.

##### As a prospective provider I want to
- see terms associated with existing providers roles
- see terms associated with open positions for new roles
- apply to an open position with one click
- one click download each auto generated key (stash, controller, session) for each role applied to
- get notified if accepted into a position
- see list of all positions I have occupied now and prior, and corresponding payouts, and circumstances of leaving.
- get notified if slashed
- get notified if evicted
- leave a role



##### As a Conductor I want to
- add an open position with given terms
- close an open position
- slash a provider from a position
- evict a provider from a position
- get in touch with a provider out of band
- add obligation to provider
- remove obligation from provider
- quickly determine if a new accepted provider is correctly configured

---

#### 2. Apollo

##### As a prospective provider I want to
- start Apollo with given keys
- stop Apollo
- see Apollo session status of node
- see Apollo recent usage log

---

#### 3. Colossus

##### As a node operator I should be able to:
- (Stake) Configure and enter storage role entirely from the command line, in an interactive process, where only essential secret keys are required on the node running the storage node software.
- (Unstake) leave the role easily without loosing access to staked (stash) keys
- Re-enter the role after unstaking without overwriting old staking keys
- Get status of my node:
  - Sync status, IPNS publishing status. Total storage consumed...
- Get usage stats:
   - number of objects served/uploaded, total data transferred
- Check if there is a version update available
- Enter a test mode - non operational mode for testing setup and configuration
- Configure a remote IPFS node to use
- Configure a remote endpoint as joystream full node
- Gracefully shutdown node

##### The node itself should:
- Not enter operational status until chain is fully synced
- Synchronize data objects over IPFS from other storage providers
- Provide a REST API for receiving new data objects from publishers, and accepting transfers to distributors nodes
- Provide a REST API for service resolution

---

#### 4. Content Directory

These stories describe functionality of a general purpose Versioned Object Database system upon which the content directory for the platform will be constructed.

##### As system sudo I can:
- create a new `class group` x1
- assign a `class group` sudo
- have same permissions as class group sudo

##### As `class group` sudo I can:
- create a new Class
- create a new Entity of an existing Class in my group
- create a new Schema for a Class in my group, supporting use of an Object Property type that can map to a DataObjectID, of a specific DataObjectFamily from the Data Directory
- create a new object of a specific schema for an existing Entity in my class group.
- update the object properties of any object in my class group

##### Any user of the platform can:
- get a list of all classes, and entities
- for each class get all its entities
- for each entity get all versions of its object representation

x1 - A `class group` is a logical grouping of Classes. It allows for segmenting the database and assigning different sudo accounts for different groups. A class group sudo can only create new classes and entities, under their group.

Assume Database has following structure:
Classes: `["Podcast", "PodcastTheme", "Episode", "Person"]`
Schemas:
```
Podcast {
  name: varchar(30),
  host: Internal(Person),
  // themes: Array(PodcastTheme) // array propertytype is not yet in spec
  theme: PodcastCategory // might be limiting if a show fits in multiple categories
}

PodcastTheme {
  name: varchar(30),
}

Person {
  memberId: Option<External("Membership", 0)>,
  email: varchar(150),
}

Episode {
   podcast: Internal(Podcast),
   title: varchar(50),
   guest: Internal(Person), // Array ? guests
   track: External("DataDirectory", DataObjectFamilyId = 0)
}
```

##### In Pioneer a user should be able to:
- browse list of `Podcast`s,
- Sort podcasts by `Theme` or show host,
- select a podcast and get a list of all `Episode`s
- find episodes (from different shows) on which a guest appeared

Should have similar stories for a `Movie` and associated classes. (Final list of content types to include in Rome is TBD)

##### Stretch Goal
- In Pioneer, anyone can use a tool to create a  *simple text formatted* description of a schema.
- Sudo can use a command line tool to build an extrinsic that can create a new schema for a class.

Instead of Arrays (eg. to add all guests that appeared on a show), we can have create a Class:
```
PodcastGuestAppearance {
  episode: Internal(Episode),
  guest: Internal(Person)
}
```

---


#### 5. Community Fund Proposal System

##### As a platform member and stakeholder, I want
- a community fund of real money.
- to be able to make proposals and apply for grants.
- to be able to propose competitions, and get paid to arrange them.
- to be able to participate in competitions and win real money.
- to be able to propose increasing participation payouts.
- a forum category to discuss and evaluate proposals.
- insight on what Council Members thinks about proposals.

##### As a Council Member candidate, I want
- to communicate to stakeholders how I would allocate the resources as part of my campaign.
- show my constituency that I want to support their cause as part of my campaign.
- show that I can make good proposals that would help build the community.
- show that I can evaluate, improve and find flaws in other proposals.

##### As a Council Member, I want
- all of the above.
- the ability to vote and allocate the funds.

---

### Minutes
**Started at:** `11:00 GMT+2`
**Present:**
  - `Alex`
  - `Bedeho`
  - `Martin`
  - `Mokhtar`

**Note** All comments are in *italic*

---

#### Item 1

NB1: provider refers to either storage provider or distributor.

NB2: These stories are kind of hand wavy. Many of the stories may be better suited off chain, e.g. coordinated through a server run by conductor. But it remains to be seen.

##### As a prospective provider I want to
- see terms associated with existing providers roles
- see terms associated with open positions for new roles
- apply to an open position with one click
- leave a role

*It was decided to make the general `actor/working group` signup module small and generic. As a consequence, a lot of this will be off-chain. It was not resolved how much of this was going to be in Pioneer, and how to represent it.*


##### As a Conductor I want to
- add an open position with given terms
- close an open position
- slash a provider from a position *(without evicting, ie. only slash part of their stake)*
- evict a provider from a position
- add obligation to provider *(content)*
- remove obligation from provider *(content)*
- quickly determine if a new accepted provider is correctly configured

*As above: It was decided to make the general `actor/working group` signup module small and generic. As a consequence, a lot of this will be off-chain. It was not resolved how much of this was going to be in Pioneer, and how to represent it.*


##### Nice to haves
- one click download each auto generated key (stash, controller, session) for each role applied to
- get notified if accepted into a position *(email in node config was considered, or just wait for the chat system)*
- see list of all positions I have occupied now and prior, and corresponding payouts, and circumstances of leaving.
- get notified if slashed *(email in node config was considered, or just wait for the chat system)*
- get notified if evicted *(email in node config was considered, or just wait for the chat system)*
- get in touch with a provider out of band *(email in node config was considered, or just wait for the chat system)*

*These stories were removed from the the "must haves" to "nice to haves"*

---

#### Item 2

##### As a prospective provider I want to
- start Apollo with given keys *(ie. use a session key, similar to running a joystream full node)*
- stop Apollo
- see Apollo session status of node *(similar to what "helios" already does)*
- see Apollo recent usage log  *(This is/will be possible using the setup guide in helpdesk)*

---

#### Item 3

##### As a node operator I should be able to:
- Get status of my node:
  - Sync status, IPNS publishing status.  *("Total storage consumed..." was moved to nice to have)*
- Configure a remote IPFS node to use

##### The node itself should:
- Not enter operational status until chain is fully synced *(This refers to the joystream-node)*
- Synchronize data objects over IPFS from other storage providers
- Provide a REST API for receiving new data objects from publishers, and accepting transfers to distributors nodes
- Provide a REST API for service resolution

*The final three points are already existing functionality*

##### Nice to haves
- Check if there is a version update available
- Get usage stats:
   - number of objects served/uploaded, total data transferred
- Enter a test mode - non operational mode for testing setup and configuration *x*
- Configure a remote endpoint as joystream full node *x*
*x these two combined would mean users could test on a "reckless" testnet*
- Gracefully shutdown node *(Refers to announcing you are down for maintenance)*
- Get status of my node:
  - Total storage consumed...

*These stories were removed from the the "must haves" to "nice to haves"*

---

This was as far as we got on the first meeting. The remaining items will be addressed at a later date.

**Other topics raised:**

While going through items 1-3, a recurring topic was how much time and effort should be put into making the products user friendly, compared to the "quantity" and "quality" of users affected.

More specifically, should we optimize to make it easy for actors, that are well paid for a role, without actually risking anything (no "real" stake), or should we rather expect them to monitor communication channels and the status of their software. By making everything easily accessible in Pioneer, and adding new ways of communicating directly, we are adding a significant workload on ourselves.

**Ended at:** `12:30 GMT+2`

---

**Day two:**
**Started at:** `17.07.19 - 09:00 GMT+2`
**Present:**
  - `Alex`
  - `Bedeho`
  - `Martin`
  - `Mokhtar`

---

#### Item 4

These stories describe functionality of a general purpose Versioned Object Database system upon which the content directory for the platform will be constructed.

##### As system sudo I can:
- create a new `content directory sudo`
- assign a `content directory sudo`

 *implement group permission in a separate module*

##### As `content directory sudo` I can:
- create a new Class
- create a new Entity of an existing Class in my group
- create a new Schema for a Class, supporting use of an Object Property type that can map to a DataObjectID, of a specific DataObjectFamily from the Data Directory
- create a new object of a specific schema for an existing Entity
- update the object properties of any object
- use a command line tool or the extrinsics app from pioneer to send a tx and create a new schema for a class.

*The final point was moved from nice to haves, as there has to be some way of making these. Whether the first implementation should be done via, extrinsics in pioneer or a standalone CLI, is TBD*

##### Any user of the platform can use Pioneer to:
- get a list of all classes, and entities
- for each class get all its entities
- for each entity get all versions of its object representation

*It was not settled whether this should be via "regular" chain state queries, or a new x*

##### As an uploader I can:
- create a subset of Entities and Objects which the permissions module will limit to Members
- update a subset of Entities and Objects which permissions module will limit to content owner

*Added so that uploaders can actually add metadata (such as "title" and "description" without extra permissions)*

Assume Database has following structure:
Classes: `["Podcast", "PodcastTheme", "Episode", "Person"]`
Schemas:
```
Podcast {
  name: varchar(30),
  host: Internal(Person),
  // themes: Array(PodcastTheme) // array propertytype is not yet in spec
  theme: PodcastCategory // might be limiting if a show fits in multiple categories
}

PodcastTheme {
  name: varchar(30),
}

Person {
  memberId: Option<External("Membership", 0)>,
  email: varchar(150),
}

Episode {
   podcast: Internal(Podcast),
   title: varchar(50),
   guest: Internal(Person), // Array ? guests
   track: External("DataDirectory", DataObjectFamilyId = 0)
}
```

##### In Pioneer a user should be able to:
- browse list of `Podcast`s, *(example)*
- Sort podcasts by `Theme` or show host,
- select a podcast and get a list of all `Episode`s
- find episodes (from different shows) on which a guest appeared

Should have similar stories for a `Movie` and associated classes. (Final list of content types to include in Rome is TBD)

*The representation of this in pioneer is very much a WIP still*

---

#### Item 5

Not addressed yet.

---


**Ended at:** `11:15 GMT+2`
