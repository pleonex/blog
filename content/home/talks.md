+++
widget = "pages"
headless = true
active = true

title = "Recent & Upcoming Talks"
subtitle = ""

weight = 60

[content]
  page_type = "talk"
  count = 0
  offset = 0
  order = "desc"

  # Filter posts by a taxonomy term.
  [content.filters]
    tag = ""
    category = ""
    publication_type = ""
    exclude_featured = false
    exclude_past = false
    exclude_future = false

[design]
  # Toggle between the various page layout types.
  #   1 = List
  #   2 = Compact
  #   3 = Card
  #   4 = Citation (publication only)
  view = 2
+++
