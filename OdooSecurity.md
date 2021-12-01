# Odoo Security

## Resources
- https://github.com/Alliantum/odoo_easy_permissions
- https://github.com/OCA/server-backend/tree/12.0/base_user_role
- https://www.youtube.com/watch?v=wgPtgPbY4uc

## Groups
- Defined in security folder within a XML file
```xml
<!-- SHOW the Group like a Checkbox-->
<odoo>
    <record id="my_group_id" model="res.groups">
        <field name="name">Group Name</field>
    </record>
</odoo>
```

```xml
<!-- SHOW the Group within a Selector -->
<odoo>
    <record id="module_category_id" model="ir.module.category">
        <field name="name">My Category Name</field>
        <field name="description">Some text explaining the category</field>
        <field name="sequence">10</field>
    </record>
    <record id="my_group_id" model="res.groups">
        <field name="name">Group Name</field>
        <field name="category_id" ref="addon_name.module_category_id"/>
    </record>
</odoo>
```

## Record Rules
- Related with Groups
- If Groups is empty then is applicable to all the groups (it's like global rule)

## Access Rights
- Related with Groups
- Defined on **ir.model.access.csv** file on security folder
- Defined for each model
```csv
id,name,model_id:id,group_id:id,perm_read,perm_write,perm_create,perm_unlink
access_id,access.name,addon.model_model_name_id,addon.group_id,1,1,1,0
access_id_2,access.name.two,addon.model_model_name_id,,1,0,0,0
```
| id          | name        | model_id:id                   | group_id:id    | perm_read | perm_write | perm_create | perm_unlink |
| ----------- | ----------- | ----------------------------- | -------------- | --------- | ---------- | ----------- | ----------- |
| access_id   | access.name | addon.model_model_name_id     | addon.group_id | 1         | 1          | 1           | 0           |
| access_id_2 | access.name.two | addon.model_model_name_id |                | 1         | 0          | 0           | 0           |

## __manifest.py__
```python
{
    'data': [
        'security/security.xml',
        'security/ir.model.access.csv'
    ]
}
```