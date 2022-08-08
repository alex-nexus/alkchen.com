---
layout: post
type: book_summary
title:  A Philosophy of Software Design
book_authors:  [John Ousterhout]
author: ashishb
categories: software
tags: [testing,documentation,complexity,coding]
description: "Good system designers get to spend a larger fraction of time in the design phase. Poor designers spend most of their time chasing bugs in complicated and brittle code."
featured: true
amazon_url: https://www.amazon.com/Philosophy-Software-Design-2nd/dp/173210221X/ref=sr_1_1?crid=175A4LGFSFC9N&keywords=A+Philosophy+of+Software+Design&qid=1659927342&sprefix=a+philosophy+of+software+design%2Caps%2C232&sr=8-1
source_url: https://ashishb.net/book-summary/book-summary-a-philosophy-of-software-design-by-john-k-ousterhout/
image: https://i.gr-assets.com/images/S/compressed.photo.goodreads.com/books/1531857377l/39996759._SX318_.jpg
image_type: tall
---

> Good system designers get to spend a larger fraction of time in the design phase. Poor designers spend most of their time chasing bugs in complicated and brittle code.

## Complexity
  - Problem decomposition is the central design task that programmers face every day. The greatest limitation in writing software is our ability to understand the systems we are creating.
  - Eventually, everyone reaches a point where your first design ideas are no longer good enough; if you want to get really great results, you have to consider a second possibility, or perhaps a third, no matter how smart you are.
  - Complexity can be reduced by eliminating special cases or using identifiers in a consistent fashion. The second approach to complexity is to encapsulate it so that programmers can work on a system without being exposed to all of its complexity at once. Isolating complexity in a place where it will never be seen is almost as good as eliminating the complexity entirely.
  - The waterfall model rarely works well for software. Incremental development means that software design is never done.
  - Tactical programming makes it nearly impossible to produce a good system design. Typically, other engineers must clean up the messes left behind by the tactical tornado, which makes it appear that those engineers (who are the real heroes) are making slower progress than the tactical tornado.
  - Your job as a developer is not just to create code that you can work with easily, but to create code that others can also work with easily. Your primary goal must be to produce a great design, which also happens to work. This is strategic programming.
  - In general, the lower layers of a system tend to be more general-purpose and the upper layers more special-purpose.
  - In general, developers tend to break up methods too much. Splitting up a method introduces additional interfaces, which add to the complexity. It also separates the pieces of the original method, which makes the code harder to read if the pieces are actually related. You shouldn’t break up a method unless it makes the overall system simpler.

## Handling errors and exceptions
  - Exception aggregation works best if an exception propagates several levels up the stack before it is handled; this allows more exceptions from more methods to be handled in the same place. This is the opposite of exception masking: masking usually works best if an exception is handled in a low-level method.
  - When exception handling code fails, it’s difficult to debug the problem, since it occurs so infrequently.
  - The Unix operating system defines file deletion more elegantly. In Unix, if a file is open when it is deleted, Unix does not delete the file immediately.

## Documentation
  - Provide precision in comments by clarifying the exact meaning of the code. Other comments provide information at a higher, more abstract, level than the code; these comments provide intuition. The comment that describes a method or variable should be simple and yet complete. If you find it difficult to write such a comment, that’s an indicator that there may be a problem with the design of the thing you are describing.
  - If the information in a comment is already obvious from the code next to the comment, then the comment isn’t helpful. One example of this is when the comment uses the same words that make up the name of the thing it is describing.
  - If documentation is duplicated, it is more difficult for developers to find and update all of the relevant copies.

## Writing code
  - Once a codebase turns to spaghetti, it is nearly impossible to fix. Google and VMware grew up around the same time as Facebook, but both of these companies embraced a more strategic approach. A developer should not need to understand the implementations of modules other than the one he or she is working in.
  - The greater the distance between a name’s declaration and its uses, the longer the name should be.
  - Adding code can sometimes simplify the interface. For example, adding garbage collection to a system actually shrinks its overall interface, since it eliminates the interface for freeing objects.
  - Imagine two classes one writing to a file and one reading from it. Even if neither class exposes that information in its interface, they both depend on the file format: if the format changes, both classes will need to be modified. Back-door leakage like this is more pernicious than leakage through an interface because it isn’t obvious.
  - Information hiding can often be improved by making a class slightly larger. Whenever possible, classes should do the right thing without being explicitly asked. Defaults are an example of this.
  - It is more important for a module to have a simple interface than a simple implementation. Configuration parameters are an example of moving complexity upwards instead of down. When deciding whether to combine or separate, the goal is to reduce the complexity of the system as a whole and improve its modularity. For example, in Java, a combined BufferedInputStream + FileInputStream class would have been better. It might provide methods to disable or replace the default buffering mechanism, but most users would not need to learn about them.
  - Module’s functionality should reflect your current needs, but its interface should not. If a system contains adjacent layers with similar abstractions, this is a red flag that suggests a problem with the class decomposition.
  - A pass-through method is one that does nothing except pass its arguments to another method, usually with the same API as the pass-through method. This typically indicates that there is not a clean division of responsibility between the classes. Eliminating pass-through variables can be challenging. One approach is to see if there is already an object shared between the topmost and bottommost methods. Otherwise, all those variables should be combined into a single context variable. Without discipline, a context can turn into a huge grab-bag of data that creates nonobvious dependencies throughout the system. Contexts may also create thread-safety issues; the best way to avoid problems is for variables in a context to be immutable. Unfortunately, I haven’t found a better solution than contexts.
  - Consistency creates cognitive leverage: once you have learned how something is done in one place, you can use that knowledge to immediately understand other places that use the same approach. The best way to enforce coding conventions is to write a tool that checks for violations and make sure that code cannot be committed to the repository unless it passes the checker.
  - Developing incrementally is generally a good idea, but the increments of development should be abstractions, not features.

## Testing
  - Without a test suite, it’s dangerous to make major structural changes to a system. As a result, developers avoid refactoring in systems without good test suites; they try to minimize the number of code changes for each new feature or bug fix, which means that complexity accumulates and design mistakes don’t get corrected.
  - The problem with test-driven development is that it focuses attention on getting specific features working, rather than finding the best design.
  - Before making any changes, measure the system’s existing behavior. This serves two purposes. First, the measurements will identify the places where performance tuning will have the biggest impact. The second purpose of the measurements is to provide a baseline so that you can re-measure performance after making your changes to ensure that performance actually improved.