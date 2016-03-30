App Rate
========

``` $ cordova plugin add cordova-plugin-apprate ```

Repositório: [https://github.com/pushandplay/cordova-plugin-apprate](https://github.com/pushandplay/cordova-plugin-apprate)

O plugin AppRate torna fácil a exibição da mensagem de avaliação do seu app para o usuário, seja para agora, depois ou nunca.

Este plugin requer: cordova-plugin-apprate. Para mais informações, por favor veja [a documentação do plugin AppRate](https://github.com/pushandplay/cordova-plugin-apprate).

Platafomas suportadas
-----
- Android
- iOS

Uso
-----

``` javascript 

import {AppRate} from 'ionic-native';

AppRate.preferences.storeAppURL.ios = '<my_app_id>';
AppRate.preferences.storeAppURL.android = 'market://details?id=<package_name>';
AppRate.preferences.storeAppURL.blackberry = 'appworld://content/[App Id]/';
AppRate.preferences.storeAppURL.windows8 = 'ms-windows-store:Review?name=<the Package Family Name of the application>';
AppRate.promptForRating();
```

Métodos estáticos
-----
``` preferences() ```

Opções para a janela de avaliação

useLanguage {String} null - tag BCP 47 customizada  
displayAppName {String} ‘’ - título da aplicação  
promptAgainForEachNewVersion {Boolean} true - mostra a janela novamente quando a versão da aplicação for atualizada  
usesUntilPrompt {Integer} 3 - conta a quantidade de vezes que a aplicação é executada antes de exibir a janela de avaliação  
openStoreInApp {Boolean} false - sai do app ou não quando a página da aplicação é aberta na App Store (por hora, somente para iOS)  
useCustomRateDialog {Boolean} false - use uma view própria para exibir a janela de avaliação do seu app  
callbacks.onButtonClicked {Function} null - função call back. chamada quando o usuário clicou em um dos botões da janela de avaliação  
callbacks.onRateDialogShow {Function} null - função call back. chamada quando a janela de avaliação está sendo exibida  
storeAppURL.ios {String} null - id da aplicação na AppStore  
storeAppURL.android {String} null - URL da aplicação no GooglePlay  
storeAppURL.blackberry {String} null - URL da aplicação no AppWorld  
storeAppURL.windows8 {String} null - URL da aplicação na WindowsStore  
customLocale {Object} null - objeto customizado para definir sua região e idioma para o app

``` promptForRating(immediately) ```

Prompts the user for rating

| Parametro                     | Tipo         | Detalhes                                     |
|-------------------------------|--------------|----------------------------------------------|
| immediately                   |```boolean``` | Mostra a janela de avaliação imediatamente   |

