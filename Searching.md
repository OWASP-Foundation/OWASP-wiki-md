This article provides an overview of OWASP's search feature.

## search

Put your text in the searchbox; it provides an input field with two
buttons:

  - **Go** - the *Go* button (or *Enter* on the keyboard), will take you
    automatically to the best match for the entered keyword.
  - **Search** - the *Search* button will return a list of matching
    results.

### Effective searching

Here are few good tips and hints for using the search feature
effectively:

#### Limiting results

  - **Any word**: The default search mode will turn up results with
    ***any*** of the words in your query.
  - **All words**: To limit to results that include ***all*** words, put
    a "+" at the beginning of each word: `+search +engine` returns only
    pages containing both words, like Google's default mode. You can
    also do a phrase search by enclosing words in quotes: `"search
    engine"]` turns up a smaller set of results, which not only have
    both words but have them in order.
  - **Exclude words**: To exclude results that include some words, put a
    "-" at the beginning: `search -engine]`

Boolean search is also possible, using words including "AND", "OR", and
"NOT".

#### Avoid short and common words

If your search terms include a common "stop word" (such as "the", "one",
"your", "more", "right", "while", "when", "who", "which", "such",
"every", "about") it may give a large number of non-relevant results.

#### Words with special characters

In a **search** for a word with a diaeresis, such as Sint Odiliënberg,
it depends whether this ë is stored as one character or as "ë". In the
first case one can simply search for Odilienberg (or Odiliënberg); in
the second case it can only be found by searching for Odili, euml and/or
nberg. This is actually a bug that should be fixed -- the entities
should be folded into their raw character equivalents so all searches on
them are equivalent.

#### Words in single quotes

If a word appears in an article with single quotes, you can only find it
if you search for the word with quotes. Since this is rarely desirable
it is better to use double quotes in articles, for which this problem
does not arise.

An apostrophe is identical to a single quote, therefore Mu'ammar can be
found searching for exactly that (and not otherwise). A word with
apostrophe s is an exception in that it can be found also searching for
the word without the apostrophe and the s.

#### Namespaces searched by default

The search only applies to the namespaces selected in the user's
[preferences](special:preferences "wikilink"). To search the other
namespaces check or uncheck the tickboxes in "Search in namespaces" box
found at the bottom of a search results page. Depending on the browser,
a box may still be checked from a previous search, but without being
effective any longer\! To make sure, uncheck and recheck it.

Searching the image namespace means searching the image descriptions,
i.e. the first parts of the image description pages.

#### Delay in updating the search index

For reasons of efficiency and priority, very recent changes are not
always immediately taken into account in searches.

### Searching the page history

To search the text that appears only in the page history, you must
[export](special:export "wikilink") the text to [XML](XML "wikilink")
format first.