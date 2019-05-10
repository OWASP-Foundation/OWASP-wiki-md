ESAPI currently does not have internationalization support, but its
clearly of significant interest.

The primary task would be to provide:

  - internationalization support for all error messages (i.e., multiple
    messages, each tagged with a particular language)
      - This includes messages that ESAPI has built into it, and
      - any custom developed error messages created by the developer
  - The ability to select which language is currently in use
      - This should be per user, rather than per ESAPI instance

Are there other internationalization issues to be addressed?

Is this all custom code (via following standard patterns?) or are their
packages/utilites out there that help you provide internationalization.