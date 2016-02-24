# 1.2 Instalando Ionic
 
Como no Ionic 1, aplicações Ionic 2 podem ser rapidamente criadas a partir da Ionic CLI ou ferramenta GUI ou construídas e testadas diretamente no navegador.
 
Para instalar o SDK do Ionic e criar projetos Ionic 2, você precisará instalar a versão beta mais recente:
```
$ npm install -g ionic@beta
```    

Não está familiarizado com NPM? Saiba mais sobre ele e quais pacotes usamos [aqui](../07-recursos/07e-using-npm.md) 
 
Preocupado com seus projetos Ionic V1? Não se preocupe! A versão beta tem todas as funcionalidades para trabalhar com ambos projetos V1 e projetos V2.

Uma vez feito isso, crie seu primeiro aplicativo Ionic:
```
$ ionic start cutePuppyPics --v2
```

Para executar o aplicativo, **cd** para o diretório que foi criado e, em seguida, execute o comando **ionic serve**:
```
$ cd cutePuppyPics
$ ionic serve
```

Você pode brincar com ele diretamente no navegador!

## Desenvolvendo para um dispositivo

Depois de ter instalado o Ionic, você pode desenvolver seu aplicativo para um dispositivo físico. Se você não tem um dispositivo físico na mão, você ainda pode desenvolver para um emulador de dispositivo. Confira os docs simulador iOS se você estiver em um Mac, ou os docs Genymotion se você estiver à procura para emular um dispositivo Android. Você também vai precisar de Cordova para executar seu aplicativo em um dispositivo nativo. Para instalar o Cordova, execute:
```
$ sudo npm install -g cordova
```

Depois que você tiver instalado Cordova e um dispositivo ou emulador pronto para iniciar, você pode seguir em frente e começar a construir sua app!

## Desenvolvendo para iOS

Para desenvolver para iOS, precisamos adicionar o módulo de plataforma iOS para Cordova:
```
$ ionic platform add ios
```

Em seguida, você precisa instalar o [Xcode](../../glossario.md). O Xcode permite que você faça o build e compile para um dispositivo de destino executando o iOS.

De lá, você deve ser capaz de executar o emulador iOS usando o seguinte comando:
```
$ ionic emulate ios
```

## Desenvolvendo para Android

Para desenvolver para o Android, será necessário você adicionar o módulo da plataforma Android para Cordova:
```
$ ionic platform add android
```

Em seguida, será necessário você instalar o [Android SDK](../../glossario.md). O SDK do Android permite que você faça o build e compile para um dispositivo de destino executando o Android. Embora o Android SDK venha com um emulador próprio, Genymotion é recomendado, uma vez que é muito mais rápido. Uma vez instalado, inicie uma imagem Android e execute:
```
$ ionic run android
```  
