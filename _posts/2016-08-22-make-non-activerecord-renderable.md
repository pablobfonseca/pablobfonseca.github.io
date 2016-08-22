---
layout: post
title:  "Make non ActiveRecord classes renderable"
date:   2016-08-22 18:00
categories: ruby, rails
---

In order to render a new partial without being an "Rails" object we can rewrite the method `to_patial_path` to do so:

```ruby
class Timeline
  def to_partial_path
    "timeline/timeline"
  end
end
```

Now we just need to create the view in `app/views/timeline/_timeline.htm.erb` and it's going to work like a charm!

or, we can extend the `ActiveModel::Naming` to make it works as well:
```ruby
class Timeline
  extend ActiveModel::Naming
end
```

<q>Happy coding!</q>
