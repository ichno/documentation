.. _regular-expression-syntax:

=========================
Regular expression syntax
=========================

.. note:: this information was based on |elastic-regex| 

.. |elastic-regex| raw:: html

   <a href="https://www.elastic.co/guide/en/elasticsearch/reference/current/regexp-syntax.html" target="_blank">Elasticsearch Regular expression syntax</a>


A |regex| is a way to match patterns in data using placeholder characters, called operators.

.. |regex| raw:: html

   <a href="https://en.wikipedia.org/wiki/Regular_expression" target="_blank">regular expression</a>

Ichno uses |apache-lucene|'s regular expression engine to parse these queries.

.. |apache-lucene| raw:: html

   <a href="https://lucene.apache.org/core/" target="_blank">Apache Lucene</a>

Reserved characters
===================

Lucene’s regular expression engine supports all Unicode characters. However, the following characters are reserved as operators:::

. ? + * | { } [ ] ( ) " \

Depending on the optional operators enabled, the following characters may also be reserved:::

# @ & < >  ~


To use one of these characters literally, escape it with a preceding backslash or surround it with double quotes. For example:::

  \@                  # renders as a literal '@'
  \\                  # renders as a literal '\'
  "john@smith.com"    # renders as 'john@smith.com'

Standard operators
==================

Lucene’s regular expression engine does not use the |pcre| library, but it does support the following standard operators.

.. |pcre| raw:: html

   <a href="https://en.wikipedia.org/wiki/Perl_Compatible_Regular_Expressions" target="_blank">Perl Compatible Regular Expressions (PCRE)</a>

.
    Matches any character. For example:

    ab.     # matches 'aba', 'abb', 'abz', etc.

?
    Repeat the preceding character zero or one times. Often used to make the preceding character optional. For example:

    abc?     # matches 'ab' and 'abc'

\+
    Repeat the preceding character one or more times. For example:

    ab+     # matches 'ab', 'abb', 'abbb', etc.

\*
    Repeat the preceding character zero or more times. For example:

    ab*     # matches 'a', 'ab', 'abb', 'abbb', etc.

{}
    Minimum and maximum number of times the preceding character can repeat. For example:

    a{2}    # matches 'aa'
    a{2,4}  # matches 'aa', 'aaa', and 'aaaa'
    a{2,}   # matches 'a' repeated two or more times

\|
    OR operator. The match will succeed if the longest pattern on either the left side OR the right side matches. For example:

    abc|xyz  # matches 'abc' and 'xyz'


( … )
    Forms a group. You can use a group to treat part of the expression as a single character. For example:

    abc(def)?  # matches 'abc' and 'abcdef' but not 'abcd'


[ … ]
    Match one of the characters in the brackets. For example:

    [abc]   # matches 'a', 'b', 'c'

    Inside the brackets, - indicates a range unless - is the first character or escaped. For example:

    [a-c]   # matches 'a', 'b', or 'c'
    [-abc]  # '-' is first character. Matches '-', 'a', 'b', or 'c'
    [abc\-] # Escapes '-'. Matches 'a', 'b', 'c', or '-'

    A ^ before a character in the brackets negates the character or range. For example:

    [^abc]      # matches any character except 'a', 'b', or 'c'
    [^a-c]      # matches any character except 'a', 'b', or 'c'
    [^-abc]     # matches any character except '-', 'a', 'b', or 'c'
    [^abc\-]    # matches any character except 'a', 'b', 'c', or '-'


Unsupported operators
=====================

Lucene’s regular expression engine does not support anchor operators, such as ^ (beginning of line) or $ (end of line). To match a term, the regular expression must match the entire string.