# Windows_Server_103
Manual de criação de um servidor Windows para CET103.
# Índice
[Manual passo a passo](#manual-passo-a-passo)

- [Criação de uma máquina virtual](#criação-de-uma-máquina-virtual)

- [Instalação do Sistema Operativo](#instalação-do-sistema-operativo)

- [Configurar o servidor](#configurar-o-servidor)

- [Atribuição de um IP na rede interna](#atribuição-de-um-ip-na-rede-interna)

## Manual passo a passo
### Criação de uma máquina virtual
É necessário um software de virtualização para criar uma máquina virtual (virtual machine), neste caso irá ser utilizado o VirtualBox.
Dentro do VitualBox, para criar uma máquina virtual de um Windows Server 2019, clicar na opção **Nova**.

![1](https://github.com/user-attachments/assets/f40f3819-7004-4148-88dc-5de90f4ec8a5)

De seguida teremos de dar um nome á máquina virtual, neste caso será **Maquina_de_teste** (1), escolher o local onde irá estar guardado o conteúdo da máquina virtual (2) e escolher o ficheiro .iso (3(imagem do sistema operativo escolhido)).

![2](https://github.com/user-attachments/assets/f4a731ac-4c74-454c-bc79-747efa0f25d0)

Na secção do Hardware iremos configurar as especificações da máquina virtual, neste caso a máquina irá ter **7 gigabytes de memória** e **4 processadores**. Temos estes parâmetros para que a máquina não fique lenta.

![3](https://github.com/user-attachments/assets/e149f818-20b6-4740-93a4-35f699444995)

Na secção Hard Disk iremos colocar o tamanho do disco pretendido (indicar quanto espaço queremos na nossa máquina). Para um bom funcionamento pelo menos **40 gigabytes** são necessários.

![4](https://github.com/user-attachments/assets/a3d36591-a80d-4adb-a226-a2cca9193a3b)

De seguida clicamos em “Terminar” e a criação da máquina virtual estará completa.
Para iniciar a máquina virtual clicar em “Iniciar”. A máquina irá iniciar.
De seguida será necessário configurar o sistema operativo escolhido, neste caso irá ser o Windows server 2019.

### Instalação do Sistema Operativo

![5](https://github.com/user-attachments/assets/5a7485cc-a5c5-4e4b-a0e4-7ff99b9f3d53)

![6](https://github.com/user-attachments/assets/a4556d2d-5ca4-44b2-a995-8cad3fe4cbdf)

Durante o setup irão aparecer várias opções, mas a que é preciso é a opção **Datacenter Evaluation (Desktop Experience)** para criar um servidor com interface gráfica.

![7](https://github.com/user-attachments/assets/4c39ec05-0a30-4b04-99ca-a912e903d957)

De seguida aceita-se os termos de licensa, escolhe-se a opção **custom: Install Windows only (advanced)** e escolhemos a **drive** desejada onde queremos **instalar o sistema operativo**. E será instalado o sistema operativo.

![8](https://github.com/user-attachments/assets/be731e0d-1ee3-4016-8c4c-f0ab6f25670e)

Depois de instalar o sistema operativo será necessário **reiniciar** a máquina virtual.

![9](https://github.com/user-attachments/assets/4718da7e-069d-4468-8e5a-4a84d2c1955b)

### Configurar o servidor

Neste passo é necessário mudar o nome do servidor e atribuir um sufixo DNS.
O nome será **Daniel** e o sufixo DNS será **pilao.pt**.

![10](https://github.com/user-attachments/assets/216589ba-c71c-43c9-84f6-2176b58775a4)

![11](https://github.com/user-attachments/assets/75e7985e-9c61-40c7-acef-735303f114f7)

![12](https://github.com/user-attachments/assets/1065b87b-397c-4610-b9ff-5fd25c2ca337)

![13](https://github.com/user-attachments/assets/6bad2a71-018b-43ac-8808-40f6c1a3b393)

![14](https://github.com/user-attachments/assets/ee0f850e-ae2f-429b-83bb-ff38233224d2)

### Atribuição de um IP na rede interna

Neste passo irá ser atribuído um IP fixo á minha rede interna, irei mudar o nome dos adaptadores para não se confundirem, á rede interna irei mudar o nome para **Int** e para a rede externa irei mudar o nome para **Ext**.

![15](https://github.com/user-attachments/assets/a3e838af-cd4c-40c5-9adb-b462e8bdcf41)

![16](https://github.com/user-attachments/assets/1c2f7a57-a302-40e3-8792-ac19b0f457a3)

Irá agora ser atribuído um IP fixo á rede interna ao configurar o adaptador **Int**.
Com o botão direito do rato, clicar em **Properties**, escolhendo a opção **Internet Protocol Version 4 (TCP/IPv4)** e de seguida **Properties** outravez.

![17](https://github.com/user-attachments/assets/f3689f2a-66ac-4ee2-a88a-f8fe17821a2a)

![18](https://github.com/user-attachments/assets/19f663e5-e9ad-4724-b9e3-bf4f1aa285be)

Nesta janela irá ser necessário introduzir um **IP** e uma **Subnet mask** (irão ser atribuidos IPs ás máquinas que fazem parte da rede interna e que estiverem ligadas ao servidor).
O IP escolhido será **192.168.1.200** e a Subnet mask **255.255.255.0**. Clicar em **Advanced**.

![19](https://github.com/user-attachments/assets/2ef73984-f03e-4dc7-b855-7d32c1a65af4)

Na opção **Interface Metric** irei colocar **1**, fazendo com que este adaptador tenha prioridade na ligação da máquina, e premir **Ok**.

![20](https://github.com/user-attachments/assets/ee1092de-755f-42fb-9a44-a492cca3be13)

Para o adaptador externo iremos só colocar no **Interface Metric** o número **20**.

![21](https://github.com/user-attachments/assets/38c5061f-32a8-4c1b-a826-229942e40e0c)

Para testar o funcionamento da configuração, abrir o **cmd**, e usamos o comando **ping**, iremos fazer ping ao IP escolhido anteriormente.

![22](https://github.com/user-attachments/assets/6f8be303-8a6a-439b-9f5f-49be19599818)

![23](https://github.com/user-attachments/assets/4d244562-0dcb-4e07-aa6a-c19bb4b15b50)

Ao escrever **ipconfig** no cmd vejo as definições dos adaptadores de rede.

![24](https://github.com/user-attachments/assets/ecaeaed8-1730-42af-946c-a665d8a65cdb)

