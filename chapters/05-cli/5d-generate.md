# Descrição #

Ionic agora fornece uma funcionadede de gerador para criar paginas e serviços para sua aplicação. Isso faz ir de um aplicativo básico para um aplicativo cheio de recursos de navegação muito fácil.

Para criar uma pagina, você pode usar o seguinte comando:

```shell
# ionic g page <nomePagina>
ionic g page myPage

√ Create app/pages/my-page/my-page.html
√ Create app/pages/my-page/my-page.js
√ Create app/pages/my-page/my-page.scss
```

Isso irá gerar um arquivo html, arquivo sass e um arquivo js com os seus componentes definidos.

Para criar um um serviço, você pode substituir **page** por **provider**:

```shell
ionic g provider MyData

√ Create app/pages/my-data/my-data.js
```

Isso irá criar uma classe padrão com um simples **http** get request usando a classe **http** do Angular.

## Uma breve nota sobre convenções  de nomenclatura ##

Ionic 2 usa kebob-casing para nome de arquivos ( **my-about-page.html** ) e nome de classes css ( **.my-about-page** ) e usa PascalCasing para classes JavaScript em ES6/TypeSciprt ( MyAboutPage ). Usando está conversão, desenvolvedores podem pegar qualquer projeto Ionic 2 e rapidamente tornar-se produtivo, semelhante ao Rails. 

