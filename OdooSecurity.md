# Odoo Security

## Resources
- https://github.com/Alliantum/odoo_easy_permissions
- https://github.com/OCA/server-backend/tree/12.0/base_user_role
- https://www.youtube.com/watch?v=wgPtgPbY4uc

## Groups
- Defined in security folder within a XML file
```xml
<record id="my_group_id" model="res.groups">
    <field name="name">Group Name</field>
</record>
```

## Record Rules
- Related with Groups
- If Groups is empty then is applicable to all the groups (it's like global rule)

## Access Rights
- Related with Groups
- Defined on ir.model.access.csv file on security folder
- Defined for each model
```csv
id,name,model_id:id,group_id:id,perm_read,perm_write,perm_create,perm_unlink
access_id,access.name,addon.model_model_name_id,addon.group_id,1,1,1,0
```