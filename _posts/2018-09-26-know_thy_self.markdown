---
layout: post
title:      "Know Thy Self"
date:       2018-09-27 00:45:09 +0000
permalink:  know_thy_self
---


Self is very important in Ruby and one of the most important things to understand. Since self is very important, I will start from the beginning and write out my understanding of self to better understand and find if I need to learn more on the subject.

Self is the "default" or "current" object. I say current because the self object can be changed, moved, and passed around. Self is typically assisgned to objects in sequence. That is why scope is very important when it comes to self. [The Well Grounded Rubyist](https://www.manning.com/books/the-well-grounded-rubyist-second-edition) says it best. "Between them, *self* and *scope* are the master keys to orienting yourself in a Ruby program. If you you know what scope you're and know what object is self, you'll be able to tell what's going on, and you'll be able to analyze errors quickly."


The top level self is the most basic program context. Top level context is for any Ruby code that is not executing inside any class, module, method, or otherwise any sub-level code block. When you open a new file and type 

```
x = 1
```

a top-level local variable is created.

```
def m
end
```

creates a top-level method. Ruby provides a star-up self at this top level. Ruby is telling us that self, at least within the top level context, is an object called [main](http://airbrake.io/blog/ruby/self-ruby-overview).

> "This is because all execution within Ruby occurs within the context of an object. When working inside a particular class, it’s obvious that that parent class is the object of that context, but when Ruby first begins execution, it automatically creates the main object. Thus, our call to self above refers to the main object instance that Ruby generates for us."
> 

It is important to keep track of on self while writing classes, modules, and methods. With class defining, we can refer to self within that context as well. A great example came in one of the Flatiron labs when writing about a Musician class.

```
class Musician
    puts "Self is: #{self}"
end
```

will output

```
Self is: Muscian
```

This results in self falling under the Musician class. Here is an example from *The Well Ground Rubyist* that shows how self can move around

```
class C
   puts "Just started class C:"
   puts self                                        #Outputs C
   module M
     puts "Nested module C::M:"
     puts self                                          #Outputs C : : M
   end
   puts "Back in the outer level of C:"
   puts self                                        #Outputs C
end
```

Once the class or keyword is "crossed," the class or module whose defintion block that was last entered becomes self. Class Instance Methods on self work similar as well.

```
class Author

    # Instance method
    def name
        puts "Self inside class instance method is: #{self}"
        puts "Self.class inside class instance method is: #{self.class}"
        return "John Doe"
    end
end

# Define instance
author = Author.new
puts "Author class instance method 'name' is: #{author.name}"

Self inside class instance method is: #<Author:0x00000002bd77c8>
Self.class inside class instance method is: Author
Author class instance method 'name' is: John Doe

```

This is obviously the tip of the iceberg to understanding thy self (Ha). Very simplified. However, I believe i have shown what self is, how it can be used, and how it can be passed around. Finally, I hoped I showed the importance of keeping track of self. 
