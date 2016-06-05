## Active Record Observer
Observer classes respond to life cycle callbacks to implement trigger-like behavior outside the original class. This is a great way to reduce the clutter that normally comes when the model class is burdened with functionality that doesn't pertain to the core responsibility of the class. Example:
```ruby
class CommentObserver < ActiveRecord::Observer
  def after_save(comment)
    Notifications.comment("admin@do.com", "New comment was posted", comment).deliver
  end
end
```
This Observer sends an email when a Comment#save is finished.
```ruby
class ContactObserver < ActiveRecord::Observer
  def after_create(contact)
    contact.logger.info('New contact added!')
  end

  def after_destroy(contact)
    contact.logger.warn("Contact with an id of #{contact.id} was destroyed!")
  end
end
```
This Observer uses logger to log when specific callbacks are triggered.

###Observing a class that can’t be inferred

Observers will by default be mapped to the class with which they share a name. So CommentObserver will be tied to observing Comment, ProductManagerObserver to ProductManager, and so on. If you want to name your observer differently than the class you’re interested in observing, you can use the ActiveModel::Observer.observe class method which takes either the concrete class (Product) or a symbol for that class (:product):
```ruby
class AuditObserver < ActiveRecord::Observer
  observe :account

  def after_update(account)
    AuditTrail.new(account, "UPDATED")
  end
end
```
If the audit observer needs to watch more than one kind of object, this can be specified with multiple arguments:
```ruby
class AuditObserver < ActiveRecord::Observer
  observe :account, :balance

  def after_update(record)
    AuditTrail.new(record, "UPDATED")
  end
end
```
The AuditObserver will now act on both updates to Account and Balance by treating them both as records.

> **Resources:**<br/>
> Ruby On Rails doc: http://api.rubyonrails.org/v3.2.0/classes/ActiveRecord/Observer.html
