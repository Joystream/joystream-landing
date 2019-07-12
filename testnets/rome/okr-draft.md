
<!-- TOC START min:1 max:3 link:true asterisk:false update:true -->
- [Release OKRs](#release-okrs)
  - [Objective: `Launch Rome Network`](#objective-launch-rome-network)
- [Rome KR-1: Dynamic Content Directory](#rome-kr-1-dynamic-content-directory)
  - [Tracking](#tracking)
    - [Specs](#specs)
    - [Backend and Runtime](#backend-and-runtime)
    - [Pioneer](#pioneer)
    - [Community](#community)
  - [Final Grading](#final-grading)
- [Rome KR-2: Generic Working Group Module](#rome-kr-2-generic-working-group-module)
  - [Tracking](#tracking-1)
    - [Specs](#specs-1)
    - [Backend and Runtime](#backend-and-runtime-1)
    - [Pioneer](#pioneer-1)
  - [Final Grading](#final-grading-1)
- [Rome KR-3: Advance SSDN](#rome-kr-3-advance-ssdn)
  - [Tracking](#tracking-2)
    - [Specs](#specs-2)
    - [Backend and Runtime](#backend-and-runtime-2)
    - [Pioneer](#pioneer-2)
    - [Community](#community-1)
  - [Final Grading](#final-grading-2)
- [Rome KR-4: Stress Test](#rome-kr-4-stress-test)
  - [Tracking](#tracking-3)
    - [Specs](#specs-3)
    - [Build](#build)
    - [Community](#community-2)
  - [Final Grading](#final-grading-3)
- [Rome KR-5: Community Fund Proposal System](#rome-kr-5-community-fund-proposal-system)
  - [Tracking](#tracking-4)
    - [Specs](#specs-4)
    - [Backend and Runtime](#backend-and-runtime-3)
    - [Pioneer](#pioneer-3)
    - [Community](#community-3)
  - [Final Grading](#final-grading-4)
<!-- TOC END -->

# Release OKRs
## Objective: `Launch Rome Network`
- **Active from:** dd.mm.yy
- **KR Measurement Deadline**: 10 days after Rome launch
- **Tracked**: Every Monday
- **Tracking Manager**: Martin
- **Key Results**:
1. `Receive 3x Content Directory Schema proposals for each (video, audio, ebook), where at least 1 is approved for each type`
  - [Rome KR-1: Dynamic Content Directory](#rome-kr-1-dynamic-content-directory) (Joystream/joystream/issue#n)
2. `Create a generic working group module, and implement it for the SSDN system`
  - [Rome KR-2: Generic Working Group Module](#rome-kr-2-generic-working-group-module) (Joystream/joystream/issue)
3. `Have 6x/2x replication for each content file for Colossus and Apollo respectively`
  - [Rome KR-3: Advance SSDN](#rome-kr-3-advance-ssdn) (Joystream/joystream/issue)
4. `Perform a stress test uploading 100 files/20GB in one hour, and download/play all content from 2 sources with 20min delay`
  - [Rome KR-3: Advance SSDN](#rome-kr-3-advance-ssdn) (Joystream/joystream/issue)
5. `Have the council approve 5 grants, 3 off-chain and 2 grants trough voting`
  - [Rome KR-5: Community Fund Proposal System](#rome-kr-5-community-fund-proposal-system) (Joystream/joystream/issue)
---

Issue for KR-1

# Rome KR-1: Dynamic Content Directory
This issue is meant to track the progress of implementing and getting interaction and use of the dynamic content directory system. The first part covers the weekly tracking, where all checkmarks have the same weight. The second part is the weighting for the final grading.

## Tracking

### Specs
@mnaamani is responsible UNO.

#### Documentation
- [ ] Explain the Dynamic Content Directory system at a high level.

#### Working Specs
- [ ] Functionality
- [ ] How a new schema will be introduced and approved
- [ ] How the runtime will parse and handle the old, new, mixed, etc.
- [ ] Pioneer Integration

### Backend and Runtime
@mnaamani is responsible UNO.

- [ ] Build generic runtime module that understands database structure
- [ ] CLI tool to create new schemas
- [ ] Migration of "old" state metadata to new `v.n.0` schema in genesis block (@bwhm)
- [ ] Allow content owner and `sudo` to migrate content from `v.n.m` to `v.n.m+a`
  (Should we make a Content Directory Sudo equivalent to Forum Sudo?)

### Pioneer
@siman is responsible UNO.
- [ ] Make pioneer compatible with new Dynamic Content Directory
- [ ] Rebuild Upload section to allow uploader to choose schema for uploads
- [ ] Allow content owner and `sudo` to migrate content from `v.n.m` to `v.n.m+a` in Pioneer
  (Should we make a Content Directory Sudo equivalent to Forum Sudo?)

### Community
@bwhm is responsible UNO.
- [ ] Make `v.n.0` schemas for Video, Audio and Ebook
- [ ] Helpdesk
- [ ] Incentivize community members to propose new version of schemas
- [ ] Approve (and if necessary) sign/activate the new schema version

## Final Grading

[Backend and Runtime](#backend-and-runtime)
@mnaamani
- All boxes have equal weighting
  - Weight: 0.4

Graded at Launch of Rome

[Pioneer](#pioneer)
@siman
- All boxes have equal weighting
  - Weight: 0.4

Graded at Launch of Rome

[Community](#community)
@Martin
- Receive 3 proposals for each schema type.
  - Weight: 0.1
- Approve 1 proposal for each schema type.
  - Weight: 0.1

Graded 10 days after launch of Rome

---

Issue for KR-2

# Rome KR-2: Generic Working Group Module
This issue is meant to track the progress of designing the new generic working group module, and implementing it for . The first part covers the weekly tracking, where all checkmarks have the same weight. The second part is the weighting for the final grading.

## Tracking

### Specs
@mnaamani is responsible UNO.

#### Documentation
- [ ] Explain the Generic Working Group Module
- [ ] Explain the SSDN Working Group Module

#### Working Specs
##### Generic
- [ ] Group lead role
- [ ] Stake (signup), Unstake
- [ ] Generic runtime
- [ ] Key structure

##### SSDN specific
- [ ] SSDN Working Group runtime


### Backend and Runtime
@mnaamani is responsible UNO.
##### Generic
- [ ] Build generic runtime working group module
- [ ] Implement triple key system similar to current staking module (but mapped to membership)

##### SSDN specific
- [ ] Implement it for the [SSDN](#rome-kr-3-advance-ssdn) roles
- [ ] Conductor tool that automatically assigns what Content each new applicant must get.
- [ ] Allow Conductor to manually override the script.

### Pioneer
@siman is responsible UNO.
- [ ] Replace current Actor module with new SSDN Working Group Module
- [ ] Imitate current staking Module for new SSDN Working Group Module
- [ ] Chain state querying for key mapping (?)

## Final Grading

[Specs](#specs-1)
@mnaamani
- Spec the [Generic Working Group Module](#generic)
- All boxes have equal weighting
  - Weight 0.1
- Spec the how the [SSDN Working Group](#ssdn-specific)
- All boxes have equal weighting
  - Weight 0.2

[Backend and Runtime](#backend-and-runtime-1)
@mnaamani
All boxes have equal weighting
- Build the the [Generic Working Group Module](#generic-1)
  - Weight: 0.1

All boxes have equal weighting
- Implement the new [SSDN Working Group](#ssdn-specific-1)
  - Weight: 0.3

[Pioneer](#pioneer-1)
@siman
All boxes have equal weighting
- Weight: 0.3

Graded at Launch of Rome


---

Issue for KR-3

# Rome KR-3: Advance SSDN
This issue is meant to track the progress of implementing and attracting users to the new advanced SSDN system. The first part covers the weekly tracking, where all checkmarks have the same weight. The second part is the weighting for the final grading.

## Tracking

### Specs
@mnaamani is responsible UNO.

#### Documentation
- [ ] Explain Apollo
- [ ] Explain Colossus
- [ ] Explain Conductor role

#### Working Specs

##### Apollo
@bedeho is responsible UNO.
- [ ] Runtime

##### Colossus
@mnaamani is responsible UNO.
- [ ] Runtime

##### Interaction
@mnaamani and @bedeho
  - [ ] `Colossus` - `Apollo`
  - [ ] `Colossus` - `Pioneer`
  - [ ] `Apollo` - `Pioneer`

### Backend and Runtime

#### Colossus
@mnaamani is responsible UNO.
- [ ] Make signup possible with CLI tools in `Colossus`

#### Apollo
@bedeho is responsible UNO.
- [ ] Make signup possible with CLI tools in and `Apollo` (@mokhtar)


### Pioneer
@mnaamani is responsible UNO.
- [ ] Update Discovery in Pioneer

### Community
@bwhm is responsible UNO.
- [ ] Incentivize new `Actors`
- [ ] Helpdesk
- [ ] Operate as Conductor

## Final Grading

[Backend and Runtime](#backend-and-runtime-2)
**Apollo**
@bedeho

**Colossus**
@mnaamani

Graded at Launch of Rome

[Pioneer](#pioneer-2)
@mnaamani
- All boxes have equal weighting
  - Weight: 0.2

Graded at Launch of Rome

[Community](#community-2)
@bwhm
- Maintain 6x replication for Storage Providers
  - Weight: 0.15
- Maintain 2x replication for Distributors
  - Weight: 0.15

From 48h after release until 10 days after release (including stress-tests).

---

Issue for KR-4

# Rome KR-4: Stress Test
This issue is meant to track the progress of building a benchmarking and stress testing tool, allowing us to verify the integrity of the SSDN system under high load. The first part covers the weekly tracking, where all checkmarks have the same weight. The second part is the weighting for the final grading.

## Tracking

### Specs
@bedeho and @siman
- [ ] Spec the SSDN benchmarking tool.

### Build
@siman
- [ ] Individual Storage Provider download capacity
- [ ] System Storage Providers download capacity
- [ ] Individual Storage Providers download capacity
- [ ] System Storage Providers download capacity
- [ ] Individual Distributor upload capacity
- [ ] System Distributors upload capacity
- [ ] Individual Distributor upload capacity
- [ ] System Distributor upload capacity

### Community
@bwhm is responsible UNO.
- [ ] Run the tool regularly as placeholder `Conductor`, to ensure role occupants have sufficient capacity
- [ ] Communicate, assist actors, and if necessary, adjust incentives
- [ ] Make a script, engage community, or manually upload/download required data

## Final Grading

[Build](#build)
@siman
- All boxes have equal weighting
  - Weight: 0.5

Graded at Launch of Rome

[Community](#community-3)
@Martin
- Successfully upload required data
  - Weight: 0.25
- Successfully download/play required data
  - Weight: 0.25  

Graded 10 days after launch of Rome

---

Issue for KR-5

# Rome KR-5: Community Fund Proposal System
This issue is meant to track the progress of implementing and getting interaction for the new Proposal System allowing the council to control a community fund to distribute to worthy grants and bounties.

**Note** This is meant to expand upon the current WIP system of using the forum as stepping stone.

## Tracking

### Specs
@x is responsible UNO.

#### Documentation
- [ ] Explain new proposal system and workflow (@bwhm)

#### Working Specs
@x is responsible UNO.
- [ ] Runtime

### Backend and Runtime
@x is responsible UNO.
- [ ] Runtime

### Pioneer
@siman is responsible UNO.
- [ ] Implement proposal system in Pioneer

### Community
@bwhm is responsible UNO.
- [ ] Design and communicate off-chain community fund, and voting system
- [ ] Communicate and explain how Rome shifts it to an on-chain system
- [ ] Incentivize grant application
- [ ] Incentivize informed council voting
- [ ] Monitor applications and communication

## Final Grading

[Backend and Runtime](#backend-and-runtime-3)
@x
- All boxes have equal weighting
  - Weight: 0.2

Graded at Launch of Rome

[Pioneer](#pioneer)
@siman
- All boxes have equal weighting
  - Weight: 0.2

Graded at Launch of Rome

[Community](#community)
@bwhm
**Off-chain**
- Receive >5 and accept >2 grant applications
  - Weight: 0.4

Graded at Launch of Rome
**On-chain**
- Receive >2 and accept >1 grant application
  - Weight: 0.2

Graded 10 days after launch of Rome
