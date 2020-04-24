# Assinando-a-key-de-um-app-do-AndroidStudio
Esse é um tutorial de como Assinar uma key do Android Studio para a públicação na PlayStory.
Tenha em mente que o tutorial conta que você já gerou a key, tanto faz se for o (padrão .apk) ou (Bundle .aab).

## ASSINANDO A KEY
Presumo que você está no windows 7 acima e já fez a parte burocratica de criar a key, coloca-lo numa pasta a parte e criou seu release.
--Bom essa pasta se chama *'KeysApps'* e está localizada nos seus arquivos de usúario
*'C:\Users\Matheus Vidigal\KeysApps'.* 
Dentro da pasta vai estar a *'KeyApp.jks'*

## Incluindo outros arquivos
Vamos incluir mais 2 arquivos que juntos irão assinar(KeyApp.jks) e criar o terceiro arquivo para enviar ao PlayStore.

  **NOTA IMPORTANTE:**
  Existe 2 formas de gerar uma assinatura com a nova atualização do AndroidStudio, o .apk e o Android App Bundle, as 2 formas são praticamente identicas para se assinar. Citarei as duas formas.
  
  obs: Faça um ou outro (**.apk** ou **.abb**) de acordo como você gerou sua assinatura (apk ou bundle).

O primeiro arquivo:
  - Abra o AndroidStudio e clique no SDK Manager
  - Veja ao lado de *'Android SDK Location:'* onde o SDK do seu app está instalado e copie o caminho
  - Abra seu explorador de arquivos e cole o caminho na aba de pesquisa
  - Dentro da pasta do SDK entre em build-tools e pesquise no canto superior direito pelo arquivo *'zipalign'*
  - Talvez tenha mais de um arquivo *'zipalign.exe'* então copie o mais recente e cole na mesma pasta *'KeysApps'* onde tanbém esta sua *'KeyApp.jks'*

O segundo arquivo(**.apk**):
  - Abra seu explorador de arquivos e entre na pasta onde está criado seu projeto(app)
  - Pesquise no canto superior direiro por:```*.apk```
  - Irá aparecer ```android-debug.apk```, você irá clicar com o botão direito e selecionar a opção 'abrir local do arquivo'
  - Irá aparecer mais três arquivos, copie o arquivo ```android-release-unaligned.apk``` e cole na pasta da sua key(*'KeysApps'*)
  

O segundo arquivo(**.aab**):
  - Abra seu explorador de arquivos e entre na pasta onde está criado seu projeto(app)
  - Adicione o caminho ```\app\build\outputs\bundle\release```
  - Irá aparecer ```app-release.aab```, copie o arquivo android-release-unaligned.apk e cole na pasta da sua key(*‘KeysApps’*)

## CMD
Agora é só colocar uma linha de comando e tudo feito:

  - Abra seu CMD(Prompt de Comando)
  - Digite e execulte o caminho da pasta *'KeysApps'* onde está seus três arquivos: 
  ```sh 
cd C:\Users\Matheus Vidigal\KeysApps
```
  - (para **.apk**) A seguir digite e execulte: 
  ```sh 
zipalign -v 4 android-release-unaligned.apk app-assinado-nomedoseuapp.apk
```
  - (para **.aab**) A seguir digite e execulte: 
  ``` sh 
zipalign -v 4 app-release.aab app-assinado-nomedoseuapp.aab
```
Assim que acabar de execultar ira aparecer a mensagem ```Verification succesful```.
O arquivo criado e assinado está com o nome: ```app-assinado-nomedoseuapp``` na sua pasta *'KeysApps'*, e com esse arquivo que você pode enviar para a PlayStore.

[Linkedin](https://www.linkedin.com/in/matheus-vidigal-armax7/)
[GitHub](https://github.com/Armax7)
[Instagram](https://www.instagram.com/matheus_armax7/)

>Armax7...
