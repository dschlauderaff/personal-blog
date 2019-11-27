---
path: blog/ruby_hash_dot_notation
date: 2019-11-27T23:34:09.868Z
title: Using dot notation with a ruby hash
description: Rails tips
---
After spending so much time in javascript, I ran into an issue where I was trying to access the session object of a rails app and running into a no method error when trying to use dot notation `object.key` instead of `object["key"]` that ruby requires.

So a quick trip down stackoverflow lane produced this little bit that will convert a ruby hash with no dot notation into a struct that does have dot notation.

```ruby
    userinfo = session[:userinfo] # get the hash data
    json_data = userinfo.to_json  # make the data a json object
    JSON.parse(json_data, object_class: OpenStruct) # parse the json object as an OpenStruct object
```

Et voila! Dot notation works.
