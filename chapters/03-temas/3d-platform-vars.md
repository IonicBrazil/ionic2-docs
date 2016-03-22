Estilos especificos de plataforma
---------------------------------

Ionic utiliza modelos para personalizar a aparência dos componentes para coincidir com a plataforma que você está usando. Por exemplo, quando você estiver vendo o aplicativo em um dispositivo Android, o ```<body>``` terá ```class="md"``` adicionado por padrão:
```html
<body class="md">
```

Abaixo segue uma tabela para os modelos padrão que são adicionados, baseados na plataforma:

[TABELA]

Você pode alterar o modelo que é atribuído na configuração do seu aplicativo. Portanto, se você queria o modelo do Material Design ```md``` no iOS, você poderia fazê-lo.

Sobreescrevendo os modelos de estilos 
---------------------------------

Cada componente Ionic tem até três folhas de estilo utilizadas para estilizá-lo. Por exemplo, o componente de abas tem uma folha de estilo única que consiste de estilos compartilhados entre todos os modelos, uma folha de estilo para o Material que contém os estilos para o modelo ```md```, e uma folha de estilo do iOS para, você adivinhou, o modelo do ```ios```. Nem todos os componentes estão decorados de forma diferente para cada modelo, assim alguns deles somente terão a folha de estilo única, ou a folha de estilo única e uma dos modelos.

É possível utilizar a classe que é aplicada ao *body* para substituir as propriedades específicas em um modelo de componentes. Por exemplo, se você queria substituir todos os botões do modelo do Material Design (md) para que tenham texto com todas as letras maiúsculas:

```css
.md button {
  text-transform: capitalize;
}
```

Os arquivos Sass para esses modelos também têm variáveis únicas que podem ser usadas para substituir os estilos. Usando o mesmo exemplo acima, nós poderíamos mudar o atributo ```border-radius``` do botão ```md```, alterando o valor da variável ```$button-md-border-radius```. Você pode fazer isso em seu próprio arquivo Sass personalizado ou em nosso arquivo principal Sass, antes do Ionic ser importado:

```scss
$button-md-border-radius: 8px;

// Ionic Sass
// ---------------------------------
@import "ionic";
```

Definindo atributos dinâmicamente
---------------------------------

Ao definir um atributo de forma dinâmica, você pode adicionar ou remover a funcionalidade de um componente com base em uma determinada condição. Para definir um atributo de forma dinâmica, use a seguinte sintaxe:

```html
<ion-list [attr.no-lines]="isMD ? '' : null">
```

Isto irá definir o atributo ```no-lines``` na lista de componentes se ```isMD``` for avaliada como verdadeira.
