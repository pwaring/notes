# Jekyll

## Quick start

```
gem install jekyll
jekyll new myblog
cd myblog
jekyll serve
```

## Building

`jekyll build` will build the contents of the current directory into `./_site`.

## Filesystem layout

`_drafts`: Unpublished posts, without a date. Filename: `title.markdown`

`_posts`: Finalised posts. Filename: `year-month-date-title.markdown`

Any other directories (e.g. `css`) will be copied verbatim into `_site`.
