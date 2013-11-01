An "easy" interface on top of the Xmlm [1] library.  This version provides more
convenient (but far less flexible) input and output functions that go to and
from [string] values.  This avoids the need to write signal code, which is
useful for quick scripts that manipulate XML.
   
More advanced users should go straight to the Xmlm library and use it
directly, rather than be saddled with the Ezxmlm interface.

# Example

In the toplevel, here's an example of how some XHTML can be selected out
quickly using the Ezxmlm combinators.  Note that this particular HTML has
been post-processed into valid XML using `xmllint --html --xmlout`.

```
# #require "ezxmlm" ;;
# open Ezxmlm ;;
# let (_,xml) = from_channel (open_in "html/variants.html") ;;
# member "html" x |> member "head" |> member_with_attr "meta" ;;
- : Xmlm.attribute list * nodes = ([(("", "name"), "generator"); (("", "content"), "DocBook XSL Stylesheets V1.78.1")], [])
# member "html" x |> member "head" |> member "title" |> data_to_string;;
- : string = "Chapter 6. Variants"                                                                                                                                                                                                                                                                                          
```

Ez peezy lemon squeezy!

[1] https://github.com/dbuenzli/xmlm
