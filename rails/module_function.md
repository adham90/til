##module_function(*args) private

Creates module functions for the named methods. These functions may be called with the module as a receiver, and also become available as instance methods to classes that mix in the module. Module functions are copies of the original, and so may be changed independently. The instance-method versions are made private. If used with no arguments, subsequently defined methods become module functions.

```ruby
module Mod
  def one
    "This is one"
  end
  module_function :one
end
class Cls
  include Mod
  def call_one
    one
  end
end
Mod.one     #=> "This is one"
c = Cls.new
c.call_one  #=> "This is one"
module Mod
  def one
    "This is the new one"
  end
end
Mod.one     #=> "This is one"
c.call_one  #=> "This is the new one"
```

> **Resources:**<br/>
> ApiDock: http://apidock.com/ruby/Module/module_function
