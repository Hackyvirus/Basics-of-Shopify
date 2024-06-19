# Build Shopify themes

Themes shape the online store experience for merchants and their customers. Build fast, flexible themes at scale using Liquid, Shopify's theme templating language, along with HTML, CSS, JavaScript, and JSON.

A theme determines the way that a Shopify online store looks, feels, and functions for merchants and their customers.

Shopify themes are built using Shopify's theme templating language, Liquid, along with HTML, CSS, JavaScript, and JSON. Using these languages, developers can create any look and feel that their clients want. Shopify provides several tools and best practices to accelerate the development process.

As a developer, you can build a custom theme for a specific merchant, customize a theme to meet a merchant's needs, or build a theme to sell in the Shopify Theme Store. You can also build apps that extend the functionality of a theme.

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

    <div>
    <main>
    <section>

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

## Section data

The sections attribute of JSON templates holds the data for the sections to be rendered by the template. These can be either theme sections or app sections. You can't share section data across JSON theme templates, so each section must have an ID that's unique within the template.

JSON templates can render up to 25 sections, and each section can have up to 50 blocks.

You can add sections to a template in code, or through the theme editor. The sections that are available to be added to a template in the theme editor might be limited by the enabled_on or disabled_on attribute of the section schema. If no enabled_on or disabled_on attribute is defined, then the section can be added to any template.

---

## article

The article template renders the article page, which contains the full content of the article, as well as an optional comments section for customers. This template is used for items like individual posts in a blog.