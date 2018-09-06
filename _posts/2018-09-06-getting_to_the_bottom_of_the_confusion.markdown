---
layout: post
title:      "Getting to the bottom of the ||= Confusion"
date:       2018-09-06 21:43:03 +0000
permalink:  getting_to_the_bottom_of_the_confusion
---


Ah the double pipes equals in Ruby. I have stumbled upon the || = in one of my labs and have quickly become confused as to what it does and its purpose. I have seen many articles and blogs trying to explain this and some are more helpful than others. I will try to write out and explain || = in my terms so I can get more of an understanding myself!

[RubyInside.com](http://www.rubyinside.com/what-rubys-double-pipe-or-equals-really-does-5488.html) starts to explain the || = with common misconceptions.

"A common misconception is that a ||= b is equivalent to a = a || b, but it behaves like a || a = b.

In a = a || b, a is set to something by the statement on every run, whereas with a || a = b, a is only set if a is logically false (i.e. if it's nil or false) because || is 'short circuiting'. That is, if the left hand side of the || comparison is true, there's no need to check the right hand side."

To me, that means that || = assigns a value and completes the || = operator **ONLY** if the left side is false or nil. A simple example:

```
a = nil
b= 10
a || = b

a # => 10
```

Very simple but effective way to describe || =.  First, a was checked to see if it was false or nil value. Since a returned nil, b was checked an returned a value of 10. Thus, `a # => 10`. "In this [case](https://medium.com/@jaredrayjohnson1/ruby-operators-double-pipe-equals-bfcbe21a7177), we get the same result. When a is set to nil (or anything that evaluates to false), the ||= operator functions the same as = would. Let’s look at an example where a is given a “truthy” value."

```
a = 2
b = 4
a ||= b #=> 2
a #=> 2
```

If the left hand side of the comparison is true, there's no need to check the right hand side. This can be very useful in iterations. To solve one of my labs, I used the code below to add student's name and grade to the school roster.

```
def add_student(student_name, grade)
    roster[grade] ||= []
    roster[grade] << student_name
  end
```

As you can see from the code above, I am calling roster on an instance of the School class and returning the list of students as a hash of grades pointing to an array of students associated with each grade. This also prevents overwrites of student entries while adding students to the same grade.
