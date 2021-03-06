---
title: Pegasus Proposal
layout: page
---

## Abstract

Pegasus is a distributed key-value storage system which is designed to
be horizontally scalable, strongly consistent and high-performance.

- Pegasus codebase: <https://github.com/XiaoMi/pegasus>
- Website: <https://pegasus-kv.github.io>

## Proposal

Pegasus is a key-value database that delivers low-latency data access together
with horizontal scalability, using hash-based partitioning. Pegasus uses PacificA
protocol for strong consistency and RocksDB as the underlying storage engine.

We propose to contribute the Pegasus codebase and associated artifacts
(e.g., documentation, website content, etc.) to the Apache Software Foundation,
and aim to build an open community around Pegasus’s continued development
in the "Apache Way".

## Background

Apache HBase was recognized as the only large-scale KV store solution in XiaoMi
until Pegasus came out in 2015 to solve the problem of high latency
of HBase because of its Java GC and RPC overhead of the underlying distributed filesystem.

Pegasus targets to fill the gap between Redis and HBase. As the former
is in-memory, low latency, but does not provide a strong-consistency guarantee.
And unlike the latter, Pegasus is entirely written in C++ and its write-path
relies merely on the local filesystem.

Apart from the performance requirements, we also need a storage system
to ensure multiple-level data safety and support fast data migration
between data centers, automatic load balancing, and online partition split.

After investigating the existing storage systems in the open source world,
we could hardly find a suitable solution to satisfy all the requirements.
So the journey of Pegasus begins.

### Rationale

Pegasus is a mature, active project that has been widely adopted in XiaoMi.
After the initial release open source project in 2017, we have seen a great amount
of interest across a diverse set of users and companies.

Our experiences at committers and PMC members on other Apache projects have convinced
us that having a long-term home at Apache foundation would be a great fit for the project,
to ensure that processes and procedures are in place to keep project and community "healthy"
and free of any commercial, political or legal faults.

### Initial Goal

- Move the existing codebase, website, documentation, and mailing lists to
  Apache-hosted infrastructure.
- Work with the infrastructure team to implement and approve our code review, build,
  and testing workflows in the context of the ASF.
- Incremental development and releases per Apache guidelines.

## Current Status

Pegasus has been an open source project on GitHub <https://github.com/XiaoMi/pegasus>
since October 2017.

### Meritocracy

The intent of this proposal is to start building a diverse developer and user community
around Pegasus following the ASF meritocracy model.
We plan to invite more people as committers if they contribute to this project.

### Releases

Pegasus has undergone multiple public releases, listed here: <https://github.com/XiaoMi/pegasus/releases>.

These old releases was not performed in the typical ASF fashion.
We will adopt the ASF source release process upon joining the incubator.

### Code review

Pegasus’s code reviews are currently public on Github <https://github.com/XiaoMi/pegasus/pulls>.

### Community

Pegasus seeks to develop developer and user communities during incubation.

### Core Developers

Currently most of the core developers of Pegasus are working in
XiaoMi KV-Storage Team. Yingchun Lai is one of the Apache Kudu PMC members.
Zuoyan Qin is an experienced open source developer who created [sofa-pbrpc](https://github.com/baidu/sofa-pbrpc)
inside baidu. Among them, Weijie Sun from ByteDance is a very important contributor.

- Zuoyan Qin (<https://github.com/qinzuoyan>)
- Yuchen He (<https://github.com/hycdong>)
- Weijie Sun (<https://github.com/shengofsun>)
- Tao Wu (<https://github.com/neverchanje>)
- Yingchun Lai (<https://github.com/acelyc111>)
- Wei Huang (<https://github.com/vagetablechicken>)

### Alignment

Pegasus is aligned with several other ASF projects.

We are working on a new feature to load data stored in the HDFS filesystem.
Pegasus can also upload checkpoints to HDFS, for both backup and analysis purpose.
We are planing to support offline analysis on checkpoint powered by Apache Spark.

## Known Risks

### Orphaned Products

The core developers of XiaoMi Pegasus team plan to work full time on this project.
There is very little risk of Pegasus getting orphaned since at least one large
company (XiaoMi) is extensively using it in their production.
For example, currently there are more than 40 Pegasus applications in production.
Furthermore, since Pegasus was open sourced at the beginning of October 2017,
it has received more than 1047 stars and been forked nearly 186 times.
We plan to extend and diversify this community further through Apache.

### Inexperience with Open Source

The core developers are all active users and followers of open source.
They are already committers and contributors to the Pegasus Github project.
All have been involved with the source code that has been released under an
open source license, and several of them also have experience developing
code in an open source environment.

Several of the developers among XiaoMi Storage Team are committers and/or PMC
members on other ASF projects (Kudu, HBase et al). They will guide others to practice
the Apache Way together along with other incubator mentors.

### Homogenous Developers

The project has received some contributions from developers outside of XiaoMi,
and is starting to attract a user community as well. We hope to continue to
encourage contributions from these developers and community members and grow
them into committers after they have had time to continue their contributions.

### Reliance on Salaried Developers

XiaoMi invested in Pegasus as a general key-value storage used in company widely.
The core developers have been dedicated to this project for about four years.

Besides, we look forward to attracting more people outside XiaoMi to contribute this project,
either payed engineers working on storage area, or individual volunteers, as long as they have
enthusiasm for the Pegasus project.

### An Excessive Fascination with the Apache Brand

Pegasus is proposing to enter incubation at Apache in order to help efforts
to diversify the committer-base, not so much to capitalize on the Apache brand.
The Pegasus project is in production use already inside XiaoMi,
but is not expected to be an Baidu product for external customers.
As such, the Pegasus project is not seeking to use the Apache brand as
a marketing tool.

## Documentation

Information about Pegasus can be found at <https://github.com/XiaoMi/pegasus>.
The following links provide more information about Pegasus in open source:

- Pegasus website: <https://pegasus-kv.github.io>

## Initial Source

Besides the core codebase, Pegasus also hosts its side projects on github under XiaoMi Group.
Specifically, the initial source includes:

Client libraries with different Languages:

- Java-Client: <https://github.com/XiaoMi/pegasus-java-client>
- Scala-Client: <https://github.com/XiaoMi/pegasus-scala-client>
- NodeJs-Client: <https://github.com/XiaoMi/pegasus-nodejs-client>
- Go-Client: <https://github.com/XiaoMi/pegasus-go-client>
- Python-Client: <https://github.com/XiaoMi/pegasus-python-client>

Components of Pegasus:

- rDSN: <https://github.com/XiaoMi/rdsn>
- RocksDB: <https://github.com/XiaoMi/pegasus-rocksdb>

rDSN was initially a distributed framework developed by Zhenyu Guo from Microsoft,
and it is heavily refactored to be more fit in Pegasus. rDSN is an MIT licensed project.
It's in our plan to merge Pegasus and rDSN as one project.

RocksDB is a Facebook-developed storage engine. Pegasus added some enhancements and modifications
that may be incompatible with the original implementation.
RocksDB is licensed under Apache 2.0 License.

## External Dependencies

Pegasus has the following external dependencies.

- RocksDB (Apache)
- Apache Thrift (Apache Software License v2.0)
- Boost (Boost Software License)
- Apache Zookeeper (Apache)
- Microsoft rDSN (MIT)
- Google s2geometry (BSD)
- Google gflags (BSD)
- fmtlib (BSD)
- POCO (Boost Software License)
- rapidjson (Tencent)
- libevent (BSD)
- gperftools (BSD)

Build and test dependencies:

- Apache Maven (Apache Software License v2.0)
- cmake (BSD)
- clang (BSD)
- Google gtest (Apache Software License v2.0)

## Required Resources

### Mailing List

There are currently no mailing lists.
The usual mailing lists are expected to be set up when entering incubation:

TODO

### Git Repositories

Upon entering incubation, we want to move the existing repo from <https://github.com/XiaoMi/pegasus>
to Apache infrastructure like <https://github.com/apache/incubator-pegasus>.

### Issue Tracking

Pegasus currently uses GitHub to track issues. Would like to continue to do so while we discuss migration possibilities with the ASF Infra committee.

### Other Resources

The existing code already has unit tests so we will make use of existing Apache continuous testing infrastructure. The resulting load should not be very large.

## Source and Intellectual Property Submission Plan

Current code is Apache 2.0 licensed and the copyright is assigned to XiaoMi.
If the project enters incubator, XiaoMi will transfer the source code & trademark
ownership to ASF via a Software Grant Agreement.

## Initial Committers

- Zuoyan Qin (<https://github.com/qinzuoyan>)
- Weijie Sun (<https://github.com/shengofsun>)
- Yuchen He (<https://github.com/hycdong>)
- Tao Wu (<https://github.com/neverchanje>)
- Yingchun Lai (<https://github.com/acelyc111>)
- Wei Huang (<https://github.com/vagetablechicken>)

## Affiliations

The initial committers are employees of XiaoMi Inc.

## Sponsors

### Champion

TODO

### Nominated Mentors

TODO

### Sponsoring Entity

We are requesting the Incubator to sponsor this project.
