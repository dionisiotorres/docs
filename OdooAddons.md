# Odoo Addons

## How to remove addon from pgsql
```SQL
-- SELECT name FROM ir_module_module WHERE name like 'base_user_role%';
UPDATE ir_module_module SET state = 'to remove' WHERE name like 'base_user_role%';
```