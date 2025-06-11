# Windows_Server_2019_CET103
Manual de criação e configuração de um servidor Windows Server 2019 para CET103.

# Índice
[Manual](#manual)

- [Criação da máquina virtual](#criação-da-máquina-virtual)

- [Instalação do Sistema Operativo](#instalação-do-sistema-operativo)

- [Configurar o servidor](#configurar-o-servidor)

- [Configuração RAID 5](#configuração-raid-5)

- [Configuração do servidor](#configuração-do-servidor)

- [Atribuição de um IP na rede interna](#atribuição-de-um-ip-na-rede-interna)

- [Instalação do Active Directory](#instalação-do-active-directory)

- [Configuração do Domain Service](#configuração-do-domain-service)

- [Configurar o DNS](#configurar-o-dns)

- [Instalação e configuração do DHCP](#Instalação-e-configuração-do-DHCP)

- [NIC Teaming](#NIC-Teaming)

- [Windows Server Backup](#Windows-Server-Backup)

- [Active Directory](#Active-Directory)

- [Group Policy Objects (GPO)](#Group-Policy-Objects-(GPO))

## Manual
### Criação da máquina virtual
> [!NOTE]
> A instalação e configuração do Windows Server 2019 foi realizada num software de virtualização onde foi criada uma máquina virtual (virtual machine), neste caso irá ser utilizado o VirtualBox.
<br>
Dentro do VirtualBox, para criar uma máquina virtual de um Windows Server 2019, clicar na opção `Nova`.
<br>
<br>
<img src="images/1.png" alt="opcao nova" style="display: block; margin: 0 auto;">
<br>
<br>
Vamos dar um nome á máquina virtual, neste caso será `Maquina_de_teste` **(1)**, escolher o local onde irá estar guardado o conteúdo da máquina virtual **(2)** e escolher o ficheiro .iso **(3(imagem do sistema operativo escolhido))**.
<br>
<img src="images/2.png" alt="opcao nova" style="display: block; margin: 0 auto;">
<br>
<br>
Na secção do Hardware iremos configurar as especificações da máquina virtual, neste caso a máquina irá ter `7 gigabytes de memória` e `4 processadores`.
Temos estes parâmetros para que a máquina não fique lenta.
<br>
<img src="images/3.png" alt="opcao nova" style="display: block; margin: 0 auto;">
<br>
<br>
Na secção `Hard Disk` iremos colocar o tamanho do disco pretendido (indicar quanto espaço queremos na nossa máquina virtual).
Para um bom funcionamento pelo menos **40 gigabytes** são necessários.
<br>
<img src="images/3.png" alt="opcao nova" style="display: block; margin: 0 auto;">
<br>
<br>
De seguida clicamos em `Terminar` e a criação da máquina virtual estará completa.
Para iniciar a máquina virtual clicar em `Iniciar`. A máquina irá iniciar.
Será necessário configurar o sistema operativo escolhido, neste caso irá ser o Windows server 2019.

### Instalação do Sistema Operativo

<img src="https://github.com/user-attachments/assets/5a7485cc-a5c5-4e4b-a0e4-7ff99b9f3d53" width="650">

<img src="https://github.com/user-attachments/assets/a4556d2d-5ca4-44b2-a995-8cad3fe4cbdf" width="650">

Durante o setup irão aparecer várias opções, mas a que é preciso é a opção **Datacenter Evaluation (Desktop Experience)** para criar um servidor com interface gráfica.

<img src="https://github.com/user-attachments/assets/4c39ec05-0a30-4b04-99ca-a912e903d957" width="650">

De seguida aceita-se os termos de licensa, escolhe-se a opção **custom: Install Windows only (advanced)** e escolhemos a **drive** desejada onde queremos **instalar o sistema operativo**. E será instalado o sistema operativo.

<img src="https://github.com/user-attachments/assets/2556019d-e3ef-4387-a0ab-17e31fde149d" width="650">

Depois de instalar o sistema operativo será necessário **reiniciar** a máquina virtual.

<img src="https://github.com/user-attachments/assets/4718da7e-069d-4468-8e5a-4a84d2c1955b" width="650">

## Configurar o servidor

### Configuração RAID 5

**RAID 5** é uma tecnologia de armazenamento que junta vários discos rígidos (HDDs ou SSDs) para funcionarem como um só sistema. Este tipo de RAID oferece desempenho, capacidade de armazenamento e tolerância a falhas.

Antes de se iniciar a máquina virtual, vamos a **armazenamento**, clicamos no ícone com um mais e escolhemos **Add SCSI Controller**.

<img src="https://github.com/user-attachments/assets/bfe74f84-3689-40f2-9434-8ffe003fbf82" width="650">

Clicamos em **Add Hard Disk**, e escolhemos **Create new disk**.

<img src="https://github.com/user-attachments/assets/684e5d8c-8937-49b8-94ea-61d2052f087b" width="650">

<img src="https://github.com/user-attachments/assets/b720a12f-9492-425f-bbbe-51aac99909f3" width="650">

<img src="https://github.com/user-attachments/assets/7deff27d-340d-4c53-b837-1ccc4d335e34" width="650">

De seguida iniciamos a máquina virtual. No server manager clicamos em **Tools** e de seguida **Computer Management**.
Iremos para **Storage** e em seguida **Disk Management**, onde conseguimos ver as partições.

<img src="https://github.com/user-attachments/assets/39f9a2a7-6e98-4f3e-b12b-c67887b151d3" width="650">

Nos discos não inicializados clicamos com o botão direito do rato e escolhemos a opção **Online**. Fazemos o mesmo para os restantes discos que se encontram offline.

<img src="https://github.com/user-attachments/assets/c5bf4828-3d79-4200-8cbf-0b9a580d611a" width="650">

De seguida com o botão direito do rato clicamos no disco e escolhemos a opção **Initialize Disk**, selecionamos todos os discos e a opção **GPT (GUID Partition Table)**.

<img src="https://github.com/user-attachments/assets/d7f87fb4-d9ba-4033-9f35-aabb75955efb" width="650">

<img src="https://github.com/user-attachments/assets/9fa29599-0fa3-40f5-8413-09d56f2fb6d3" width="650">

Com o botão direito do rato clicamos num disco não alocado e escolhemos a opção **Convert to Dynamic Disk**, selcionamos os discos e clicamos **Ok**.

<img src="https://github.com/user-attachments/assets/c495e2a9-48a0-4d03-9ec8-1a0c74595111" width="650">

<img src="https://github.com/user-attachments/assets/a144fefe-7d05-4e0c-81a0-c017f6f78867" width="650">

Com obotão direito do rato cliamos sobre um dos discos e escolhemos a opção **New RAID-5 Volume...** para inicar o assistente.

<img src="https://github.com/user-attachments/assets/53e996b5-0641-4fc7-bc70-1ac257550d86" width="650">

Iremos agora esxcolher os discos que queremos que façam parte do RAID, selcionamos os discos e clicamos **Next**.
E de seguida escolhemos a letra do novo volume.

<img src="https://github.com/user-attachments/assets/53201ea4-2c2b-425f-83b9-7070dec11889" width="650">

<img src="https://github.com/user-attachments/assets/c85d9798-02a9-4ad2-bafc-fa14de43e944" width="650">

Definimos as opções de formatação, no final o volume RAID 5 irá ser entrar no processo de formatação e sincronização.

<img src="https://github.com/user-attachments/assets/ec23e9cf-248b-4056-bb67-f2ad3beee330" width="650">

<img src="https://github.com/user-attachments/assets/7ed88b89-2f17-4621-b485-ce9e9eea611c" width="650">

### Configuração do servidor

Neste passo é necessário mudar o nome do servidor e atribuir um sufixo DNS.
O nome será **Daniel** e o sufixo DNS será **pilao.pt**.

<img src="https://github.com/user-attachments/assets/216589ba-c71c-43c9-84f6-2176b58775a4" width="650">

<img src="https://github.com/user-attachments/assets/75e7985e-9c61-40c7-acef-735303f114f7" width="650">

<img src="https://github.com/user-attachments/assets/1065b87b-397c-4610-b9ff-5fd25c2ca337" width="650">

<img src="https://github.com/user-attachments/assets/6bad2a71-018b-43ac-8808-40f6c1a3b393" width="650">

<img src="https://github.com/user-attachments/assets/6bad2a71-018b-43ac-8808-40f6c1a3b393" width="650">

<img src="https://github.com/user-attachments/assets/ee0f850e-ae2f-429b-83bb-ff38233224d2" width="650">

### Atribuição de um IP na rede interna

Neste passo irá ser atribuído um IP fixo á minha rede interna, irei mudar o nome dos adaptadores para não se confundirem, á rede interna irei mudar o nome para **Int** e para a rede externa irei mudar o nome para **Ext**.

<img src="https://github.com/user-attachments/assets/a3e838af-cd4c-40c5-9adb-b462e8bdcf41" width="650">

<img src="https://github.com/user-attachments/assets/1c2f7a57-a302-40e3-8792-ac19b0f457a3" width="650">

Irá agora ser atribuído um IP fixo á rede interna ao configurar o adaptador **Int**.
Com o botão direito do rato, clicar em **Properties**, escolhendo a opção **Internet Protocol Version 4 (TCP/IPv4)** e de seguida **Properties** outravez.

<img src="https://github.com/user-attachments/assets/f3689f2a-66ac-4ee2-a88a-f8fe17821a2a" width="650">

<img src="https://github.com/user-attachments/assets/19f663e5-e9ad-4724-b9e3-bf4f1aa285be" width="650">

Nesta janela irá ser necessário introduzir um **IP** e uma **Subnet mask** (irão ser atribuidos IPs ás máquinas que fazem parte da rede interna e que estiverem ligadas ao servidor).
O IP escolhido será **192.168.1.200** e a Subnet mask **255.255.255.0**. Clicar em **Advanced**.

<img src="https://github.com/user-attachments/assets/2ef73984-f03e-4dc7-b855-7d32c1a65af4" width="650">

Na opção **Interface Metric** irei colocar **1**, fazendo com que este adaptador tenha prioridade na ligação da máquina, e premir **Ok**.

<img src="https://github.com/user-attachments/assets/ee1092de-755f-42fb-9a44-a492cca3be13" width="650">

Para o adaptador externo iremos só colocar no **Interface Metric** o número **20**.

<img src="https://github.com/user-attachments/assets/38c5061f-32a8-4c1b-a826-229942e40e0c" width="650">

Para testar o funcionamento da configuração, abrir o **cmd**, e usamos o comando **ping**, iremos fazer ping ao IP escolhido anteriormente.

<img src="https://github.com/user-attachments/assets/6f8be303-8a6a-439b-9f5f-49be19599818" width="650">

<img src="https://github.com/user-attachments/assets/4d244562-0dcb-4e07-aa6a-c19bb4b15b50" width="650">

Ao escrever **ipconfig** no cmd vejo as definições dos adaptadores de rede.

<img src="https://github.com/user-attachments/assets/ecaeaed8-1730-42af-946c-a665d8a65cdb" width="650">

### Instalação do Active Directory

O **Active Directory (AD)** é um serviço de diretório da Microsoft que centraliza e organiza informações sobre recursos de rede. Ele é usado para gerir contas de usuário, computadores, impressoras e outros recursos. 
O AD é usado em ambientes corporativos que utilizam sistemas operacionais Windows. 

**Principais funcionalidades do AD**
- Armazenar informações sobre objetos na rede, como usuários, computadores, impressoras e serviços
- Fornecer uma estrutura hierárquica e lógica para organizar as informações de diretório
- Controlar a autenticação e autorização de usuários e computadores
- Fornecer políticas de segurança

**Configurar o AD**
No canto superior direito iremos clicar na opção **Manage** e de seguida **Add Roles and Features**.

<img src="https://github.com/user-attachments/assets/24949837-75dd-40e0-8a60-01aa546b3298" width="650">

Iremos **Next** até chegarmos á etapa **Server Selection**.

<img src="https://github.com/user-attachments/assets/cbb98f06-ec80-4667-9bd8-1b89a62b227c" width="650">

Escolhemos o servidor desejado, que irá funcionar como controlador de dominio (neste caso iremos ter só uma opção). Clicamos **Next**.

<img src="https://github.com/user-attachments/assets/422a0a36-1b94-4bf7-9458-01ce4f271d28" width="650">

No passo seguinte escolhemos a opção **Active Directory Domain Services**. Continuamos com a instalação.

<img src="https://github.com/user-attachments/assets/6e18a948-fbeb-4abc-bcae-fb634e4e2dc2" width="650">

<img src="https://github.com/user-attachments/assets/1a76edbb-57bc-4144-82d9-0ec74d346d32" width="650">

<img src="https://github.com/user-attachments/assets/3978a1ab-83ec-4d45-ab8f-13937189f7f7" width="650">

No final da instalação será necessário **reiniciar**.

### Configuração do Domain Service

Na secção **AD DS** no Server Manager irá ter um alerta para configurar o Domain Service. Clicamos na opção **More...**.

<img src="https://github.com/user-attachments/assets/cf7d010e-ecb9-47dd-9626-493592ddea9d" width="650">

Iremos escolher a opção sobrelinhada.

<img src="https://github.com/user-attachments/assets/d1652574-74e3-458d-bcc5-c35f188fad61" width="650">

Escolhemos a opção **Add a new forest** com o Root domain name **pilao.pt**.

<img src="https://github.com/user-attachments/assets/e774bccd-c211-4b87-a4e8-ec7e8989a149" width="650">

Na página seguinte escolhemos uma password para o **DSRM**, para que se necessário haja a **manutenção** e **recuperação** da base de dados do **AD**. E clicamos **Next**.

<img src="https://github.com/user-attachments/assets/4169580e-90da-489d-83aa-e2adac2351a8" width="650">

Iremos clicar **Next** até aparecer a opção **Install**. Clicamos.
O computador irá **reiniciar** quando completar a instalação.

<img src="https://github.com/user-attachments/assets/aba00bba-5141-4cbb-a1c3-2539b8375cb1" width="650">

### Configurar o DNS

**O que é o DNS**

DNS é a sigla para **Domain Name System**, que significa Sistema de Nomes de Domínio. É um serviço que permite aos utilizadores acederem à internet através de nomes de domínio, como "google.com" em vez de memorizar IPs.

Para configurar o DNS, no server manager na opção tools escolher a opção **DNS** para abrir o **DNS Manager**.

<img src="https://github.com/user-attachments/assets/e4f68c93-f274-4c42-a33b-e66f0ea432d9" width="650">

No painel, clicar com o botão direito do rato na opção **Reverse Lookup Zones** selecionando a opção **New Zone**.

<img src="https://github.com/user-attachments/assets/8a695ce2-3c2d-41fb-b5d7-4c9374f42725" width="650">

Irá aparecer a janela do setup, escolher a opção **Next**, de seguida escolher a opção **Primary zone**, esta opção faz com que este servidor DNS seja responsável por manter e gerir de forma principal, armazenando os registos DNS. Clicamos **Next**.

<img src="https://github.com/user-attachments/assets/820c11df-bc65-45b9-a608-ebbedc284fe5" width="650">

Escolhemos a opção **To all DNS servers running on domain controllers in this domain: pilao.pt**, para replicar a zona de DNS apenas para os servidores DNS que estão a executar controladores de domínio dentro do domínio **pilao.pt**, clicamos **Next** e na próxima etapa escolhemos a opção **IPv4 Reverse Lookup Zone**, clicamos **Next**.

<img src="https://github.com/user-attachments/assets/dd057318-ce2c-4e32-b43c-b1ff0b26e21b" width="650">

<img src="https://github.com/user-attachments/assets/13131ddc-027f-41f9-ab56-70a05cc6df9d" width="650">

Coloquei o endereço IP da rede interna, que será **192.168.1**, e cliquei **Next**.

<img src="https://github.com/user-attachments/assets/a68f0df0-96a6-4cdc-96a8-3f29762c6372" width="650">

Escolher a opção **Allow only secure dynamic updates**, clicamos **Nex** e damos por terminado o setup.
<img src="https://github.com/user-attachments/assets/fbcb407e-4743-4e4c-9e2d-3f692cc9f12a" width="650">

<img src="https://github.com/user-attachments/assets/c20e729e-7824-4105-8718-ac80253394d3" width="650">

Para concluir a configuração do Reverse Lookup é preciso criar um novo **Pointer** e indicar que o meu servidor é aquele que faça a conversão, indicando o **host**.
<img src="https://github.com/user-attachments/assets/d3262894-54b2-4d4e-98dd-7f0b612aad2b" width="650">

<img src="https://github.com/user-attachments/assets/38af1bef-bf68-4529-8a1e-fb2429ebe251" width="650">

<img src="https://github.com/user-attachments/assets/80d45ae2-be7f-4f7b-9fa6-22d458d3dadd" width="650">

Testar o foward lookup e o reverse lookup para confirmar se o servidor está a fazer a correta conversão.

### Instalação e configuração do DHCP

Para começar-mos a instalação e configuração do DHCP clicamos no **Manage** e de seguida **Add Roles and Features**.

<img src="https://github.com/user-attachments/assets/3e7dd452-0461-4baf-a880-bbe1fc3292b1" width="650">

Na instalação escolhemos a opção **DHCP Server** e clicamos **Next** até o botão **Install** fique ativo, instalamos.

<img src="https://github.com/user-attachments/assets/aebcb661-6a49-4099-a9f6-a1b653783b0b" width="650">

<img src="https://github.com/user-attachments/assets/04cc7cc0-6212-49c4-89ad-42b993e44e96" width="650">

Depois da instalação aparece um aviso no Server Manager, o DHCP precisa de ser configurado.

<img src="https://github.com/user-attachments/assets/c8c41fce-4a77-44a7-bca2-5251f61b02bb" width="650">

<img src="https://github.com/user-attachments/assets/91c4d3ce-35dd-451b-bffe-78aba7558a43" width="650">

<img src="https://github.com/user-attachments/assets/9133bfd1-1fcb-42a5-8cb2-48ffde36016c" width="650">

<img src="https://github.com/user-attachments/assets/df77207e-32f0-4085-b778-e1128f60e0f0" width="650">

Para criar um scope DHCP selecionamos **Tools**, clicamos em **DHCP**, no painel da esquerda clicamos com o botão direito do rato em cima do **IPv4** e clicamos em **New Scope...**, iniciando o Wizard.

<img src="https://github.com/user-attachments/assets/503e3443-e566-4f18-913b-8eb9d1f141a7" width="650">

<img src="https://github.com/user-attachments/assets/a8b8daa5-8acf-4c15-a13b-e7ff72c1ab7c" width="650">

O nome e a descrição será **"Aulas"**, clicamos **Next**.

<img src="https://github.com/user-attachments/assets/7fda55ae-696b-4769-9aa4-4fc741f988b6" width="650">

Indicamos os intervalos de endereços de IP.

<img src="https://github.com/user-attachments/assets/e2bfe75a-b4d6-4735-bd23-536ae811aa71" width="650">

Definimos agora IPs dentro de um intervalo que não queremos que sejam atribuídos automaticamente, clicamos **Next**.

<img src="https://github.com/user-attachments/assets/c43cfd38-ca3a-4a7b-a6f0-6792a0422387" width="650">

Escohemos a opção **Yes, I want to configure these options now**.

<img src="https://github.com/user-attachments/assets/c6830777-5ada-4890-91e7-00ae6ff1a6d7" width="650">

De seguida indicamos o endereço de IP do nosso servidor, sendo esse o dispositivo que faz a ligação á rede.
Neste caso será **192.168.1.200**
Clicamos em **Add** e de seguida **Next**.

<img src="https://github.com/user-attachments/assets/2fc95291-0719-47c0-984e-204522c08eda" width="650">

Clicamos **Next** até aparecer para escolhermos umas das opções, escolhemos a opção **Yes, I want to activate this scope now**.

<img src="https://github.com/user-attachments/assets/ebd9c945-14d7-4deb-9c9b-9471bbd691ba" width="650">

### NIC Teaming

NIC Teaming é uma técnica usada para combinar duas ou mais placas de rede físicas num único interface lógico.

Fora da máquina virtual adicionamos mais 2 placas de rede.

<img src="https://github.com/user-attachments/assets/da27e054-f0e3-49c6-b65e-6818c97cd8bf" width="650">

Dentro da máquina virtual mudei o nome das placas para as identificar mais facilmente.

<img src="https://github.com/user-attachments/assets/eb916e16-4506-4a0d-b65b-d4cfdc9452a3" width="650">

No Server Manager clicamos na opção **Disabled** á frente de **NIC Teaming**.

<img src="https://github.com/user-attachments/assets/3322dcef-2363-42e1-ab34-7e2302026ace" width="650">

Em cima de uma das placas clicamos com o botão direito e escolhemos a opção **Add to New Team**.

<img src="https://github.com/user-attachments/assets/901f0f4e-48c8-4d4d-bf0a-b860d5f3a88f" width="650">

Escolhemos o **Team name**, escolhemos as placas, escolhemos **Aditional Properties** e de seguida **Next**.

<img src="https://github.com/user-attachments/assets/73907da8-a872-4e83-b125-a0da5d60f3a4" width="650">

E fazemos o mesmo para a rede interna.

### Windows Server Backup

Para instalar o **Windows Server Backup** clicamos em **Manage** e de seguida em **Add Roles and Features**.

<img src="https://github.com/user-attachments/assets/975a467c-f068-4228-9339-5da1992af002" width="650">

Avançamos até **Features** e selecionamos **Windows Server Backup**, clicamos em **Install**.

<img src="https://github.com/user-attachments/assets/33265267-dc4b-4993-8fb3-75b2297da9d7" width="650">

Para criar o agendamento do Backup clicamos em **Tools** e de seguida **Windows Server Backup**.

<img src="https://github.com/user-attachments/assets/c57418a3-7afa-4166-b9e1-7567ab20a346" width="650">

Na próxima janela, na parte esquerda da janela, clicamos em **Local Backup** e na parte direita iniciamos o Wizard ao clicar **Backup Schedule...**.

<img src="https://github.com/user-attachments/assets/be91cac8-2ad8-431f-baf9-fb2751b7acd2" width="650">

<img src="https://github.com/user-attachments/assets/61a3cdcc-39be-4686-aa13-b9b91418f66a" width="650">

Concluido o Wizard irá estar concluida a instalação do **Windows Server Backup**.

### Active Directory

Clicamos em **Tools**, **Active Directory Users and Computers**.

<img src="https://github.com/user-attachments/assets/f55bff74-691e-42ec-a119-b23e264ebb41" width="650">

De seguida com o botão direito clicar em **pilao.pt**.

<img src="https://github.com/user-attachments/assets/fa9b5cfa-5957-49c0-8763-e10c5df53c39" width="650">

Criamos duas pastas, **Cinel_Lisboa** e **Cinel_Porto**.

<img src="https://github.com/user-attachments/assets/39f4b03b-f4d0-4576-88cb-032e8f0b1d55" width="650">

Dentro da pasta **Cinel_Lisboa** criamos três sub-pastas com o nome de **IT**, **HR** e **Finance**. Da mesma maneira que criámos as pastas iniciais.

<img src="https://github.com/user-attachments/assets/5511bd54-cf72-4e01-a930-ffaad45afded" width="650">

De seguida, criamos dois grupos dentro de **IT** com o nome de **IT_Admins** e **IT_Analysts**. Ambos de scope **Global** e type **Security**.

<img src="https://github.com/user-attachments/assets/bf5a6829-f359-448a-8cb4-5d075d1c9a8f" width="650">

<img src="https://github.com/user-attachments/assets/ff09e7f6-dcbb-41fb-8aaf-e1ab786cf610" width="650">

Para criar um utilizador na pasta **IT** clicamos com o botão direito, clicamos em **New** e de seguida **User**.

<img src="https://github.com/user-attachments/assets/4704a36d-9825-4b3b-a00c-e21c7b8c04a8" width="650">

O nome do novo User será **João Silva** e o User Logon name será **jsilva**.

<img src="https://github.com/user-attachments/assets/f5f14b02-856b-42b0-8c20-f7e7e428101a" width="650">

De seguida criamos uma password e marcamos a opção **User must change password at next logon**.

<img src="https://github.com/user-attachments/assets/3bc50538-17c2-400f-a4a2-b8a30dd0c2e9" width="650">

Para juntarmos um User a um grupo clicamos com o botão direito em cima do User e clicamos **Add to a group...**.

<img src="https://github.com/user-attachments/assets/384e0b9e-8ea3-4873-b180-621325b9651c" width="650">

<img src="https://github.com/user-attachments/assets/e2c3367e-ac5c-497c-931e-3fa33fdc5e01" width="650">

### Group Policy Objects (GPO)

Para começar iremos a **tools** e de seguida **Group Policy Management**.

<img src="https://github.com/user-attachments/assets/e3108f6a-2c0d-41e9-b61c-a50a5d7ae7a8" width="650">

Vamos até **Group Policy Objects** e clicamos com o botão direito do rato, de seguida **New**.
Escolhemos um nome, neste caso será **DC-Segurança**.

<img src="https://github.com/user-attachments/assets/3c49636a-2395-4ead-9a6d-459c98b04fd7" width="650">


