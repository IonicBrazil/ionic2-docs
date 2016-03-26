# Emulate #

| Comando  |  Descrição  |
|----------|-------------|
| ionic emulate | Emular o projeto no simulador ou no emulador |
| **Flags** | |              
| --livereload&#124;-l | |
| --address | |
| --port&#124;-p  | |
| --livereload-port&#124;-r | |
| --consolelogs&#124;-c | Imprimir console logs da aplicação no Ionic CLI (requer livereload) |
| --serverlogs&#124;-s | Imprimir dev server logs no Ionic CLI (requer livereload) |  
| --debug&#124;--release | | 
| --device&#124;--emulator&#124;--target=FOO  | | |


# Descrição #

O comando **emulate** irá fazer deploy de sua aplicação para dispositivos das plataformas específicas. Você também pode rodar em **live reload¹** especificando ao emulador através da flag --livereload. A funcionalidade de **live reload¹** é similar ao do comando **ionic server**, mas em vez de desenvolver e debugar um aplicativo usando o navegador padrão, o aplicativo hibrido compilado está observando todas as mudanças aos arquvios e recarregando o aplicativo quando necessario.


** Notas de tradução: **  
¹Live reload: As mudanças de seus arquivos serão refletidas em tempo real.
