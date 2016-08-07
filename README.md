# Literate Routing

This project aims to improve the implementation of HTTP servers (or, more
generally, any project that needs to provide a mapping from strings ->
functions) by separating the description of the server's routes (it's API) from
it's implementation. Specifically, this project specifies a way of describing
your server's API in a declarative, textual format designed for human
consumption, and then automatically connecting your server's implementation to
that external API.

This project aims to achieve the following goals:
 - Describe a syntax for writing declarative, human readable API specifications
 - Implement tools for transforming those API specifications into other human
   readable documentation formats (arbitrarily themeable webpages, PDFs, etc.)
 - Implement libraries for multiple programming languages to load and use those
   API specifications

## What's it look like?

Currently still in the planning phase--I envision something roughly this:

    # API
    This is a description of our API, these are some common vars:

    :x = 2
    :y = 4

    ## Data

    You can get data from:

    Route: /data/:x/:id
    Where: :id Integer Id of the data to fetch
    Result:
        {x:1,y:'abc'}
    Result: :code 404
        {err:'Id not found!'}


Open ideas to settle before implementation:
  - key/values in Markdown have no definite, standardized syntax; adopt our own,
    or use some mishmash of existing solutions? (kramdown (kramed in JS) has
    syntax for it, or could use some form of table/list, or could abuse link
    notation)
  - Role of headings (for inheritance?), if any
  - What sort of looping, if any
  - What sort of file includes, if any
  - Specifying middleware (how to turn it into text, along with some related
    flags)

Other ideas:
 - For clojure (or any languages with similar functionality): look up relevant
   metadata of linked functions and embed it in the API (or some transformation
   of it--maybe event automatically textualizing core.spec input descriptions)
 - in a similar vein, generally being able to statically extract some data from
   the implementation would be nice (statically typed languages could make this
   great, for example)
 - drive generative testing
 - support org mode as well (and restclient-mode support would be amazing,
   thought it might be easier to implement support for this project in
   restclient-mode)
 - multiple backends for, say, JS: express Router form, purely functional form,
   etc.
