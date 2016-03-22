Tematizando aplicativos Ionic
=============================

Tematizando seu aplicativo Ionic
-----------------------------

O suporte a temas já está incorporado em seus aplicativos Ionic. Para alterar o tema, basta ajustar os valores de ```$colors``` no arquivo ```app/theme/app.variables.scss```.

```scss
$colors: (

  primary:    #387ef5,
  secondary:  #32db64,
  danger:     #f53d3d,
  light:      #f4f4f4,
  dark:       #222,

);
```
A maneira mais rápida de alterar o tema do seu aplicativo Ionic é definir um novo valor para ```primary```, pois o Ionic usa a cor primária por padrão para botões e outros componentes.

Cores personalizadas
---------------------

Para adicionar cores personalizadas, basta adicioná-las em ```$colors```:

```scss
$colors: (
  // ...
  twitter:    #55acee
)
```

O Ionic torna as chaves de ```$colors``` disponíveis como propriedades de muitos componentes. Por exemplo, para usar nossa cor ```twitter``` adicione a chave como uma propriedade:
```html
<button twitter>I'm a button</button>
```


