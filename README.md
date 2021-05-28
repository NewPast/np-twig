NP Twig Front End for WordPress Custom Field and Advance Custom Fields. Renders data using a twig template. It supports both free ACF and ACF pro

## Arabic Version of this Article
* https://www.miniindustry.com/d/ar-np-twig

## Installation

1.  Install Timber plugin: [https://wordpress.org/plugins/timber-library/](https://wordpress.org/plugins/timber-library/)
2.  Upload this plugin folder to the ``/wp-content/plugins/`` directory, or install it through the WordPress plugins screen directly.
3.  Activate the plugin through the 'Plugins' screen in WordPress
4.  and you will more benefit from our plugin if you could install Advanced Custom Fields: [https://wordpress.org/plugins/advanced-custom-fields/](https://wordpress.org/plugins/advanced-custom-fields/)
5.  This plugin runs well on both AMP and none AMP sites

## Description of  WordPress Front End for Custom Field & ACF

*   I use [Twig](https://twig.symfony.com/) template to display your post or custom post or [Advanced Custom Fields](https://wordpress.org/plugins/advanced-custom-fields/)
*   [Twig](https://twig.symfony.com/) and [ACF](https://wordpress.org/plugins/advanced-custom-fields/) are a third-party plugin, we used them to render templates

### Template requirements of WordPress Front End for Custom Field

*   Ensure installs of Timber plugin: [https://wordpress.org/plugins/timber-library/](https://wordpress.org/plugins/timber-library/)
*   Then create a private post or page or of any post type
*   For custom post type template ensures that your template name looks like: `tpl-{{post_type}}`
*   or add a custom field to your post name it **twig** and store the template name inside it

## Custom Fields and ACF

*   WordPress supports custom fields, and you could add them directly to your post,
*   and ACF plugin gives more power to the custom fields
*   Use the Advanced Custom Fields plugin to take full control of your WordPress edit screens & custom field data.
*   Read more about ACF on [https://wordpress.org/plugins/advanced-custom-fields/](https://wordpress.org/plugins/advanced-custom-fields/)

## Template Syntax: a quick guide for WordPress Front End for Custom Field

Note: [WordPress Classic Editor](https://wordpress.org/plugins/classic-editor/) is preferred to edit templates

### Comments

*   Use `{# comments #}` for comments, and comments will not render to the user,

### Variables output

Variables in templets are post title, post object, and custom fields. To output post title you can use `{{ title }}`. If your post has a custom field called price. We use `{{ price }}` to output the price. Use a dot (.) to access attributes of a variable (methods or properties of an object, or items of an array: `{{ foo.bar }}`

### Conditional output

The `if` statement in Twig check if a variable has a value or an expression evaluates to `true` We can add conditions to display any text. Let's say that we have a custom field named "agent" and want to display a text when the field agent contains a text. We can write

<pre lang="twig">{% if agent %}
    We have an agent in your area
    Our agent: {{ agent }}
{% endif %}</pre>

another example; let's say that we have a field named price. We want to display a text if the price is zero

<pre lang="twig">{% if price == 0 %}
   &lt;p&gt;This product is free&lt;/p&gt;
{% endif %}
</pre>

Please note that we use the operator `==` to check the equality You can also test if an array is not empty:

<pre lang="twig">{% if meanings %}
   &lt;p&gt;The array or repeater field **meaning** contains some values&lt;/p&gt;
{% endif %}</pre>

### Closing condition block

Always use `{% endif %}` to close the previous if condition, Read more about [if keyword in twig](https://twig.symfony.com/doc/3.x/tags/if.html)

### Repeater field and arrays

If our field or variable is an array or a repeater field we can loop over each item in a sequence using for keyword

#### The for statement code example

<pre>{% for m in meanings %}
   Meaning: {{ m.meaning }}
{% endfor %}</pre>


#### The for statement format

*   We use  `{% for m in meanings %}` to loop over an array or repeater field called `meanings` using **`m`** to mention for each row
*   Inside the loop starts the subfields or array items with the variable name `**m.**`
*   Always close the loop use `{% endfor %}`
*   Read more about [the `for` keyword in twig](https://twig.symfony.com/doc/3.x/tags/for.html)

### Important notes for templates code

*   In WordPress classic editor show source and ensure there are no tags inside the template code; ex `{% <del><span></del> endfor <del></span></del> %}`
*   For more details, see: [https://twig.symfony.com/doc/2.x/](https://twig.symfony.com/doc/2.x/)

### Power templating with only 4 keyword

Using `if, endif, for and endfor` allows to generate a powerful template; however, twig contains many other useful keywords to see other keyword and how to use them visit [twig documentation](https://twig.symfony.com/doc/2.x/)

### Template Example

<pre>&lt;h2&gt;Meaning of {{ title }}&lt;/h2&gt;
{# This is a comment and will not render #}
{% for m in meanings %}
    {% if m.meaning %}
        Meaning: {{ row.meaning }}
    {% endif %}
    {% if m.example %}
        Example: {{ m.example }}
    {% endif %}
{% endfor %}
</pre>

### Output post data

We can access the post using the post keyword. to access any property of the post we put a dot (.)  and then we put the property name for example use `post.content` to access post content

<pre lang="twig"><h2>{{ post.title }}</h2>
   <img src="{{ post.thumbnail.src }}" 
        alt="{{ post.thumbnail.alt }}" >
{{ post.content }}
</pre>

read more about accessing post content on [timber documents](https://timber.github.io/docs/v2)

## Why templating engine and not a raw PHP programming language

*   More Simple; so templating is more readable, and very easy that allows users to learn quickly,
*   and Limit the allowed function to prevent bad mistakes,
*   and easy to edit using WordPress classic editor

## About Twig templating engine

*   The twig template engine process templates data, and output a webpage.
*   and it is a flexible, fast, and secure template engine for PHP.
*   We use Twig a template language, and we allow users to modify the template design.
*   It is fast because Twig compiles templates into optimized PHP code.
*   Get flexible, so it allows the developer to define its own custom tags and filters.
*   Read more about Twig on [https://twig.symfony.com](https://twig.symfony.com)

## Timber and Twig

*   Timber helps to include Twig in WordPress,
*   with Timber, you write your HTML using the Twig Template Engine separate from your PHP files,
*   and this cleans up your template code so, for example, and your Twig template can focus on the HTML and display.

## Developers and WordPress Front End for Custom Field

### Add custom data to fields

*   Edit the file user-functions.php
*   Create a function and name it `get_fields_{{post_type}}`
*   If your custom post type contains '-' replace it with '_'
*   I include a sample function in user-functions.php
*   Backup your functions, and keep in mind that the file user-function may be replaced on upgrade

### Add custom data for each singular page

*   Edit the file user-functions.php,
*   then create a function and name it `np_content_singular`
*   I include a sample function in user-functions.php
*   Backup your functions, and keep in mind that the file user-function may be replaced on upgrade

## Screenshots

1. A screenshot of the template edit using WordPress classic editor.

## Frequently Asked Questions about WordPress Front End for Custom Field

This section may be added in the next version
