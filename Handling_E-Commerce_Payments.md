[Development Guide Table of
Contents](Guide_Table_of_Contents "wikilink") __TOC__

Commerce using the Internet relies solely on trust; users will not use
systems that they believe are insecure. This chapter presents best
practices compliant with the Payment Card Industry (PCI) guidelines. PCI
compliance is mandatory for merchants, third party processors, and
service bureaus - not optional.

While this chapter summarizes several key PCI DSS requirements and
offers implementation guidelines, it is not a substitute for utilizing
the PCI DSS as a baseline.

There are three documents which are useful in this regards.

  - PCI DSS 1.1

<!-- end list -->

  - PCI Self Assessment Guide - *The self assessment currently only
    covers PCI 1.0 requirements - the 1.1 version is forthcoming*

<!-- end list -->

  - PCI Security Audit Procedure v.1.1 - ''This is the audit guide
    utilized by PCI QSA for performing a Level 1 assessment, but the
    requirements are mandatory for all levels of merchant ''

These documents can be accessed via the Further Reading section at the
bottom of this article.

## Objectives

This chapter sets out to document methods to:

  - Secure Payment Account Number handling

<!-- end list -->

  - Minimize fraud from cardholder not present (CNP) transactions

<!-- end list -->

  - Maximize privacy and trust for users of e-commerce systems

<!-- end list -->

  - Comply with all local laws and PCI (merchant agreement) standards

## Compliance and Laws

If you are an e-commerce merchant, you must comply with all your local
laws, such as all tax acts, trade practices, Sale of Goods (or similar)
acts, lemon laws (as applicable), and so on. You should consult a source
of legal advice competent for your jurisdiction to find out what is
necessary.

If you are a credit card merchant, you have agreed to the credit card
merchant agreements. Typically, these are extremely strict about the
amounts of fraud allowed, and the guidelines for “card holder not
present” transactions. You must read and follow your agreement.

'''If you do not understand your agreement, you should consult your
bank’s merchant support for more information. '''

## PCI Compliance

In brief, here are the twelve requirements you are required to use if
you are going to handle credit card payments:

|  |                                             |  |                                                                                          |
|  | ------------------------------------------- |  | ---------------------------------------------------------------------------------------- |
|  | **Goal**                                    |  | **Action**                                                                               |
|  | Build and maintain a secure network         |  | Install and maintain a firewall configuration to protect data                            |
|  |                                             |  | Do not use vendor-supplied defaults for system passwords and other security parameters   |
|  | Protect Cardholder Data                     |  | Protect stored data                                                                      |
|  |                                             |  | Encrypt transmission of cardholder data and sensitive information across public networks |
|  | Maintain a Vulnerability Management Program |  | Use and regularly update anti-virus software                                             |
|  |                                             |  | Develop and maintain secure systems and applications                                     |
|  | Implement Strong Access Control Measures    |  | Restrict access to data by business need-to-know                                         |
|  |                                             |  | Assign a unique ID to each person with computer access                                   |
|  |                                             |  | Restrict physical access to cardholder data                                              |
|  | Regularly Monitor and Test Networks         |  | Track and monitor all access to network resources and cardholder data                    |
|  |                                             |  | Regularly test security systems and processes                                            |
|  | Maintain an Information Security Policy     |  | Maintain a policy that addresses information security                                    |
|  |                                             |  |                                                                                          |

## Handling Credit Cards

Every week, we read about yet another business suffering the ultimate
humiliation - their entire customer's credit card data stolen... again.
What is not stated is that this is often the end of the business (see
CardSystems being revoked by Visa and AMEX in the *Further Reading*
section). Customers hate being forced to replace their credit cards and
fax in daily or weekly reversals to their bank’s card services. Besides
customer inconvenience, merchants breach their merchant agreement with
card issuers if they have insufficient security. No merchant agreement
is the death knell for modern Internet enabled businesses.

This section details how you should handle and store payment
transactions.

### Payment Card Handling Best Practices

The PCI DSS 1.1 restricts which card data elements can and cannot be
stored. While the ultimate guide is the PCI DSS document, card handling
best practices are summarized below, along with guidelines for
implementing the requirements.

Following is a summary of Payment Card elements which can, and can't be
stored:

**Storage permitted but protection required:**

PAN (Primary Account Number) -'' Must be stored in unreadable form per
PCI DSS 3.4. Strong one way hash, truncation, index tokens and pads with
secure storage for pads, or strong cryptography with associated key
management processes and procedures are allowed.''

Cardholder Name

Service Code

Expiration Date

*The PAN, at minimum, should not be stored in a readable format.*

There are a number of commercial database encryption vendors with
products that perform column and database level encryption. Used
properly, these fulfill the 'strong cryptography with associated key
management processes and procedures' requirement. Several are listed in
the references at the bottom of this page. This type of solution is
typically used for recurring transactions.

**Sensitive authentication data - storage not allowed:**

Full magnetic stripe

CVC2/CVV2/CID

PIN / PIN Block

### Auth numbers

After successfully processing a transaction, you are returned an
authorization number. This is unique per transaction and has no
intrinsic value of its own. It is safe to store this value, write it to
logs, present it to staff, and e-mail to the customer.

### Handling Recurring payments

About the only business reason for storing credit card numbers is
recurring payments. However, you have several responsibilities if you
support recurring payments:

  - You must follow the terms of your merchant agreement. Most merchant
    agreements require you to have original signed standing
    authorizations from credit card holders. This bit of signed paper
    will help you if the customer challenges your charges.

<!-- end list -->

  - It is best practice to encrypt credit card numbers. This as a
    mandatory requirement in the PCI guidelines

<!-- end list -->

  - Limit the term of the recurring payment to no more than one year,
    particularly if you have “Card holder not present” (CNP)
    transactions

<!-- end list -->

  - Expunge the credit card details as soon as the agreement is finished

The problem with encryption is that you must be able to decrypt the data
later on in the business process. When choosing a method to store cards
in an encrypted form, remember there is no reason why the front-end web
server needs to be able to decrypt them. Database-layer column or table
level encryption is considered best practice.

### Displaying portions of the credit card

PCI only allows the presentation of the first six (the BIN) or the last
four digits. We strongly urge you to not display the credit card at all
if it can be avoided.

There are many reasons why tracing, sending or presenting a credit card
number can be handy, but it is not possible to present credit card
numbers safely due to several reasons:

  - If a large organization has several applications, all with different
    algorithms to present an identifying portion of the credit card, the
    card number might be disclosed.

<!-- end list -->

  - Sending an email invoice is a low cost method of informing users of
    charges to their credit cards. However, email is not secure.

<!-- end list -->

  - For many workplaces, call center staff traditionally has high
    employee turnover rates which means credit card info exposed to
    these employees will quickly spread outside the workplace.

<!-- end list -->

  - Logs are not attacked to eliminate evidence, but to obtain
    additional secrets such as credit card info.

<!-- end list -->

  - In countries with relatively few banking institutions, the
    institutional BIN numbers are limited. Therefore, it is possible to
    guess workable BIN numbers and thus reconstruct a card number even
    if most of the card number has been obscured.

Most credit cards consist of 16 digits (although some are 14 or 15
digits, such as Amex):

'''XXXX XXYY YYYY YYYC '''

C is the checksum. X is the BIN number, which refers to the issuing
institution. Y is the client's card number.

**You must not store the CCV, CCV2 and PVV (or PIN Verification
Value).** These are a credit card validation field used by many payment
gateways to protect against imprint fraud as the value is on the reverse
of the card. Storing this value is not allowed as per sections 3.2.3 and
3.4.

  - For online forms, you must use a "password" type field for CCVs to
    provide some protection against shoulder-surfing. Some browsers
    cannot tell the difference between this and a login form, and will
    offer to remember the details. This is not good, because it
    interrupts the checkout process and many users click "Yes" without
    thinking and thus violate their card holder agreement. Adding
    *autocomplete="off"* to the form tag will prevent many browsers from
    doing this.

For these reasons, it is strongly recommended that you do not present
the user or your staff with open or obscured credit card numbers. If
possible, do not to display any digits of a credit card at all – just
the expiration date.

### Patching and maintenance

The PCI DSS 6.6 requires that patches are applied within one month of
becoming available for any part of your system that stores, processes,
or transmits payment card information. Additionally, a formal change
management process and patch testing procedure must be in place,
utilizing separate development, test, and production environments.

### Reversals

There are two potential frauds from reversals: an insider pushing money
from the organization's account to a third party, and an outsider who
has successfully figured out how to use an automated reversal process to
"refund" money which is not owing, for example by using negative
numbers.

  - Reversals should always be performed by hand, and should be signed
    off by two distinct employees or groups. This reduces the risk from
    internal and external fraud.

<!-- end list -->

  - It is essential to ensure that all values are within limits, and
    signing authority is properly assigned.

For example, in Melbourne, Australia in 2001, a trusted staff member
used a mobile EFTPOS terminal to siphon off $400,000 from a sporting
organization. If the person had been less greedy, she would never have
been caught.

It is vital to understand the amount of fraud the organization is
willing to tolerate.

### Chargeback

A chargeback is a credit card transaction that is billed back to the
merchant after the sale has been settled - chargebacks are initiated by
the card issuer on behalf of the card holder. Typically, card holder
disputes involve product delivery failure or product/service
dissatisfaction.

Card issuers and merchant banks take a dim view of merchants with high
charge back ratios as it costs them a lot of time and money and might
indicate lack of fraud control.

You can take some simple steps to lower your risks. These are:

  - Money is not negative. Use strong typing to force zero or positive
    numbers, and prevent negative numbers.

<!-- end list -->

  - In your source code, don't overload a charge function to be a
    reversal function by allowing negative values.

<!-- end list -->

  - Require logging, auditing, and manual authorization for all charge
    backs and reversals.

<!-- end list -->

  - There should be no code on your web site for automating reversals or
    charge backs.

<!-- end list -->

  - Don't ship goods until you have an authorization receipt from the
    payment gateway.

<!-- end list -->

  - The overwhelming majority of credit cards have a strong relationship
    between BIN numbers and the issuing institution's country. Strongly
    consider not shipping goods to out-of-country BIN cards.

<!-- end list -->

  - For high value goods, consider making the payment with an
    over-the-phone or fax authorized process.

Some customers will try charge backs one time too many. Keep tabs on
customers who charge back, and decide if they present excessive risk.

Always ask for the customer's email as well as the phone number that the
issuing institution has for the customer. This helps if other red flags
pop up.

Attackers look for soft targets. Make it known on your website that you
prosecute fraud to the fullest extent of the law and all transactions
are fully logged.

## Further Reading

  - AMEX, Visa, Mastercard, Discover, JCB, Diner’s Club – Payment Card
    Industry

Payment Card Industry (PCI) Data Security Standards council

<u><https://www.pcisecuritystandards.org></u>

PCI DSS Documents Library

<u><https://www.pcisecuritystandards.org/security_standards/documents.php></u>

  - Commercial database encryption products

Application Security Inc. DBEncrypt -
<u><http://www.appsecinc.com/products/dbencrypt/index.shtml></u>

  - News Articles: TJX Data Breach

<u><http://www.securityfocus.com/news/11438></u>

<u><http://www.eweek.com/article2/0,1895,2106322,00.asp></u>

  - News Article: Visa and AMEX revoke CardSystems for PCI breaches:

<u><http://www.theregister.co.uk/2005/07/19/cardsystems/></u>

## Reference

[Development Guide Table of
Contents](Guide_Table_of_Contents "wikilink")

[Category:OWASP_Guide_Project](Category:OWASP_Guide_Project "wikilink")