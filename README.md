# SEO Recipe for Drupal

---

## Overview
A powerful SEO toolkit for Drupal applications, designed to optimize content for search engines. This package provides configurable metadata management, schema markup, and URL handling, ensuring SEO best practices are maintained. Ideal for improving visibility and search rankings across your Drupal site.

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
        "url": "https://github.com/nikolabintev/seo-recipe"
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
composer require nikolabintev/seo-recipe
```

---

## Applying the recipe

Apply the recipe using the following command:
```bash
php web/core/scripts/drupal recipe web/recipes/contrib/seo-recipe

```

---
