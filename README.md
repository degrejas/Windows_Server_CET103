# Windows_Server_103
Manual de criação de um servidor Windows para CET103.
# Índice
[Manual passo a passo](#manual-passo-a-passo)

- [Criação de uma máquina virtual](#criação-de-uma-máquina-virtual)

- [Instalação do Sistema Operativo](#instalação-do-sistema-operativo)

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
