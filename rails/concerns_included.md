## Concerns included

The code contained within the `included` block will be executed within the context of the class that is including the module.

*example*
```ruby
module MyModule
  extend ActiveSupport::Concern
  included do
    # somecode
  end
end

class MyClass < ActiveRecord::Base
  # the code within included block will be executed immediately
  include MyModule
end
```
> **Resources:**<br/>
> [Code Concerns in Rails 4 Models blog post](https://goo.gl/1tm029)<br/>
> [stackoverflow](http://stackoverflow.com/questions/28009772/ruby-modules-included-do-end-block)
