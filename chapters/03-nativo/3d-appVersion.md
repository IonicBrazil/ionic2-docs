App Version
========

``` $ cordova plugin add cordova-plugin-app-version ```

Repositório: [https://github.com/whiteoctober/cordova-plugin-app-version](https://github.com/whiteoctober/cordova-plugin-app-version)

Faz a leitura da versão do seu app das suas configurações de *build*. 

Este plugin requer: cordova-plugin-app-version. Para mais informações, por favor veja [a documentação do plugin Cordova App Version](https://github.com/whiteoctober/cordova-plugin-app-version).

Platafomas suportadas
-----
- Android
- iOS

Uso
-----

``` javascript 

import {AppVersion} from 'ionic-native';

AppVersion.getAppName();
AppVersion.getPackageName();
AppVersion.getVersionCode();
AppVersion.getVersionNumber();
```

Métodos estáticos
-----
``` getAppName() ```  
Retorna o nome do aplicativo  
**Retorna**: ``` Promise ```


``` getPackageName() ```  
Retorna o nome do pacote aplicativo  
**Retorna**: ``` Promise ```


``` getVersionCode() ```  
Retorna o identificador da *build* do aplicativo  
**Retorna**: ``` Promise ```


``` getVersionNumber() ```  
Retorna a versão do  aplicativo  
**Retorna**: ``` Promise ```



