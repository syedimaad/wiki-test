### Brief

This document recommends a code review process for application and
Infrastructure code changes. Motivation of this process is to provide a
flow that can provide for:

- at least one step of review by someone other than code committer

- a process which can fit well with existing flow, tools and can be
  introduced quick without many changes

- code commits and review can be linked to ticket system for audit
  purposes

### Process

On a high-level the process can be summarised as the following sequence:

#### Steps Involved:

1.  A developer makes a change in their feature branch and tests it.
    When they're happy they push, and make a merge request.\

2.  The developer assigns the merge request to a reviewer, who looks at
    it and makes line and design level comments as appropriate. When the
    reviewer is finished, they assign it back to the author.\

    \
    \

3.  The author addresses the comments. This stage can go around for a
    while, but once both are happy, one assigns to a final reviewer who
    can merge.\

4.  The final reviewer follows the same process again. The author again
    addresses any comments, either by changing the code or by responding
    with their own comments.

5.  Once all concerns from the reviewer are addressed and the pipeline
    is green, they will merge.\

### Pre-Requisites

1.  [Integration between Jira and
    Gitlab](https://about.gitlab.com/blog/2021/04/12/gitlab-jira-integration-selfmanaged/)
    must be established for linking gitlab commits in JIRA. Based on the
    integration the Merge Requests will need to be named in certain
    format like Merger Request Title should start with Ticket number to
    have automatic association.
