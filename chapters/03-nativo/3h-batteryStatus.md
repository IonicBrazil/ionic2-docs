Battery Status  
========

```$ cordova plugin add cordova-plugin-batterystatus```  
Repositório: [https://github.com/apache/cordova-plugin-battery-status](https://github.com/apache/cordova-plugin-battery-status)

Requer o plugin cordova: cordova-plugin-batterystatus. Para mais informações, por favor veja a documentação do plugin BatteryStatus.

Plataformas suportadas
-----
- Amazon Fire OS
- iOS
- Android  
- BlackBerry 10  
- Windows Phone 7
- Windows Phone 8
- Windows
- Firefox OS
- Browser   

Uso  
-----

``` javascript 

import {BatteryStatus} from 'ionic-native';


// ver diferenças no estado da bateria  
let subscription = BatteryStatus.onChange().subscribe(
 status => {
   console.log(status.level, status.isPlugged);
 }
);

// deixar de ver
subscription.unsubscribe();  
```

Métodos estáticos  
-----

``` onChange() ```  
Ver diferença no nível da bateria  
**Retorno** : ```Observable``` Retorna um observável que empurra o estado de um objeto

``` onLow() ```  
Ver o nível da bateria quando estiver baixo  
**Retorno** : ```Observable<StatusObject>``` Retorna um observável que empurra o estado de um objeto

``` onCritical() ```  
Ver o nível da bateria quando estiver crítico  
**Retorno** : ```Observable<StatusObject>``` Retorna um observável que empurra o estado de um objeto
