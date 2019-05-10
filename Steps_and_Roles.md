[OWASP Code Review Guide Table of
Contents](OWASP_Code_Review_Guide_Table_of_Contents "wikilink")__TOC__

## Roles

Code reviews are carried out by personnel in four roles: author,
moderator, reader, and scribe. There are typically reviewers who are
simply inspectors, focused on finding defects in the code, who do not
fit in any of the four roles. Depending on the size of your inspection
team and the formality of your inspection process, some people may serve
in multiple roles at the same time. However, if you have a large enough
team, it is useful to assign each role to a different person so each can
focus on their duties.

1.  **Moderator**: The Moderator is the key role in a code review. The
    moderator is responsible for selecting a team of reviewers,
    scheduling the code review meeting, conducting the meeting, and
    working with the author to ensure that necessary corrections are
    made to the reviewed document.
2.  **Author**: The Author wrote the code that is being reviewed. The
    author is responsible for starting the code review process by
    finding a Moderator. The role of Author must be separated from that
    of Moderator, Reader, or Recorder to ensure the objectivity and
    effectiveness of the code review. However, the Author serves an
    essential role in answering questions and making clarifications
    during the review and making corrections after the review.
3.  **Reader**: The Reader presents the code during the meeting by
    paraphrasing it in his own words. It is important to separate the
    role of Reader from Author, because it is too easy for an author to
    explain what he meant the code to do instead of explaining what it
    actually does. The reader's interpretation of the code can reveal
    ambiguities, hidden assumptions, poor documentation and style, and
    other errors that the Author would not be likely to catch on his
    own.
4.  **Scribe**: The Scribe records all issues raised during the code
    review. Separating the role of Scribe from the other roles allows
    the other reviewers to focus their entire attention on the code.

## Steps

Code reviews consist of the following four steps:

1.  **Initialization**: The Author informs a Moderator that a
    deliverable will be ready for inspection in the near future. The
    Moderator selects a team of inspectors and assigns roles to them.
    The Author and the Moderator together prepare a review package
    consisting of the code to be reviewed, documentation, review
    checklists, coding rules, and other materials such as the output of
    static analysis tools. The Moderator will announce the time, place,
    and duration for the code review meeting.
2.  **Preparation**: After receiving the review package, the inspectors
    study the code individually to search for defects. Preparation
    should take about as long as the duration of the meeting. Some less
    formal code review techniques skip the preparation phase.
3.  **Meeting**: The Moderator initiates the meeting, then the Reader
    describes the code to the participants. After each segment of code
    is presented, reviewers will bring up any issues they found during
    Preparation or discovered during the meeting. The interaction
    between reviewers during the meeting will usually bring up issues
    that were not discovered during the Preparation step. The Scribe
    notes each defect with enough detail for the Author to address it
    afterwards. It is the responsibility of the Moderator to keep the
    meeting focused on defects, ensuring that the participants do not
    attempt to produce solutions during the meeting instead. Some less
    formal code review steps skip the meeting phase, choosing instead to
    e-mail the code to one or more reviewers who return comments without
    ever meeting as a group.
4.  **Corrections**: The Author addresses the defects recorded during
    the meeting, and the Moderator checks the corrections to ensure that
    all problems are resolved. If the number of defects raised was
    large, the Moderator may decide to schedule a review of the revised
    code.

[Category:OWASP Code Review
Project](Category:OWASP_Code_Review_Project "wikilink")