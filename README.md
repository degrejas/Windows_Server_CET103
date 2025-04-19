# Windows_Server_103
Manual de criação de um servidor Windows para CET103.
# Índice
[Manual](#manual)

- [Criação de uma máquina virtual](#criação-de-uma-máquina-virtual)

- [Instalação do Sistema Operativo](#instalação-do-sistema-operativo)

- [Configurar o servidor](#configurar-o-servidor)

- [Configuração RAID](#configuração-raid)

- [Configuração do servidor](#configuração-do-servidor)

- [Atribuição de um IP na rede interna](#atribuição-de-um-ip-na-rede-interna)

- [Instalação do Active Directory](#instalação-do-active-directory)

- [Configuração do Domain Service](#configuração-do-domain-service)

- [Configurar o DNS](#configurar-o-dns)

## Manual
### Criação de uma máquina virtual
É necessário um software de virtualização para criar uma máquina virtual (virtual machine), neste caso irá ser utilizado o VirtualBox.
Dentro do VitualBox, para criar uma máquina virtual de um Windows Server 2019, clicar na opção **Nova**.

<img src="https://github.com/user-attachments/assets/f40f3819-7004-4148-88dc-5de90f4ec8a5" width="650">

De seguida teremos de dar um nome á máquina virtual, neste caso será **Maquina_de_teste** (1), escolher o local onde irá estar guardado o conteúdo da máquina virtual (2) e escolher o ficheiro .iso (3(imagem do sistema operativo escolhido)).

<img src="https://github.com/user-attachments/assets/f4a731ac-4c74-454c-bc79-747efa0f25d0" width="650">

Na secção do Hardware iremos configurar as especificações da máquina virtual, neste caso a máquina irá ter **7 gigabytes de memória** e **4 processadores**. Temos estes parâmetros para que a máquina não fique lenta.

<img src="https://github.com/user-attachments/assets/e149f818-20b6-4740-93a4-35f699444995" width="650">

Na secção Hard Disk iremos colocar o tamanho do disco pretendido (indicar quanto espaço queremos na nossa máquina). Para um bom funcionamento pelo menos **40 gigabytes** são necessários.

<img src="https://github.com/user-attachments/assets/a3d36591-a80d-4adb-a226-a2cca9193a3b" width="650">

De seguida clicamos em “Terminar” e a criação da máquina virtual estará completa.
Para iniciar a máquina virtual clicar em “Iniciar”. A máquina irá iniciar.
De seguida será necessário configurar o sistema operativo escolhido, neste caso irá ser o Windows server 2019.

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

<img src="https://github.com/user-attachments/assets/53e996b5-0641-4fc7-bc70-1ac257550d86" width="650"

### Configuração do servidor

Neste passo é necessário mudar o nome do servidor e atribuir um sufixo DNS.
O nome será **Daniel** e o sufixo DNS será **pilao.pt**.

<img src="https://github.com/user-attachments/assets/216589ba-c71c-43c9-84f6-2176b58775a4" width="650">

<img src="https://github.com/user-attachments/assets/75e7985e-9c61-40c7-acef-735303f114f7" width="650">

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

