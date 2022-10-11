## Linux 🐧

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

### Divisão das Partições 💾

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
 
### Instalação do Linux 👽

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


### Comando de manipulação de terminal 💻

O linux é <b>case sensitive</b>, ou seja, ele faz diferença entra maiúsculas e minúsculas.<br>

O usuário root(raiz) também é representado por #(sustenido)

* su : entrar no modo administrador

O usuário convidado é representado por $.<br><br>

* ls    : lista o conteúdo do diretório
* ls -l : lista os arquivos por linha
* ls -r : inverte a ordem de seleção (ordem decrescente)
* ls -a : lista os arquivos ocultos
* ls|more: lista pausadamente os arquivos
* ls*.extensão_do_arquivo: lista somente arquivos com uma extensão<br><br>

* cd ..: volta um diretório
* cd nome_da_pasta : mudar diretório (change directory)
* cd / : mudar diretamente para o diretório raiz(/)<br><br>

* clear : limpa a tela do prompt
* pwd : mostra o caminho completo do diretório
* mkdir nome_da_pasta : cria uma pasta (diretório)
* rmdir nome_da_pasta: apaga uma pasta (diretório. Obs.: a pasta precisa estar vazia)
* cat nome_do_arquivo: visualiza o conteúdo do arquivo no modo texto<br><br>

O linux possui um comando de auto-completar. Ex. caso queira entra na pasta home, fica:<br>
cd /h --> ao apertar TAB, o linux completara com o caminho /home
Se no diretório possuir mais de uma pasta com a inicial "h", ao apertar TAB duas vezes o linux mostrará as opções de escolha.<br><br>

<b> Comandos CP - Copia os arquivos</b><br>
* cp arquivo.extensão arquivo1.extensão : copia o arquivo "teste.txt" para "teste1.txt"
* cp arquivo.extensão/diretório arquivo.extensão: copia o arquivo "teste.txt" para a pasta /tmp
* cp * /diretório: copia todos os arquivos do diretório atual para o diretório especificado.
* cp-R/diretório/* /diretório: copia todos os arquivos e subdiretórios para a pasta especificada (cópia recursiva).

<b> Comandos MV - move arquivos e diretórios</b><br>
* mv arquivo.extensão /diretório: move o arquivos para o diretório especificado.
* mv /diretório/* /diretório: move todos os arquivos do diretório para o outro especificado.

<b> Comandos RM - Apaga um arquivo</b><br>
* rm arquivo.extensão: apaga o arquivo "teste.txt" no diretório atual.
* rm * .extensão: apagam os arquivos do diretório atual com a extensão ".txt"
* rm -rf diretório/sub-diretório/* : apaga todos os arquivos do diretório e subdiretório
* rm -rf diretório/sub-diretório: apaga todos os arquivos e o diretório

![image](https://user-images.githubusercontent.com/89140035/193950065-8952b678-0e54-4493-b1da-5f1fdf0735ce.png)

![image](https://user-images.githubusercontent.com/89140035/193950699-e61e42a7-807d-4b27-ab24-30b758a2fece.png)

![image](https://user-images.githubusercontent.com/89140035/193950961-2d8aaca1-49c6-402b-929e-0cb15cf58017.png)

![image](https://user-images.githubusercontent.com/89140035/193951364-6028ae6f-d651-4d93-9fa5-2076d1560e8d.png)


### Comandos do Linux 💣

* Ctrl + C : parar a atividade atual
* Alt + F1, F2, F3... : trocar de terminal de usuário
* <b> Use su -l ou su - para iniciar o shell raiz com um ambiente semelhante a um shell de 'login' normal. </b>


### Editor de Arquivos 💼

No linux existem vários editores de arquivos, por padrão no sistema nós temos o vi.

vi - Para criar ou abrir um arquivo já existente nós utilizamos o comando:<br>
<b>vi nome_do_arquivo</b>

Opções: para fechar a opção pressionar ESC
* i : insere texto a partir do cursor atual
* a : insere texto depois do cursor atual
* l : insere texto no início da linha
* A : insere texto no final da linha
* /Expressão : Procura expressão (que pode ser qualquer palavra) no texto
* n : procura próxima ocorrência de Expressão no texto
* N : procura a ocorrência anterior
* v : seleciona o texto
* yy : copia linha atual do texto para memória
* p : cola conteúdo da memória no texto
* dd : apaga linha atual (e coloca na memória)
* u : desfaz última ação executada
* . : refaz última ação executada
* :n : Pula para linha de número n
* :w : salva o arquivo atual
* :wq : salva o arquivo atual e sai do Vi
* :q : sai do Vi
* :q! : sai do Vi, independente de salvar o conteúdo atual

### Histórico e Edição de Comandos 🪐

Trabalhando com um prompt de comando pode ser necessário e interessante conusltar ou até mesmo repetir um determinado comando executado.

Os shells modernos, como o <b>bash</b>, incluem um importante conjunto de recursos chamados de histórico, expansão e edição dos comandos.

A primeira parte desse conjunto é o histórico.

A lista de históricos é controlada pela variável de shell HISTSIZE.

Por padrão é definida com 500 linhas.

Podemos consultar o tamanho da variável lendo ela com o comando: <b>echo $HISTSIZE</b>

![image](https://user-images.githubusercontent.com/89140035/194132446-7b46065b-213f-48ea-aec7-0b197d1ce1f7.png)

Para visualizar o seu histórico de comandos, use o comando <b>history</b>.

Heverá um número de linha antes de cada comando.

Esse número poderá ser usado posteriormente na expansão do histórico.

![image](https://user-images.githubusercontent.com/89140035/194162739-ba6acf12-e3c7-4134-8abf-b4e78fc1e94e.png)

### Designadores de expansão de histórico 🗄️

* !! : refere-se ao último comando executado
* !n : refere-se ao comando n do histórico, use o comando history para exibir esses números
* !string : refere-se ao comando mais recente que comece com string (ex.:!c - buscará o comando mais recente no histórico que comece com a letra "c")
* !?string : refere-se ao comando mais recente que contenha a string (ex.:caso queria entrar no comando "pwd" mas só lembra das letras "wd", basta colocar !?pw)

### Criação e manipulação de arquivos 📂

Digitando sequencia de comandos: pode acontecer de surgir à necessidade de digitar dois comando na mesma linha do prompt, o linux permite essa opção, mas os comandos devem ser separados por <b>;</b>

Exemplo: #ls ; ps

Comando <b>touch</b>: esse comando é utilizado para criar arquivos vazios e alterar o registro de data e hora dos arquivos.

![image](https://user-images.githubusercontent.com/89140035/194166904-00836626-612d-46d0-a76c-e55cb8419917.png)

Ele também pode criar vários arquivos de uma vez

![image](https://user-images.githubusercontent.com/89140035/194167032-519c0e7b-c853-4d50-9204-e7b4142cfa17.png)

Ele também modifica a data e hora de acesso e modificação de arquivos.

Você pode modificar tanto a hora de acesso quanto a hora de modificação dos arquivos, ou os dois ao mesmo tempo.

Legenda:
* A - ano (é considerado a faixa de 1969 - 2068)
* M - mês
* D - dia
* h - hora
* m - minutos
* s - segundos

Para modificar a data e hora de acesso e modificação de um arquivo basta fazermos o seguinte:

<b>touch -t AAAAMMDDhhmm arquivo</b>

Para mudar a data e a hora de modificação para a atual, utilize a opção <b>-m</b>

<b>touch -m teste.txt</b>

O comando touch não substitui (caso você crie arquivos com o mesmo nome) os arquivos já criados!!! 💣

### Processos de sistema

* <b>ps</b>

O comando ps exibe informações sobre os processos que estão executando na máquina.

Opções:

* -a : mostra os processos de todos os usuários
* -A : mostra todos os processos
* -f : mostra a árvore de execução de comandos
* -x : mostra os processos que não foram iniciados no console
* -u : fornece o nome do usuário e a hora de início do processo

![image](https://user-images.githubusercontent.com/89140035/194173001-e88367b4-fbb1-47d4-baf1-ca248dc74b1a.png)

* <b>top</b>

O comando <b>top</b> oferece uma saída semelhante à ps, porém em uma exibição continuamente atualizada.

Isso é útil em situações nas quais você precisa monitorar o status de um ou mais processos ou para ver como eles estão usando o seu sistema.

Opções:

* -i : ignora os processos ociosos, listando apenas os em execução.

![image](https://user-images.githubusercontent.com/89140035/194173990-16fea730-b6d8-4fe7-80d1-3eb9307ae934.png)

* <b>kill</b>

Em sua simples forma o kill é usado para parar um processo imediatamente. Basta inserir o número do processo que tem que ser finalizado.

#kill 1000

OBS.: Ocasionalmente com o comando ps ou top um processo pode estar marcado como zumbi, são processos que ficaram travados ao tentar terminar, assim como nos filmes, não é possível matar um processo zumbi porque ele já esta morto.

* <b>free</b>

Esse comando exibe a quantidade de memória livre e usada do sistema.

Opções:

* -b : mostra o uso da memória em bytes
* -k : mostra o uso da memória em kilobytes
* -m : mostra o uso da memória em megabytes

![image](https://user-images.githubusercontent.com/89140035/194176090-6aae23f0-808d-47ec-9548-7376e866e22d.png)

* <b>uptime</b>
 
 O comando uptime mostra as seguintes informações: hora atual, quanto tempo o sistema rodando e quantos usuários estão logados no momento e as médias de carga no sistema (processamento) nos últimos 1, 5 e 15 minutos.
 
 ![image](https://user-images.githubusercontent.com/89140035/194177023-eacf1cb3-8327-4f7a-bb24-c28292df542d.png)

 ### Desligando e reiniciando o Linux modo texto 📴
 
 * shutdown tempo_em_minutos -r : reiniciar (caso não funcione use: systemctl reboot)
 * shutdown tempo_em_minutos -h : desligar
 * shutdown -h now : desligar no mesmo momento (caso não funcione use: systemctl poweroff)
 * shutdown -c : cancelar os shutdown agendadas nas opções acima
 * halt : para o sistema operacional, porém o hardware continuará em execução
 * reboot : reiniciar o computar imediatamente
 

### Usuários e Grupos 🧑 👨‍👨‍👦‍👦

No Linux, existem 3 tipos de usuários:

* 1º Administrador

Esse usuário tem permissão total de utilização do sistema, podendo criar pastas/arquivos em qualquer diretório, além de poder editar e excluir qualquer arquivos de qualquer usuário ou de sistema.

Esse usuário pode executar, também, qualquer comando disponível no sistema operacional.


* 2º Comum

Esse usuário tem algumas restrições na utilização do sistema, não podem executar todos os comandos, configurações ou acessar qualquer diretório.

* 3º Sistema

É um usuário criado durante a instalação de algum programa ou serviço para executar tarefas específicas daquele programa. Não é possível logar no sistema utilizando este usuário.

<b>Comandos</b>

* adduser nome_do_usuário : criar um novo usuário
* deluser nome_do_usuário : apaga um usuário
* deluser no_do_usuário -remove-home : apago o usuário e seu diretório /home
* passwd nome_do_usuário : trocar ou define uma nova senha
* passwd -l nome_do_usuário : bloquear a conta de um usuário
* passwd -u nome_do_usuário : desbloquear a conta de um usuário
* logname : mostra o usuário logado no sistema no mesmo terminal
* users : mostra os usuários conectados no sistema em todos terminais

Os usuários são cadastrados no sistema através do arquivo <b>/etc/passwd</b>. É possível editar as configurações do usuário manualmente através deste arquivo.

![image](https://user-images.githubusercontent.com/89140035/194397461-e41a88bf-557b-4dd2-a259-03457cc847c5.png)


* groupadd nome_do_grupo : cria um novo grupo
* adduser usuário grupo : adiciona um usuário a um grupo
* groups nome_do_grupo : mostra os usuários do grupo
* group nome_do_usuário : mostrar os grupos a qual o usuário pertence

As informações sobre os grupos e seus usuários ficam salvas em <b>/etc/group</b>.<br>
Neste arquivo é possível adicionar um usuário a um grupo manualmente, é necessário colocar umam virgula seguida do nome do usuário que se deseja acrescentar:

![image](https://user-images.githubusercontent.com/89140035/194398548-cd161271-194d-49e4-8106-205537b9b243.png)

Ex.: <b>nome_do_grupo:x1002:eduardo, nome_do_novo_integrante</b>

![image](https://user-images.githubusercontent.com/89140035/194399783-93207fc6-c4d0-4440-bdb0-b78bdfbea98d.png)


<b>root:x:0:0:root:/root:/bin/bash</b>

root : nome de login do usuário<br>
x : indica que a senha do usuário está localizada no arquivo /etc/shadow (criptografa)
0 : UID do usuário
0 : GID do usuário
/root : diretório HOME do usuário
/bin/bash : shell do usuário, o programa interpretador de comandos

Para usuários comuns, ainda pode aparecer:

,,, - informações do usuários, como nome, telefone...

O arquivo <b>/etc/shadow</b> é utilizado para armazenar as senhas dos usuários no linux, de maneira criptografada. Também armazena informações sobre datas de expiração e validade das contas.

![image](https://user-images.githubusercontent.com/89140035/194412065-938785ed-2fad-47da-8c9e-ce2d0c024737.png)

<b>root</b> : nome de login do usuário<br>
<b>$y$j9T...</b> : indica a senha do usuário criptografada<br>
<b>19269</b> : data da ultima alteração de senha, armazenada como o número de dias decorridos desde 01/01/1970<br>
<b>0</b> : dias até que a senha possa ser alterada novamente<br>
<b>99999</b> : dias antes que uma alteração seja necessária<br>
<b>7</b> : dias de avisos antes da expiração da senha<br><br>

Algumas distribuições podem ainda usar os 3 últimos campos (:::) que são, <b>dias entre expiração e desativação, data de expiração, flag especial</b> (campo reservado).


### Instalação e Gerenciamento de Pacotes do Linux

* <b>Gerenciar Bibiotecas Compartilhadas</b>

Quando um programa é compilado no linux, muitas das funções requeridas pelo programa são vinculadas a partir de bibliotecas de sistema que lidam com discos, com a memória e com outras funções.<br>
Por exemplo, quando a função printf() da linguagem C padrão é usado em um programa, o programador não fornece o código finte de pintf(), mas, em ve disso, espera que o sistema já possua uma biblioteca contendo esse tipo de função.<br>
Programas utilizam as rotinas do sistema, mas não incorporam o código das bibliotecas. Em vez disso, esse código é vinculado ao executável no momento da execução.<br>
Esse processo de vinculação são compartilhados entre muitos aplicativos e, por isso, são chamadas de bibliotecas compartilhadas.

* <b>Dependências de Bibliotecas Compartilhadas</b>

Qualquer programa que esteja dinamicamente vinculado precisará de pelo menos algumas poucas bibliotecas compartilhadas. Se a biblioteca requeria não existir ou não puderem ser conectadas, o programa não poderá rodar.<br>
Isso poderia acontecer, por exemplo, se você tentar rodar um aplicativo escrito para o ambiente gráfico GNOME sem ter instalado as bibliotecas GTK+ requeridas.<br>
Instalar as bibliotecas corretas deve ser o suficiente para eliminar tais problemas.<br>


* <b>ldd</b>

O utilitário ldd pode ser usado para se determinar quais bibliotecas são necessárias para um executável específico, deverá ser executado dentro da pasta /bin.<br><br>
Exemplo: O top requer 12 bibliotecas compartilhadas:<br>

![image](https://user-images.githubusercontent.com/89140035/194417699-ddf7f166-bfe5-438c-bfdc-a810d43b7076.png)

A primeira linha é o kernel (linux-vdso.so.1), e tudo que estiver com setas "=>" são as bibliotecas.

* <b>Visão geral do gerenciamento de pacotes do Debian </b>

Cada pacote do Debian contém arquivos de programas, configurações, documentação e indicação de dependências. Os nomes dos pacotes do Debian possuem três elementos em comum, incluindo:

<b>Nome do pacote</b><br>
Um nome de pacote do Debian é sempre curto e descrito e quando várias palavras são usadas elas são separadas por hifens.<br><br>

<b>Número da versão</b><br>
Cada pacote tem uma versão. A maioria das versões dos pacotes tem o mesmo número que o software que elas contêm.<br><br>


<b>Extensão do arquivo</b><br>
Por padrão todos os pacotes do Debian terminam com a extensão .deb

Exemplo: nano-tiny_2.2.4-1_amd64.deb

* <b>Gerenciando os pacotes do Debian</b>

No inicio havia o <b>.tar.gz</b>. Os usuários tinham de penar para compilar cada programa usado em seu sistema GNU/Linux.<br>
Quando o Debian foi criado, sentiu-se a necessidade de um sistema de gerenciamento de pacotes instalados no sistema.<br>
Deu-se a esse sistema o nome de <b>dpkg</b>. Logo após a Red Hat resolver criar seu sistema conhecido como <b>rpm</b>.<br>
Rapidamente outro dilema tomou conta das mentes dos produtores de GNU/Linux. Uma maneira rápida, prática e eficiente de se instalar pacotes, gerenciando suas dependências automaticamente e tomando conta de seus arquivos de configuração ao atualizar.<br>
Assim, o Debian, criou o <b>APT ou Advanced Packging Tool</b>
A ferramenta original de gerenciamento de pacotes do Debian é dpkg, que opera diretamente sobre os arquivos de pacotes .deb e pode ser usada para automatizar a instalação e a manutenção dos pacotes de software.<br>
A ferramenta alternativa apt opera usando nomes de pacotes, obtendo-os a partir de uma fonte predefinida (CD-ROMS e sites FTP).<br>
O comando <b>alien</b> permite o uso de pacotes não Debian, tais como o formato RPM do Red Hat.

* <b>dpkg</b>

Opções de entrada:

<b>-E</b> : instrui o comando a não sobrescrever um pacote instalado, da mesma versão

<b>-G</b> : instrui o comando a não sobrescrever um pacote instalado com uma versão mais antiga

<b>--configure package</b> : configura um pacote descompactado

<b>-i package_file</b> : instala o respectivo pacote

<b>--purge package</b> : remove tudo a respeito de package

<b>-r package</b> : remove tudo, exceto os arquivos de configuração

<b>-s package</b> : relata o status do package

<b>dpkg --get-selections</b> : lista dos pacotes já instalados

![image](https://user-images.githubusercontent.com/89140035/194428803-42db912d-1ce3-4efc-b1ba-5c031c331013.png)



Baixar o Pacote<br>
![image](https://user-images.githubusercontent.com/89140035/194430185-8a5c94e8-454e-4ec9-88a0-62966a973448.png)

Instalar o pacote<br>
![image](https://user-images.githubusercontent.com/89140035/194430279-a3434d3d-4ee8-47de-bf61-e89acbc45cec.png)


*<b>APT</b>

Sintaxe:

apt-get opções nome_do_pacote

Ele não trabalha diretamente com os arquivos .deb como o dpkg, mas usa, em vez disso, nomes de pacotes .apt-get, além de fazer a configuração automática das dependências do pacote.

<b>-d</b> : faz o download de arquivos, mas não instala

<b>-s</b> : simula os passos em uma modificação de pacotes, mas não modifica realmente o sistema

<b>-y</b> : responde "yes" as todas as perguntas do prompt

<b>-dist-upgrade</b> : faz upgrade do Debian

<b>install</b> : instala ou faz upgrade de pacotes mais novos

<b>-remove</b> : remove os pacotes especificados

<b>-update</b> : obtém uma lista atualizada de pacotes disponíveis para o APT-GET

<b>-upgrade</b> : faz upgrade do conjunto de pacotes instalados no sistema

<b>OBS</b>: O apt-get usa o arquivo /etc/apt/sources.list para determinar de onde os pacotes deverão ser obtidos:

![image](https://user-images.githubusercontent.com/89140035/194432165-b6db55a6-93c8-475d-a2df-197d78e2f6b1.png)

O sustenido # é uma linha comentada, logo não será necessário inserir CD-ROM toda vez que instalar o sistema.

*<b>Procurar programas na lista do repositório</b>

apt-cache search nome_do_programa

![image](https://user-images.githubusercontent.com/89140035/194432781-19e5c136-b9ac-4ee1-bb52-a6e7bb7fdb6e.png)


* <b>Alien</b>

Comando converte ou instala um pacote não Debian. Os tipos de pacotes suportados incluem o .rpm do Red Hat, o .tgz do Slackware, além de arquivos .tar.gz genéricos.

OBS: Não é uma garantia de funcionamente - tenta converter o pacote

O RPM tem que estar instalado no seu sistema para poder fazer a conversão.

Opções:

<b>-i</b> : instala automaticamente o pacote gerado<br>
<b>-r</b> : converte o pacote para RPM<br>
<b>-t</b> : converte o pacote em um arquivo gzip tar<br>
<b>-d</b> : converte o pacote para DEB<br>

Exemplo:

Instalar automaticamente um pacote não Debian em um sistema Debian

<b>alien -i package.rpm</b>
<b>alien -d package.rpm</b>


### Localizadores de Arquivos 🔎

* <b>Find</b>

O comando find, realiza a busca de arquivos pelo seu nome, podemos utilizar a sintaxe abaixo:

<b>root@debian:/# find -name nome_do_arquivo</b>

Esse comando buscará a partir do diretório que o usuário se encontra

![image](https://user-images.githubusercontent.com/89140035/194637991-2bf9d75c-678f-4d18-a96d-4c972cf3edd1.png)

Podemos listar todos os arquivos contido em um diretório junto com os seus subdiretórios utilizando a sintaxe:

<b>root@debian:/# find</b> ou <b>find .</b>

![image](https://user-images.githubusercontent.com/89140035/194639169-cd602c73-cc60-45f5-9e08-1b87fcbe5bbc.png)

Com o comando find também podemos listar somente arquivos ou somente diretórios com a opção <b>-type f</b> para arqvuios e <b>-type d</b> para diretórios

* <b>locate</b>

O comando locate utiliza uma base indexada para localização de arquivos.

Antes de sua utilização é necessário construir esta base com o comando <b>updatedb</b>

Na primeira execução deste comando é criada a base e todo o hd/ssd é varrido para a construção da base e de sua indexação

Por questão de performance e segurança, este comando não indexa diretórios temporários, dirtórios pessoais (/home, /root) e sistemas de arquivos remotos (mapeamentos)

Qualquer pesquisa realizada por qualquer usuário somente retornará os dados a que o usuário tiver permissão de acesso.

![image](https://user-images.githubusercontent.com/89140035/194644173-416a5622-9199-4e60-9f3d-400714b9e45a.png)

![image](https://user-images.githubusercontent.com/89140035/194644236-3ee1f47c-8d6b-4c7d-a6ee-150490e6b5a2.png)

![image](https://user-images.githubusercontent.com/89140035/194644528-2db2b9a6-f733-412b-989f-6533464fbe2a.png)


### Comando GREP 🔡

Muitas vezes, precisamos localizar um arquivo pelo seu conteúdo e não apenas pelo seu nome. Para isso utilizamos o comando grep.

Sintaxe:

<b>grep opções filtro-a-aplicar arquivo ou diretório</b>

Ex.: Localizar a ocorrência "ldap" dentro do arquivo /etc/services:

grep "ldap" /etc/services

![image](https://user-images.githubusercontent.com/89140035/194645121-9149c00e-14b2-4a93-b07f-58d066bcb94d.png)

Outro exemplo pode se a pesquisa por ocorrência em letras que independentemente estejam em maiúsculas ou minúsculas com a opção -i

<b>grep -i "name" /etc/services</b>
 
 ![image](https://user-images.githubusercontent.com/89140035/194645850-d67839bd-cc84-4404-8431-4e4e9e374a1a.png)
 
 Utilizando o grep também podemos destacar a cor do item procurando como no exemplo abaixo, utilizando <b>--color</b>
 
 <b>root@debian:/pasta_teste# grep "teste" --color eduardo.doc</b>
 
 Também é útil saber em qual linha se encontra a ocorrência, para isso adicionamos a opção <b>-n</b>
 
 <b>root@debian:/pasta_teste# grep -i "teste" --color -n eduardo.doc</b>
 
 Podemos ainda utilizar um caractere coringa como o * para realizar a busca em vários arquivos:
 
 <b>root@debian:/pasta_teste# grep -i "teste" --color -n *.doc</b>

 ![image](https://user-images.githubusercontent.com/89140035/194647943-13416d0b-8049-40d1-a84b-f6c6b31249e7.png)

Podemos realizar a pesquisa recursiva, isso é, realizando a busca em sub-diretórios -r

Outro recurso de grep é a opção -w onde será eliminado os resultados que conterem números, trazendo ocorrências que somente tiverem textos

![image](https://user-images.githubusercontent.com/89140035/194648555-e16c23ac-9bd9-4259-b60d-465185918f09.png)

Podemos solicitar que o comando grep conte o número de ocorrências da string com a opção -c

![image](https://user-images.githubusercontent.com/89140035/194649174-ece82ff3-289d-482a-aad2-76c67cca4881.png)

A opção -o mostra somente o texto que coincide com a string

![image](https://user-images.githubusercontent.com/89140035/194649499-3aecb492-175c-4cf8-b956-a50bb7977dd8.png)

A opção -B "n" mostra as linhas N antes da string

![image](https://user-images.githubusercontent.com/89140035/194650263-027d5018-629f-48fc-bf7d-e2183213e13e.png)

A opção -A "n" mostra as linhas N depois da string

![image](https://user-images.githubusercontent.com/89140035/194650793-22c959f3-cd0e-423f-8324-33b6f75df288.png)

A opção -C uni as duas opções, pegando e imprimindo linhas antes e depois da linha que contem a string pesquisada

![image](https://user-images.githubusercontent.com/89140035/194652544-9a9d25db-3709-4e41-be35-d2cd759c9df1.png)

A opção -l mostra somente o arquivo, não a string

![image](https://user-images.githubusercontent.com/89140035/194652854-9f408d2c-1ed0-40d1-99dc-74891393dd71.png)

A opção -L retorna os arquivos que não possuem a strig pesquisada

![image](https://user-images.githubusercontent.com/89140035/194653120-c43c9d2d-6f33-4c81-a40f-196447c4a0eb.png)

Com o grep, também é possível realizar buscar utilizando o que chamamos de Expressões Regulares. Para isso utilizamos a opção -E. A opção | funciona como se fosse um "OU"

![image](https://user-images.githubusercontent.com/89140035/194654607-40308851-80db-45dc-a354-a73cd4661b8e.png)

A opção . funciona substituindo o texto<br>
A opção \ funciona como um "escape" para que possa entender o . no exemplo

![image](https://user-images.githubusercontent.com/89140035/194668842-08d3f55f-a2f7-4e59-8694-25774dbd5a7b.png)

O comando grep pode ser utilizado junto com outro comando, utilizando o <b>pipe</b>

![image](https://user-images.githubusercontent.com/89140035/194669524-357270b9-88fc-40cd-8abd-e5971ce5c86c.png)


### Compactadores de Arquivos 🧬

* Comando Tar

O Tar(Tape Archive) é o que faz o empacotamento com a extensão .tar<br>
A Sintaxe do Tar é a seguinte:

<b>tar [parâmetros] [nome_do_arquivo_tar] [arquivo_de_origem]</b>

Exemplo: tar -cf dados.tar arquivo1 arquivo2 trabalho.doc planilha xls

Em parâmetros, é possível utilizar várias opções. Eis as principais:

-c : Cria um novo arquivo tar<br>
-t : exibe o conteúdo do um arquivo tar<br>
-r : adiciona arquivos a um arquivo tar existente<br>
-f : permite especificar o arquivo tar a ser utilizado<br>
-v : exibe detalhes da operação<br>
-w : pede confirmação antes de cada ação no comando<br>
-x : extrai arquivos de um arquivo tar existente<br>

1 - Compactar arquivos:
 
 <b>cf dados.tar arquivo1 arquivo2 arquivo3 (Obs:pode ser usado o caractere curinga*)</b>
  
2 - Visualizar o conteúdo de um arquivo tar:
  
<b>tar -tf dados.tar</b>
 
3 - Descoompactar um arquivo tar:

<b>tar -xf dados.tar</b>
 
4 - Adicionar um arquivo ao arquivo já compactado:
 
<b>tar -rf dados.tar arquivo_novo</b>
 
5 - Compactar arquivos e pedir confirmação de arquivo por arquivo:
 
<b>tar -cwf dados.tar*</b>
 
* bzip2
 
Compacta ou descompacta arquivos usando-se o algoritmo de compressão de texto que ordena blocos chamados Burrows-Wheeler e a codificação Huffman. Os arquivos compactados com bzip2 normalmente possuem a extensão .bz2.
 
Opções:
 
-d : descompacta um arquivo .bzip2
 
-1 a -9 : define o tamanho do bloco para 100k, 200k, 300k, ...900k ao fazer compactação. Isso define os níveis de compactação.
 
Compactar um arquivo usando o nível mais alto de compactação.<br>
<b>bzip -9*.doc</b> : compactar todos os arquivos .doc
  
Descompactar um arquivo com a extensão .bz2<br>
<b>bzip2 -d *.bz2</b> : descompactar todos arquivos .bz2
   
* gzip e gunzip
   
Esses comandos servem para compactar e descompactar arquivos usando a codificação Lempel-Ziv, o gzip é um dos formatos de compactação mais comuns encontrados em sistemas Linux, embora esteja sendo substituído pelo bzip2 que é mais eficiente. Os arquivos compactados com gzip normalmente possuem a extensão .gz.
   
Opções:

-d : descompactar um arquivo<br>
-r : navega pela estrutura de diretórios recursivamente, compactanto tudo

Descompactando o arquivo eduardo.gz
 
gunzip eduardo.gz<br>
ou<br>
gzip -d eduardo.gz
 

![image](https://user-images.githubusercontent.com/89140035/194924143-86db5601-05e0-418c-99d8-4db2b6785e81.png)

![image](https://user-images.githubusercontent.com/89140035/194924433-710d0295-e10d-4a8b-8699-0c5387225077.png)

![image](https://user-images.githubusercontent.com/89140035/194924881-56d93f09-aae8-4e60-b40c-a0eb75999835.png)

![image](https://user-images.githubusercontent.com/89140035/194928440-4caa7902-1f7c-4598-ba37-63db179a8253.png)

![image](https://user-images.githubusercontent.com/89140035/194928709-c78fddbf-dcfb-4ec7-8288-6f33850aca2f.png)

![image](https://user-images.githubusercontent.com/89140035/194928975-638ee18b-8274-4cf4-9aca-f2b89bdbe240.png)

![image](https://user-images.githubusercontent.com/89140035/194929130-1ab9e256-74bb-4941-bb58-b1ba69501003.png)

![image](https://user-images.githubusercontent.com/89140035/194929744-1c4d193b-456d-42c5-8d4c-2b17b475da38.png)

![image](https://user-images.githubusercontent.com/89140035/194929988-f3fcf69c-1dde-477e-9ac1-35c56edc3b5b.png)

![image](https://user-images.githubusercontent.com/89140035/194930435-e824d158-2731-4a85-a2f7-23ce5fd8c005.png)


### Gerenciamento de Sistemas de Arquivos 🗄️

O gerenciamento do sistema de arquivos está entre as atividades mais importantes que você precisa realizar para manter um sistema Linux estável.<br>
Em situações simples, após uma instalação com sucesso, você talvez nunca tenha um problema nem precise gerenciar detalhes específicos do sistema de arquivos.<br>
No entanto, entender como configurar e fazer a manutenção dos sistemas de arquivos do Linux é essencial para gerenciar com segurança o seu sistema.

* Partições de disco

Quase todos os sistemas operacionais tem suporte a um sistema para dividir um disco em dispositivos lógicos, chamados particções.<br>
O Linux oferece suporte a diversos formatos de particionamento diferentes, mas, por padrão, usa o formato do MS-DOS.<br>
A tabela de partição do MS-DOS permite até *quatro partições primárias*.<br>
Uma dessas quatro partições primárias pode ser substituída por uma partição estendida, que pode conter até 12 partições lógicas, para um total de 15 partições possíveis (16 se você incluir o container da partição estendida).<br>
O tipo de partição, bem como o tipo de dispositivo, afeta o nome do dispositivo que o Linux usa para acessar a partição.

* Partições de disco

Partições primária em um disco IDE:<br>
/dev/hda1<br>
/dev/hda2<br>
/dev/hda3<br>
/dev/hda4<br>

Partições estendidas:<br>
/dev/hda1<br>
/dev/hda2<br>
...<br>

As partiç~eso lógicas existem dentro da partiçao estendida e são numeradas de 5 a 16.

* Gerenciando partições

O Linux tem a opção básica para o particionamento de drivers de disco.<br>
O comando <b>fdisk</b> é um programa de modo texto fácil de usar e que existe em todas as distribuições do Linux.

Sintaxe:

<b> fdisk dispositivo </b>

O comando fdisk manipula ou exibe a tabela de particionamento para dispositivo usando uma interface de texto interativa, dirigida por comandos.<br>
Dispositivo é um disco físico, como <b>/dev/hda</b>, e não uma partição como /dev/hda1.<br>
Os comando interativos para fdisk são na forma de uma letra seguida por um retorno.<br>
Os comando não usam argumentos, mas iniciam um diálogo interativo.<br>
Os comando operam sobre partições que irão pedir o número da partição, que é um número inteiro.<br>
As fazer modificações à tabela de partição, fdisk acumula modificações sem escrevê-las em disco, até receber o comando <b>write</b>.

![image](https://user-images.githubusercontent.com/89140035/194937987-d86e140e-70fa-4fc9-861f-ad5ef33b96e9.png)

<b> #fdisk /dev/sdb</b>

![image](https://user-images.githubusercontent.com/89140035/194938836-e4b59e35-2037-40c4-b890-8d03e65cc6f3.png)

* Criar uma partição /dev/sdb no Virtual Box
* Pressionar a tecla <b>n</b> : criar nova partição

![image](https://user-images.githubusercontent.com/89140035/194940782-0de1c3db-720a-4627-adb6-117a4e3f4b24.png)

* Criar duas partições primárias e uma estendida

![image](https://user-images.githubusercontent.com/89140035/194941293-f2e4c8a5-2da2-4a9d-a149-2c29c7ec33c0.png)

![image](https://user-images.githubusercontent.com/89140035/194942505-4250ccb3-3aa8-424a-93c9-00e7f3fbe29d.png)

* Criando sistemas e arquivos

Uma vez particionado um disco, podem ser criados sistemas de arquivos nessas partições usando-se o utilitário <b>mkfs.</b><br>
O mkfs é uma ferramenta de criação de sistemas de arquivos, tais como mkfs.ext2 e mkfs.msdos, mkfs.ext3...<br>

Sintaxe: mkfs -tipo -opções dispositivo

O comando mkfs cria um sistema de arquivo, se o fstype for omitido, ext é usado por padrão (depende de qual distribuição estiver usando, por exemplo, o Debian 7 usa o ext4 como padrão).<br>
É comum ver referencias de comandos como mkfs.ext2, mkfs.ext4 que são alias para mkfs, especificando o tipo de sistema de arquivo desejado.

Opções:

-c : verifica se existem ba blocks em dispositivo antes de criar o sistema de arquivo. <br>
-L rótulo : define o rótulo do volume para o sistema de arquivos (apenas sistemas de arquivos com base em ext).<br>
-q : usa mkfs em modo silencioso, resultando em uma saída bastante reduzida.<br>
-j : cria um arquivo de jornal ext3.<br>

Exemplo:

Criar uma partição ext em /dev/sdb1:<br>
<b> mkfs /dev/sdb1 </b>

* Formantando o disco

![image](https://user-images.githubusercontent.com/89140035/194946801-05f88cc9-14a8-401b-a707-e004e8d12ef1.png)


### Montagem e desmontagem de sistema de arquivos ⚡

Quando o Linux faz o boot, o kernel realiza uma verificação de todos os sistemas de arquivos de <b>/etc/fstab.</b><br>
Todos os sistemas de arquivos que não tenham sido desmontados de forma limpa são verificados.<br>
Se essa verificação encontrar erros significativos, o sistema entra em modo de usuário único para que você possa excutar o <b>fsck</b> manualmente.

* Controlar a montagem e a desmontagem do sistema de arquivos

O Linux geralmente se compõe de várias partições, cada uma conectada ao sistema de arquivos root(/).<br>
Sistemas de arquivos de mídia removível, como CD-ROMS, USB..., são conectados da mesma forma, mas geralmente de forma temporária.<br>
Cada um desses sistemas de arquivos separados é montado no sistema na forma de diretório (ponto de montagem). <br>
Os diretórios criados para serem pontos de montagem geralmente não contém arquivos nem outros diretórios.<br>
Se um diretório que já contiver arquivos for usado como um ponto de montagem, os seus arquivos serão obscurecidos e ficarão indisponíveis até que o sistema de arquivos seja desmontado.<br>
Essas informações são registradas no arquivo <b>/etc/fstab.</b>
O arquivo /etc/fstab é de texto simples e consiste de linhas com seis campos:<br>

<b> Dispositivo: </b> : Este campo especifica o arquivo de dispositivo da partição que armazena o sistema de arquivos (/dev/hda1). Ele pode ser tanto o nome do dispositivo, ou o UUID do dispositivo. <br>

<b> Ponto de montagem </b> : Este campo especifica o diretório no qual o sistema de arquivos deve ser montado. Por exemplo, se /dev/hda1 contiver o sistema de arquivos root, ele será montado em /. <br>

<b> Tipo do sistema de arquivos </b> : Em seguida, é especificado o tipo do sistema de arquivos. Este pode ser do tipo ext4, swap, isso 9660 (CD-ROM) entre outros.

<b> Opções de montagem </b> : Este campo contém uma lista de opções, separadas por vírgulas. Algumas opções são específicas de determinados tipos de sistemas de arquivos.<br>

<b> Frequencia de dump </b> : O programa dump, um utilitário de backup padrão do Unix, consulta /etc/fstab para obter informações sobre a frequencia com que ele deve fazer o dumping de cada sistema de arquivos.

<b> Número de passe para fsck </b> : Este campo é usado pelo <b>fsck</b> quando a opção <b>-A</b> é especificada, geralmente no momento do boot. Trata-se de um flag que pode conter apenas os valores 0, 1 ou 2.

1 - instrui o fsck a verificar esse sistema primeiro.

2 - instrui o fsck a verificar os sistemas de arquivos correspondentes, após aqueles com um valor 1.

0 - instrui o fsck a não verificar o sistema de arquivos.

O arquivo /etc/fstab é criado automaticamente quando o Linux é instalado e é baseado na configuração de particionamento e de ponto de montagem especificada.

Esse arquivo pode ser modificado a qualquer momento para adicionar dispositivos e pontos de montagem.

Há uma série de parâmetros disponíveis como opções para se montarem sistemas de arquivos.<br>
Essas opções podem ser especificadas em /etc/fstab.

<b> auto </b> : habilita a montagem automática na inicialização do sistema operacional.<br>
<b> defaults </b> : implica rw, exec, auto, nouser. É encontrada comumente em entradas de /etc/fstab para pontos de montagem ext2, ext3 e ext4. <br>
<b> exec </b> : habilita a execução de programas contidos na partição montada. <br>
<b> noauto </b> : proíbe a montagem automática. É geralmente especificadas para mídias removíveis. <br>
<b> noexec </b> : proíbe a execução de programas executáveis, uma potencial medida de segurança. <br>
<b> nouser </b> : proíbe que usuários não root montem e desmontem o sistema de arquivos. <br>
<b> ro </b> : configura a partição para ser montada em modo de somente leitura. <br>
<b> rw </b> : configura a partição para ser montada em modo escrita. <br>
<b> users </b> : permite que qualquer usuário monte e desmonte o sistema de arquivos.

![image](https://user-images.githubusercontent.com/89140035/194956663-ede0d9d2-f1c3-40c1-91bc-58a497c431ea.png)

Para ver como isso funciona na prática, foi feita uma pasta chamada "mp3" no diretório /. Após isso, entramos com a opção de edição do arquivo fstab, com o comando:

<b> vi /etc/fst </b> 

E acrescentamos o ponto de montagem manualmente:

![image](https://user-images.githubusercontent.com/89140035/194958921-87ed138d-499b-49ca-b69a-562e17962d16.png)

Com o comando df -h é possível que o ponto de montagem ainda não foi montado, isso acontece porque a montagem acontece na inicialização:

![image](https://user-images.githubusercontent.com/89140035/194959388-fc26b6b0-b8c7-47e2-afee-f853a62919c9.png)

Logo, inicializaremos a máquina com o comando reboot

![image](https://user-images.githubusercontent.com/89140035/194959611-66dd8454-4ace-4871-a480-3499c3ffc3d7.png)

Agora vamos formatar o disco sdb2 com o comando <b> mkfs /dev/sdb2 </b>
 
![image](https://user-images.githubusercontent.com/89140035/194959894-335350b8-c06d-4217-b65b-d9c965563da4.png)

Agora vamos criar outra pasta em que só pode ser feita somente leitura pelo usuário.<br>
<b> mkdir leitura </b> <br>
 
Logo em seguida editaremos o arquivo fstab com o comando: <br>
<b> vi /etc/fstab </b> <br>
 
![image](https://user-images.githubusercontent.com/89140035/194961152-61d41c2f-02af-483e-9a92-dd141d85a080.png)

Veja que no mesmo caso não é possível ver montado sem o reboot:
 
![image](https://user-images.githubusercontent.com/89140035/194961285-cfc73aa6-2d63-4be2-8914-3fff73be877c.png)

Caso acontece algo de errado, por exemplo, erro de digitação, no reboot entrará em modo de emergência com a mensagem:
 
 <b> [FAILED] Failed to mount /leitura </b>

Neste caso só é possível entrar no modo root para verificar o erro e consertar.

![image](https://user-images.githubusercontent.com/89140035/194963907-738770ea-99b8-4117-a3a3-d83d782b6be8.png)
 
![image](https://user-images.githubusercontent.com/89140035/194964124-a92c23eb-10e0-4220-aaad-cc8e0b399fe2.png)

Veja que não é possível fazer qualquer alteração no diretório leitura, uma vez que ele foi mapeado apenas para ser leitura. Isso é importante para disponibilizar um disco para um determinado usuário que só terá poder de leitura mas não de alteração.

* Montando Sistemas de Arquivos
 
Os sistemas de arquivos são montados usando-se o comando <b> mount </b>.<br>
No momento do boot, os sistemas de arquivos com um número de passe diferente se zero em <b> /etc/fstab </b> são verificados e montado automaticamente. <br>
Depois disso, você pode rodar <b> mount </b> manualmente para adicionar outros sistemas de arquivos do sistema.
O problema do mount é ele perde a montagem quando desligamos ou reiniciamos a máquina.<br>

Sintaxe:

<b> mount opções dispositivo diretório </b>

Opções de linha de comando:<br>
-a : monta todas as partições especificadas em /etc/fstab, exceto aquelas com a opção noauto.<br>
-r : monta o sistema de arquivos como somente leitura. <br>
-v : define o modo verbose. <br>
-w : monta o sistema de arquivos no modo escrita.
 
![image](https://user-images.githubusercontent.com/89140035/194965213-a55f4a76-9a9a-4799-a973-7419c3e5b4e7.png)

* Desmontando sistema de arquivos

Uma vez montado um sistema de arquivos, ele pode ser desmontado, liberando assim seu diretório ou dispositivo. Para descontar é utilizado o comando <b> umont. </b>

Sintaxe:

<b> umont opções dispositivo diretório </b>

Opções:<br>
-a : desmonta todos os sistemas de arquivos descritos em /etc/fstab. Este dispositivo é mantido pelos comandos mount e umount e contêm uma lista atualizada de sistemas montados.<br>
-t fstype : desmonta apenas sistemas de arquivos do tipo fstype.

Exemplo:<br>
Desmontar o CD-ROM /dev/hdc montado em /mnt/cdrom:

<b> umount/mnt/cdrom </b>

Desmontar todos os sistemas de arquivos NFS:

<b> umount -at nfs </b>


### Monitorando e Consertando Sistemas de Arquivos 🛠️

* Monitorar o espaço livre em disco

Um sistema de arquivos de leitura/escrita não é muito útil se ele crescer até o ponto em que não aceite mais arquivos novos.<br>
Isso poderia acontecer se o sistema de arquivos tiver a sua capacidade totalmente preenchida. <br>
O comando <b>df</b> lhe fornece as informações de que precisa sobre o status tanto da utilização do espaço em disco como também sua vida útil.<br>

<b>df</b>

Sintaxe: df opções

Exibe informações gerais sobre a utilização do disco para sistemas de arquivos montados em arquivos.<br>
Em geral, arquivo é um arquivo de dispositivo para uma partição, como /dev/hda1.<br>
As informações para sistemas montados em todos os dispositivos ficam em <b>/etc/fstab.</b><br>

Opções:

-h : Exibe os resultados em um formato legível, incluindo sufixos momo M (megabytes) e G (gigabytes).<br>
-i : Exibe informações sobre os <b>inodes</b> restantes, em vez de as informações padrão sobre o espaço em disco.

Para cada arquivo existe um <b>inode</b>, que armazena informações sobre o arquivo relacionado. Essas informações, também conhecidas como Metadados, são importantes para administração do arquivo. O inode guarda informações como permissões, tempo, grupo e proprietário do arquivo.

![image](https://user-images.githubusercontent.com/89140035/195164176-67b6a254-388c-45cd-8476-fb005fdca262.png)

<b> du </b>

O comando du exibe informações de utilização de disco para diretórios. Se diretórios forem omitidos, a busca é feita no diretório de trabalho atual.

Sintaxe:<br>
du opções diretórios

Opções:<br>
-a : mostra todos os arquivos, e não apenas diretórios.<br>
-h : exibe resultados em um formato legível, incluindo sufixos como M (megabytes) e G (gigabytes).<br>
-s : exibe um resumo para cada um dos diretórios especificados, em vez de totais para cada subdiretório encontrado recursivamente.<br>
-S : exclui subdiretórios de contagens e de totais, limitando os totais aos diretórios. <br>
-c : somatória geral de todos os ítens. <br>

![image](https://user-images.githubusercontent.com/89140035/195198710-90a40dd9-c77e-4a3e-95cc-2ac52fb35d28.png)

![image](https://user-images.githubusercontent.com/89140035/195199501-c5d26261-6b1f-473e-aa32-b53f991bdba6.png)


Exemplo:

Examinar a utilização de disco em /etc, incluindo os subdiretórios dentro dele.<br>

![image](https://user-images.githubusercontent.com/89140035/195175188-0fd03a20-b751-4c22-9054-b22679ce6764.png)

Exibir um resumo de todos os subdiretórios de /home, com uma saída legível:

![image](https://user-images.githubusercontent.com/89140035/195175490-4a09caaf-e80b-4f12-bedf-a72e83245aba.png)

Computadores eventualmente podem falhar, mesmo por uma parada de energia ou até mesmo uma arquivo malicioso.<br>
Se uma operação de escrita em disco for abortada antes de se completar, os dados em trânsito poderão se perder e as partes do disco que haviam sido alocadas para eles serão marcadas como utilizadas.<br>
Ambos os cenários levam a inconsistências no sistema de arquivos e precisam ser corrigidos para se garantir uma operação confiável.<br>
Os sistemas de arquivos são verificados com o <b>fsck.</b><br>

<b> fsck </b>

Sintaxe:<br>
fsck opções tipo_sistema_aquivo

O fsck verifica se há erros nos sistemas de arquivos e, opcionalmente, os corrige.<br>
Por padrão, fsck assume que o tipo do sistema é o ext e roda interativamente, pausando para lhe pedir permissão antes de aplicar quaisquer reparos.

Opções:

-A : roda verificações em todos os sistemas de arquivos especificados em /etc/fstab. Esta opção é para uso no momento do boot, antes de os sistemas de arquivos serem montados.<br>
-N : não executa, mas mostra o que seria feito, quais arquivos e partições que seriam corrigidos.<br>
-t tipo : especifica o tipo de sistema de arquivos a ser verificado; o padrão é o ext. O valor de tipo determina qual verificador, de qual sistema de arquivos será chamado.<br>
-c : verifica se há bad blocks.<br>
-f : força uma verificação, mesmo que o sistema de arquivos pareça ok. <br>
-p : repara automaticamente o sistema de arquivos, sem pedir confirmação ao usuário. <br>
-y : responde "yes" a todos os prompts interativos.

<img width="452" alt="image" src="https://user-images.githubusercontent.com/89140035/195200420-96ca99d0-181c-40cd-8640-0b1617a5036a.png">


### Permissões de Arquivos ❗

* Gerenciar a prioridade e as permissões dos arquivos

A segurança do sistema de arquivos é um requerimento fundamental para qualquer sistema operacional multiusuários.<br>
Arquivos de sistema, kernel, arquivos de configuração e os programas precisam ser protegidos contra acidentes e contra a manipulação feita por pessoas não autorizadas.<br>
Os arquivos dos usuários precisam ser protegidos contra modificações feitas por pessoas sem autorização e em alguns casos precisam ser mantidos completamente privados.<br>
Em geral, é preciso implementar alguma forma de controle de acesso para se permitir as operações seguras. <br>

* Controle de Acesso Linux

O controle de acesso ao sistema de arquivos do Linux é implementado usando um conjunto de propriedades mantidas separadamente para cada arquivo. <br>
Essas propriedades são chamadas de modo de acesso de um arquivo. <br>
O controle de acesso é dividido em três categorias:

<b> Usuários (User)</b> : o usuário que é o proprietário do arquivo. <br>
<b> Grupo (Group) </b> : o grupo que é o proprietário do arquivo. <br>
<b> Outros (Other) </b> : todos os outros usuários do sistema. <br>

As definições de propriedade do usuário e do grupo fazem parte do inode e ambas são atribuídas quando um arquivo é criado.<br>
Geralmente, o proprietário é o usuário que criou o arquivo.<br>
O grupo do arquivo normalmente é definido como o grupo padrão do seu criador. <br>
Os "outros" usuários são aqueles que não são membros do grupo do arquivo e também não são o seu proprietário. <br>
Para cada uma dessas três categorias, são definidas três tipos de permissões, que se aplicam diferentemente para arquivos e diretórios.<br>

![image](https://user-images.githubusercontent.com/89140035/195203337-bcf9eafc-5be5-4d5c-a766-8d3c1c78fe86.png)

Essas três permissões se aplicam às três classes diferentes: usuário, grupo e outros. Sendo que pode haver duas formas:<br>
0 : não permite
1 : permite

![image](https://user-images.githubusercontent.com/89140035/195204546-303acb00-e596-4700-8d24-bc3f4e34de4f.png)

Quando exibidas por comandos como ls -l, as permissões usam as abreviaturas. <br>
Para representar apenas a permissão de leitura, por exemplo, seria usado <b> r-- </b><br>
Leitura e gravação juntas, seriam indicadas com <b> rw-- </b> <br>
Essas notações normalmente são apresentadas em conjuntos de três, como por exemplo: <b> rw-rw-r-- </b>

![image](https://user-images.githubusercontent.com/89140035/195205110-2068cc9e-bc63-49ad-a55d-65503e9bc594.png)

O traço separa as classes, logo a seguinta notação: <br>
rw-rw-r--<br>
rw : user --> poderá ler e escrever <br>
rw : grupo --> poderá ler e escrever <br>
r : outros --> poderá apenas ler

* Os bits para permissão

As permissões de arquivos e diretórios podem ser representadas em uma string de 9 bits. <br>
É comum referir-se a esses bits em três conjuntos de três, traduzidos para três dígitos octais (base-8). <br>
Os dígitos octais representam as permissões de leitura, escrita e execução.

![image](https://user-images.githubusercontent.com/89140035/195206689-aeee2d77-cd20-41aa-a8e1-b22758d70b50.png)

A permissão de leitura sozinha é r--, que pode ser entendida como um 100 binário ou 4 octal.<br>
Adicionando-se a permissão de escrita, tem-se rw- ou 110 binário, que equivale a 6 octal.

![image](https://user-images.githubusercontent.com/89140035/195207097-595171ed-2387-4e05-9289-45bef221d417.png)

Para transformar os bits de modo <b>111101001</b> em uma representação octal, primeiramente separa-se em pedaçõs com três bits cada um:<br>

111 , 101 e 001 <br>

O primeiro grupo, representando as permissões do usuário é o 111, ou 4 + 2 + 1 = 7. <br>
O segundo grupo, representando as permissões do grupo, é o 101, ou 4 + 0 + 1 = 5. <br>
O último grupo, representando as outras permissões, é o 001, ou 0 + 0 + 1 = 1. <br>

A string de modo para este exemplo pode, então, ser escrita como o número <b> octal 751. </b> <br>
Este formato é usado para se exibir o modo do arquivo na saída do comando <b> stat. </b>

![image](https://user-images.githubusercontent.com/89140035/195209949-337465a4-4beb-4529-8ab1-202ca8213b00.png)

644 é o valor em octal: usuário dono do arquivo pode ler, escrever, mas não pode executar, o grupo desse usuário só pode ler, e os outros usuários também só podem ler.

* Modificando modos de acesso

Os modos de acesso podem ser modificados com o comando <b>chmod</b>, o qual aceita especificações de modo de acesso octais ou simbólicos. <br>
As especificações de modo simbólico possuem três partes, compostas de caracteres individuais. <br>

![image](https://user-images.githubusercontent.com/89140035/195211126-f02e1abe-6b92-4a66-b21a-5f76f8037b99.png)

Os caracteres que representam a classe individual do usuário e os que representam as permissões podeer ser agrupados para se formarem expressões compostas. <br>
Exemplo, ug para usuário e grupo combinados, ou rw para leitura e escrita. <br>

<b> u+x </b> : adiciona a permissão de execução para o usuário. <br>
<b> go-w </b> : remove a permissão de escrita das classes grupo e outros. <br>
<b> a=rw </b> : define as permissões de leitura e escrita, mas não de execução, para todos.<br>
<b> a+x </b> : concede a todos a permissão de execução para diretórios e para os arquivos que já tenham alguma permissão de execução.
