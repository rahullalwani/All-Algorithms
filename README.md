# Bootstrap notes

## 1.Buttons

### Button 

```
<div>
  <b-button>Button</b-button>
  <b-button variant="danger">Button</b-button>
  <b-button variant="success">Button</b-button>
  <b-button variant="outline-primary">Button</b-button>
</div>
```
### Link and router-link

```
<div>
  <b-button>I am a Button</b-button>
  <b-button href="#">I am a Link</b-button>
</div
```
### Type 
`You can specify the button's type by setting the prop type to 'button', 'submit' or 'reset'. The default type is 'button'.`

### Size

```
<b-row>
  <b-col lg="4" class="pb-2"><b-button size="sm">Small Button</b-button></b-col>
  <b-col lg="4" class="pb-2"><b-button>Default Button</b-button></b-col>
  <b-col lg="4" class="pb-2"><b-button size="lg">Large Button</b-button></b-col>
</b-row>

```
### Solid Color Variants

```
<div>
  <b-button variant="primary">Primary</b-button>
  <b-button variant="secondary">Secondary</b-button>
  <b-button variant="success">Success</b-button>
  <b-button variant="danger">Danger</b-button>
  <b-button variant="warning">Warning</b-button>
  <b-button variant="info">Info</b-button>
  <b-button variant="light">Light</b-button>
  <b-button variant="dark">Dark</b-button>
</div>
```
### Outline Color Variants

```
<div>
  <b-button variant="outline-primary">Primary</b-button>
  <b-button variant="outline-secondary">Secondary</b-button>
  <b-button variant="outline-success">Success</b-button>
  <b-button variant="outline-danger">Danger</b-button>
  <b-button variant="outline-warning">Warning</b-button>
  <b-button variant="outline-info">Info</b-button>
  <b-button variant="outline-light">Light</b-button>
  <b-button variant="outline-dark">Dark</b-button>
</div>

```
### Link Variant

```
Variant link will render a button with the appearance of a link while maintaining the default padding and size of a button.

<div>
  <b-button variant="link">Link</b-button>
</div>

```

### Block Level Button
```
Create block level buttons — those that span the full width of a parent — by setting the block prop.

<div>
  <b-button block variant="primary">Block Level Button</b-button>
</div>
```
### Disabled State

```
<div>
  <b-button disabled size="lg" variant="primary">Disabled</b-button>
  <b-button disabled size="lg">Also Disabled</b-button>
</div>

```
