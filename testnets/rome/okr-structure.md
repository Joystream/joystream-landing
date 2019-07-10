
<!-- TOC START min:1 max:3 link:true asterisk:false update:true -->
- [Release OKRs](#release-okrs)
  - [Objective: `Launch Rome Network`](#objective-launch-rome-network)
    - [Dynamic Content Directory Implementation](#dynamic-content-directory-implementation)
    - [SSDN Improvement](#ssdn-improvement)
    - [Proposal System](#proposal-system)
    - [SSDN Benchmarking Tool](#ssdn-benchmarking-tool)
<!-- TOC END -->


# Release OKRs
## Objective: `Launch Rome Network`
- **Active from:** dd.mm.yy
- **KR Measurement Deadline**: 7-9 days after Rome launch (first weekday)
- **Tracked**: Every Monday
- **Tracking Manager**: Martin
- **Key Results**:
1. `Receive n suggestions for "Content Directory" for each schemas covering a variety of video, audio, and written media content categories`
  - [Tasks](#dynamic-content-directory-implementation) (Joystream/joystream/issue)
2. `Add tranches/groups to Colossus and <distributor-node>, with 3x coverage`
  - [Tasks](#ssdn-improvement) (Joystream/joystream/issue)
3. `Have the council approve 5 grants, 3 off-chain and 2 grants trough voting`
  - [Tasks](#proposal-system) (Joystream/joystream/issue)
4. `SSND Benchmarking tool, that allows, users to test: 1 config 2 capacity, conductor to test both group and actor: 3 capacity 4 response/uptime`
  - [Tasks](#ssdn-benchmarking-tool)

---

### Dynamic Content Directory Implementation
This issue is meant to track the progress of implementing and getting interaction and use of the dynamic content directory system

#### Specs
Responsible: `Mokhtar`
Each mark weighted (n/m)
- High level:
  - [ ] Explain the dynamic Content Directory system
- Low level:
  - [ ] Functionality
  - [ ] How a new schema will be introduced and approved
  - [ ] How the runtime will parse and handle the old, new, mixed, etc.
  - [ ] Pioneer Integration

#### Backend
Responsible: `Mokhtar`
Each mark weighted (n/m)
  - [ ] "MySQL like database"
  - [ ] Runtime module
  - [ ] Migration from current metadata to new schema based metadata
  - [ ] Migrate content from old to new schema
  - [ ] CLI tool to "make" them

#### Pioneer
Responsible: `Alex`
Each mark weighted (n/m)
  - [ ] Make Pioneer read the correct state
  - [ ] Add a dropdown/path to the various "live" schema types
  - [ ] Add a feature allowing content owner (and sudo) to migrate from "existing" metadata to schema `vN`
  - [ ] Add a feature allowing content owner (and sudo) to migrate from schema `vN` to schema `vN+1`
  - [ ] Create an tab inside `pioneer` where users/sudos can suggest new schemas? (Can be forum)

#### Community
Responsible: `Martin`
Each mark weighted (n/m)
  - [ ] Create a `v0` of the schema(s)
  - [ ] Helpdesk  
  - [ ] Incentivize community members to propose new version of schemas
  - [ ] Approve (and if necessary) sign/activate the new schema version

---

### SSDN Improvement
This issue is meant to track to progress of designing and implementing the new and improved Substrate Storage and Distribution Network (SSDN).

#### Specs
Responsible: `Bedeho and Mokhtar`
Each mark weighted (n/m)
- `Colossus:`
  - [ ] Tranches/groups
  - [ ] Typescript?
  - [ ] Allow them not to run nodes (connect to other websocket)?
  - [ ] Allow them to avoid hosting website (websocket)?  
  - [ ] ...
- `<distributor>:`
  - [ ] Tranches/groups
  - [ ] Typescript?
  - [ ] Allow them not to run nodes (connect to other websocket)?
  - [ ] Allow them to avoid hosting website (websocket)?  
  - [ ] ...
- Interaction (p2p)
  - [ ] `Colossus` - `<distributor>`
  - [ ] `Colossus` - `Pioneer`
  - [ ] `<distributor>` - `Pioneer`
  - [ ] [Benchmarking tool](#ssdn-benchmarking-tool)?
  - [ ] ...
- Runtime
  - [ ] Improve/replace `Actors` module
  - [ ] Add `<distributor>` module
  - [ ] Interaction/discovery
  - [ ] ...

#### Build
Responsible: `Bedeho and Mokhtar`
Each mark weighted (n/m)
- `Colossus`
  - [ ] Factor out `<distributor>` (to new repo)
  - [ ] Re-write in typescript
  - [ ] ..
- `<distributor>`
  - [ ]`<distributor>` repo
  - [ ] Re-write in typescript
  - [ ] ..
- Interaction
  - [ ] Interaction/discovery
  - [ ] Authentication
  - [ ] ..

#### Pioneer
Responsible: `Alex`
Each mark weighted (n/m)
  - [ ] Integrate new `Actors` module
  - [ ] Resolve new upload/download system
  - [ ] Runtime?
  - [ ] ..

#### Community
Responsible: `Martin`
Each mark weighted (n/m)
  - [ ] Incentivize new `Actor`
  - [ ] Helpdesk  
  - [ ] ..

---

### Proposal System
This issue is meant to track the progress of implementing and getting interaction for the new Proposal System allowing the council to control a community fund to distribute to worthy grants and bounties.

**Note** This is meant to expand upon the current WIP system of using the forum as stepping stone.

#### Specs
Responsible: `Bedeho`
Each mark weighted (n/m)
  - [ ] ...

#### Build
Responsible: `Alex and Bedeho`
Each mark weighted (n/m)
- Runtime
  - [ ] ..

#### Pioneer
Responsible: `Alex`
Each mark weighted (n/m)
  - [ ] Integration
  - [ ] ...


#### Community
Responsible: `Martin`
Each mark weighted (n/m)
  - [ ] Incentivize new informed voting
  - [ ] Incentivize proposals
  - [ ] ...

---

### SSDN Benchmarking Tool
This issue is meant to track the progress of implementing and the SSDN Benchmarking Tool.

#### Specs
Responsible: `Bedeho and Alex`
Each mark weighted (n/m)
  - [ ] ...

#### Functionality
Responsible: `Alex`
Each mark weighted (n/m)
- Live Benchmarking
  - [ ] Individual Storage Provider download capacity
  - [ ] System Storage Providers download capacity
  - [ ] Individual Storage Providers download capacity
  - [ ] System Storage Providers download capacity
  - [ ] Individual Distributor upload capacity
  - [ ] System Distributors upload capacity
  - [ ] Individual Distributor upload capacity
  - [ ] System Distributor upload capacity
- Test benchmarking and configuration
  - [ ] Verify individual Storage Provider setup and download/upload capacity before "activating" them
  - [ ] Verify individual Distributor setup and download/upload capacity before "activating" them

#### Monitoring
Responsible: `Martin and Alex`
Each mark weighted (n/m)
  - [ ] Make the tool usable for a future `Conductor`
  - [ ] Use the tool as a sudo `Conductor` placeholder
