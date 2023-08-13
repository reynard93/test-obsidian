> Your biggest problem is the sheer amount of unknown unknowns
------------------------------------------------------------

When I backtracked the path I was walking in solidbook, I realized that the biggest problem all Code-First developers face is that **_you don't even know what you need to know, and you don't know how to BEGIN to know what you need to know._**

It's the wild west.

If you listen to what everyone else tells you to do, you'll learn new libraries and frameworks every few weeks and NOT lead yourself towards their depths.,

Clipped from [essentialist.dev | Master the Essentials of Software Design](https://www.essentialist.dev/products/the-software-essentialist/categories/2153149734/posts/2169189601) at 2023-08-13.> The Expert Junior Developer
---------------------------

This trap of taking a **breadth-first approach** keeps you stuck at the surface and can potentially turn you into the **_Expert Junior Developer_**.,

Clipped from [essentialist.dev | Master the Essentials of Software Design](https://www.essentialist.dev/products/the-software-essentialist/categories/2153149734/posts/2169189601) at 2023-08-13.> Do less, more.

> 🌀 **Focus on the main idea:** _Responsibilities_. The metaphysical, atomic unit of matter that describes what software is comprised of is called a **Responsibility** (for **doing** and **_knowing_**). Let's continually refine our understanding of this.,

Clipped from [essentialist.dev | Master the Essentials of Software Design](https://www.essentialist.dev/products/the-software-essentialist/categories/2153149734/posts/2169189601) at 2023-08-13.> ### Step 1: Shift your focus to Responsibilities instead of Code,

Clipped from [essentialist.dev | Master the Essentials of Software Design](https://www.essentialist.dev/products/the-software-essentialist/categories/2153149734/posts/2169189601) at 2023-08-13.> We want to get to Value-First so that you can do life-changing stuff.

But to do that, we need to get to Responsibility-First.

So the first step is changing what you place your awareness on.

Start to pay attention to the various **responsibilities** your tools handle.

Start to notice the various things that your tools **do** and **know**.

What are the things that your web server **_does_** and **_knows_**?

What about React? What does it **_do_** and what does it **know**?,

Clipped from [essentialist.dev | Master the Essentials of Software Design](https://www.essentialist.dev/products/the-software-essentialist/categories/2153149734/posts/2169189601) at 2023-08-13.> ### Step 2: Commit to becoming a Value-First developer (which means you have to become a fullstack developer)

You want to be able to produce as much value as possible.

That means you need the ability to create information systems from end to end.

But not just **any** information system. I'm not just talking about using CRUD and REST.

These need to be information systems that are **Software Artifacts** of **_Value_**.

This means they help **_users_**, help **customers** achieve their goals, and **_developers_** can carry out their common development use cases.,

Clipped from [essentialist.dev | Master the Essentials of Software Design](https://www.essentialist.dev/products/the-software-essentialist/categories/2153149734/posts/2169189601) at 2023-08-13.> ### Step 3: Build an information system from end to end, making all the mistakes

In this module, I will ask you to build a system from end to end.

But while you're doing it, don't worry about **best practices** or if you're doing things right.

**_Just make it work_**.

Make it work and survey the landscape of tools you need to use along the way.

How do they help you cross the gap?

### Step 4: Validate your understanding

As I said, the main challenge at the Code-First level is **unknown unknowns**.

I will give you some strategies for ensuring you understand the role your tools play, the responsibilities at play, and how they either help or hurt the three roles in achieving their goals.,

Clipped from [essentialist.dev | Master the Essentials of Software Design](https://www.essentialist.dev/products/the-software-essentialist/categories/2153149734/posts/2169189601) at 2023-08-13.> There’s a lot of great advice out there on how to write effective **User Stories.**

Typically, you want to follow this pneumonic tool called INVEST, which keeps stories:

*   “I” ndependent (of all others)
*   “N” egotiable (meaning that **customers** and **developers** can discuss them)
*   “V” aluable
*   “E” stimable (to a good approximation)
*   “S” mall (so as to fit within an iteration)
*   “T” estable (in principle, even if there isn’t a test for it yet),

Clipped from [essentialist.dev | Master the Essentials of Software Design](https://www.essentialist.dev/products/the-software-essentialist/categories/2153149734/posts/2169191459) at 2023-08-13.> The Starter Architecture: MVC
=============================

If software is made from Responsibilities…

And you know there’s a ton of them to handle…

From network requests to button clicks to database transitions to validation logic…

Then **architectural patterns are blueprints — starting points — that make big upfront decisions about how we’ll organize those responsibilities.**

If you’ve never done backend before, without this one foundational pattern, you’d probably be lost.

The pattern is called MVC.,

Clipped from [essentialist.dev | Master the Essentials of Software Design](https://www.essentialist.dev/products/the-software-essentialist/categories/2153149734/posts/2169191533) at 2023-08-13.> Architectural patterns use divide and conquer to make your code more maintainable
---------------------------------------------------------------------------------

Dividing large problems into smaller parts is generally a good idea, right?

Why’s that? Because it makes your code more **discoverable** and **understandable** for other developers.

And when your code is more discoverable and maintainable, it’s a lot easier to scale as it grows over time.

**Architectural patterns do this by separating your responsibilities into what are called Concerns.**,

Clipped from [essentialist.dev | Master the Essentials of Software Design](https://www.essentialist.dev/products/the-software-essentialist/categories/2153149734/posts/2169191533) at 2023-08-13.> Concerns
--------

What are concerns exactly?

### They’re categories of responsibilities,

Clipped from [essentialist.dev | Master the Essentials of Software Design](https://www.essentialist.dev/products/the-software-essentialist/categories/2153149734/posts/2169191533) at 2023-08-13.