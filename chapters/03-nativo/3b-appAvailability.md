App Availability
========

``` $ cordova plugin add cordova-plugin-appavailability ```

Repositório: [https://github.com/ohh2ahh/AppAvailability](https://github.com/ohh2ahh/AppAvailability)

Esse plugin permite que você verifique se um aplicativo está instalado no dispositivo do usuário. Ele requer um *URI scheme* (e.g. twitter://) no iOS ou um *Package Name* (e.g com.twitter.android) no Android.

Este plugin requer: cordova-plugin-appavailability. Para mais informações, por favor veja [a documentação do plugin AppAvailability](https://github.com/ohh2ahh/AppAvailability).

Platafomas suportadas
-----
- Android
- iOS

Uso
-----

``` javascript 

import {AppAvailability} from 'ionic-native';


var app;

if(device.platform === 'iOS') {
  app = 'twitter://';
}else if(device.platform === 'Android'){
  app = 'com.twitter.android';
}

AppAvailability.check(app)
  .then(
    yes => console.log(app + " is available"),
    no => console.log(app + " is NOT available")
  );
```

Métodos estáticos
-----

``` check(app) ```

Verifica se um aplicativo está disponível no dispositivo do usuário

| Parametro                     | Tipo         | Detalhes                                     |
|-------------------------------|--------------|----------------------------------------------|
| app                           |              | Nome do pacote no Android ou URI no iOS   	  |

**Returns**: ``` Promise<boolean> ```


