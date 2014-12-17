# Custom elements

Create common design components with custom HTML elements instead of the (stereo)typical `<div>`-itis we often run into.

Built by [@mdo](https://twitter.com/mdo) to scratch an idealogical itch.

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
    <input type="radio" id="radio1" name="radios" checked> Radio input
  </label>
  <label for="radio2">
    <input type="radio" id="radio2" name="radios"> Another radio input
  </label>
</formgroup>

<formgroup>
  <label for="checkbox1">
    <input type="checkbox" id="checkbox1" checked> Checkbox input
  </label>
  <label for="checkbox2">
    <input type="checkbox" id="checkbox2"> Checkbox input with a super long string of text that can wrap to a second line to show the hanging input.
  </label>
</formgroup>

---

## Grids

Uses custom `<row>`s and `<column>`s to create a basic grid layout. Columns are then sized with a `cols` attribute.

Note that not all possible column combinations are used here. I've purposely avoided adding 1, 5, 7, and 11 as they seem rather uncommon.

<row>
  <column cols="2">2</column>
  <column cols="2">2</column>
  <column cols="2">2</column>
  <column cols="2">2</column>
  <column cols="2">2</column>
  <column cols="2">2</column>
</row>

<row>
  <column cols="3">3</column>
  <column cols="3">3</column>
  <column cols="3">3</column>
  <column cols="3">3</column>
</row>

<row>
  <column cols="4">4</column>
  <column cols="4">4</column>
  <column cols="4">4</column>
</row>

<row>
  <column cols="6">6</column>
  <column cols="6">6</column>
</row>

<row>
  <column cols="8">8</column>
  <column cols="4">4</column>
</row>

<row>
  <column cols="9">9</column>
  <column cols="3">3</column>
</row>

<row>
  <column cols="10">10</column>
  <column cols="2">2</column>
</row>

---

## Alerts

Contextual messages for warnings, errors, status confirmation, and the like.

<alert>
  <p>This is an alert with some text in it.</p>
</alert>

<alert is="info">
  <p>This is an alert with some text in it.</p>
</alert>

<alert is="warning">
  <p>This is an alert with some text in it.</p>
</alert>

<alert is="danger">
  <p>This is an alert with some text in it.</p>
</alert>

---

## Dropdowns

Contextual menus for buttons and more. Built with a custom `<dropdown>` element and several `<button>` elements as the dropdown actions.

<button type="button" id="dropdown-toggle" active>
  Dropdown button
</button>
<dropdown role="menu" aria-labelledby="dropdown-toggle">
  <button type="button" disabled>Cut</button>
  <button type="button" disabled>Copy</button>
  <button type="button">Paste</button>
  <hr>
  <button type="button">Spelling and Grammar...</button>
  <hr>
  <button type="button">Inspect Element</button>
</dropdown>

---

## Combo buttons

Attach multiple buttons together when their actions relate to one another.

<combo-button role="group" aria-label="Combo button">
  <button type="button">Button</button>
  <button type="button">Button</button>
</combo-button>

<combo-button role="group" aria-label="Combo button with disabled button">
  <button type="button" disabled>Disabled</button>
  <button type="button">Button</button>
  <button type="button" active>Active</button>
</combo-button>

---

## Breadcrumb

Show the current path to a particular page with breadcrumb navigation.

<breadcrumb>
  <a href="#">Home</a>
  <a href="#">Subfolder</a>
  <a href="#">Subfolder</a>
  <a href="#">Page</a>
</breadcrumb>

---

## Does it work?
Yes, but beyond that I'm not sure, but I'm super intrigued.


