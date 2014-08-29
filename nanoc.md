# nanoc

## Installation

```
gem install nanoc adsf
```

## Usage

Common commands:

 * `nanoc` - Compile the site
 * `nanoc view` - Start the webserver

## Markdown

First install kramdown: `gem install kramdown`.

Open `Rules` and change:

```
  if item[:extension] == 'css'
    # don’t filter stylesheets
```

to:

```
  if item[:extension] == 'md'
    filter :kramdown
    layout 'default'
  elsif item[:extension] == 'css'
    # don’t filter stylesheets
```