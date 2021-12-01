# Translations

## Resources
- https://stackoverflow.com/questions/51594309/override-translation-from-original-module
- https://odoo-development.readthedocs.io/en/latest/dev/translation/overwrite-translation.html

1. Export the translation file from the add-ons you want to override.
2. Translate it using POEeit or similar.
3. Drop the translation file inside a i18n_extra folder in the addon. E.g.: addon/i18n_extra/fr.pot
4. Update the addon.

- ??? To overwrite original translation, the following values must be added to command line server:
_**--i18n-overwrite -u new_Inherited_module**_

## How to overwrite built-in translation
You may need to change built-in translation via a module. You could be done via data xml files by calling _set_ids method. For example, for menus it could look as following:
```xml
<function
  model="ir.translation"
  name="_set_ids"
  eval="('ir.ui.menu,name', 'model', 'ru_RU', [ref('project.menu_main_pm')], 'Проекты Компании', 'Project')"/>
```