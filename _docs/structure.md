---
title: Folder Structure
permalink: /docs/structure/
---

First, create and register your theme, like you would normally do in Mageto 2. Following an example of a directory structure:

    app/design/frontend/Wamoco/theme-amado/
      - Wamoco_TwigTheme/
        - layout/
        - templates/
        - web/
          - css/
          - fonts/
          - img/
          - js/
          - templates/
          requirejs-config.js
        composer.json
        config.xml
        registration.php
        theme.xml

Note the Module directory `Wamoco_TwigTheme` and a separate config file `config.xml` which is described in detail in the following section. Twig templates will be placed under `Wamoco_TwigTheme/web/templates`. Any other assets which should be accessible in the frontend should also be placed under `web`. The remaining folders like `layout`, `templates` and `requirejs-config` behave like they normally do in a Magento 2 installation.
