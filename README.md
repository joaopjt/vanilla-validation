
# Vanilla Validation

A lightweight validation form inspired in [Jquery Validation](https://jqueryvalidation.org) (Still under coding).

⚡️ ~ 24kb in browser only. As a project dependency, it falls to 6kb only.

## Getting Started

**Download** the script file clicking [here](http://github.com/joaopjt/vanillajs-validation/blob/master/dist/vanillajs-validation.min.js)

OR

**Install package** via npm:
```bash
npm install vanillajs-validation
```
---

### Creating instance
```html
<form data-form>
  <div data-field-holder>
    <input name="testfield" />
    <span data-field-error></span>
  </div>
  <div data-input-holder>
    <input name="cpf" />
    <span data-field-error></span>
  </div>
</form>


<script src="vanillajs-validation.min.js"></script> // Import downloaded script file
<script type="text/javascript">
var form = document.querySelector('[data-form]');
var v = new vanillaValidation(form, {
  rules: {
    testfield: {
      minlength: 2,
      required: true
    },
    cpf: {
      cpf: true,
      required: true
    }
  },
  messages: {
    testfield: {
      minlength: 'O campo precisa de pelo menos 2 caracteres',
      required: 'Campo teste obrigatorio!'
    }
  }
});
</script>
```

You can import the module with ES6 syntax too:

```javascript
// const Validator = require('vanillajs-validation');
import Validator from 'vanillajs-validation';

const formValidation = new Validator(document.querySelector('[data-form]', {
  rules: {
    ...
  }
});
```
---
### Rules (required)

The rules should be an **object** passed by in ``options`` at the follow format:
```javascript
rules: {
  fieldName: {
    ruleName: value
  }
}
```

The default rules avaiable are:

|Rule Name       |Value Type                     |Description              |
|----------------|-------------------------------|-------------------------|
|`cep`           |**boolean**                    | [BR] postal code format |
|`cpf`           |**boolean**                    | [BR] CPF number         |
|`cnpj`          |**boolean**                    | [BR] CNPJ  number       |
|`email`         |**boolean**                    | Verify email format     |
|`equalTo`       |**string**               | A input selector string |
|`digits`        |**boolean**              | Only numbers            |
|`maxlength`     |**integer**              | Max value length        |
|`minlength`     |**integer**              | Min value length        |
|`required`      |**boolean**              | Not empty value         |

---

### Custom Error Messages
Adding a ``messages`` **object** in ``options`` at the follow format:

```javascript
messages: {
  fieldName: {
    ruleName: 'errorMessage goes here'
  }
}
```


## Advanced
### ``vanillaValidation``(``Form``, ``Options``)

**Form**
> Type: **DOM Element**
>
> The form DOM element

**Options**
> Type: **Object**
>
> Object with configuration, rules and custom error messages


## ``options``:

### Events:

**onfocusout** (default: **false**)
> Type: **Boolean**
>
> If true, make field validation on the **onfocusout** event trigger.

```javascript
{ // options object
  onfocusout: false
}
```

### Handlers:

**errorPlacement**
> Type: **Function**
>
> After a submit with errors, the **errorPlacement** is called for every field with an error. The function will receive 2 params, the **error** (An object with the error type and the message) and the **input** (The node of the input with error).

```javascript
{ // options object
  errorPlacement: function (error, input) {
    console.log(error); // { rule: exempleRule, message: 'The field has a exempleRule error' }
    console.log(field); // <input name="exemple" type="text" />
  }
}
```

**invalidHandler**
> Type: **Function**
>
> Called on submit if form has a error. The function receives one param: the **validator** with the instance object of vanillajs-validation;

```javascript
{ // options object
  invalidHandler: function (validator) {
    console.log(validator); // Validator instance object
  }
}
```

**submitHandler**
> Type: **Function**
>
> Called on submit instead of default form submit. The function receives one param: the **form** with the node reference to form;

```javascript
{ // options object
  submitHandler: function (form) {
    console.log(form); // <form data-form> ... </form>
  }
}
```

**

## Contribute

In first of all, fork the repo.

After clone the fork, make sure of use node `v6.11.4`. Install the dependencies, and **rollup** globally.
To build files, use the `rollup -c`.

Then, make a pull request with a nice description of changes.

## License

[MIT License](https://opensource.org/licenses/MIT).

## Made with ❤️ by
- [João Julio](http://github.com/joaopjt)

> be a part of this list too, contribute with us :)
