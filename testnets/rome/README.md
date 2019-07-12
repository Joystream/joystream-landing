
<img src="img/rome-cover.svg"/>

<div align="center">
  <h3>
    <a href="specification/README.md">
      Specification
    </a>
  </h3>
</div>

# Table of contents
<!-- TOC START min:1 max:3 link:true asterisk:false update:true -->
- [Table of contents](#table-of-contents)
- [Overview](#overview)
  - [Live Milestones](#live-milestones)
  - [Actual dates:](#actual-dates)
- [Past Release Meetings](#past-release-meetings)
- [Specification](#specification)
- [GitHub Projects](#github-projects)
- [OKR results](#okr-results)
- [Release Plan](#release-plan)
  - [Name](#name)
  - [Manager](#manager)
  - [Release Date](#release-date)
  - [OKRs](#okrs)
- [Release OKRs](#release-okrs)
    - [Objective: `Launch Rome Network`](#objective-launch-rome-network)
  - [Constraints](#constraints)
  - [Risks](#risks)
  - [Deployment](#deployment)
  - [Products](#products)
    - [Runtime](#runtime)
    - [Full node](#full-node)
    - [Colossus](#colossus)
    - [Apollo](#apollo)
    - [Pioneer](#pioneer)
  - [Milestones](#milestones)
    - [Rome Announced](#rome-announced)
    - [Spec Draft](#spec-draft)
    - [Spec Release](#spec-release)
    - [Sub-system Test](#sub-system-test)
    - [Final Test](#final-test)
    - [Launch Ready](#launch-ready)
    - [Release Checklist Verification](#release-checklist-verification)
    - [Release](#release)
  - [Go-To-Market](#go-to-market)
    - [Communications](#communications)
    - [Website](#website)
    - [Guides](#guides)
    - [Public Tools and Infrastructure](#public-tools-and-infrastructure)
    - [Internal Tools and Infrastructure](#internal-tools-and-infrastructure)
  - [Internal Operations](#internal-operations)
    - [Testnet Incentive Payouts](#testnet-incentive-payouts)
    - [Support](#support)
<!-- TOC END -->

# Overview

**Draft**

For every new release, we produce a new release plan following the formulae outlined [here](/#testnet-planning). Once merged, everything below [this section](#release-plan) will not be amended, with the exception of trivial things like broken links, spelling mistakes, etc.

## Live Milestones

Although we always aim to follow the planned [milestones](#milestones), experience has shown that we will often have to re-evaluate them in flight. If that happens, this section will be updated to reflect the changes, instead of changing the "original" ones.

## Actual dates:

Once we have reached a [milestones](#milestones), an entry will be made below, with comments if applicable.


# Past Release Meetings

| Name/category               | Date      | Agenda and Minutes                                          |
| --------------------------- | :--------:|:--------------------------------------------------------------:|
| Launch Meeting              | 10.07.19  | [link](../../meetings/rome#launch-meeting)                     |
| User Stories                | 16.07.19  | [link](../../meetings/rome#user-stories-meeting)               |
<!--
| Release Plan Finalization   | dd.mm.19  | [link](../../meetings/rome#release-plan-finalization-meeting)  |
| Release Checklist Meeting   | dd.mm.19  | [link](../../meetings/rome#release-checklist-meeting)          |
| Lessons Learned             | dd.mm.19  | [link](../../meetings/rome/#lessons-learned)                   |
-->

#  Specification

TBD

# GitHub Projects

After the [Acropolis Lessons Learned Meeting](/meetings/acropolis#lessons-learned), we decided to change our approach to how we organize the release projects.
- For Athens and the beginning of Acropolis we planned on making `issues` for each task related to the testnet in its applicable repo, and then adding them to the release project.
- For Rome, we will instead `issues` tied to a specific KR, with a high level description of tasks. Each task will be represented by a checkmark, and if applicable, include a link to an `issue` in the repo describing the task with more granularity.
- Each Monday, the affected personnel/group will go through the list with the Release Manager, discuss progress/problems/solutions, and check off boxes as they are completed.
- A summary of each of these meetings will be added as a comment that also includes the tracking score, and presented in the Tuesday all hands meeting.
- The project may also include competitions tied to the release, despite not formally tied to the [Release OKR](#okr)

The project for the Rome Release can be found [here](https://github.com/orgs/Joystream/projects/9).

# OKR results

This section will be only include the final grading after network release. In the meantime, you can track the progress [here](/okrs#release-okrs).


# Release Plan

**Draft**
**This plan was made in advance, and anything below this line will not be updated inspite of changing circumstances.**


## Name

`Rome`

## Manager

`Martin`

## Release Date

06.11.19, 12:00 (GMT+2)

## OKRs

# Release OKRs
### Objective: `Launch Rome Network`
- **Active from:** dd.mm.yy
- **KR Measurement Deadline**: 7-9 days after Rome launch (first weekday)
- **Tracked**: Every Monday
- **Tracking Manager**: Martin
- **Key Results**:
[Link to Draft](testnets/rome/okr-draft.md)


Go [here](/okrs#release-okrs) for tracking.

## Constraints

1. Team size

## Risks

1. In general, a large release means it's difficult to set realistic [milestones](#milestones).
2. At the time of writing, there are still many details unresolved, increasing the risk noted in `1.`.
3. Hiring new people at an early stage, means either:
    - Assigning them to already established goals (hopefully leading to less work/person)
    - Sending them to work on sideprojects unrelated to the release (thus diverting resources)
    - Adding more meat to the release (thus not following the release plan)
4. Critical bugs found in the substrate node template version we are using, forcing us to pull from upstream.
    - This may require significant extra work.
5. The summer holiday may impact the ability to coordinate properly during the initial stages of the release.

## Deployment

Start a fresh chain, (built from a more recent version of the [substrate](https://github.com/paritytech/substrate) node template).
**Transferring of the following:**

- Memberships
- Forum posts
- Media Content

All `keys` stored locally in the browser of each user will still work (though the balance will not be transferred).
In practice, this means all `keys` associated with a `member` will still have the following qualities:

- `forum` posts can still be edited by the `member` that made the post.
- `content` uploaders will still be able to use their keys to edit `metadata` of their uploaded content.

All `keys` tied to a `Membership` will start with a small balance to allow them to post on the `forum` and upload `content`.

## Products

The following public products will be part of this release.

### Runtime
---
- **Description:** Runtime for the Joystream full node
- **Manager:** **Mokhtar**
- **Core Team:**
  - **Mokhtar:** Developer
  - **Alex:** Developer
  - **Bedeho:** Developer
  - **Martin:** Testing
- **Main repo:** [substrate-runtime-joystream](https://github.com/Joystream/substrate-runtime-joystream)
- **Current version:** `v5.4.0` (any in flight ugrades will be versioned `v5.5+n.0`)
- **New version:** target `v6.0.0`
- **Audit:** No
- **Documentation:** Publish the rust docs for the runtime at testnet.joystream.org/runtime-docs/ *delete/fill in*
- **Legal Review/ToS update:** No
- **Build/CI system:**
  - **Mokhtar:**
    * CI: Simple travis job for PRs, running cargo tests, and verifying build doesn't fail and rustfmt is used to format code *delete/fill in*
    * Build: Will have a working Docker file for building proposed WASM runtime blob
- **New/Altered Functionality:**
    * Improvements to forum module (*delete/fill in*)
    * Updated Actors module, thus changing the signup process and `key` management
    * Updated Storage modules to support storage tranches
    * Separate the [storage](#colossus) and [distribution](#apollo) role
    * Re-write and migrate the content directory
    * Cleanup old migration code in members module (Mokhtar) (*delete/fill in*)
    * Add a new proposal type.
- **Refactor/Reorganization:**
  * Best effort should be made to make new and refactored runtime modules as separate git repos
  * Existing modules can remain in same repo
- **Deployment/Distribution:**
  * Build a new runtime, included in the [Full node binaries](#full-node)

### Full node
---
- **Description:** Joystream full node
- **Manager:** **Mokhtar**
- **Core Team:**
  - **Mokhtar:** Developer
  - **Martin:** Testing
- **Main repo:** [substrate-node-joystream](https://github.com/Joystream/substrate-node-joystream)
- **Current version:** `v1.0.0`
- **New version:** target `v1.0.1` OR `v1.1.0` (pending pulling from upstream or not)
- **Audit:** No
- **Documentation:** No
- **Legal Review/ToS update:** No
- **Build/CI system:**
  - **Mokhtar:**
    * CI: Simple travis job for PRs, running cargo tests, and verifying build doesn't fail and rustfmt is used to format code *delete/fill in*
    * Repo (and Docker?) *fill in*
- **New/Altered Functionality:**
    * New genesis block
- **Deployment/Distribution:**
    * Tag new release

### Colossus
---

- **Description:** Storage node (no longer storage AND distribution)
- **Manager:** **Mokhtar**
- **Team:**
  - **Mokhtar:** Developer
  - **Bedeho:** Review
  - **Martin:** Testing
- **Main repo:** [storage-node-joystream](https://github.com/Joystream/storage-node-joystream) *change name/fill in*
- **Current version:** 0.2.0 (TBD, start tagging release of current node?) *fill in*
- **New version:** 0.3.0 *fill in*
- **Audit:** No
- **Documentation:**
  * [README](https://github.com/Joystream/storage-node-joystream/blob/master/README.md)
  * [Released API specs](-) *fill in*
- **Legal Review/ToS update:** No *add to repo*
- **Build/CI system:**
  - **Mokhtar**
    * CI: Simple travis job, running unit tests.
    * Add more unit test
- **Target Platforms:** Linux
- **New/Altered Functionality:**
  - Support storage groups. The main difference is to stake for joining a group rather than the storage provider role.
  - New signup process (actors module)
  - Authenticate (?) and connect to `Distributors` *fill in*
  - Rewrite in typescript (*delete/fill in*)
  - Run in testmode *fill in*
  - No longer contain the `Distributor` side of the software. *fill in*
- **Nice to have:**
  * Run in testmode *fill in*
- **New Key User Stories:**
  * *fill in*
- **Deployment/Distribution:**
  * *fill in*

### Apollo
[Apollo](https://en.wikipedia.org/wiki/Apollo)

- **Description:** Distributor node
- **Manager:** Bedeho
- **Team:**
  - **Bedeho:** Developer
  - **Mokhtar:** Reviewer
  - **Martin:** Testing
- **Main repo:** [distributor-node-joystream](https://github.com/Joystream/distributor-node-joystream) *fill in*
- **Current version:** -
- **New version:** `0.1.0`
- **Audit:** No
- **Documentation:**
  * [README](https://github.com/Joystream/distributor-node-joystream/blob/master/README.md) *fill in*
  * [Released API specs](-) *delete/fill in*
- **Legal Review/ToS update:** Same as [Colossus](#colossus) *add to repo*
- **Build/CI system:**
  * CI: Simple travis job, running unit tests.
- **Target Platforms:** Linux
- **New/Altered Functionality:**
  * Authenticate and connect to `Storage nodes`
  * ... *fill in*
- **Nice to have:**
  * Run in testmode *fill in*
- **New Key User Stories:**
  * *fill in*
- **Deployment/Distribution:**
  * *fill in*

### Pioneer
---

 - **Description:** The user interface for interacting with the platform.
 - **Manager:** Alex
 - **Team:**
    - **Alex:** Developer
    - **Mokhtar:** Developer
    - **Martin:** Testing
 - **Main repo:** [apps](https://github.com/Joystream/apps) *renmae to pioneer*
 - **Current version:** N/A
 - **New version:** `0.5.0`
   - `0.1.x` - goes to Polka Apps.
   - `0.2.x` - Sparta.
   - `0.3.x` - Athens
   - `0.4.x` - Acropolis
    - *Not sure we actually need to tag releases for `pioneer` as it is meant as a more dynamic. For me, I would be happy just showing the hash of the latest commit*
    - *fill in*
 - **Audit:** No
 - **Documentation:** No
 - **Legal Review/ToS update:** No. License to be added to migrated Repo. *delete/fill in*
 - **Build/CI system:** Yes
 - **Target Platforms:** Cross-platform and cross-browser.
 - **New/Altered Functionality**:
    - Integration with new Substrate Storage and Distribution Network (SSDN)
    - New Working Group `*` module integration
    - Support new proposal type
    - *fill in*
    - Support dynamic content directory
      - Landing page
      - Improve forum
      - Sidebar *fill in*
 - **New Key User Stories:**
  - *fill in*
 - **Deployment/Distribution:**
    - Upgrade of [hosted](#hosted-joystream-pioneer) Pioneer must be timed with release for integration with new storage system, distributor system, and proposals.
    - Frequent non-breaking improvements/updates performed expected.


## Milestones

| Date     |   Event                                                |     Involved                   |
| :-------:|:------------------------------------------------------:|:------------------------------:|
| 19.07.19 | [Rome Announced](#rome-announced)                      |  Martin, Bedeho, Elpassion     |
| 26.07.19 | [Spec Draft](#spec-draft)                              |  Alex, Bedeho, Mokhtar         |
| 13.08.19 | [Spec Release](#spec-release)                          |  Alex, Bedeho, Mokhtar         |
| dd.mm.19 | [n](-)                                                 |   -                            |
| dd.mm.19 | [n](-)                                                 |   -                            |
| 19.10.19 | [Sub-system Test Checklist](#sub-system-test-checklist)| All                            |
| 21.10.19 | [Sub-system Test](#sub-system-test)                    | All                            |
| 26.10.19 | [Final Test Checklist](#final-test-checklist)          | All                            |
| 28.10.19 | [Final Test](#final-test)                              | Martin, Mokhtar + 3x testers   |
| 01.11.19 | [Launch Ready](#launch-ready)                          | All                            |
| 05.11.19 | [Release Checklist](#release-checklist)                | All                            |
| 06.11.19 | [Release](#release)                                    | All                            |
**Rename `spec`**

### Rome Announced

- **Description:** Announce the Rome upcoming testnet, with release plan and theme, and website update.
- **Manager:** **Martin**
- **Team:**
  - **Martin:**
  - **Bedeho:**
  - **Elpassion:**
- **Tasks:**
  - Finalize the logomark for Rome
  - Publish blog post outlining the goals for Rome
  - Newsletter outlining the goals for Rome
  - Update the (webflow) website with "next testnet section"

### Spec Draft

- **Description:** Create and mark for review, a PR for the Rome specs
- **Manager:** **Bedeho**
- **Team:**
  - **Mokhtar:**
  - **Bedeho:**
  - **Alex:**
- **Tasks:**
  - The person or group assigned to produce the specs, must open the PR at this date.
  - Each team of writer/reviewer must coordinate to ensure a reasonable time window to implement changes and get approval

### Spec Release

- **Description:** Release/merge the PR for the Rome specs
- **Manager:** **Bedeho**
- **Team:**
  - **Mokhtar:**
  - **Bedeho:**
  - **Alex:**
- **Tasks:**
  - Assuming the time line for the [Working Spec Draft](#working-spec-draft) has been upheld, the PR must be merged at this date.

### Sub-system Test Checklist
- **Description:** Checklist for Sub-System Test
- **Manager:** **Martin**
- **Team:**
  - **All:**
- **Tasks:**
  - Finalize a [checklist](checklists#sub-system-test-checklist) of what needs to be tested for the Sub-System Test

### Sub-system Test

- **Description:** Test all sub-systems/software separately on the [`staging-reckless`](#staging-testnets) testnet(s)
- **Manager:** **Martin**
- **Storage Team Lead:**
  - **Mokhtar:**
- **Distributor Team Lead:**
  - **Bedeho:**
- **SSDN Leads:**
  - **Mokhtar and Bedeho:**
- **Proposal Team Lead:**
  - *TBD*
- **Test specification:**
  * [Checklist](checklists#sub-system-test-checklist)
  * The members of each **Team** must be able present full functionality of their sub-systems/software, in the following environment:
    1. Build a runtime that contains all modules needed to properly test the functionality of all new features and software in each sub-system.
        * It's a preference, but not a requirement, for the same runtime to be used for both tests.
    2. Working branch of Pioneer, that has full compatibility with the runtime.
    3. Supporting software and tools
    4. if applicable, present clear list of items outstanding with:
        * dependencies / responsible person(s)
        * realistic timeline
        * what, if any, should be postponed/abandoned for late release or next release.
        * note that both RM and developer are responsible for this list not coming as a surprise.


**Note** After this test, only bugfix PRs can be merged to master branch of relevant repos.

### Final Test Checklist
- **Description:** Checklist for Final Test
- **Manager:** **Martin**
- **Team:**
  - **All:**
- **Tasks:**
  - Finalize a [checklist](checklists#final-test-checklist) of what needs to be tested for the Final Test

### Final Test

- **Description:** Upgrade the [`staging-lts`](#staging-testnets) testnet runtime to "Rome", and perform a full feature test.
- **Manager:** **Mokhtar**
- **Team:**
  - **Martin:** Lead tester
  - **Community Member 1:** Tester
  - **Community Member 2:** Tester
  - **Community Member 3:** Tester
  - **On call:** All team members must be available to assist when needed.
- **Test specification:**
  * All software must run from `development` branch in each repo, with no open PRs meant for Rome (Pioneer excluded)
  1. Build a [full node](#full-node) binary for Linux, Mac OS and Windows *RBP and docker?*
  2. Use `staging-lts` as bootnode and host for [Pioneer](#pioneer)
  3. Deploy [full nodes](#full-node) locally on Mac *and RBP* and windows (azure)
  4. Deploy multiple instances of [Colossus](#colossus) and [Apollo](#apollo).
  5. Follow [Checklist](checklists#final-test-checklist)

### Launch Ready

- **Description:** Prepare and finalize **all** communications, website, guides and infrastructure.
- **Manager:** **Martin**
- **Team:**
  - **Martin:** Manager/author/devops
  - **Bedeho:** ElPassion Manager
  - **Tomasz:** Designer
  - **Mokhtar:** Developer/devops
  - **Alex:** Developer
- **Tasks:**
  - **Note:** In case all this can not be completed in time, the Manager is responsible to prioritize correctly.
  * [Communications](#communications)
  * [Website](#website)
  * [Guides](#guides)
  * [Public Tools and Infrastructure](#public-tools-and-infrastructure)
    * [Hosted Pioneer](#hosted-pioneer)
    * [Faucet Frontend](#faucet-frontend)
    * [Bootnodes](#bootnodes)
    * [Status Server](#status-server)
    * [Hosted Storage Node](#hosted-storage-node)
    * [Hosted Distributor Node](#hosted-distributor-node)
    * [Content Schema Tool](-) *fill in*
  * [Internal Tools and Infrastructure](#internal-tools-and-infrastructure)
    * [Faucet Backend](#faucet-backend)
    * [Payout Scripts](#payout-scripts)
    * [Endpoint Selector](#endpoint-selector)
    * [Staging Testnets](#staging-testnets)
    * [SSDN Benchmarking tool](#ssdn-benchmarking-tool)
- **Timeline:**
  * At this point, everything *should* be written and ready for deployment
  * Dates and details for actual deployment can be found in the links above
    * Some of these might be necessary to prepare before the date in [milestones](#milestones)

### Release Checklist Verification
- **Description:** Following the [Release Checklist Meeting](../../meetings/rome#release-checklist-meeting)
- **Manager:** **Martin**
- **Team:**
  - **Martin:** Manager
  - **All:** Verifiers
- **Tasks:**
  * Go through the [Release Checklist](checklists#release-checklist), and verify all points are completed and/or deployed.


### Release
- **Description:** Launch and deploy all necessary nodes/tools/infrastructure
- **Manager:** **Martin**
- **Team:**
  - **Martin:** Devops
  - **Mokhtar:** Devops
- **Tasks:**
  * Go through the [Release Checklist](checklists#release-checklist), and verify they are deployed in the correct order.

---

## Go-To-Market

### Communications

- **Description:** List of all public communication to be prepared:
- **Manager:** **Martin**
- **Team:**
  - **Martin:** Manager/Author
  - **Bedeho:** ElPassion Manager/Reviewer
  - **ElPassion:** Designer
- **Tasks:**
    - **Rome Incentive System**
      - Publish a blog post with information about the Rome testnet
        1. Roles (`Validators`, `Council Members`, `Storage Providers`, `Distributors`, ...?)
        2. Participation incentives
        3. Link to [Guides](#guides)
      - Publication date: 01.11.19
    - **Roles Newsletter**
      - Publish newsletters for with updates for all roles affected by the Rome testnet
        1. Roles (`Validators`, `Council Members`, `Storage Providers`, `Distributors`, ...?)
        2. Participation incentives
        3. Link to [Guides](#guides)
      - Publication date: 01.11.19
    - **Coordinating with web3/parity**
      - Coordinate release PR campaign with above.
    - **Rome Released**
      - Publish a blog post announcing the release of Rome
        1. Link to proposal and/or launch date/time.
        2. Point to old posts for reminders.
      - Publication date: 04.11.19
    - **Rome Released**
      - Send "main" newsletter
        1. Link to proposal and/or launch date/time.
        2. Point to old posts for reminders.
      - Publication date: 04.11.19

### Website
- **Description:** Finalize website for the new release
- **Deadline:** 01.11.19
- **Manager:** **Bedeho**
- **Team:**
  - **Bedeho:** Manager
  - **ElPassion:** Designer
  - **Martin:** Devops
- **Deployment:**
  - Github repo replacing webflow
- **Tasks:**
  - Update all images and links to reflect the new testnet
  - Update all scripts
  - Test for responsiveness

### Guides

- **Description:** Update all guides to reflect how to operate each role
- **Manager:** **Martin**
- **Team:**
  - **Martin:** Manager
  - **Community Member 1:** Author/Reviewer
  - **Community Member 2:** Author/Reviewer
  - **Community Member 3:** Author/Reviewer
  - **ElPassion:** Designer
- **Tasks:**
  - Update all guides and links on the [helpdesk repo](https://github.com/JoyStream/helpdesk) and [forum](https://testnet.joystream.org/acropolis/pioneer/#/forum)


### Public Tools and Infrastructure

- **Description:** Make and/or update all public tools
- **Manager:** **Martin**
- **Tasks:**
  - Follow up on development, maintenance and deadlines

#### Hosted Pioneer
- **Description:** Host a version of Joystream Pioneer on testnet.joystream.org
- **Manager:** **Mokhtar**
- **Repo:** [apps](https://github.com/Joystream/apps) joystream branch
- **Team:**
  - **Mokhtar:** Manager/Devops
  - **Alex:** Developer
  - **Martin:** Devops
- **Tasks:**
  - Update Caddy file to redirect
  - Setup Cloudflare/load balancing hosting (?)
  - Deploy [Endpoint Selector](#endpoint-selector)
  - Ensure proper deployment after upgrade (if applicable)
    - See [Acropolis Lessons Learned](https://github.com/Joystream/joystream/blob/master/meetings/acropolis/README.md#minutes-4) (Item 5, point 5).

#### Faucet Frontend
- **Description:** Host the faucet frontend
- **Manager:** **Mokhtar**
- **Repo:** Private
- **Team:**
  - **Mokhtar:** Manager/Devops
  - **Elpassion:** Designer
- **Tasks:**
  - Improve design with new branding
  - Improve README.md

#### Bootnodes
- **Description:** Hosting of network bootnodes
- **Manager:** **Mokhtar**
- **Repo:** [substrate-node-joystream](https://github.com/Joystream/substrate-node-joystream)
- **Team:**
  - **Mokhtar:** Manager/Devops
  - **Martin:** Devops
- **Tasks:**
  - Upgrade nodes (if applicable)
  - Update Caddy file to redirect
  - Setup Cloudflare/load balancing hosting (?)

#### Status Server
- **Description:** Status server for live stats (on website)
- **Manager:** **Martin**
- **Repo:** [status-endpoint-joystream](https://github.com/Joystream/status-endpoint-joystream)
- **Team:**
  - **Martin:** Manager/Developer
- **Tasks:**
  - Add new stats of interest
  - Maintainance


#### Hosted Storage Node
- **Description:** Hosting of storage node
- **Manager:** **Mokhtar**
- **Repo:** [storage-node-joystream](https://github.com/Joystream/storage-node-joystream)
- **Team:**
  - **Mokhtar:** Manager/Devops
  - **Martin:** Devops
- **Tasks:**
  - Upgrade nodes (if applicable)
  - Update Caddy file to redirect

#### Hosted Distributor Node
- **Description:** Hosting of storage node
- **Manager:** **Mokhtar**
- **Repo:** [distributor-node-joystream](https://github.com/Joystream/distributor-node-joystream)
- **Team:**
  - **Mokhtar:** Manager/Devops
  - **Martin:** Devops
- **Tasks:**
  - Upgrade nodes (if applicable)
  - Update Caddy file to redirect

### Internal Tools and Infrastructure
- **Description:** Make and/or update all public tools
- **Manager:** **Martin**
- **Tasks:**
  - Follow up on development, maintenance and deadlines

#### Faucet Backend
- **Description:** Host the faucet backend
- **Manager:** **Mokhtar**
- **Repo:** Private
- **Team:**
  - **Mokhtar:** Manager/Devops
- **Tasks:**
  - Update README with instructions on how to deploy backend
  - Keep it stocked with tokens
  - Delete old data at least weekly


#### Payout Scripts
- **Description:** Scripts assisting [Testnet Incentive Payouts](#testnet-incentive-payouts)
- **Manager:** **Martin**
- **Repo:** Private
- **Team:**
  - **Martin:** Manager/Development
- **Tasks:**
  - Improve and add new roles
  - Migrate to linode

#### Endpoint Selector
- **Description:** Fallback system for [Hosted Pioneer](#hosted-pioneer) if node goes down
- **Manager:** **Mokhtar**
- **Repo:** [pioneer-endpoint-selector](https://github.com/Joystream/pioneer-endpoint-selector)
- **Team:**
  - **Mokhtar:** Manager/Devops
  - **Martin:** Devops
- **Tasks:**
  - Deploy and maintain

#### Staging Testnets

- **Description:** Run a staging testnet with latest stable development runtime so that both ourselves and interested users can test new features, software, nodes without running closed `--dev` chains.
- **Manager:** **Martin**
- **DevOps:** **Martin**
- **Repo:** N/A
- **Team:**
  - Martin
- **Tasks:**
  - Keep at least two staging testnets running.
  - One continuous that will mirror existing testnet - `staging-lts`
  - One or more "on demand" for reckless testing - `staging-reckless`

#### SSDN Benchmarking Tool
- **Description:** Benchmark and monitoring tool for SSDN
- **Manager:** **Alex**
- **Repo:** TBD
- **Team:**
  - **Alex:** Manager/Developer
  - **Martin:** Testing
- **Tasks:**
  - [TBD](https://github.com/Joystream/joystream/issues/28)

## Internal Operations

### Testnet Incentive Payouts

- **Description:** Conduct regular payouts
- **Manager:** **Martin**
- **Team:**
  - **Martin**
- **Schedule:**
    - Mondays at 10:00 GMT+2

### Support

- **Description:** Provide support to users engaging with testnet functionality and campaigns
- **Manager:** - **Martin**
- **Team:**
  - **Martin**
  - **Community Member 1:**
  - **Community Member 2:**
  - **Community Member 3:**
- **Duration:**
  - Very high availability in the week following releases
  - No more than 24 hour lag in response to queries after that
- **Channels:**
  - Telegram
  - GitHub
  - On-chain forums
  - ??
