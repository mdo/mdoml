---
layout: default
---

# Custom elements

Create common design components with custom HTML elements instead of the (stereo)typical `<div>`-itis we often run into.

Built by [@mdo](https://twitter.com/mdo). Learn more, suggest changes, or report bugs via [the GitHub repo](https://github.com/mdo/custom-elements).

## Premise

Instead of reinventing the same design components again, let's use custom HTML elements with a bit of CSS to create an extended HTML design language. Put another way, let's augment the lack of element breadth in the HTML language.

More specifically, there are questions I want to explore the answers to:

* What kind of elements would we need to build?
* Does this simplify the overall HTML or CSS?
* Does team communication and productivity improve with this element-based system vs classes?
* What could these common components be if they were natively supported?

This might not be as practical as a more mature, well-thought out system, but I wanted to experiment the idea anyway.

## Things to know

* This isn't about Web Components. This is specifically about writing non-compliant, custom HTML tags as a shorthand.
* This is for all modern browsers, and IE9+. **IE8 and below need help initializing custom HTML elements.** Consider using the HTML shim.
* By design, custom HTML elements have no assumed semantics. For example, you gain obvious browser-backed advantages by using a `<form>` over a `<custom-form>` element. **Don't replace semantic elements.**
* Because of that lack of browser-assumed semantics, theoretically there's no disadvantage with custom elements for many components. Instead of a `<div>` for dropdowns, `<dropdown>`s could be used with no discernable impact to accessibility.
* **Custom elements are inline by default.** If you need a block-level element, you'll need to specify that in the CSS.

---

## Potential concerns

* Accessibility wise, where do we need the ARIA roles? Likely in all the same places as a `<div>`-based approach.
* Does this perform well (enough?) in CSS benchmarks?
* What about future HTML spec name collisions?

---

## Form groups

Uses a custom `<formgroup>` element to contain, position, and align checkboxes and radios.

<formgroup>
  <label for="radio1">
    <input type="radio" id="radio1" name="radios" checked>
    Radio input
  </label>
  <label for="radio2">
    <input type="radio" id="radio2" name="radios">
    Another radio input
  </label>
</formgroup>

{% highlight html %}
<formgroup>
  <label for="radio1">
    <input type="radio" id="radio1" name="radios" checked>
    Radio input
  </label>
  <label for="radio2">
    <input type="radio" id="radio2" name="radios">
    Another radio input
  </label>
</formgroup>
{% endhighlight %}
