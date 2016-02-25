## instance_variable_set & instance_variable_get

### `instance_variable_set(p1, p2)`
`instance_variable_set` is a method provided by the Ruby language. It is used to set the instance variable names by symbol to object . The variable did not have to exist prior to this call. This means that you will be able to call the variable as:

```ruby
instance_variable_set(:@variable, 'bar')
puts @variable # 'bar'
```

*apidock example*
```ruby
class Fred
  def initialize(p1, p2)
    @a, @b = p1, p2
  end
end
fred = Fred.new('cat', 99)
fred.instance_variable_set(:@a, 'dog')   #=> "dog"
fred.instance_variable_set(:@c, 'cat')   #=> "cat"
fred.inspect                             #=> "#<Fred:0x401b3da8 @a=\"dog\", @b=99, @c=\"cat\">"
```

### `instance_variable_get(p1)`
Returns the value of the given instance variable, or nil if the instance variable is not set. The @ part of the variable name should be included for regular instance variables. Throws a NameError exception if the supplied symbol is not valid as an instance variable name.

*apidock example*
```ruby
class Fred
  def initialize(p1, p2)
    @a, @b = p1, p2
  end
end
fred = Fred.new('cat', 99)
fred.instance_variable_get(:@a)    #=> "cat"
fred.instance_variable_get("@b")   #=> 99
```

> Resources:
> Restful Rails Development Book by Silvia Puglisi<br/>
> instance_variable_set: http://apidock.com/ruby/Object/instance_variable_set<br/>
> instance_variable_get: http://apidock.com/ruby/Object/instance_variable_get<br/>
