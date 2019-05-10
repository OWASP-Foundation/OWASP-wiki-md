## Possible Enhancements

  - Reduce the number of required parameters to validation methods by
    creating new methods signatures that use default parameters.

<!-- end list -->

  - Change the Validation methods to Validation classes that can be
    applied in a [Strategy
    Pattern](http://en.wikipedia.org/wiki/Strategy_pattern). This means
    that rather than having specific methods such as validateCreditCard
    and validateEmailAddress there would be a Validator interface which
    would be implemented by classes like CreditCardValidator and
    EmailAddressValidator. This is analogous to the Encoding classes in
    ESAPI. This offers the benefit that new Validation classes can be
    created and current Validation classes can be modified without
    changing the interface. Additionally, Validators can be stacked to
    provide multiple forms of validation