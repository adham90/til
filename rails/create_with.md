## create_with
Find the first user named "Scarlett" or create a new one with a particular last name.
*example*
```ruby
User.create_with(last_name: 'Johansson').find_or_create_by(first_name: 'Scarlett')
```
> **Resources:**<br/>
> [ruby on rails api](http://api.rubyonrails.org/classes/ActiveRecord/Relation.html#method-i-find_or_create_by)<br/>
