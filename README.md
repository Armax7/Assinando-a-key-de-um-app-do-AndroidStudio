<h1 align="center">
  Assinando-a-key-de-um-app-do-AndroidStudio
  <br>
</h1>
<h4 align="center">Esse é um tutorial de como Assinar uma key do Android Studio para a públicação na PlayStory.
Tenha em mente que o tutorial conta que você já gerou a key, tanto faz se for o (padrão .apk) ou (Bundle .aab).</h4>
<br>

## ASSINANDO A KEY 🖋️🔑
Presumo que você está no windows 7 acima e já fez a parte burocratica de criar a key, coloca-lo numa pasta a parte e criou seu release.
--Bom essa pasta se chama *'KeysApps'* e está localizada nos seus arquivos de usúario
*'C:\Users\Matheus Vidigal\KeysApps'.* 
Dentro da pasta vai estar a *'KeyApp.jks'*

## Incluindo outros arquivos 📝📂
Vamos incluir mais 2 arquivos que juntos irão assinar(KeyApp.jks) e criar o terceiro arquivo para enviar ao PlayStore.

  **⚠️NOTA IMPORTANTE⚠️**
  Existe 2 formas de gerar uma assinatura com a nova atualização do AndroidStudio, o .apk e o Android App Bundle, as 2 formas são praticamente identicas para se assinar. Citarei as duas formas.
  
  obs: Faça um ou outro (**.apk** ou **.aab**) de acordo como você gerou sua assinatura (apk ou bundle).

O primeiro arquivo:
  - Abra o AndroidStudio e clique no SDK Manager
  - Veja ao lado de *'Android SDK Location:'* onde o SDK do seu app está instalado e copie o caminho
  - Abra seu explorador de arquivos e cole o caminho na aba de pesquisa
  - Dentro da pasta do SDK entre em build-tools e pesquise no canto superior direito pelo arquivo *'zipalign'*
  - Talvez tenha mais de um arquivo *'zipalign.exe'* então copie o mais recente e cole na mesma pasta *'KeysApps'* onde tanbém esta sua *'KeyApp.jks'*
  
>Abra o AndroidStudio e clique no SDK Manager ...
<p align="center">
  <img src="https://user-images.githubusercontent.com/52816125/81102184-a2e82800-8ee5-11ea-9d2f-cf2c8c9767df.png" width="600px">
</p>

>Dentro da pasta do SDK entre em build-tools e pesquise ...
<p align="center">
  <img src="https://user-images.githubusercontent.com/52816125/81102325-df1b8880-8ee5-11ea-8ec6-89646076c8b4.png" width="600px">
</p>

O segundo arquivo(**.apk**):
  - Abra seu explorador de arquivos e entre na pasta onde está criado seu projeto(app)
  - Pesquise no canto superior direiro por:```*.apk```
  - Irá aparecer ```android-debug.apk```, você irá clicar com o botão direito e selecionar a opção 'abrir local do arquivo'
  - Irá aparecer mais três arquivos, copie o arquivo ```android-release-unaligned.apk``` e cole na pasta da sua key(*'KeysApps'*)

>Pesquise no canto superior direiro por:```*.apk``` ...
<p align="center">
  <img src="https://user-images.githubusercontent.com/52816125/81102329-dfb41f00-8ee5-11ea-9207-5994805d6f83.png" width="500px">
</p>

>Irá aparecer mais três arquivos, copie o arquivo ```android-release-unaligned.apk``` ...
<p align="center">
  <img src="https://user-images.githubusercontent.com/52816125/81102330-e04cb580-8ee5-11ea-8fd6-f0d3c1b1f58d.png" width="500px">
</p>

O segundo arquivo(**.aab**):
  - Abra seu explorador de arquivos e entre na pasta onde está criado seu projeto(app)
  - Adicione o caminho ```\app\build\outputs\bundle\release```
  - Irá aparecer ```app-release.aab```, copie e cole na pasta da sua key(*‘KeysApps’*)
  
>Adicione o caminho ```\app\build\outputs\bundle\release``` ...
<p align="center">
  <img src="https://user-images.githubusercontent.com/52816125/81102328-dfb41f00-8ee5-11ea-8296-4891d666d48f.png" width="500px">
</p>

A pasta (*‘KeysApps’*) ficara com 3 itens colados:
<p align="center">
  <img src="https://user-images.githubusercontent.com/52816125/81102335-e0e54c00-8ee5-11ea-954f-95003a537186.png" width="500px">
</p>

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
<p align="center">
  <img src="https://user-images.githubusercontent.com/52816125/81102337-e17de280-8ee5-11ea-92e5-3dadec2103ae.png" width="600px">
</p>

  - (para **.aab**) A seguir digite e execulte: 
  ``` sh 
zipalign -v 4 app-release.aab app-assinado-nomedoseuapp.aab
```
<p align="center">
  <img src="https://user-images.githubusercontent.com/52816125/81102336-e0e54c00-8ee5-11ea-9b9f-13efe923debd.png" width="600px">
</p>

Assim que acabar de execultar ira aparecer a mensagem ```Verification succesful```.
O arquivo criado e assinado está com o nome: ```app-assinado-nomedoseuapp``` na sua pasta *'KeysApps'*, e com esse arquivo que você pode enviar para a PlayStore.

>O arquivo criado e assinado está com o nome: ```app-assinado-nomedoseuapp``` na sua pasta *'KeysApps'* ...
<p align="center">
  <img src="https://user-images.githubusercontent.com/52816125/81102339-e17de280-8ee5-11ea-80a4-8a698448b8cd.png" width="500px">
</p>

  **⚠️aviso⚠️**
  - Se você deseja instalar o arquivo .aab fora da Play Store, é necessário extrair primeiro os arquivos APK da AAB e instalá-los manualmente no seu dispositivo Android.
  - Diferentemente dos arquivos .apk tradicionais, não é possível compartilhar ou carregar o arquivo .aab para teste. 

## Contato ✉️
| [<img src="https://user-images.githubusercontent.com/52816125/81789587-93b33c80-94da-11ea-8c9a-413824e6424e.jpg" width=115><br><sub>@MatheusVidigal🦊</sub>](https://github.com/Armax7) |
| :---: |

[Linkedin](https://www.linkedin.com/in/matheus-vidigal-armax7/) |
[Instagram](https://www.instagram.com/matheus_armax7/) |
[gmail](https://mail.google.com/mail/u/1/#inbox?compose=GTvVlcSGLCKpKJfwPsKKqzXBplKkGtCLvCQcFWdWxCxQFfkHzzjVkgzrMFPBgKBmWFHvrjrCsMqSH)
