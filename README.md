# Just-validate

Implementação bem simples da biblioteca.

Para maiores informações acesse a documentação no link: [Just-validate](https://github.com/horprogs/Just-validate)

1. Crie um arquivo `html` e na mesma pasta execute o comando:  
```
npm install just-validate --save
```
2. Copie e cole o código abaixo no arquivo `html`:
```html
<!DOCTYPE html>
<html lang="pt-br">

<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Just-validate</title>

  <style>
    header {
      text-align: center;
    }

    form {
      display: flex;
      flex-direction: column;
      align-items: center;
    }

    label,
    button {
      margin-top: 10px;
    }
  </style>
</head>

<body>
  <header>
    <h1>Just-validate</h1>
  </header>
  <form>

    <!-- Adicionar nas tags input o atribut data-validate-field="identificador" -->
    <label for="name">Nome</label>
    <input type="text" name="name" id="name" data-validate-field="name"> <!-- identificador predefinido-->

    <label for="email">E-mail</label>
    <input type="text" name="email" id="email" data-validate-field="email">

    <label for="numero">Apenas números</label>
    <input type="text" name="numero" id="numero" data-validate-field="num">

    <button>Enviar</button>
  </form>

  <!-- Adicionado tag script após executar comando (npm install just-validate --save) na pasta do projeto. -->
  <script src="node_modules/just-validate/dist/js/just-validate.min.js"></script>

  <script>
    const regEx = /^\d*$/; // Regular Expression para números inteiros

    function mostraErros() {
      alert('Formulário com erros!');
    }

    function mostraSucesso() {
      alert('Formulário preenchido com sucesso!');
    }

    // Objeto para regras
    const rules = {
      rules: {
        num: {
          required: true,
          strength: {
            custom: regEx
          }
        }
      },
      messages: {
        num: {
          strength: 'Apenas números'
        }
      },
      focusWrongField: true,
      submitHandler: mostraSucesso,
      invalidFormCallback: mostraErros
    }


    // Aplicando regras da biblioteca ao formulário e objeto com regras customizadas
    new JustValidate('form', rules);
  </script>
</body>

</html>
```