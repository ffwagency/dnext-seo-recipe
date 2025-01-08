# DNext - SEO Recipe

## Table of Contents
- [Overview](#overview)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Applying the recipe](#applying-the-recipe)
- [Features](#features)

---

## Overview
A powerful SEO toolkit for DNext applications, designed to optimize content for search engines. This package provides configurable metadata management, schema markup, and URL handling, ensuring SEO best practices are maintained. Ideal for improving visibility and search rankings across your Drupal site.

---

## Prerequisites
Configure Drupal to apply recipes by following the instructions:
- [Drupal 10](https://git.drupalcode.org/project/distributions_recipes/-/blob/1.0.x/docs/getting_started.md)
- [Drupal 11](https://git.drupalcode.org/project/distributions_recipes/-/blob/1.0.x/docs/getting_started_d11.md)

---

## Installation

### Ignore the contributed recipes directory
Add the following line to the project's .gitignore file

```txt
# Ignore contributed recipes
web/recipes/contrib
```

### Configure composer.json
- Update the `repositories` section of the project's composer.json, so it includes a reference to this repository.
```json
"repositories": [
    {
        "type": "vcs",
        "url": "git@github.com:ffwagency/dnext-seo-recipe.git"
    }
]
```
- Configure the installer paths in the `extra` section of the project's composer.json.

```json
{
    "extra": {
        "installer-paths": {
            "web/recipes/contrib/{$name}": [
              "type:drupal-recipe"
            ]
        }
    }
}
```

### Require the package
Require the package using composer.
```bash
composer require jakala/dnext-seo-recipe
```

---

## Applying the recipe

### Cache rebuild
Before applying the recipe, ensure the cache is rebuilt, so the module and theme extensions are updated with
the newly installed ones from the recipe.

```bash
drush cr
```

### Apply

<strong>Important!</strong> The recipe must be applied within the Drupal container from Drupal's project root directory.
```bash
php core/scripts/drupal recipe recipes/contrib/dnext-seo-recipe
```
---

## Features

_The features below are general configurations. Content type-specific (or entity type-specific) configurations must be
captured in separate recipes._

### Metatags
The [metatags](https://www.drupal.org/project/metatag) setup includes both basic and advanced tags as well as Opem Graph and Twitter Cards configurations.

### Schema.org
Based on the [schemaorg module](https://www.drupal.org/project/schemaorg), it enhances the global metatag configuration with website and web page data.

### URL aliases
The [pathauto module](https://www.drupal.org/project/pathauto) is set up so it generate URL aliases for the following entity types:
- Nodes: `[node:title]`
- Taxonomy terms: `[term:name]`
- Users: `u/[user:account-name]`

### Redirects
The [redirect module](https://www.drupal.org/project/redirect) is installed and configured so when a URL is changed, a redirect is created to the new URL.

### Robots.txt
The [robots.txt module](https://www.drupal.org/project/robotstxt) allows you to maintain different robots.txt files if the same codebase is used for many sites.

### XML Sitemap
The XML sitemaps are based on the [Simple Sitemap module](https://www.drupal.org/project/simple_sitemap). It comes with two sitemap types: index and content.
The index sitemap includes links to all other sitemaps, whereas the content sitemap includes links to all content entities. It is worth mentioning that the
content sitemap isn't configured to include any content types as this is a content type-agnostic setup and should be configured per site.

_None of the sitemaps will be generated until the content sitemap is configured to include specific content types. This
is a per site configuration_
