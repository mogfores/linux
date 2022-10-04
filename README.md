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
 
 Suporte a <b>journalin</b> que dá suporte ao sistema operacional manter um log(<i>journal</i>), de todas as mudanças no sistema de arquivos antes de escrever os dados no disco, com a possibilidade de recuperar um arquivo mesmo que o mesmo tenha sido delatado da lixeira. <br>
 
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
 

