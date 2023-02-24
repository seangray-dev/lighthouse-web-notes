# Character Encoding

## Character Encoding for beginners.

[This Artcile](https://www.w3.org/International/questions/qa-what-is-encoding.en) explains character encodings, which are sets of mapping between bytes in a compter and characters in a character set. Characters are grouped into a character set, each associated with a code point number, and are stored in the computer as one or more bytes.

The article notes that lack of character encoding information can affect the readability of displayed text and may mean that data cannot be found by search engines or reliably processed by machines.

The article recommends using a UTF-8 as a good choice for a single character encoding to handle any character needed.

The articles also notes that a font is a collection of glyph definitions and that a font will usually cover a single character set or a subset of all the characters in a set.

The article provides additional information on mapping between bytes, code points, and characters, such as how ISO 8859-1 maps the same code point value to different characters and how Unicode contains all the characters needed in a single set.

It is important for applications to know which character encoding is appropriate for data and how to handle that encoding.

## Characters, Symbols and the Unicode Miracle

In [This Video](https://www.youtube.com/watch?v=MijmeoH9LT4) Tom Scott explains how the character encoding system called UTF-8 solved a lot of problems with the exisiting ASCII standard. ASCII is a 7-bit binary system that was used to encode characters in the English-speaking world. However, as computer technology advanced and the internet became more widespread, the need for universal character encoding system that would work for all languages and character sets became more important.

The Unicode Consoritum was established to create a universal character encoding system. UTF-8 was devloped to be a solution that was backward-compatible, avodied waste and could be easily moved forward and backward. UTF-8 starts by taking ASCII, so anything under 128 can be expressed in 7 digits. Anything abouve that requires two or three byte , and UTF-8 can go all the way up to six-bytes.

UTF-8 solved many issues with character encoding system, and it became the dominant character encoding system on the web a few years ago. It is a beautiful hack that is used worldwide every second of every day.
