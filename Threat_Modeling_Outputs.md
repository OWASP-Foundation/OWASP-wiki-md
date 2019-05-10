# Summary

\=

This page summarizes discussion on the OWASP Slack threat modeling
project, prompted by the question "Are all outputs of threat modeling
bugs?"

Not everything is a bug. Hard to call an issue in code that’s not
written a bug. The same issue discovered at different times will take
different forms. So to use a trivial example, if I'm at a design stage
of a web app and TM throws "spoofing", I'd create a story: as a user, I
want secure authentication so that only I can access my data". But if
I'm deep into development, and we are doing threat modelling and the
same spoofing comes up, it will be a bug: "Oops, our change password
function does not ask for current password". (Text mostly from
Irene221b)

  - Changed whiteboard diagram
  - Bugs
  - Requirements
      - Requirements for technical or procedural control
  - User stories into the backlog
  - Wiki as intermediate stage
  - Findings
  - “Let’s call them threats”

Organizational discipline:

  - Agreement
  - TM to drive discussion
  - Tagging

Either:

1.  Pulling it out of TM and prioritizing alongside everything else that
    needs to happen in the finite period of time - you can then weigh
    the risk vs value and bugs get the appropriate amount of 'air time'
    with whoever is prioritizing
2.  (preferred\*) - Having whoever makes the prioritization call in the
    threat model, they bring the context of everything else that's
    happening and can make the call on what goes on the backlog and is
    prioritized in the session and what becomes 'research/ spike'
    stories for further focus at a later date. (text from Tash)

Delivered to:

  - Software
  - Operations/IT
  - Risk management

Thanks: Avid, irene221b, .lojikil, mplatt, Sparticvs, swierckx,tash,
tonyuv, zeroxten,