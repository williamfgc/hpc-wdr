# HPC Workforce Development and Retention

## What is this?

This is a repository that contains the files for the official HPC Workforce Development and Retention group website hosted at https://hpcwdr.com.
The site is built with [Jekyll](https://jekyllrb.com/) and hosted on GitHub. 

## How do I contribute?

We encourage the community to contribute to the content of the website.  
To do this: fork the repository, make your proposed changes, test locally (see below), and then create a pull request against `main`. For more details about opening pull requests and issues, see our [Contributing Guide](.github/CONTRIBUTING.md).


### 1. How do I add a blog post?

You can add a blog post to the site by adding a markdown file in the [_posts](_posts)
folder, organized by year. Jekyll requires blog post files to be named according to the following format:

`YEAR-MONTH-DAY-title.MARKUP`

Where `YEAR` is a four-digit number, `MONTH` and `DAY` are both two-digit numbers, and `MARKUP` is the file extension representing the format used in the file. If you use a future date, Jekyll will not post the page until that date.

You can find an event template under [templates](templates/event_template.md).

```markdown
---
layout: post
title:  "Welcome to Jekyll!"
date:   2017-10-26 11:54:05 -0400
author: Kita Cranfill
categories: jekyll update
expires: 2025-10-26
---

Blog content here
```

The top section is frontend matter that must include the layout as "post", title, date, author, 
categories, and an expiration date.
Notice that the post date is a string that doesn't get parsed,
while the expires must be a date in the format shown.
The bottom section (the content) you can write any amount and length
of markdown that is desired. When the post is active (before expiration) the full content will
be shown on the "Blog" page. Once it expires, it will move into the posts archive.
In both cases, clicking on the post will take the viewer to it's page, and they can
view additional content and the url provided. In the case of the archive, the bulk of content
is only viewable on this page.


### 3. How do I add an event?

You can add an event or webinar to the site by adding a markdown file in the [_events](_events)
folder, organized by year. Do not use the full date (e.g. YYYY-MM-DD-<event-name>.md) in the file name,
Jekyll will not post pages that it interprets to have a future date in the filename. You can find an event template under [templates](templates/event_template.md).

```markdown
---
layout: event
title:  "Event #1"
location: Oak Ridge, TN # event location
event_url: https://ornl.gov/ # optional
date:   2022-10-26 11:54:05 -0400 # event_date
category: "webinar" # webinar or community
expires: 2025-10-26
repeated: false
---

Event content here
```

The top section is frontend matter that must include the title, location, layout as "event" 
event date, an expiration date, and a "repeated" variable (true or false).
Notice that the event date is a string that doesn't get parsed,
while the expires must be a date in the format shown.
The bottom section (the content) you can write any amount and length
of markdown that is desired. When the event is active (before expiration) the full content will
be shown on the "Events and Training" page. Once it expires, it will move into the events archive.
In both cases, clicking on the Event will take the viewer to it's page, and they can
view additional content and the url provided. In the case of the archive, the bulk of content
is only viewable on this page.

### What is a repeated event?


You'll notice that there is a folder called "repeated" in the events folder:

```
$ ls _events/
2019  2020  repeated
```

A repeated event is one that happens weekly, monthly, or on a regularly scheduled
basis that typically does not change, meaning that you wouldn't need to
update the post. A weekly call that has a description and a consistent link
to an agenda would be appropriate, while the same call that varies in schedule
or requires an updated description would not quality.
An annual event, or one that would require a different description, would
not be repeated, and should be placed in a folder named by date.
Repeated events are always shown at the top of the events page, and 
do not expire.

### 4. How do I add an announcement?

We maintain a list of announcements in [_data/announcements.yml](_data/announcements.yml).
You can add a new announcement to this list, and so that newer announcements appear at the top, we ask
that you **add the new entry to the top of the list.**
Specifically, we ask that you provide a name, description, and an expiration date to the posting.
The expiration date is not shown on the page, however it will determine when the job doesn't appear 
anymore. We suggest setting a timeframe such as a month, and if you want to extend it, you
can open a pull request to update the date. An example posting is shown below. This
announcement would appear on the site until the first of July, 2019.

```yml
- expires: 2019-07-01
  name: Announcement 1
  description: Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
```

### Previewing the Site

To preview the site locally, you'll need to [install jekyll](https://jekyllrb.com/docs/installation/)
It's then typical to go to the root of the site and issue (just once):

```bash
$ bundle install
```

And then (also in the top level directory of your forked repository) run 

```bash
$ jekyll serve
# or
$ bundle exec jekyll serve
```

and open your browser to <http://localhost:4000>.
If you are having trouble try `rm -rf _site`, followed by `bundle update`, then `bundle exec jekyll serve`.
