---
author: André van Delft
title: Tailwind Typography
---

<img src="tailwind-logo.svg" style="zoom: 150%" />

Until now, trying to style an article, document, or blogpost with Tailwind has been a tedious task that required a keen eye for typography and a lot of complex custom CSS.

By default, Tailwind removes all of the default browser styling from paragraphs, headings, lists and more. This ends up being really useful for building application UIs because you spend less time undoing user-agent styles, but when you _really are_ just trying to style some content that came from a rich-text editor in a CMS or a markdown file, it can be surprising and unintuitive.

We get lots of complaints about it actually, with people regularly asking us things like:

> Why is Tailwind removing the default styles on my `h1` elements? How do I disable this? What do you mean I lose all the other base styles too?

We hear you, but we're not convinced that simply disabling our base styles is what you really want. You don't want to have to remove annoying margins every time you use a `p` element in a piece of your dashboard UI. And I doubt you really want your blog posts to use the user-agent styles either — you want them to look _awesome_, not awful.

The `@tailwindcss/typography` plugin is our attempt to give you what you _actually_ want, without any of the downsides of doing something stupid like disabling our base styles.

It adds a new `prose` class that you can slap on any block of vanilla HTML content and turn it into a beautiful, well-formatted document:

```html
<article class="prose">
  <h1>Garlic bread with cheese: What the science tells us</h1>
  <p>
    For years parents have espoused the health benefits of eating garlic bread
    with cheese to their children, with the food earning such an iconic status
    in our culture that kids will often dress up as warm, cheesy loaf for
    Halloween.
  </p>
  <p>
    But a recent study shows that the celebrated appetizer may be linked to a
    series of rabies cases springing up around the country.
  </p>
  <!-- ... -->
</article>
```

For more information about how to use the plugin and the features it includes, [read the documentation](https://github.com/tailwindcss/typography/blob/master/README.md).

---

## What to expect from here on out

What follows from here is just a bunch of absolute nonsense I've written to dogfood the plugin itself. It includes every sensible typographic element I could think of, like **bold text**, unordered lists, ordered lists, code blocks, block quotes, _and even italics_.

It's important to cover all of these use cases for a few reasons:

1. We want everything to look good out of the box.
2. Really just the first reason, that's the whole point of the plugin.
3. Here's a third pretend reason though a list with three items looks more realistic than a list with two items.

Now we're going to try out another header style.

### Typography should be easy

So that's a header for you — with any luck if we've done our job correctly that will look pretty reasonable.

Something a wise person once told me about typography is:

> Typography is pretty important if you don't want your stuff to look like trash. Make it good then it won't be bad.

It's probably important that images look okay here by default as well:

![Image caption](https://images.unsplash.com/photo-1556740758-90de374c12ad?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1000&q=80)

Now I'm going to show you an example of an unordered list to make sure that looks good, too:

- So here is the first item in this list.
- In this example we're keeping the items short.
- Later, we'll use longer, more complex list items.

And that's the end of this section.

## What if we stack headings?

### We should make sure that looks good, too.

Sometimes you have headings directly underneath each other. In those cases you often have to undo the top margin on the second heading because it usually looks better for the headings to be closer together than a paragraph followed by a heading should be.

### When a heading comes after a paragraph …

When a heading comes after a paragraph, we need a bit more space, like I already mentioned above. Now let's see what a more complex list would look like.

- **I often do this thing where list items have headings.**

  For some reason I think this looks cool which is unfortunate because it's pretty annoying to get the styles right.

  I often have two or three paragraphs in these list items, too, so the hard part is getting the spacing between the paragraphs, list item heading, and separate list items to all make sense. Pretty tough honestly, you could make a strong argument that you just shouldn't write this way.

- **Since this is a list, I need at least two items.**

  I explained what I'm doing already in the previous list item, but a list wouldn't be a list if it only had one item, and we really want this to look realistic. That's why I've added this second list item so I actually have something to look at when writing the styles.

- **It's not a bad idea to add a third item either.**

  I think it probably would've been fine to just use two items but three is definitely not worse, and since I seem to be having no trouble making up arbitrary things to type, I might as well include it.

After this sort of list I usually have a closing statement or paragraph, because it kinda looks weird jumping right to a heading.

## Code should look okay by default.

I think most people are going to use [highlight.js](https://highlightjs.org/) or [Prism](https://prismjs.com/) or something if they want to style their code blocks but it wouldn't hurt to make them look _okay_ out of the box.

Here's what a default `tailwind.config.js` file looks like at the time of writing:

```js
module.exports = {
  purge: [],
  theme: {
    extend: {},
  },
  variants: {},
  plugins: [],
};
```

Hopefully that looks good enough to you.

### What about nested lists?

Nested lists basically always look bad which is why editors like Medium don't even let you do it, but I guess since some of you goofballs are going to do it we have to carry the burden of at least making it work.

1. **Nested lists are rarely a good idea.**
   - You might feel like you are being really "organized" or something but you are just creating a gross shape on the screen that is hard to read.
   - Nested navigation in UIs is a bad idea too, keep things as flat as possible.
   - Nesting tons of folders in your source code is also not helpful.
2. **Since we need to have more items, here's another one.**
   - I'm not sure if we'll bother styling more than two levels deep.
   - Two is already too much, three is guaranteed to be a bad idea.
   - If you nest four levels deep you belong in prison.
3. **Two items isn't really a list, three is good though.**
   - Again please don't nest lists if you want people to actually read your content.
   - Nobody wants to look at this.
   - I'm upset that we even have to bother styling this.

The most annoying thing about lists in Markdown is that `<li>` elements aren't given a child `<p>` tag unless there are multiple paragraphs in the list item. That means I have to worry about styling that annoying situation too.

- **For example, here's another nested list.**

  But this time with a second paragraph.

  - These list items won't have `<p>` tags
  - Because they are only one line each

- **But in this second top-level list item, they will.**

  This is especially annoying because of the spacing on this paragraph.

  - As you can see here, because I've added a second line, this list item now has a `<p>` tag.

    This is the second line I'm talking about by the way.

  - Finally here's another list item so it's more like a list.

- A closing list item, but with no nested list, because why not?

And finally a sentence to close off this section.

## There are other elements we need to style

I almost forgot to mention links, like [this link to the Tailwind CSS website][tailwind]. We almost made them blue but that's so yesterday, so we went with dark gray, feels edgier.

<!-- The above link makes use of a link-reference. The reference is defined below, which will be displayed in Typora: -->

[tailwind]: https://tailwindcss.com "Tailwind docs"

We even included table styles, check it out:

| Wrestler                |    Origin    |           Finisher |
| ----------------------- | :----------: | -----------------: |
| Bret "The Hitman" Hart  | Calgary, AB  |       Sharpshooter |
| Stone Cold Steve Austin |  Austin, TX  | Stone Cold Stunner |
| Randy Savage            | Sarasota, FL |         Elbow Drop |
| Vader                   | Boulder, CO  |         Vader Bomb |
| Razor Ramon             | Chuluota, FL |       Razor's Edge |

We also need to make sure inline code looks good, like if I wanted to talk about `<span>` elements or tell you the good news about `@tailwindcss/typography`.

### Sometimes I even use `code` in headings

Even though it's probably a bad idea, and historically I've had a hard time making it look good. This _"wrap the code blocks in backticks"_ trick works pretty well though really.

Another thing I've done in the past is put a `code` tag inside of a link, like if I wanted to tell you about the [`tailwindcss/docs`](https://github.com/tailwindcss/docs) repository. I don't love that there is an underline below the backticks but it is absolutely not worth the madness it would require to avoid it.

#### We haven't used an `h4` yet

But now we have. Please don't use `h5` or `h6` in your content, Medium only supports two heading levels for a reason, you animals. I honestly considered using a `before` pseudo-element to scream at you if you use an `h5` or `h6`.

We don't style them at all out of the box because `h4` elements are already so small that they are the same size as the body copy. What are we supposed to do with an `h5`, make it _smaller_ than the body copy? No thanks.

### We still need to think about stacked headings though.

#### Let's make sure we don't screw that up with `h4` elements, either.

Phew, with any luck we have styled the headings above this text and they look pretty good.

Let's add a closing paragraph here so things end with a decently sized block of text. I can't explain why I want things to end that way but I have to assume it's because I think things will look weird or unbalanced if there is a heading too close to the end of the document.

What I've written here is probably long enough, but adding this final sentence can't hurt. If we want to have another line quickly we can always<br>force a line break in here.

## Syntax highlighting

We already showed some examples of codeblocks in `html` and `js`. Here are some other popular formats, to demo the syntax highlighting:

### CSS

```css
@tailwind base;
@tailwind components;
@tailwind utilities;

@layer base {
  h1 {
    @apply text-2xl;
  }
  h2 {
    @apply text-xl;
  }
  /* ... */
}

body {
  font-family: "Crimson Pro", "Alegreya", serif;
  margin: 0;
  font-size: 20px;
  --link-color: rgb(57, 139, 152);
  --link-background-color: rgba(100, 143, 150, 0.1);
}

.container {
  max-width: 700px;
  margin: auto;
  margin-top: 50px;
  padding: 1rem;
}
```

### Python

```python
from unidecode import unidecode
import re

from django.template.defaultfilters import slugify as _slugify

PREFIXES = ["der", "die", "das", "den"]

PREFIX_FILTER = re.compile(fr'^(?:{"|".join(PREFIXES)})\s+')


def gen_sort_key(value):
    # Normalize unicode
    value = unidecode(value)
    # Convert to lowercase
    value = value.lower()
    # Filter some prefixes
    value, n = PREFIX_FILTER.subn("", value)
    while n:
        value, n = PREFIX_FILTER.subn("", value)
    return value


def slugify(value):
    """Slugify function extended with `unidecode` for better unicode representation"""
    return _slugify(unidecode(value))
```

### JSON

```json
{
  "firstName": "John",
  "lastName": "Smith",
  "isAlive": true,
  "age": 27,
  "address": {
    "streetAddress": "21 2nd Street",
    "city": "New York",
    "state": "NY",
    "postalCode": "10021-3100"
  },
  "phoneNumbers": [
    {
      "type": "home",
      "number": "212 555-1234"
    },
    {
      "type": "office",
      "number": "646 555-4567"
    }
  ],
  "children": [],
  "spouse": null
}
```

### YAML

```yaml
address:
  city: New York
  postalCode: 10021-3100
  state: NY
  streetAddress: 21 2nd Street
age: 27
children: []
firstName: John
isAlive: true
lastName: Smith
phoneNumbers:
  - number: 212 555-1234
    type: home
  - number: 646 555-4567
    type: office
spouse: null
```

### JSX

```jsx
<>
  <Title>{users.name}</Title>
  <Header>
    <div className="flex items-center gap-8 text-xl truncate">
      {tabs.map((tabName, i) => (
        <a
          key={i}
          className={
            tabName === activeTab
              ? "font-semibold p-2" 
              : "block p-2 rounded-md hover:bg-transparent-white cursor-pointer"
          }
          onClick={() => setActiveTab(tabName)}
        >
          {tabName}
        </a>
      ))}
    </div>
  </Header>
  <UsersGrid />
</>
```

## Typora extensions

Additionally, Typora supports ==highlights==, ~~strikethrough~~, <u>underline</u>, inline formula's $E = mc^2$ and block-level formula's:

$$
R_{\mu \nu} - {1 \over 2}g_{\mu \nu}\,R + g_{\mu \nu} \Lambda =
{8 \pi G \over c^4} T_{\mu \nu}
$$

Tailwind also supports HTML blocks:

<div style="display: flex; justify-content: center;">
  <p style="margin: 0;">
   Look at this text!<br>
    It's centered!
  </p>
</div>

Also, here's a checklist![^1]

- [x] I have done this thing
- [ ] But not this one
- [ ] A checklist can have multiple paragraphs

  Like this one does. Here is some more text so it will span multiple lines, as you can see now.

- [ ] Some last item. I haven't done a lot yet!

### Diagrams

And, of course, there are diagrams! Examples are copied from [here](https://support.typora.io/Draw-Diagrams-With-Markdown/#sequence-diagrams-options).

#### Sequence

```sequence
Alice->Bob: Hello Bob, how are you?
Note right of Bob: Bob thinks
Bob-->Alice: I am good thanks!
```

#### Flowchart

```flow
st=>start: Start
op=>operation: Your Operation
cond=>condition: Yes or No?
e=>end

st->op->cond
cond(yes)->e
cond(no)->op
```

#### Mermaid

```mermaid
%% Example of sequence diagram
  sequenceDiagram
    Alice->>Bob: Hello Bob, how are you?
    alt is sick
    Bob->>Alice: Not so good :(
    else is well
    Bob->>Alice: Feeling fresh like a daisy
    end
    opt Extra response
    Bob->>Alice: Thanks for asking
    end
```

### GitHub style alerts

Typora has added support for in version 1.8!🎉

> [!NOTE]
> Highlights information that users should take into account, even when skimming.

> [!TIP]
> Optional information to help a user be more successful.
>
> > Maybe I want to add a quote as well?

> [!IMPORTANT]
> Crucial information **necessary** for users to succeed.

> [!WARNING]
> Critical content demanding [immediate user attention](#) due to potential risks.
>
> * You should style list markers inside this warning
> * So that lists blend well with the message container
>

Here is some normal text in between two alerts

> [!CAUTION]
> Negative potential consequences of an action.

### Table of contents

[TOC]

[^1]: And here is some footnote! What should we do with this?
