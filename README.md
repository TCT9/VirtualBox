# VirtualBox, Ubuntu Server, SSH, MySql e Node.js
Instalação e configuração do VirtualBox junto com Ubuntu Server - Acesso remoto com SSH - MySql e Node.js

Tenho o objetivo de agrupar em um único local:
* instalção;
* configuração;
* e correções de erros.

Do VirtualBox, Ubuntu Server, SSH, MySql e Node.js em uma máquina virtual do VirtualBox.

Juntamente com a referência de material escrito e em vídeos.

## Menu

1. [Instalar WSL 2](#cap1)
2. [Instalar e configurar o Ubuntu Server 22.04 LTS no Virtualbox](#cap2)
3. Criar pasta compartilhada Windows e Virtualbox;
4. Configurar IP estático no Ubuntu Server;
5. Gerenciar usuários;
6. Configuração de Rede NAT;
7. SSH - Acesso remoto de usuário root;
8. SSH - Acesso remoto de usuário root sem senha e usando passphrase;
9. SSH - Acesso remoto de usuário não root;
10. Instalar MySql no modo Headless;
11. SSH - Conectar MySql remoto;
12. ;

Observação: 
Para os vídeos em inglês ative a tradução automática:

a. Clique em legenda: 

![image](https://user-images.githubusercontent.com/39566289/166954732-76284264-f72c-439c-aaf3-8c4a25c99008.png)

b. Clique em Detalhes => Legendas/CC: 

![image](https://user-images.githubusercontent.com/39566289/167017221-f20a34fd-3991-47f1-8695-4d4bac2b0f88.png)

c. Clique em Traduzir automáticamente => e por fim selecione Português:

![image](https://user-images.githubusercontent.com/39566289/167017693-3f9d9356-c253-437f-9eb7-932fcb93947e.png)


<a id="cap1"></a>
## 1. Instalar WSL 2
O [vídeo](https://www.youtube.com/watch?v=hd6lxt5iVsg&t=580s)(abra em nova guia) abaixo descreve como instalar o WSL 2, que será fundamental para simulação de sistemas Linux remotamente.

Outra obrigação é a instalação do Windows Terminal e VS Code.

Fonte(s):
<a id = "link_video1">
[WSL 2 - A solução para rodar Linux dentro do Windows 10 - Root #08](https://www.youtube.com/watch?v=hd6lxt5iVsg&t=580s)

  Observação: veja na descrição do vídeo acima os links para instalação do Windows Terminal, VS Code, Ubuntu para Windows etc...
  

<a id="cap2"></a>
## 2. Instalar e configurar o Ubuntu Server 22.04 LTS no Virtualbox

Será necessário baixar a imagem <code>iso</code> do Ubuntu Server, sendo a versão mais atual a 20.04 LTS.
  
Acesse https://ubuntu.com/download/server e selecione o link <code>Option 2: Manual server installation</code> e por fim click no link 
  <code>Download Ubuntu Server 22.04 LTS</code> para baixar o arquivo <code> ubuntu-22.04-live-server-amd64.iso</code>.
  
Reserve a imagem do Ubuntu para uso posterior.

Vamos verificar no Windows 10 se a virtualização está ativada. Para isso faça:
  
  <code>Ctrl+Alt+Del</code> --> Gerenciador de Tarefas --> guia Desempenho --> selecione CPU
  
  Verifique se a virtualização está habilitada. Se não estiver, você terá que ativar esse recurso no [Bios](https://www.youtube.com/watch?v=yDGdAXGItH0)(acesse o link para detalhes) do seu computador:
  
  ![image](https://user-images.githubusercontent.com/39566289/166926260-0f19631f-8cb5-4be2-9b30-73e55501bf5b.png) 
  

  Em "Digite aqui para pesquisar" escreva "Ativar", conforme figura abaixo, e selecione "Ativar ou Desativar recursos do Windows":
  
  ![image](https://user-images.githubusercontent.com/39566289/166927703-d37ad7b5-38a8-4516-9cef-fee4c706e053.png)

  Selecione os serviços destacados em vermelho:
  
  ![image](https://user-images.githubusercontent.com/39566289/166928302-0cd11c34-136f-4563-a85a-f5195e6eba56.png)

  Aguarde a instalação e reinicie o computador. 
  
  Em caso de falha desmarque estas opções e reinicie o computador. Depois marque as opções novamente e por fim reinicie o computador.

  Vídeos de instalação do VirtualBox:
  1. Básico => [Instalação do VirtualBox no Windows : Curso Linux Básico : Módulo 02 : Aula#03](https://www.youtube.com/watch?v=r66V3hrHyO8&t=18s)
  2. Completo + IP estático => [Install Ubuntu Server 21.04 on VirtualBox 6.1 - Static IP Addresses and SSH Server](https://www.youtube.com/watch?v=zx3bICfe5PY)

