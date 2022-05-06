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
  
  a. Básico => [Instalação do VirtualBox no Windows : Curso Linux Básico : Módulo 02 : Aula#03](https://www.youtube.com/watch?v=r66V3hrHyO8&t=18s)
  
  b. Completo + IP estático => [Install Ubuntu Server 21.04 on VirtualBox 6.1 - Static IP Addresses and SSH Server](https://www.youtube.com/watch?v=zx3bICfe5PY)
  
  Para efeito de simulação de servidores VPS minha sujestão é usar dois adapatores de rede na máquina virtual. Para saber mais sobre tipos de rede veja este vídeo:
  [ VirtualBox - Configuração da REDE na Máquina Virtual (VM) - Aula 9 - www.professorramos.com](https://www.youtube.com/watch?v=JI1iOo2igEY&list=PL0Vu-kzOParACWUIVIwMnxFmhsyWTQ5ON&index=2&t=445s). Assim, para efeitos de configuração, usaremos o IP estático da nossa rede local e uma NAT Interna para comunicação entre servidor da aplicação, banco de dados e clientes
  
  No VirtualBox => Rede => Adpatador 1: escolha Placa em modo <code>bridge</code>. 
  
  Para confirgurar a rede interna NAT veja estes vídeos:
  
  [Mix - VirtualBox - Configurações da Placa de Rede na Máquina Virtual](https://www.youtube.com/watch?v=_jsR6CFbVnI&list=PLYI3TmXCT9q7QFdaRaREsYzoTqT7PL9zM)
  [COMO CONFIGURAR AS PLACAS DE REDE DO VIRTUALBOX | part 01 -Atualizado!!](https://www.youtube.com/watch?v=_uTa2EAEK8k)
  
  [Mix - Confihurações de rede no VirtualBox](https://www.youtube.com/watch?v=ipdURBligTE&list=PLlJpkMCbRGXq2FU0riG_VDa9TGNiuKBQ6)
  
  E depois selecione o Adaptador 2: escolha Rede NAT. 
  
  O passo-a-passo para configurar IP estático é:
  
  <p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;~$ => Isso é o terminal do guest ou seja, da nossa máquina virtual</p>
  <p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;my_user@DESKTOP-PUCC98R => Isso é o terminal do nosso host, ou seja do nosso computador. Estou supondo que você está com Windows 10, WSL 2, Ubuntu e o Terminal Windows instalados.</p>

```
	
    1. atualizar pacotes
	~$ sudo apt update
		Aguardar atualização

	~$ sudo apt upgrade
		Aguardar atualização

  2. Instalar o pacote net-tools, pois vamos usar 'ifconfig'
	~$ sudo apt install net-tools
		Aguardar instalação

  3. Definir o IP estático
	Vamos acessar o arquivo de configurações
	~$ sudo nano /etc/netplan/00- [tecle TAB para preencher automaticamente!]
	~$ sudo nano /etc/netplan/00-installer-config.yaml

	 Abaixo da ethernet que tem nosso endereço de rede local, fazemos:
		addresses: [192.168.1.X/24]

	Onde 'X' é um valor bem distante dos endereços usados em sua casa.

	Para salvar: crtl+o e depois tecle ENTER. Para sair: ctrl-x

	Agora basta atualizar as diretivas:
		~$ sudo netplan apply

	Para ver as alterações:
		~$ ifconfig
	
```

	Fonte: [Para configurar um IP estático no Linux](https://pt.linux-console.net/?p=124#:~:text=Para%20configurar%20um%20IP%20est%C3%A1tico,ao%20espa%C3%A7amento%20no%20arquivo%20YAML.&text=Em%20seguida%2C%20salve%20o%20arquivo,abaixo%20para%20salvar%20as%20altera%C3%A7%C3%B5es.&text=Em%20seguida%2C%20voc%C3%AA%20pode%20confirmar,rede%20usando%20o%20comando%20ifconfig)

  
  
  
  
  
  Dessa forma vamos usar um IP estático no Adpatador 1, com possibilidade de acessar via SSH, e depois criar outras máquinas virtuais para simular uma rede interna com clientes e um servidor back-end e outro servidor de banco de dados.

