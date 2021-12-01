# Smart Buttons

![smart buttons](img/smart-buttons.png)

```python
class MyModel(models.Model):
  _name="my.model"

  name = fields.Char('Name')
  payments = fields.One2many('account.payment')

  def open_method_name(self):
    action = {
      'name': _('Payments'),
      'domain': [('id','in',payments.ids)],
      'view_type': 'form',
      'res_model': 'account.payment',
      'view_id': False,
      'view_mode': 'tree, form',
      'type': 'ir.actions.act_window'
    }
    return action
```


```xml
<odoo>
  <record>
    <field name="arch" type="xml">
      <form>
        <sheet>
          <div class="oe_button_box" name="button_box">
            <button name="open_method_name"
              string="Button label"
              type="object" class="oe_stat_button" icon="fa-cog">
              <field name="" widget=""/>
            </button>
          </div>
        </sheet>
      </form>
    </field>
  </record>
</odoo>
```