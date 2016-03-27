# Usando NPM #

Existe um monte de nova terminologia em Ionic V2, muitas tem a ver com Node e NPM. Vamos dar uma olhada nos conceitos chave de Node/NPM e como eles se relacionam com Ionic.

## Pacotes Ionic em NPM - Qual a Importância de um Nome? ##

Existe dois pacotes relacionados ao Ionic no NPM, o pacote Ionic CLI e o pacote Ionic-Angular.

### Ionic CLI ###

O CLI (Command Line Interface ou Interface de linha de comando) é a principal ferramenta que você irá utilizar para criar um projeto, fazer build de aplicativo nativo e lidar com associações de recursos do seu aplicativo. Este pacote está disponivel no NPM e tem o nome de **ionic**. Para instalar, execute:

```shell
# Se esta no linux/osx, execute com sudo
npm install -g ionic
```

Isto irá instalar a ultima versão estável lançada do Ionic CLI. Para instalar a ultima versão beta estável, que atualmente é necessário para o desenvolvimento da V2, execute: 

```shell
# Se esta no linux/osx, execute com sudo
npm install -g ionic@beta
```

Então nós podemos usar CLI a partir da linha de comando executando **ionic &#60;comando&#62;**.

### Ionic Angular ###

O framework está disponivel no NPM com o nome de **ionic-angular**. Quando você criar um projeto usando o CLI, você automaticamente vai obter a instalação do pacote Ionic Angular. O pacote e sua versão é gerenciado pelo NPM e o **package.json** de um projeto. Um projeto simples deve ter um **package.json** parecido com este aqui.

```js
{
  "devDependencies": {
  // lista de dependencias de desenvolvimento
  },
  "dependencies": {
    "ionic-angular": "2.0.0-beta.3"
  }
  // e qualquer outra coisa
}
```

Aqui nos podemos dizer que este projeto depende do pacote **ionic-angular** e usa a versão **2.0.0-beta.3**

Mas como podemos atualizar um pacote quando uma nova versão sai? Para verificar se há uma atualização, podemos executar: 

```shell
npm outdated

Package                           Current          Wanted          Latest  Location
ionic-angular                2.0.0-beta.2    2.0.0-beta.2    2.0.0-beta.3  myApp
```

Isso nos diz que existe uma atualização para o pacote ionic-framework para versão 2.0.0-beta.3. Para poder obter a atualização, nos podemos executar **run install ionic-angular@latest**.  
Podemos tambem atualizar o **package.json** para **"ionic-angular": "2.0.0-beta.3"** e executar o comando **npm update**.

