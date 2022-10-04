## Linux

*Sistema de Arquivos*

 -- Windows --
* A: unidade de disquete
* B: unidade de disquete
* C: unidade de disco rígido
* D: unidade de disco rígido
* E: unidade de disco rígido ou removível

-- Linux --

Sendo ligado em uma IDE(placas-mãe mais antigas) <br>
* Master primário IDE: /dev/hda
* Escravo primário IDE: /dev/hdb
* Master secundário IDE: /dev/hdc
* Escravo secundário IDE: /dev/hdd <br>

Os arquivos de dispositivos SCSI ou SATA são semelhantes, exceto pelo fato de que não há uma limitação de quatro dispositivos.

* Primeiro drive SCSI: dev/sda
* Segundo drive SCSI: dev/sdb
* Terceiro drive SCSI: dev/sdc
* ...assim por diante

### Divisão das Partições

Sendo uma IDE, o linux dividirá as partições em: HDA1, HDA2, HDA3 e HDA4. <br>
Sendo uma SATA, o linux dividirá as partições em: SDA1, SDA2, SDA 3 e SDA4. <br>

O linux não trabalha com unidades de disco como o Windows (C:\D:). <br>
O linux trabalha com diretórios (pontos de montagem) e tudo começa com o diretório /(raiz) <br>

![image](https://user-images.githubusercontent.com/89140035/193908624-c5a7bb47-470a-4c6e-83d9-9754df96797c.png)

Cada um dos diretórios acima, poderia estar em um partição separada.<br>
O sistema de arquivo do linux é conhecimo como <b>ext4</b>. Esse sistema permite gravação de arquivos de até 16TB com partições de até 1Exabyte.<br>
 
 Suporte a <b>journaling</b> que dá suporte ao sistema operacional manter um log(<i>journal</i>), de todas as mudanças no sistema de arquivos antes de escrever os dados no disco, com a possibilidade de recuperar um arquivo mesmo que o mesmo tenha sido delatado da lixeira. <br>
 
 O linux é capaz de montar uma série de sistemas de arquivos, como:<br>
 * ext2: O sistema de arquivos padrão linux
 * ext3: Um sistema de arquivos com recursos de journaling
 * ext4: Um sisgema de arquivos com recursos de journaling
 * ntfs: A partição nativa do MS Windows
 
### Instalação do Linux

O Debian é especialmente conhecido pelo seu sistema de gestão de pacotes, chamado APT, que permite: atualização, instalação quase sem esforço para novos pacotes e remoção limpa de pacotes antigos.<br>

O ciclo de desenvolvimento das versões do Debian passa por três fases:<br>
* Unstable - instável
* Testing - teste
* Stable - estável

Quando as versões estão na fase "testing" elas são identificadas por codinomes tirados dos personagens do filme Toy Story. Ao se tornarem "stable" as versões recebem um número de versão.<br>
 
Utilização do Debian 11 e VirtualBox para instalação no modo texto padrão.<br>

Após a montagem da .ISO e posterior instação, seguindo os passos de idioma, local e teclado, o sistema perguntará com o nome da máquina na rede.

![image](https://user-images.githubusercontent.com/89140035/193921631-af0a1617-f943-4515-b647-2b71ac513cfa.png)

Deixando como padrão ficará apenas debian, mais para frente será mostrado como mudar isso dentro do sistema. Logo em seguida será perguntado o nome do domínio, que por hora ficará em branco.

![image](https://user-images.githubusercontent.com/89140035/193922154-8e3b7ef0-b9e7-4439-b9dd-c3c011c51912.png)

Após o sistema apresentará uma tela para definição de senho do administrador do sistema (usuário root).

![image](https://user-images.githubusercontent.com/89140035/193922709-42b80191-1170-40b4-ba48-2606a961bb34.png)

A senha escolhida foi: "teste"

Será pedido a confirmação da senha:

![image](https://user-images.githubusercontent.com/89140035/193923205-58539544-5ea0-4d4a-b3fe-0b64303be24f.png)

Após pergunta o nome completo do usuário:

![image](https://user-images.githubusercontent.com/89140035/193923499-f33dbd70-ab23-45aa-8158-7da940c53c3c.png)

Depois pergunta o nome de uma conta (convidado), já sugerindo o primeiro nome do root:

![image](https://user-images.githubusercontent.com/89140035/193923935-aaf06da7-12bf-4e42-8255-1a2f321b56f4.png)

Após uma senha para essa conta nova:

![image](https://user-images.githubusercontent.com/89140035/193924281-76e685a7-489f-4925-8b88-dc6b9ed82eb3.png)

Depois o linux perguntará o fuso horário, e após isso o <b>particionamento do disco</b>.

![image](https://user-images.githubusercontent.com/89140035/193924815-a47cba49-d266-493a-acd0-705ba5cfc2d3.png)

Utilizaremos a opção "manual", será selecionado a opção que foi criada pela nossa máquina virtual.

![image](https://user-images.githubusercontent.com/89140035/193925590-13386210-4e73-4b7b-97f0-e6797fef5171.png)

Selecione a opção "Sim" em Criar nova tabela de partições vazia neste dispositivo?<br>
Veja que agora foi criado um espaço vazio, que será nossa opção, conforme figura:

![image](https://user-images.githubusercontent.com/89140035/193926040-98a6ab23-7d7d-48a5-9adf-87caec1fdd68.png)

Será perguntado então a criação de uma nova partição, ao selecionar "Criar nova partição"

Dentro dos padrão da Certificação LPI, é aconselhável a criação de uma partição de 100MB:

![image](https://user-images.githubusercontent.com/89140035/193927055-55a00fd3-8bf8-4625-a303-ec3350438e68.png)

Esse disco será uma partição primária, alocando-o no ínicio.

![image](https://user-images.githubusercontent.com/89140035/193927459-09f870c2-7bf5-4fbd-a095-5afd7177f2a7.png)

Veja que foi criado um sistema de arquivo do tipo ext4, com um ponto de montagem / nele, no entanto, ele é muito pequeno (100 MB) para tê-lo como ponto de montagem, então vá até a linha de "ponto de montagem" para mudar a opção para /boot:

![image](https://user-images.githubusercontent.com/89140035/193927939-525077e3-407f-4022-bf2c-39d10104ffe6.png)

Após a seleção vá em "Finalizar a configuração da partição". O sistema mostrará que o sistema /boot foi criado com sucesso, sendo que ainda existe um espaço livre, selecione, crie uma nova partição. Agora para o diretório de dados selecione pelo menos 20 GB de dados. Esse partição também será primária e alocada no início. Após isso crie as áreas de /home (local de arquivos do usuário) e o diretório de swap (área de troca do HD/SSD para a memória RAM, caso a memória RAM estaja 100% ocupada, havevrá um espaço no HD para alocação de dados).

![image](https://user-images.githubusercontent.com/89140035/193930928-fb233bb8-eb07-448b-a265-476b4ebef730.png)

Após, será perguntado sobre o gerenciamento de pacotes, nele selecione o país e o espelhodo repositório do Debian. Após será perguntado se da utilização de servidor proxy, como não é o caso, ficará em branco, apenas aperte continuar.

![image](https://user-images.githubusercontent.com/89140035/193933210-588fe4cb-d126-40df-b244-e289ece385af.png)

Após o processo de download dos pacotes e instalação o sistema perguntará se o usuário deseja participar do concurso de utilização de pacotes, apenas aperte "Não".

Após isso será perguntado dos itens que se deseja instalar, selecione apenas o básico:

![image](https://user-images.githubusercontent.com/89140035/193933997-22ab04c1-5946-445c-aa2d-bb69377829af.png)

Na próxima tela o linux esta solicitando a instação do carregado de inicialização GRUB. Sem ele o sistema operacional não será capaz de inicializar, então selecione "Sim". Logo em seguida, será perguntado qual dispositivo será feita a instalação, selecione o /dev/sda:

![image](https://user-images.githubusercontent.com/89140035/193934780-44fbba3b-eac7-4297-888e-0673cb6c84c6.png)

Finalizado:

![image](https://user-images.githubusercontent.com/89140035/193935277-d10a1c1b-f46d-4ba3-aa65-f5683aa44c3b.png)


### Comando de manipulação de terminal







