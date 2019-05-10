__TOC__

## Not all bugs are equal

A development house will have various degrees of code changes being
reviewed, from simple one line bug fixes in backend scripts that run
once a year, to large feature submissions in criticial business logic.
Typically the intensity of the code review varies based on the perceived
risk that the change presents, though typically the perception of this
risk is informal and ad hoc.

It comes down to the management of resources (skilled persons, company
time, machines, etc). It would not be common to bring in multiple
security architects/experts for every code change occuring on a product,
the bandwidth of those persons or those teams would not be large enough
to handle every change. Therefore companies can make a call on which
changes are important and need to be closely scrutenized, and which ones
can be allowed through with minimal inspection. This will allow
management to better size the development cycle, e.g. if a change is
going to be done in an area which is high risk, management can know to
set aside a day for code review, and ensure persons with relevant skills
will be available. The process of deciding which changes need which
level of code review is based on the risk level of the module the change
is within.

## Who makes the call on Code Review Risk?

If the review intensity of code changes is based on the risk level of
the module being changed, who should decide the level of risk?
Eventually, company Management are responsible for the output of a
company, and thus they are responsible for the risk associated with
products sold by the company. Therefore it is up to Management (or
persons delegated to by Management) to create a reproducable measure or
framework for deciding the risk associated with a code change.

Decisions on the risk of a module or piece of code should be based on
some solid cost/benefit analysis. It would be irresponsible to decide
all modules are high risk, instead management should meet with persons
who have an understanding of the code base, and security issues faced by
the products, and create a measure of risk for various elements of code.
Code could be split up into modules, directories, products, etc, each
with a risk level associated with it.

Various methods exist in the realm of Risk Analysis to assign risk to
entities, and many books have been dedicated to this type of discussion.
At a high level 3 options of establishing risk could include:

1.  Quantitive: bring people together and establish a monitary value on
    the loss associated with the modules, and gauge the likelyhood that
    the module could be compromised. Use the dollar values produced from
    these calculations to determine the level of risk.
2.  Qualitive: bring people together and discuss opinions on what level
    of loss is associated with the modules, and opinions on likelyhood
    of compromise. Qualitive does not attempt to nail down monitary
    assocations with the loss, but tends towards the perception or
    opinion of associated losses.
3.  Delphi: Independently interview or question persons on the losses
    and compromises of the modules, whilst letting the person know the
    feedback will be anonymous. The impression here is that the persons
    interviewed will give more honest answers to the questions and will
    not be swayed by other persons arguments/answers.

## Options for deciding the risk associcated with a code change

Risk is chance of something bad happening and the damage that can be
caused if it occurs. The criteria for deciding the risk profile of
different code modules will be up to the management team resposible for
delivering the changes, however some common critera used would include:

1.  Ease of exposure: Is the code change in a piece of code directly
    exposed to the internet? Does an insider use the interface directly?
2.  Value of loss: How much could be lost if the module has a bug
    introduced? Is the module some critical password hashing mechanism,
    or a simple change to HTML border on some internal test tool?
3.  Regulatory controls: If a piece of code implements business logic
    associated with some standard that must be complied with, then these
    modules can be considered high risk as the penalities for
    non-conformity can be high.

## Feeding risk into continuous processes

When levels of risk have been associated with modules, then the policies
can be created determining what level of code review must be conducted.
It could be that code changes in module X must be reviewed by 3 persons
including a Secuirty Architect, whereas changes in element Y only need a
quick one person peer review. Possibly the code structure could be split
up so that riskier code is placed into a separate repository with
limited developer access.

Other options (or critera) for riskier modules can include demands on
automated testing or static analysis, e.g. code changes in high risk
code must include 80% code coverage on static analysis tools, and
sufficient automated tests to ensure no regressions occur. These
criteria can be demanded and checked as part of the code review to
ensure they are capable of testing the changed code.

Some companies logically split their code into differing repositories,
with more risky code appearing in a repository with a limited subset of
developers having access. If the code is split in this fashion, then it
must be remembered that only developers with access to the code should
be able to conduct reviews of that code.

## What decisions can be made with code reviews which contain risky changes

The previous sections have covered the risk analysis decisions on what
level of code review should be applied. Risk analysis could also be used
during the code review to decide how to react to a code change that
introduces risk into the product. At the end of the day, with typical
Risk Analysis, the decisions to be made are "Do I accept, transfer,
avoid or reduce this risk?". In the environment of code review,
"transfer" of risk does not really make sense (transfer normally means
taking out insurance to cover the cost of exposure), but accept, avoid
and reduce can still apply:

1.  Reduce: This would be the typical resolution path: if the reviewer
    finds that the code change introduces risk into an element of
    business logic, a different code change should be sought that
    satisifies the requirements but at a lower risk.
2.  Accept: If there is a risk in the code, but there is no other way to
    implement the business logic then the code can pass code review the
    risk is considered acceptable.
3.  Avoid: It should be possible to consider not performing a code
    change, if the risk introduced by the change is too great. Idealy
    this decision should be reached before the code review stage, but it
    is entirely possible that factors can arise during development that
    changes the risk profile and prompts management to reconsider if a
    change should go ahead.