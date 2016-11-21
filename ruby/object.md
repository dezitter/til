# #is_a? vs #kind_of? vs #instance_of?

Given the following example:

```ruby
module ParentModule; end
module ChildModule;  end

class Parent;
  include ParentModule
end

class Child < Parent
  include ChildModule
end

child  = Child.new
parent = Parent.new
```

The methods behave as below:

* `obj.kind_of?( klass )`
 * `true` if *klass* is the class or a superclass of *obj*
 * `true` if *klass* is a module included in *obj*

```ruby
child.kind_of? Parent       == true
child.kind_of? ParentModule == true # Child include ParentModule through its superclass Parent
child.kind_of? Child        == true
child.kind_of? ChildModule  == true

parent.kind_of? Parent       == true
parent.kind_of? ParentModule == true
parent.kind_of? Child        == false
parent.kind_of? ChildModule  == false
```

* `obj.instance_of?( klass )`
 * returns `true` **only** if *klass* is the class of *obj*

```ruby
child.instance_of? Parent       == false
child.instance_of? ParentModule == false
child.instance_of? Child        == true
child.instance_of? ChildModule  == false

parent.instance_of? Parent       == true
parent.instance_of? ParentModule == false
parent.instance_of? Child        == false
parent.instance_of? ChildModule  == false
```

* `#is_a?` is an alias of `#kind_of?`
 * both point to the same implementation (see [ruby/object.c](https://github.com/ruby/ruby/blob/v2_3_0/object.c#L3461))
