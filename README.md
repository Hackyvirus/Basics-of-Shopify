# Build Shopify themes

Themes shape the online store experience for merchants and their customers. Build fast, flexible themes at scale using Liquid, Shopify's theme templating language, along with HTML, CSS, JavaScript, and JSON.

A theme determines the way that a Shopify online store looks, feels, and functions for merchants and their customers.

Shopify themes are built using Shopify's theme templating language, Liquid, along with HTML, CSS, JavaScript, and JSON. Using these languages, developers can create any look and feel that their clients want. Shopify provides several tools and best practices to accelerate the development process.

As a developer, you can build a custom theme for a specific merchant, customize a theme to meet a merchant's needs, or build a theme to sell in the Shopify Theme Store. You can also build apps that extend the functionality of a theme.

## Start Working Project

To start developing theme for your cliets, you have to follow the steps with me

1. **Register for Shopify Partner's Programm** : [Click Here](https://www.shopify.com/partners)

By Signing up for Parter's programs you will get access to create stores and after that you will upload your products their and as well as you will get theme editor in your browser. You will get access to multiple themes at themes sections,you can choose what you want to use as your primary theme. You can upload your custom theme that you have developed.

2. _Download Shopify theme kit_: [Click Here](https://shopify.dev/docs/storefronts/themes/tools/theme-kit/getting-started)
   Shopify theme kit is CLI tool, that will help as develop our shopify theme in our local environment and connect with your exhisting store on shopify.

use this command to install themekit on Windows:

```bash
choco install themekit
```

Use this cammand to install themekit on MacOS:

```bash
brew tap shopify/shopify
brew install themekit
```

3. _Get the Theme Password_: [Click here](https://apps.shopify.com/theme-access?shpxid=31bbb0ee-12BF-4973-8340-3E480DB8A39E)
   By using above link you will get access shopify's page where you have to add that into your shopify partener's account, you just have to click on left side, where you will see button to add that or you will see button get access. in this way you will get a password via your email. You have to copy that password, we will use that in next step.

4. _Create a theme_:

```bash
theme new --password=[your-password] --store="[your-store.myshopify.com]" --name=[theme name]
```

Running the theme new command does the following:

- Generates a basic theme template locally
- Creates a new theme in your Shopify store
- Uploads the new files to your Shopify store
- Creates or updates your config.yml file with the configuration for your new theme

5. _Push updates to your theme_:

```bash
theme watch
```

## Anatomy of a Shopify theme

A theme controls the organization, features, and style of a merchant's online store. Theme code is organized with a standard directory structure of files specific to Shopify themes, as well as supporting assets such as images, stylesheets, and scripts.

As a theme developer, you should optimize the organization, features, and style of your themes for specific market segments or use cases. The best themes are made with a specific merchant profile in mind. Learn more about considerations and best practices for designing your theme.

If you're building a theme for the Shopify Theme Store, then you need to meet certain requirements in terms of the layout options that your theme offers, your theme's style, and the features that you include.

## Content

## Theme files fall into the following general categories:

    - Markup and features - These files control the layout and functionality of a theme. They use Liquid to generate the HTML markup that makes up the pages of the merchant's online store.
    - Supporting assets - These files are assets, scripts, or locale files that are either called or consumed by other files in the theme.
    - Config files - These files use JSON to store configuration data that can be customized by merchants using the theme editor.

1). The layout file => The base of the theme. Use the layout file to host repeated theme elements like headers and footers.

2). The template => The template that controls what's displayed on a page. Each theme should include different types of templates to display different types of content, such as the home page and products. You can also create multiple templates for the same resource type and associate them with your store resources, to allow for variation. JSON templates act only as a wrapper for sections, while Liquid templates contain code.

3). The section groups rendered by the layout => Containers that enable merchants to add, remove, and reorder sections in areas of the layout file such as the header and footer.

4). The sections rendered by the template => Reusable, customizable modules of content that merchants can add to JSON templates and section groups.

5). The blocks that each section contains => Reusable, customizable modules of content that can be added to sections, removed, and reordered.

Features can be introduced into themes in Liquid template files, sections, blocks, and snippets. You can implement theme features using Liquid, CSS, and JavaScript. A theme's features determine how customers can interact with the content on an online store. For example, your theme needs to allow customers to add products to a cart by providing a Liquid form tag with a product type.

## Directory structure and component types

Themes must use the following directory structure:

    .

    ├── assets

    ├── config

    ├── layout

    ├── locales

    ├── sections

    ├── snippets

    └── templates

        └──

## Layouts

Layouts are the base of the theme, through which all templates are rendered.

Layouts are Liquid files that allow you to include content, that should be repeated on multiple page types, in a single location. For example, layouts are a good place to include any content you might want in your <head> element, as well as headers and footers.

You can edit the default theme.liquid layout, or you can create multiple custom layout files to suit your needs. You can specify which layout to use, or whether to use a layout at all, at the template level:

    - In JSON templates, the layout that's used to render a page is specified using the layout attribute.

    - In Liquid templates, the layout that's used to render a page is specified using the layout Liquid tag.

## content_for_header

The content_for_header object is required in theme.liquid. It must be placed inside the HTML <head> tag. It dynamically loads all scripts required by Shopify into the document head. These scripts are required for features like reCAPTCHA, Shopify apps, and more.

You shouldn't try to modify or parse the content_for_header object. If content_for_header changes, then the behavior of your Liquid will change.

## content_for_layout

The content_for_layout object dynamically outputs the content for each template. You need to add a reference to this object between the <body> and </body> HTML tags.

## Templates

Templates control what's rendered on each type of page in a theme.

Each page type in an online store has an associated template type. You can use the template to add functionality that makes sense for the page type. For example, to render a product page, the theme needs at least one template of type product. Similarly, to render a metaobject page, the theme needs at least one template of type metaobject/{metaobject-type}, for example: metaobject/book or metaobject/author, depending on the type of metaobject definition.

You can create multiple versions of the same template type to create custom templates for different use cases. For example, you can create a separate product template for outerwear products, or a separate page template for pages with video content.

## JSON vs. Liquid

If you want to use sections in a template, then you should use a JSON template.

JSON templates provide more flexibility for merchants to add, remove, and reorder sections, including app sections. Additionally, they minimize the amount of data in settings_data.json. Instead, data is stored directly in the template, which improves the performance of the theme editor.

## Template types

Each available template type represents a type of content in a merchant's online store. No template types are required. However, you must have a matching template for any page type that you want to render. For example, to render a product page, you need at least one template of type product.

You can have a maximum of 1000 JSON templates in your theme, across all template types. For example, if you have 20 JSON product templates, 10 JSON page templates, and 5 JSON collection templates, then you can add up to 965 additional templates to the theme.

## Alternate templates

In some cases, you might need to create different markup for the same template. For example, you might want to create an alternate template that includes different sections for specific products.

**You can't replace the default template with an alternate template. If the default template doesn't meet your needs, then you can edit the template code to customize it.**

## Name structure

Alternate template files use the following name structure, where template-name is the template name, template-suffix is the alternate name, and template-file-type is the file type, which is either json or liquid:

    template-name.template-suffix.template-file-type

For example, if you create an alternate JSON product template with the name of alternate, then the file name would be the following:

    product.alternate.json

## Use an alternate template

After an alternate template has been created, it can be applied in the following ways:

    - It can be assigned to an associated resource in the Shopify admin.
    - It can be previewed in the theme editor.
    - It can be rendered on the storefront with the view URL parameter.

## Render an alternate template

Alternate templates can be rendered on the storefront with the view URL parameter. This parameter should be in the format of ?view=[template-suffix], where [template-suffix] is the template's alternate name.

For example, given the product.alternate.json template from the previous section, and a product called Example product, you can render that product with that template using the following:

    /products/example-product?view=alternate

## Naming JSON templates

The filename must be a valid theme template type, with an optional suffix for an alternate template. For example, a product template can be named product.json or product.alternate.json.

A template can only exist as a JSON or Liquid template, not both. For example, if product.liquid already exists, then you can't create product.json.

## The wrapper property

The wrapper property makes it possible to insert HTML tags around all of the sections in a JSON template. You can use the following HTML tags:

1. `<div>`
2. `<main>`
3. `<section>`

```bash
    {
    "wrapper": "div#div_id.div_class[attribute-one=value]",
    "sections": {
        "main": {
        "type": "product"
        }
    },
    "order": [
        "main"
    ]
    }
```

## Section data

The sections attribute of JSON templates holds the data for the sections to be rendered by the template. These can be either theme sections or app sections. You can't share section data across JSON theme templates, so each section must have an ID that's unique within the template.

JSON templates can render up to 25 sections, and each section can have up to 50 blocks.

You can add sections to a template in code, or through the theme editor. The sections that are available to be added to a template in the theme editor might be limited by the enabled_on or disabled_on attribute of the section schema. If no enabled_on or disabled_on attribute is defined, then the section can be added to any template.

---

## article

The article template renders the article page, which contains the full content of the article, as well as an optional comments section for customers. This template is used for items like individual posts in a blog.

## Content

You should include the following in your article template or a section inside of the template:

    1. `The article object`
    2. `The comment form`

## Paginate article comments

Article comments can be accessed through the article object, and have a limit of 50 per page. For this reason, you should paginate article comments to ensure that they’re all accessible:

```javascript
{% paginate article.comments by 20 %}
  {% for comment in article.comments %}
    <!-- comment info -->
  {% endfor %}

  {{ paginate | default_pagination }}
{% endpaginate %}
```

## Sections

Sections are Liquid files that allow you to create reusable modules of content that can be customized by merchants. They can also include blocks which allow merchants to add, remove, and reorder content within a section.

For example, you can create an Image with text section that displays an image and text side-by-side with options for merchants to choose the image, set the text, and select the display order.

Sections can be dynamically added to pages using JSON templates or section groups, giving merchants flexibility to easily customize page layouts. Sections that are included in JSON templates or section groups can support app blocks, which give merchants the option to include app content within a section without having to edit theme code. JSON templates and section groups can render up to 25 sections, and each section can have up to 50 blocks.

Sections can also be included statically, which can provide merchants with in-context customization options for static content.

By default, sections are available for any template or section group. You can limit which templates and section groups have access in the section schema.

## Render a section

You can render sections in one of the following ways:

    - Reference the section in a JSON template, or a section group in a layout file.
    - Statically render the section with the section Liquid tag.
    - Use the Section Rendering API.

```bash
If you want to render sections inside a template, then use a JSON template. JSON templates provide more extensive customization options for merchants, and improve the theme editor's performance.
```

## Statically render a section

Whenever possible, you should avoid statically rendering sections. Instead, you should reference them in a JSON template or section group. Statically rendered sections can't be removed or reordered by merchants.

You can statically render a section using the Liquid section tag.

For example, to include a section in a Liquid template, you can include it with a section tag:

```bash
{% section 'featured-product' %}
```

     You can include a statically rendered section in multiple theme files. However, only one instance of the section exists. If you change section settings in one location, then the change will be applied to all locations where the section is rendered.

## Integrate sections with the theme editor

When users customize sections through the theme editor, the HTML of those sections is dynamically added, removed, or re-rendered directly onto the existing DOM, without reloading the entire page. However, any associated JavaScript that runs when the page loads won't run again.

Additionally, you must make sure that when a section or block is selected, that section or block becomes, and remains, visible while it’s selected. For example, a slideshow section should scroll into view when the section is selected, slide to a selected block (slide), and pause while that block is selected.

To help identify theme editor actions like section and block selection or reordering, you can use the JavaScript events emitted by the theme editor.

You might also want to prevent specific code from running in the theme editor. To do so, you can use Liquid and JavaScript variables for detecting the theme editor.

    Section files must define presets in their schema to support being added to JSON templates using the theme editor. Section files without presets should be included in the JSON file manually, and can't be removed using the theme editor.

## Support app blocks

App blocks allow app developers to create blocks for merchants to add app content to their theme without having to directly edit theme code.

## Section schema

Sections support the {% schema %} Liquid tag. This tag allows you to define various attributes of a section, such as the section name, any section blocks, and settings to allow for theme editor customization options.

## Schema

Each section can have only a single {% schema %} tag, which must contain only valid JSON using the attributes listed in Content. The tag can be placed anywhere within the section file, but it can’t be nested inside another Liquid tag.

The following is an example of a valid section schema.

```javascript
{% schema %}
{
  "name": "Slideshow",
  "tag": "section",
  "class": "slideshow",
  "limit": 1,
  "settings": [
    {
      "type": "text",
      "id": "title",
      "label": "Slideshow"
    }
  ],
  "max_blocks": 5,
  "blocks": [
     {
       "name": "Slide",
       "type": "slide",
       "settings": [
         {
           "type": "image_picker",
           "id": "image",
           "label": "Image"
         }
       ]
     }
  ],
  "presets": [
    {
      "name": "Slideshow",
      "settings": {
        "title": "Slideshow"
      },
      "blocks": [
        {
          "type": "slide"
        },
        {
          "type": "slide"
        }
      ]
    }
  ],
  "locales": {
    "en": {
      "title": "Slideshow"
    },
    "fr": {
      "title": "Diaporama"
    }
  },
  "enabled_on": {
    "templates": ["*"],
    "groups": ["footer"]
  }
}
{% endschema %}
```

## name

The name attribute determines the section title that is shown in the theme editor. For example, the following schema returns the following output:

```bash
{% schema %}
{
  "name": "Slideshow"
}
{% endschema %}
```

## tag

By default, when Shopify renders a section, it’s wrapped in a <div> element with a unique id attribute:

```bash
<div id="shopify-section-[id]" class="shopify-section">

  // Output of the section content

</div>
```

If you don’t want to use a <div>, then you can specify which kind of HTML element to use with the tag attribute. The following are the accepted values:

    1. `article`
    2. `aside`
    3. `div`
    4. `footer`
    5. `header`
    6. `section`

For example, the following schema returns the following output:

```bash
{% schema %}
{
  "name": "Slideshow",
  "tag": "section"
}
{% endschema %}
```

## class

When Shopify renders a section, it’s wrapped in an HTML element with a class of shopify-section. You can add to that class with the class attribute:

```bash
{% schema %}
{
  "name": "Slideshow",
  "tag": "section",
  "class": "slideshow"
}
{% endschema %}

```

Output:

```bash
<section id="shopify-section-[id]" class="shopify-section slideshow">
  // Output of the section content
</section>
```

## limit

By default, there's no limit to how many times a section can be added to a template or section group. You can specify a limit of 1 or 2 with the limit attribute:

```bash
{% schema %}
{
  "name": "Slideshow",
  "tag": "section",
  "class": "slideshow",
  "limit": 1
}
{% endschema %}
```

## settings

You can create section specific settings to allow merchants to customize the section with the settings object:

```bash
{% schema %}
{
  "name": "Slideshow",
  "tag": "section",
  "class": "slideshow",
  "settings": [
    {
      "type": "text",
      "id": "header",
      "label": "Header"
    }
  ]
}
{% endschema %}
```

## blocks

You can create blocks for a section. Blocks are reusable modules of content that can be added, removed, and reordered within a section.
