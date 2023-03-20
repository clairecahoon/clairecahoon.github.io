---
layout: home
title: Welcome!

header:
    image: /assets/images/home.jpg  # Putting the path to an image here will add that image to this page's header.
    alt: "A large library with tall bookshelves and marble busts." # Describe the header image here
    caption: "[Photo by Alex Block on Unsplash](https://unsplash.com/@alexblock)" # Add a visible caption to your image or give credit to the photographer or source.

sidebar:
    nav: "categories"

include_categories: # Sets which project categories are visible as galleries on homepage. See _data/content.yml and https://digbmc.github.io/ds-project/how-to/adding-content/#editing-the-homepage for more instructions.
  - getting-started   
  - how-to

classes: # Setting the class as wide will extend the page's content into the right margin.
---

Welcome to the Critical Web Design Toolkit—we’re so glad you’re here. The CWDT is a learning resource and template created to simplify the creation of static websites for Digital Scholarship projects. This site was built to live up to our core values of sustainability and accessibility while maintaining an easy-to-use and minimalist design.

Hopefully, the Toolkit not only inspires you to build your best project, but also encourages you to continue your learning journey in web design and development.

To access this site's [GitHub repository, click here.](https://github.com/digbmc/ds-project) 


{% comment %} You can replace the text in this section with your own text such as an introduction to your site.

Below you will find instructions on how to install and configure your site as well as how to add and format your own content. You can safely delete them from your repository if you are done referencing them.{% endcomment %}

{% comment %}The text content in this section is written in Markdown (the text directly below the front matter that looks like plain, readable text), but you will notice that this section also contains some Liquid (in the curly brackets) and some HTML. This code adds some unique features to the homepage that Markdown itself cannot support. The Markdown text at the top of the section (above this comment) can be safely edited, but the Liquid and HTML code at the bottom (below this comment) should not be changed.{% endcomment %}

{% comment %} "Spotlight" projects display as boxes that take up the full width of this content section. They are ideal for highlighting your website's most important projects or if you do not have so many projects that a gallery view would be necessary. Add projects to this section by giving them the 'spotlight' category. {% endcomment %}

<div class="spotlight"> 
{% assign spotlight_projects = site.projects | where: 'category', 'spotlight' %}
{% include spotlight projects = spotlight_projects %}
</div>

{% comment %} The "collection_row" section displays a gallery of projects organized by category. You must specify which categories you would like to be displayed on your homepage in the front matter of this file under "include_categories", and the code below will loop through all of the projects, find the posts in each of the specified "include_categories", and display them in corresponding sections. {% endcomment %}
{% for c in page.include_categories %}
<div id="{{ c }}" class="pane">
<h2 class="category_title">{{ site.data.content.display_categories[c] }}</h2>
{% assign category_projects = site.projects | where: 'category', c  %}
{% include collection_row projects = category_projects %} 
</div>
{% endfor %}
