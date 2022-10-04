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
 
 Suporte a <b>journalin<b> que dá suporte ao sistema operacional manter um log(<i>journal<i>
 

