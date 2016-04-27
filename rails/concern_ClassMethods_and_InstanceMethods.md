## Concern ClassMethods and InstanceMethods

*example*
```ruby
module MyModule
  extend ActiveSupport::Concern

  module ClassMethods
    # any method placed here will apply to classes, like Hickwall
  end

  module InstanceMethods
    # any method placed here will apply to instaces, like @hickwall
  end
end
```
