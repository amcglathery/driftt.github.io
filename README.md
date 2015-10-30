# Driftt External Documentations

This repo is built with [Jekyll](https://help.github.com/articles/using-jekyll-with-pages/), a simple, blog-aware static site generator.

This allows easy editing of our documentations in [markdown](https://daringfireball.net/projects/markdown/syntax) by anyone.

"intended to be as easy-to-read and easy-to-write as is feasible" - [markdown](https://daringfireball.net/projects/markdown/syntax)

#### List of Docs:
  - [HTTP API](https://github.com/Driftt/driftt.github.io/blob/master/http-api.md)
  - [SDK](https://github.com/Driftt/driftt.github.io/blob/master/sdk.md)
  
## How to edit documenations

All documents are in markdown files with the extension of ```.md```

So the first step is to get yourself familar with the [markdown](https://daringfireball.net/projects/markdown/syntax) syntax [here](https://daringfireball.net/projects/markdown/syntax) 

once you are familar with the markdown syntax, use your favorite text editor to edit it! Once you are happy with the change, commit the change and THAT'S IT!

#### What is the easiest tool to edit and commit the change?

I would recommend simply using the web editor github provides. Two reasons why it is easy:
  - On page preview of changes
    - not only can you edit the content of the markdown document, you also have pretty good preview of what the document looks like in simple html
  - On page commit UI.
    - the web editor makes it easy for you to commit the change right there as you finish editing.

## Advanced Topics

#### Nagvigation Links

Each document can express what index links it maybe have for the document page's nav bar to display.

The nav links for each document is configuration via [Front Matter](http://jekyllrb.com/docs/frontmatter/), a configuration/meta concept in Jekyll.

once you understand the concept a link structure for the document may look something like this:

```
links:
    - title: What is Driftt
      url: "#whats-driftt"
    - title: Installing
      url: "#installing"
    - title: What it looks like in action
      url: "#in-action"
      links:
          - title: HTML Example
            url: "#html-example"
    - title: Methods
      url: "#methods"
      links:
          - title: identify
            url: "#identify"
          - title: track
            url: "#track"
          - title: debug
            url: "#debug"
```

each link is structure as following
  - title: the name of the link
  - url: the hashtag link used to navigate within the document
  - links: its children links **IMPORTANT** children links are not allowed to have children. Currently we are limiting the link structure to two levels only.

Once the links structure is solidified, make sure the hashtag urls are associated with valid positions in the actually document. For example if you have a link:
```
links:
    - title: What is Driftt
      url: "#whats-driftt"
…
````

make sure somewhere in the document there is an actually index postion:

```
<div id="whats-driftt"></div>
# What is Driftt
```

This will allow the link to direct the page position just right above the ```# What is Driftt``` portion of the document. For now it has to be a HTML element :-\.
