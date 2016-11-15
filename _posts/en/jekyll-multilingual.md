That's nice of you, @StartZeroGnu, but once again, the thanks should go Sylvain Durand.

But just some ramdom thoughts that were not obvious at first (at least for me) about the topic (and that hopefully can help some one out there):

### Expanding
A really nice aspect of this method is that one can use only what is necessary, but still being able to expand upon it. Let's that there a couple of posts translated to another language and that the "Toggle Switch" button is working.
If in the future the project gets more articles into another language, it is possible to implement a translated menu as well (and offer a better experience to the user).

If the project has a lot menus and/or a lot of other languages involved, the `_config.yml` might become a mass. But it is always possible to create something like`_data/nav.yml` and have a unique place for handling the navigation.

Then, in the layout, the file can be called as:

```
{% for nav in site.data.nav.t[page.lang] %}
```

Thanks to @Chris 's themes for pointing the way to `_data/*yml`.

### Styling special characters
I've got in a weird situation where a native speaker said that all those weird two characters (the language menu) correspond to abbreviations in their languages. So I decided in stead of using those two characters (they were obvious for me, but not for someone not used to see multilangual pages), to use the full name of the language, in the language. 
It worked nice locally, but once pushed, it couldn't be built because SASS could't handle those characters as CSS's classes (`.português` and `.français` for exemple). If there is a way to tell CSS (or any other framework) to use that, I would like to hear about.

But it worked adding something like this to the frontmatter:
```
lang: français
ref: about
class: fr
```

So, in order to compose the menu, the html got like this:

```
<ul>
{% assign posts=site.posts | where:"ref", page.ref | sort: 'lang' %}
{% for post in posts %}
<li>
<a href="{{ post.url }}" class="{{ post.class }}">{{ post.lang }}</a>
</li>
{% endfor %}
```
