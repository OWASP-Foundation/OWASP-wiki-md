# ![Image:T._secure_coding.jpg](T._secure_coding.jpg "Image:T._secure_coding.jpg")

The track seeks to add to OWASP's cache of "secure code". Facilitators
will chose a focus for each of the track's sub-sections addressing a
"development scenario" developers consistently face in each application
they build. Each sub-section aims to deliver secure functionality or
code useful in helping developers build security into their application
when addressing that development scenario even if it delivers only "code
snippets". Two principals govern this track:

  - All track participants will support analysis, design,
    implementation, and testing activities for each section
  - Each track sub-section should deliver design and implementation
    useful as a leave-behind, for building security into applications

The first implementation of this track aims to deliver only code
snippets because track organizers want freedom to select topics beyond
what already exists in secure programming toolkits, if necessary. For
those familiar with OWASP's
[ESAPI](http://www.owasp.org/index.php/Category:OWASP_Enterprise_Security_API),
the track will seek to:

  - Use existing ESAPI (or other OWASP project) material where
    appropriate
  - Roll-up and contribute back to OWASP projects, all applicable code
    developed during this track

Track sub-sections regarding "input validation" and AppSensor represent
two OWASP project targets we've already included focus on.

Our goal will be to extend the practice of "building security into
applications" without a preference for whether or not the application
exists in a calcified form of maintenance or whether it's being
developed in a green-field manner. Summarizing: the objective of each
sub-section is to make our technology better not necessarily to raise
awareness of its existence.

## Facilitation

A set of facilitators, each with both a security and development
background, will take turns leading their chosen focus. Facilitators
will come prepared with their sub-section problem definition, session
goals, and supporting material. Do not expect the facilitator to lead a
lecture. Rather, expect the facilitator to come with a skeleton analysis
of the development scenario and framework for analyzing the security
challenge.

Expect facilitators to divide their sub-section into a list of goals for
the development scenario. Facilitators will break the goal into
intermediate objectives and will either delegate these objectives to
participants or help to direct the conversation across contexts for
participants. For example: during a sub-section on persistence
frameworks, the facilitator may present risks associated with
configuring and implementing auto-binding in a particular framework,
then direct snippet implementation on other persistence frameworks,
owned and implemented by participants themselves.

## Participants

Participants will be expected to arrive with at least a conversational
understanding (preferably experience) in the sub-topic area. They will
be expected to contribute to analysis, design, implementation, and/or
testing. Track participants will need to self-police each sub-section.
If things get too introductory and forward progress stalls, participants
can help a lagging participant "Get up to speed" with the rest of the
session quickly in a side conversation/demo/hand-holding exercise.

## Sub-Sections (Topic Areas)

**[1. Applying ESAPI Input
Validation](http://www.owasp.org/index.php/Summit_2011_Working_Sessions/Applying_ESAPI_Input_Validation)**

  - Serial Decomp: Decode, canonicalize, filter
  - Structured data (SSN, CC, etc.)
  - Unstructured data (comments, blogs, etc.)
  - Other input exaples (ws-, database, etc.)

**2. Defining AppSensor Sensors for:**
\*Forced Browsing
\*Request Velocity
\*Unexpected encodings
\*Impersonation (Sudden user switch)
**3. Managing Sessions**
\*Across requests
\*Across containers
\*Invalidating sessions (Timeout, attack event, logout)
\*Invalidating sessions (across containers, SSO token invalidation, user
termination)
**[4. Protecting Information Stored
Client-Side](http://www.owasp.org/index.php/Summit_2011_Working_Sessions/Protecting_Information_Stored_Client-Side)**
\*Threat Modeling the problem
\*Protecting theft and re-playability of application-specific info (on
client & in flight)
\*Protecting theft and re-playability of session-specific info (in
flight)
\*Protecting session-specific information from attack on the client
**[5. Protecting against
CSRF](http://www.owasp.org/index.php/Summit_2011_Working_Sessions/Protecting_Against_CSRF)**
\*Hygiene: Discuss/show frames-busting, cross-domain policy; Discuss
referrer and other red herrings
\*Tokens (crafting, scoping, and checking)
\*Discussions, techniques on scale
\*Discussions, techniquest on CAPTCHA, re-auth, etc.
**[6. Providing Access to Persisted
Data](http://www.owasp.org/index.php/Summit_2011_Working_Sessions/Providing_Access_to_Persisted_Data)**
\*Controlling visibility of tables by role
\*Providing access to safe SQL-like query through DAO layer
\*Discussions, techniques for providing secure'auto-wiring' /
marshaling
\*Encoding and canonicalization for storage (or alternatively: Security
concerns with heirarchical caching and object pooling)
\== Resources == GITHUB will allow us to share track code pretty
rapidly. Find code-based resources associated with this track here:

["Secure Coding Workshop (Google
Code)"](https://code.google.com/p/secure-coding-workshop/)
["Secure Coding Workshop
(Github)"](https://github.com/jsteven/OWASP-Secure-Coding-Workshop)

[Category:Summit_2011_Tracks](Category:Summit_2011_Tracks "wikilink")