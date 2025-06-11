<!-- PROJECT LOGO -->
<br />
<div align="center">
  <a href="">
    <img src="images/serverlogo.jpg" alt="Logo" width="100" height="100">
  </a>

  <h3 align="center">Windows Server 2019</h3>
  <h4 align="center">Manual CET 103</h4>

  <p align="center">Manual de criação e configuração do Windows Server 2019</p>
</div>



<!-- TABLE OF CONTENTS -->
<details>
  <summary>Índice</summary>
  <ol>
     <li>
      <a href="#sobre-o-manual">Sobre o manual</a>
    </li>
    <li>
      <a href="#software-de-virtualização">Software de virtualização</a>
    </li>
    <li>
      <a href="#criação-e-configuração-da-máquina-virtual">Criação e configuração da máquina virtual</a>
    </li>
    <li>
      <a href="#instalação-e-configuração-do-sistema-operativo">Instalação e configuração do Sistema Operativo</a>
    </li>
    <li><a href="#roadmap">Configuração do servidor</a>
    <ul>
        <li><a href="#active-directory">Active Directory</a></li>
      <li><a href="#domain-service">Domain Service</a></li>
        <li><a href="#dns">DNS</a></li>
      <li><a href="#dhcp">DHCP</a></li>
      <li><a href="#nic-teaming">NIC Teaming</a></li>
      </ul>
      </li>
    <li><a href="#configuração-do-raid-5">Configuração do RAID 5</a></li>
    <li><a href="#server-backup">Server Backup</a></li>
    <li><a href="#configuração-do-active-directory">Configuração do Active Directory</a></li>
    <ul>
        <li><a href="#criação-de-grupos-e-utilizadores">Criação de grupos e utilizadores</a></li>
        <li><a href="#group-policy-objects">Group Policy Objects</a></li>
      </ul>
    <li><a href="#Creditos">Créditos</a></li>
  </ol>
</details>



<!-- ABOUT THE PROJECT -->
## Sobre o manual

Este manual foi desenvolvido para o curso CET103, destinado para a avaliação e armazenamento de conhecimentos.


## Software de virtualização

Foi utilizado o software VirtualBox para a criação e configuração do Windows Server 2019.

<div align="center">
  <a href="https://www.virtualbox.org">
    <img src="https://raw.githubusercontent.com/degrejas/Windows_Server_CET103/refs/heads/main/images/virtualboxlogo.avif" alt="Logo" width="100" height="100">
  </a>

<!-- GETTING STARTED -->
## Criação e configuração da máquina virtual

Dentro do VirtualBox escolhemos a opção `Nova`.

<div align="center">
    <img src="images/1.png" alt="Logo" width="567" height="122">
  </a>
  

Damos o nome á máquina, será `Maquina_de_teste` **(1)**, escolhemos a pasta onde ficará guardada **(2)** e escolhemos o .iso do Sistema Operativo desejado **(3)**.

<div align="center">
    <img src="images/2.png" alt="Logo" width="657" height="392">
  </a>

<br>

Em termos de Hardware a máquina irá ter `7 GB de RAM`, `4 processadores` e `50 GB de armazenamento`.

<div align="center">
    <img src="images/3.png" alt="Logo" width="619" height="372">
  </a>

  <div align="center">
    <img src="images/4.png" alt="Logo" width="625" height="378">
  </a>

Podemos iniciar a máquina virtual.

## Instalação e configuração do Sistema Operativo

Iniciamos a máquina virtual e fazemos o setup do Windows Server 2019.

<div align="center">
    <img src="images/5.png" alt="Logo" width="500" height="419">
  </a>

<div align="center">
    <img src="images/6.png" alt="Logo" width="500" height="419">
  </a>

<div align="center">
    <img src="images/7.png" alt="Logo" width="540" height="453">
  </a>
  
<div align="center">
    <img src="images/8.png" alt="Logo" width="567" height="475">
  </a>

<div align="center">
    <img src="images/9.png" alt="Logo" width="567" height="475">
  </a>


## Configuração do servidor

Com o SO instalado a primeira coisa a fazer é mudar o nome do servidor e atribuir um sufixo DNS.

<div align="center">
    <img src="images/10.png" alt="Logo" width="567" height="475">
  </a>

<div align="center">
    <img src="images/11.png" alt="Logo" width="567" height="475">
  </a>

<div align="center">
    <img src="images/12.png" alt="Logo" width="567" height="475">
  </a>

<div align="center">
    <img src="images/13.png" alt="Logo" width="567" height="475">
  </a>

<div align="center">
    <img src="images/14.png" alt="Logo" width="567" height="475">
  </a>
  
Alteramos o nome da rede interna e da rede externa e atribuimos um IP á rede interna.

<div align="center">
    <img src="images/15.png" alt="Logo" width="567" height="475">
  </a>

  <div align="center">
    <img src="images/16.png" alt="Logo" width="567" height="475">
  </a>

<div align="center">
    <img src="images/17.png" alt="Logo" width="567" height="475">
  </a>

  <div align="center">
    <img src="images/18.png" alt="Logo" width="567" height="475">
  </a>

<div align="center">
    <img src="images/19.png" alt="Logo" width="567" height="475">
  </a>

<div align="center">
    <img src="images/20.png" alt="Logo" width="567" height="475">
  </a>

  <div align="center">
    <img src="images/21.png" alt="Logo" width="567" height="475">
  </a>

<div align="center">
    <img src="images/22.png" alt="Logo" width="567" height="475">
  </a>    

  <div align="center">
    <img src="images/23.png" alt="Logo" width="567" height="475">
  </a>

    <div align="center">
    <img src="images/24.png" alt="Logo" width="567" height="475">
  </a>

  
  ## Active Directory

O Active Directory (AD) é um serviço de diretório desenvolvido pela Microsoft, fundamental para o gerenciamento de redes Windows em ambientes corporativos. Pense nele como uma central de informações e controle para tudo que existe na sua rede.

<div align="center">
    <img src="images/25.png" alt="Logo" width="567" height="475">
  </a>

<div align="center">
    <img src="images/26.png" alt="Logo" width="567" height="475">
  </a>

  <div align="center">
    <img src="images/27.png" alt="Logo" width="567" height="475">
  </a>

    <div align="center">
    <img src="images/28.png" alt="Logo" width="567" height="475">
  </a>

  <div align="center">
    <img src="images/29.png" alt="Logo" width="567" height="475">
  </a>

    <div align="center">
    <img src="images/30.png" alt="Logo" width="567" height="475">
  </a>


## Domain Service

<div align="center">
    <img src="images/31.png" alt="Logo" width="567" height="475">
  </a>

<div align="center">
    <img src="images/32.png" alt="Logo" width="567" height="475">
  </a>

<div align="center">
    <img src="images/33.png" alt="Logo" width="567" height="475">
  </a>

  <div align="center">
    <img src="images/34.png" alt="Logo" width="567" height="475">
  </a>
    
  <div align="center">
    <img src="images/35.png" alt="Logo" width="567" height="475">
  </a>


  ## DNS
  
O DNS (Domain Name System) é como se fosse a lista telefónica da Internet. Em vez de procurar um nome e obter um número de telefone, o DNS traduz nomes de domínio que são fáceis de ler para humanos (como www.google.com) em endereços IP numéricos que os computadores usam para comunicar.

 <div align="center">
    <img src="images/37.png" alt="Logo" width="567" height="475">
  </a>

<div align="center">
    <img src="images/38.png" alt="Logo" width="567" height="475">
  </a>

<div align="center">
    <img src="images/39.png" alt="Logo" width="567" height="475">
  </a>

<div align="center">
    <img src="images/40.png" alt="Logo" width="567" height="475">
  </a>

<div align="center">
    <img src="images/41.png" alt="Logo" width="567" height="475">
  </a>

<div align="center">
    <img src="images/42.png" alt="Logo" width="567" height="475">
  </a>

<div align="center">
    <img src="images/43.png" alt="Logo" width="567" height="475">
  </a>

<div align="center">
    <img src="images/44.png" alt="Logo" width="567" height="475">
  </a>

<div align="center">
    <img src="images/45.png" alt="Logo" width="567" height="475">
  </a>

<div align="center">
    <img src="images/46.png" alt="Logo" width="567" height="475">
  </a>


  ## DHCP

O DHCP (Dynamic Host Configuration Protocol) é um protocolo de rede que atribui automaticamente endereços IP e outras informações de configuração de rede a dispositivos numa rede.

<div align="center">
    <img src="images/62.png" alt="Logo" width="567" height="475">
  </a>

<div align="center">
    <img src="images/63.png" alt="Logo" width="567" height="475">
  </a>

<div align="center">
    <img src="images/64.png" alt="Logo" width="567" height="475">
  </a>

<div align="center">
    <img src="images/65.png" alt="Logo" width="567" height="475">
  </a>

<div align="center">
    <img src="images/66.png" alt="Logo" width="567" height="475">
  </a>

<div align="center">
    <img src="images/67.png" alt="Logo" width="567" height="475">
  </a>

<div align="center">
    <img src="images/68.png" alt="Logo" width="567" height="475">
  </a>

<div align="center">
    <img src="images/69.png" alt="Logo" width="567" height="475">
  </a>

<div align="center">
    <img src="images/70.png" alt="Logo" width="567" height="475">
  </a>

<div align="center">
    <img src="images/71.png" alt="Logo" width="567" height="475">
  </a>

<div align="center">
    <img src="images/72.png" alt="Logo" width="567" height="475">
  </a>

<div align="center">
    <img src="images/73.png" alt="Logo" width="567" height="475">
  </a>

<div align="center">
    <img src="images/74.png" alt="Logo" width="567" height="475">
  </a>

<div align="center">
    <img src="images/75.png" alt="Logo" width="567" height="475">
  </a>


  ## NIC Teaming

NIC Teaming, também conhecido como agregação de ligações (link aggregation), agregação de portas (port aggregation), bonding de NICs, ou ainda Agrupamento de NICs (termo da Microsoft), é uma técnica utilizada em sistemas operativos (principalmente Windows Server, mas também noutros como Linux) que permite combinar múltiplas placas de rede físicas (NICs) num único servidor, para que funcionem como uma única interface de rede lógica.

<div align="center">
    <img src="images/76.png" alt="Logo" width="567" height="475">
  </a>

<div align="center">
    <img src="images/77.png" alt="Logo" width="567" height="475">
  </a>

<div align="center">
    <img src="images/78.png" alt="Logo" width="567" height="475">
  </a>

<div align="center">
    <img src="images/79.png" alt="Logo" width="567" height="475">
  </a>

<div align="center">
    <img src="images/80.png" alt="Logo" width="567" height="475">
  </a>

<div align="center">
    <img src="images/81.png" alt="Logo" width="567" height="475">
  </a>


## Configuração do RAID 5

RAID é o acrónimo para Redundant Array of Inexpensive Disks (ou, mais modernamente, Redundant Array of Independent Disks). É uma tecnologia de armazenamento de dados que permite combinar vários discos rígidos (HDDs ou SSDs) numa única unidade lógica, com o objetivo de melhorar o desempenho, a redundância ou ambos.

O RAID 5 é um dos níveis de RAID mais comuns e populares em ambientes empresariais de pequena e média dimensão, equilibrando bem desempenho, tolerância a falhas e eficiência de armazenamento.

<div align="center">
    <img src="images/47.png" alt="Logo" width="567" height="475">
  </a>

<div align="center">
    <img src="images/48.png" alt="Logo" width="567" height="475">
  </a>

<div align="center">
    <img src="images/49.png" alt="Logo" width="567" height="475">
  </a>

<div align="center">
    <img src="images/50.png" alt="Logo" width="567" height="475">
  </a>

<div align="center">
    <img src="images/51.png" alt="Logo" width="567" height="475">
  </a>

<div align="center">
    <img src="images/52.png" alt="Logo" width="567" height="475">
  </a>

<div align="center">
    <img src="images/53.png" alt="Logo" width="567" height="475">
  </a>

<div align="center">
    <img src="images/54.png" alt="Logo" width="567" height="475">
  </a>

<div align="center">
    <img src="images/55.png" alt="Logo" width="567" height="475">
  </a>

<div align="center">
    <img src="images/56.png" alt="Logo" width="567" height="475">
  </a>

<div align="center">
    <img src="images/57.png" alt="Logo" width="567" height="475">
  </a>

<div align="center">
    <img src="images/58.png" alt="Logo" width="567" height="475">
  </a>

<div align="center">
    <img src="images/59.png" alt="Logo" width="567" height="475">
  </a>

<div align="center">
    <img src="images/60.png" alt="Logo" width="567" height="475">
  </a>

<div align="center">
    <img src="images/61.png" alt="Logo" width="567" height="475">
  </a>


  ## Server Backup

Server Backup (ou Cópia de Segurança de Servidor) refere-se ao processo de criar e armazenar cópias dos dados, aplicações e configurações de um servidor para poder recuperá-los em caso de perda de dados ou falha do sistema.

<div align="center">
    <img src="images/82.png" alt="Logo" width="567" height="475">
  </a>

<div align="center">
    <img src="images/83.png" alt="Logo" width="567" height="475">
  </a>

<div align="center">
    <img src="images/84.png" alt="Logo" width="567" height="475">
  </a>

<div align="center">
    <img src="images/85.png" alt="Logo" width="567" height="475">
  </a>

<div align="center">
    <img src="images/86.png" alt="Logo" width="567" height="475">
  </a>


## Configuração do Active Directory

O Active Directory (AD) é um serviço de diretório da Microsoft, uma espécie de base de dados centralizada que organiza e gere todos os recursos e utilizadores numa rede baseada em Windows.


### Criação de grupos e utilizadores

<div align="center">
    <img src="images/87.png" alt="Logo" width="567" height="475">
  </a>

<div align="center">
    <img src="images/88.png" alt="Logo" width="567" height="475">
  </a>

<div align="center">
    <img src="images/89.png" alt="Logo" width="567" height="475">
  </a>

<div align="center">
    <img src="images/90.png" alt="Logo" width="567" height="475">
  </a>

<div align="center">
    <img src="images/97.png" alt="Logo" width="567" height="475">
  </a>


### Group Policy Objects

<div align="center">
    <img src="images/98.png" alt="Logo" width="567" height="475">
  </a>

<div align="center">
    <img src="images/99.png" alt="Logo" width="567" height="475">
  </a>


<!-- USAGE EXAMPLES -->
## Créditos

Manual realizado por Daniel Egrejas.
