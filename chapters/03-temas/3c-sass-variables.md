Variáveis Sass
-----------------------------

Variáveis Sass permitem que você defina um valor uma única vez e o utilize em múltiplos lugares. Variáveis começam com o sinal de dolar ($) e são definidas como propriedades CSS. Você pode mudar o valor de uma variável em um lugar e todas as instâncias onde ela é utilizada também se alterarão. Por exemplo, se você quiser definir a mesma altura para dois seletores diferentes, você poderia criar uma variável chamada ```$control-height```:
```scss
$control-height: 40px;
```
Assim, você pode usar essa variável em múltiplos lugares. Por um questão de simplicidade, vamos atribuir ```$control-height``` para o atributo ```height``` de dois seletores:
```css
.header {
  height: $control-height;
}

.sub-header {
  height: $control-height;
}
```
Quando for traduzido para CSS, o resultado é o seguinte:
```css
.header {
  height: 40px;
}

.sub-header {
  height: 40px;
}
```
Isso é extremamente útil se você decidir posteriormente mudar o valor de ```$control-height``` que está sendo usado por múltiplos seletores. Em vez de revisar todo o seu código para encontrar os lugares de mudar esse valor, bastará você atualizar a variável ```$control-height```.

Variáveis Sass andam de mãos dadas com o Ionic. Com alguns frameworks CSS, você tem que criar um novo estilo e substituir os estilos do framework para alterar a aparência do seu aplicativo. Com o Ionic, você pode modificar o Sass diretamente, de modo que o arquivo CSS que é gerado tem a personalização que você deseja.

Saiba como você pode substituir variáveis Sass do Ionic, a fim de obter um estilo personalizado para seu aplicativo na [próxima seção](http://ionicframework.com/docs/v2/theming/overriding-ionic-variables/).