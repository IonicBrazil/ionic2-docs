<h1 id="Troubleshooting">Solucionando problemas no seu aplicativo Ionic</h1>

Não consegue encontrar uma solução nesta página? Confira o [fórum oficial do Ionic](http://forum.ionicframework.com), onde os amigáveis Ionites da comunidade podem lhe ajudar!

<h3 id="Blank_app">Ajuda! A tela do meu aplicativo está em branco e não aparecem erros</h3>

- Garanta que seu @App tenha `template` ou `templateUrl`
- Garanta que o template do seu @App tenha um elemento `<ion-nav></ion-nav>` com a propriedade `root`:
```
  <ion-nav [root]="firstPage"></ion-nav>
```

<h3 id="Directive_not_working">Meu componente ou diretiva não está carregando!</h3>

Você pode fazer algumas verificações caso seu componente ou diretiva não estiver funcionando. Certifique-se que:

- o componente/diretiva foi incluído no array de `directives` de quaisquer componentes cujo template contém o item com problema
- seu seletor não tenha erros de ortografia
- você esteja utilizando o seletor corretamente, como um atributo, elemento ou classe CSS
- seu seletor tenha uma [sintaxe apropriada](http://learnangular2.com/components/):
  - `[attr]` se é um seletor de atributo
  - `element` se é um seletor de elemento
  - `.class` se é um seletor de classe CSS

```ts
@Directive({
  selector: '[my-dir]' // <-- [my-dir] porque é um atributo
})                     // Poderia ser my-dir, [my-dir], .my-dir
class MyDir {
  constructor(){ console.log("Estou vivo!"); }
}

@Page({
  template: `<div my-dir>Hello World</div>`

  // Ou, dependendo do tipo da sua diretiva
  //template: `<my-dir>Hello World</my-dir>`
  //template: `<div class="my-dir">Hello World</div>`

  directives: [MyDir] // <-- Não me esqueça!
})
class MyPage {}
```

<h3 id="Common_mistakes">Erros comuns:</h3>

- Esquecer `()` depois de uma anotação: `@Injectable()`, `@Optional()`, etc.

```ts
@Directive({
  selector: 'my-dir'
})
class MyDirective {
  // Errado, deveria ser @Optional()
  // Neste caso @Optional faz nada, então MyDirective lançará um erro se parent estiver indefinido
  constructor(@Optional parent: ParentComponent) {}
}
```

- Adicionar provedores (providers) para cada componente quando na verdade você deseja ter a mesma instância de provedor injetada em todos (por exemplo serviços).  Para uma classe ser injetável ela apenas precisa estar no array de `providers` do componente ou qualquer componente pai (por exemplo `@App`), mas não em ambos.  Colocá-la tanto no componente que tem aquele provedor injetado quanto no componente-pai ou acima na hierarquia criará duas instâncias separadas do provedor. O exemplo abaixo demonstra esse problema:

```ts
let id = 0;
class MyService {
  constructor(){ this.id = id++; }
}

@Component({
  selector: 'my-component',
  template: 'Hello World',
  providers: [MyService] // <-- Cria uma nova instância de MyService :(
})                       // Desnecessário pois MyService está no providers do App
class MyComp {
  // id é 1, s é uma instância de MyService diferente daquela que está em MyApp
  constructor(s: MyService) { console.log("MyService id é: " + s.id); }
}

@App({
  template: '<my-component></my-component>',
  providers: [MyService], // MyService precisa apenas estar aqui
  directives: [MyComp]
})
class MyApp {
  // id é 0
  constructor(s: MyService) { console.log("MyService id é: " + s.id); }
}
```
Plunker: http://plnkr.co/edit/QzgR5H0r8FijHeVtv2dd

<h3 id="Common_JS_errors">Erros comuns de JS:</h3>

`Cannot resolve all parameters for YourClass(?). Make sure they all have valid type or annotations.`

Também pode ser precidido por `Error during instantiation of Token(Promise<ComponentRef>)` se o erro estiver no seu componente `@App`.

Isso significa que o Angular está confuso sobre um ou mais parâmetros do construtor da sua classe.  Para fazer injeção de dependência o Angular precisa saber o tipo do objeto que deveria ser injetado.  Você pode informá-lo especificando o tipo do parâmetro. Certifique-se que:

- você está importando a classe do parâmetro
- você tenha colocado anotação correta no parâmetro ou especificado seu tipo

```ts
import {MyService} from 'myservice'; // Não esqueça de me importar!

@Page({
  template: `Hello World`
})
export class MyClass {
  constructor(service: MyService){}
    /* Ou caso não esteja utilizando o pacote TypeScript */
  constructor(@Inject(MyService) service){}
}
```

Algumas vezes você pode ter erros de referência circular no seu código.  Referência circular significa que dois objetos dependem entre si e não é possível declarar um antes do outro.  Para contornar essa situação, nós podemos utilizar a função [`forwardRef`]() construída no Angular 2.

```ts
import {forwardRef} from 'angular2/core';

@Component({
  selector: 'my-button'
  template: `<div>
               <icon></icon>
               <input type="button" />
             </div>`
  directives: [forwardRef(() => MyIcon)] // MyIcon ainda não foi definida
})                                       // forwardRef vai resolver a dependência de MyIcon quando MyIcon for utilizada

@Directive({
  selector: 'icon'  
})
class MyIcon {
  constructor(containerButton: MyButton) {} // MyButton foi definida
}
```

-------

`No provider for ParamType! (MyClass -> ParamType)`

Isso significa que o Angular sabe qual o tipo do objeto que deveria injetar, mas não sabe como injetá-lo. Certifique-se que:

- caso o parâmetro seja um serviço, você tenha adicionado a classe especificada à lista de provedores disponíveis no seu aplicativo


```ts
import {MyService} from 'myservice';

@App({
  templateUrl: 'app/app.html',
  providers: [MyService] // Não me esqueça!
})
class MyApp {
```

Caso o parâmetro seja outro componente ou diretiva (por exemplo, um componente-pai), adicioná-lo à lista de providers fará com que o erro suma, mas causará o mesmo efeito que o item #2 da seção [Erros comuns](#Common_mistakes) acima.  Ou seja, você criará uma nova instância da classe do componente (pense nisso como um "processo de transformação" do seu componente em um serviço), mas na verdade você não receberá a referência para a instância que deseja (aquela obtida durante a compilação do seu aplicativo, feita pelo Angular).  Invés disso, certifique-se que a diretiva ou componente que você espera ser injetada esteja disponível para o seu componente (exemplo: que realmente seja um componente-pai se você está esperando que seja um pai). Veja o código abaixo para facilitar o entendimento:

```ts
@Component({
  selector: 'my-comp'
  template: '<div my-dir></div>',
  directives: [forwardRef(() => MyDir)]
})
class MyComp {
  constructor(){ this.name = "Meu Component"; }
}

@Directive({
  selector: '[my-dir]'
})
class MyDir {
  constructor(c: MyComp) { <-- Esse é o ponto de interesse do exemplo

    // Ocorrerá erros quando a diretiva estiver em uma div normal por que não existe MyComp
    // na árvore de componentes então não há o que injetar
    console.log("Nome do componente host: " + c.name);
  }
}

@App({
  template: "<my-comp></my-comp>" + // Sem erro no construtor MyDir, pois MyComp é pai de MyDir
            "<my-comp my-dir></my-comp>" + // Sem erro no construtor MyDir, pois MyComp é host de MyDir
            "<div my-dir></div>", // Erros no construtor de MyDir
  directives: [MyComp, MyDir]
})
class MyApp {}
```

Segue um diagrama ilustrando quais injectors estão disponíveis:

```
                 +-------+                                         
                 |  App  |                                         
                 +---+---+                                         
                     |                                                        
       +-------------+------------+                                       
       |                          |                                       
+------+------+          +--------+--------+                      
| Div (MyDir) |          | MyComp (MyDir)  | <- MyComp pode ser injetado                    
+-------------+          +--------+--------+                      
       ^                          |                                       
Sem MyComp para injetar    +------+------+
                           | Div (MyDir) | <- MyComp pode ser injetado pela herança
                           +-------------+
```


Aprofundando um pouco mais o exemplo anterior, você pode utilizar a anotação `@Optional` do Angular 2 caso nem sempre você queira esperar por uma referência de um componente/diretiva:

```ts
@Directive({
  selector: '[my-dir]'
})
class MyDir {
  constructor(@Optional() c: MyComp) {
    // Não haverá mais erros, mesmo que c seja indefinido
    if (c) {
      console.log("Nome do componente host: " + c.name);
    }
  }
}
```

--------

`Can't bind to 'propertyName' since it isn't a known property of the 'elementName' element and there are no matching`
`directives with a corresponding property`

A mensagem acima é bem auto-explicativa. O erro acontece quando você tenta fazer um bind de uma propriedade em um elemento que não possui aquela propriedade.  Exemplo: quando o elemento é um componente ou tem mais de uma diretiva, o erro ocorrerá caso nem o componente nem as diretivas tenham a propriedade.

```html
<!-- div não tem uma propridade chamada 'foo' -->
<div [foo]="bar"></div>
```
--------

`EXCEPTION: No provider for ControlContainer! (NgControlName -> ControlContainer)`

Esta é uma versão mais específica do erro `No provider` acima.  Acontece quando você utiliza um controle de formulário como [NgControlName](https://angular.io/docs/js/latest/api/core/NgControlName-class.html) sem especificar um elemento pai do tipo [NgForm](https://angular.io/docs/js/latest/api/core/NgForm-class.html) ou [NgFormModel](https://angular.io/docs/js/latest/api/core/NgFormModel-class.html).  Na maioria das vezes, isso pode ser resolvido garantindo que seu controle de formulário esteja dentro do elemento de formulário atual. NgForm utiliza `form` como seletor então isso instanciará um novo NgForm:

```ts
@Page({
  template:
    '<form>' +
      '<input ng-control='login'>' +
    '</form>'
})
```
