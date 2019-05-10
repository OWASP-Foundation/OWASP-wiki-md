I’ve discovered a discrepancy between a code comment, and some
implementation in the ASP version of the Reform Library.

In the HtmlAttributeEncodeEx() function, the comment for what shall be
allowed to pass direct through without conversion lists space,comma,
period.

The code, however, doesn’t implement it this way, but only impliments
for the a-z, A-Z, 0-9 sequences

Checking with the other languages (ruby, perl, python, java) they are
all implemented in the same way, but their comments correspond properly.

I think that simply removing the reference to SPACE , . in the comments
will go a long way.

I also, however, think that some acknowledgement should be made in that
particular function as to why it allows different pass-through’s than
the other three functions do. With a comment, I’d have understood it was
intentional.