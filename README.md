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


<a id="cap1"></a>
## 1. Instalar WSL 2
O [vídeo](https://www.youtube.com/watch?v=hd6lxt5iVsg&t=580s)(abra em nova guia) abaixo descre como instalar o WSL 2, que será fundamental para simulação de sistemas Linux remotamente.

Outra obrigação é a instalação do Windows Terminal e VS Code.

Fonte(s):
<a id = "link_video1">
[WSL 2 - A solução para rodar Linux dentro do Windows 10 - Root #08] https://www.youtube.com/watch?v=hd6lxt5iVsg&t=580s
Observação: veja na descrição do vídeo acima os links para instalação do Windows Terminal, VS Code, Ubuntu para Windows etc...

<a id="cap2"></a>
## 2. Instalar e configurar o Ubuntu Server 22.04 LTS no Virtualbox

Será necessário baixar a imagem <code>iso</code> do Ubuntu Server, sendo a versão mais atual a 20.04 LTS.
  
Acesse https://ubuntu.com/download/server

[Como Ativar o Recurso de Virtualização no BIOS do PC Processadores Intel e AMD] https://www.youtube.com/watch?v=yDGdAXGItH0
[Instalação do VirtualBox no Windows : Curso Linux Básico : Módulo 02 : Aula#03] https://www.youtube.com/watch?v=r66V3hrHyO8&t=18s

