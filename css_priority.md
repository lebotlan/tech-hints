
# Mitigate CSS lack of priorities.

CSS is poorly designed. It is unmodular, it lacks composition operators. Its specification of z-index ordering is a joke...
(Yes, I am really angry after CSS spec.)

...And it lacks priorities on rules. 

## Priorities: the problem with current CSS spec.

- The official priority calculation (aka selector specificity) is unmodular. It works for small toy examples. It does not scale.
  For instance, you might want `span.verybigwarn` to have priority over `section.test > span`. 
- Your only option is to use `!important`, which is, again, unmodular and does not scale (it works only once, what if something is even more important?).

## Priorities: an easy fix.
- On every html document, I add an identifier `h` on the root html node.
- Then, in order to increase a selector priority, I prefix it with one or several `#h`.

`#h#h span.verybigwarn`

Of course, it is a poor fix. A better way to do this would be to define a set of named priority levels, along with a partial order on these names (this would be indeed modular).

Reference : [https://www.w3.org/TR/2018/REC-selectors-3-20181106/#specificity]



