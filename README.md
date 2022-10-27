Fonte Principal: Curso Linux Completo + Servidores <br>
Udemy: https://www.udemy.com/course/linux-completo-servidores/

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

<b> chmod </b>

O comando chmod modifica o modo de acesso para arquivos.<br>
Na primeira forma, usa uma ou mais especificações de modo simbólico, separadas por vírgula, para modificar os arquivos. <br>
Na segunda forma, usa um modo octal para modificar os arquivos.<br>

Sintaxe:<br>
chmod opções modo_simbólico arquivos <br>
chmod opções modo_octal arquivos <br>

Opções: <br>
-R : usa o modo recursivo, repassando as hierarquias de diretórios abaixo dos arquivos e fazendo modificações em todo o percurso. <br>
-v : usa o comportamento verbose, relatando todas as ações para todos os arquivos.

Exemplo:

Definir o modo de um arquivo como rw-r-r--, usando especificações octal:<br>
chmod 644 arquivo

Exemplo:

Definir a mesma permissão, usando-se especificação simbólica, com a opção verbose:<br>
chmod -v u=rw, go=r arquivo

Exemplo:

Remover recursivamente todas as permissões para os outros em um diretório:<br>
chmod -R -v o-rwx diretório

<b> chown </b>

O comando chown é usado para modificar o proprietário e/ou grupo de arquivos.

Sintaxe: <br>
chown opções usuário-proprietário *arquivos* <br>
chown opções usuário-proprietário.grupo-proprietário *arquivos* <br>
chown opções grupo-proprietário *arquivos* <br>

Na primeira forma, definimos o usuário proprietário. <br>
Na segunda forma, definimos o usuário proprietário e o grupo proprietário. <br>
Na terceira forma, definimos o grupo proprietário. 

Opções: <br>
-R : usa o modo recursivo, descendendo através dos diretórios e fazendo alterações. <br>
-v : usa o comportamento verbose, relatando ações para todos os arquivos.

Exemplo:

Define o usuário proprietário de um arquivo: <br>
chown -v eduardo *arquivo* <br>

Define o usuário e o grupo proprietário de um arquivo: <br>
chown -v eduardo.grupo *arquivo* <br>

![image](https://user-images.githubusercontent.com/89140035/195216646-876f5912-6473-4c4e-b38f-ee4e12eab26b.png)

![image](https://user-images.githubusercontent.com/89140035/195216903-5910951c-428e-448c-8e4b-e53914b43ef6.png)

![image](https://user-images.githubusercontent.com/89140035/195216985-82eadf7f-f201-4676-86ed-f04e29dc93d1.png)

OBS: Não é possível liberar a permissão de escrita se não for concedida a permissão de leitura.

![image](https://user-images.githubusercontent.com/89140035/195217828-853c75f2-5795-42a6-88e8-ea881e4f1d7f.png)

![image](https://user-images.githubusercontent.com/89140035/195218069-630f5d17-f95f-47ee-a8ca-0b03c7b3198d.png)

![image](https://user-images.githubusercontent.com/89140035/195218498-f6f69521-0bad-48b9-947e-7202755884a0.png)

OBS.: O usuário root, independente da permissão que você defina, ele será capaz de fazer qualquer alteração em todos os usuários e arquivos da máquina.

### Redes Linux ➡️

* Entendendo a Placa de Rede Virtualizada

Modos: Bridge, NAT e Interna <br>

Bridge: divisão da placa de rede da máquina real para as máquinas virtuais (compartilhada fisicamente), a máquina virtualizada vai poder se comunicar com o roteador, switch e outros equipamentos na rede. Elá receberá um IP da rede. <br>

NAT: a maquina real fará um reteamento para a máquina virtual, sem compartilhar a mesma placa de rede. O compartilhamento o processamento e armazenamento. O equipamento virtualizado solicita o pacote para o equipamento real, e este então se encarrega de solicitá-lo e depois mandar para a máquina virtual. A máquina virtual receberá um endereço de IP secundário. <br>

Modo Interno: As máquinas virtuais não possuem nenhum tipo de acesso externo. Só são capazes de se comunicar entre si (entre máquinas virtuais). <br>

Quando se trata de ambientes de servidores Linux, independente da distribuição escolhida, normalmente você vai se deparar apenas com a <b> interface modo texto </b>, o que nos faz realizar as configurações de rede manualmente, escrevendo as configurações em um arquivo. <br>
No Linux, nas maiorias das distribuições, o arquivo de configuração de redes é o arquivo <b> interfaces. </b> Localizado dentro de <b> /etc/network. </b> <br>
Antes de começar a explorar esse arquivo, também é importante compreender como o Linux chama suas <b> interfaces de rede. </b> <br>
Para sistemas que possuam a interface gráfica instalada, utilizamos o <b> Network Manager. </b> <br>
Antigamente se tratando de interface de rede cabeada, o Linux chamava suas interfaces de <b> eth0, eth1, eth2. </b> <br>
Se tratando da interface de rede wireless, o Linux chamava suas interfaces pelo nome de <b> wlan0 </b> e as próximas seguem o mesmo padrão. <br>
É importante salientar que esse padrão não é REGRA, pois ele pode ser alterado em algumas distribuições Linux. <br>

* Nova Nomenclatura de Onterfaces no Linux

As principais distribuições Linux estão adotando o padrão <b> systemd </b>, onde ocorre algumas padronizações em relaçãoas configurações do sistema, uma delas é justamente a padronização dos comandos e interfaces de rede. <br>
A partir da versão Debian 8 (Jessie) passou a ser utilizado o padrão, portanto a não ser que você instale o aplicativo <b> net-tools </b>, seus padrões de rede serão os padrões novos. <br>
A partir da versão <b> v197 do systemd </b>, o Linux passou a utlizar um novo mecanismo para nomenclatura das interfaces de redes, denominado <b> Predictable Network Interface Names </b>. O objetivo da nova nomenclatura foi solucionar problemas reais decorrentes da generalização dos nomes tradicionais que utilizavam o formato ethX (ethernet), wlanX (wireless), etc. <br>
O problema da nomenclatura tradicional é que as interfaces de mesma natureza recebem seus nomes do kernel de maneira sequencial (no formato eth0, eth1, eth2, etc...) assim que elas são consultadas pelo driver. <br>
Ocorre que o mecanismo de comunicação entre o driver e a interface não é previsível, o que implica na possibilidade de alteração nos nomes das interfaces durante o processo de boot de máquinas que tenham múltiplas interfaces de rede em caso de atualização de hardware. <br>
Essa situação traz riscos de segurança em ambientes que tenham configurações e scripts de firewall que foram baseados nos nomes tradicionais. <br>
O novo mecanismo de nomenclatura traz suporte nativo a diferentes políticas para nomeação das interfaces de rede, a destacatar: <br>
1. Nomes Indexados via Firmware/BIOS On-Board
2. Nomes Indexados via Firmware/BIOS PCI Express
3. Nomes Indexados via Localização Física do Hardware
4. Nomes Indexados via Endereço Físico (MAC)
5. Nomes Clássicos Nativos do Kernel (Imprevisíveis) <br> <br>


Todas essas políticas são utilizadas em conjunto, de forma que a primeira política será adotada caso as informações do firmware on-board estejam disponíveis, seguida pela segunda política caso as informações do firmware PCI estejam disponíveis, seguida pela terceira política e assim por diante. <br>
Por exemplo, possíveis nomes de interfaces baseados na primeira, segunda, terceira, quarta e quinta políticas, respectivamente, seriam: <b> eno1, ens1, enp2s0, enx78e7d1ea46da e eth0. </b> <br>
Apesar das políticas padrões, as configurações realizadas pelo administrador sempre tem precedência.

* Comandos de Redes

Os primeiros comandos de redes são para verificação e controle da interface.

<b> ip a </b>

O comando irá trazer todas as interfaces de rede configuradas como também os endereços IPv4 e IPv6, os endereços MAC, entre outras opções.

![image](https://user-images.githubusercontent.com/89140035/195946636-a982c994-5f5b-4a72-9850-74ebaabc4396.png)

Caso você queira ainda uma visão mais limpa, você pode selecionar apenas os endereços IPv4 ou o IPv6, com os comandos: <b> ip -4 a e ip -6 a </b>
 
![image](https://user-images.githubusercontent.com/89140035/195946953-b8cc1a61-2526-4e99-92a3-9fbf59d23650.png)

![image](https://user-images.githubusercontent.com/89140035/195947004-01d819ca-4662-4e09-8149-29596e46ccdb.png)

<b> ip r </b>
 
Esse comando mostrará o Gateway padrão.

![image](https://user-images.githubusercontent.com/89140035/195947291-c6d15722-f917-474b-a977-68adf5e1ee49.png)

<b> ip -s link </b>

Esse comando irá checar o tráfego da placa de rede

![image](https://user-images.githubusercontent.com/89140035/195947495-bb220865-bd7a-4cc2-b402-cccf56b2b66f.png)

Também podemos ativar ou desativar uma determinada interface de rede (placa de rede), utilizando os comandos <b> ifup e ifdown </b>. <br>

<b> ifdown enp0s3 </b> : Parar a placa de rede

<b> ifup enp0s3 </b> : Ativar a placa de rede

![image](https://user-images.githubusercontent.com/89140035/195948013-964f61cf-d24a-439f-af24-0c23f2226247.png)

* Achar a interface da placa de rede

Comando <b> dmesg | grep -i network </b>

![image](https://user-images.githubusercontent.com/89140035/195948389-c60d7f4f-3cb0-4f31-9972-84229f022695.png)

![image](https://user-images.githubusercontent.com/89140035/195948623-ec9b219b-1708-4d7e-a1fc-3a2245624942.png)

![image](https://user-images.githubusercontent.com/89140035/195948874-61b29aad-94dd-425a-bc89-c80ca04cb6ac.png)

* Configuração da Interface de Rede

Existem duas maneiras da interface de rede adquirir um endereço IP, ou você tem na sua rede um serviço habilitado de <b> DHCP (Dynamic Host Configuration Protocol) </b> ou então você irá ter que <b> configurar manualmente </b> a sua interface de rede.

O arquivo de configuração de rede se localiza dentro do diretório <b> /etc/network. </b>. O arquivo se chama <b> interfaces. </b>

Fazendo a leitura do arquivo interfaces, observamos a seguinte configuração por default:

![image](https://user-images.githubusercontent.com/89140035/195990356-b5f3d9cb-99eb-49dc-91c9-922458837296.png)

Note que no nosso exemplo são apresentados duas interfaces, a interface do <b> lo </b> e a interface de rede <b> enp0s3 </b>.

OBS.: A interface de lo ou também chamada de Loopback refere-se ao roteamento de sinais eletrônicos, fluxo de dados digitais ou fluxos de itens que retornam para suas origens sem processamento ou modificação intercional.

O loopback pode ser um canal de comunicação com apenas um ponto final de comunicação, de forma que qualquer mensagem transmitida por meio de tal canal é imediatamente recebida pelo mesmo canal.

Em telecomunicações, dispositivos de loopback realizam teste de transmissão.

No arquivo de configuração a respeito da interface enp0s3, encontramos as seguintes linhas:

<b> allow-hotplug enp0s3 <br>
iface enp0s3 inet dhcp </b>

E isto nos diz muitas coisas, como por exemplo:

<b> allow-hotplug - </b> : ativa a placa de rede na inicialização. <br>
<b> enp0s3 - </b> : nome da interface de rede adicionado automaticamente utilizando o sistema de nomenclatura. <br>
<b> iface - </b> : interdace de rede. <br>
<b> inet dhcp - </b> : está especificando que o endereço (inet) será atribuído via DHCP.

Esse resumo, essas configurações dizem que a interface será iniciada junto com o sistema e terá a sua configuração através do <b> protocolo DHCP </b>.

Agora vamos configurar a interface manualmente. Devemos abrir o arquivo interface e adicionar os seguintes itens:

auto enp0s3 : inciar a placa de rede junto ao sistema <br>
iface enp0s3 inet static : especificando que o endereço para enp0s3 será manual <br>
address 192.168.1.100 : endereço IP <br>
netmask 255.255.255.0 : máscara de sub rede <br>
network 192.168.1.0 : endereço de rede <br>
broadcast 192.168.1.255 : endereço de broadcast <br>
gateway 192.168.1.1 : endereço do gateway <br>

![image](https://user-images.githubusercontent.com/89140035/195991947-25c49676-d369-4072-8f5e-c865f8f82a9b.png)

Ao término para carregar as novas configurações, entre com o comando para reiniciar o serviço de rede:

<b> service networking restart </b> 

* Comandos de Redes

Outro comando muito importante é o ping, que serve para verificar se um dispositivo na rede responde a uma solicitação, isso mostra que o dispositivo está ativo na rede.

Sintaxe:

<b> ping endereço_ip </b>

![image](https://user-images.githubusercontent.com/89140035/196006229-beacdfef-d333-4b29-bea8-9c5b2ba8bc4b.png)

Também podemos verificar o <b> DNS </b> consultado o arquivo <b> resolv.conf </b> localizado dentro do <b> /etc </b>

![image](https://user-images.githubusercontent.com/89140035/196004501-963399c6-faf7-44e7-9010-cb80ba914030.png)

Você pode alterar ou acrescentar novos servidores DNS inserindo a linha <b> "nameserver" </b> mais o endereço IP.

Aproveintado o DNS, vamos falar agora sobre o arquivo <b> hostname </b>, esse que serve para consultar ou definir o nome do equipamento.

![image](https://user-images.githubusercontent.com/89140035/196004595-977a1354-c7f8-430c-8771-d98b950e891b.png)

O arquivo <b> hostname </b> fica localizado dentro do diretório <b> /etc </b>, você pode editar o arquivo afim de trocar o nome da estação.

Também podemos consultar o IP de determinados sites consultando o nosso DNS utilizando o <b> nslookup </b>

![image](https://user-images.githubusercontent.com/89140035/196006037-824cc7b1-22ba-4f74-a55c-285495478b63.png)

OBS.: O NSLOOKUP faz parte do pacote do <b> dnsutils, </b> que deve ser instalado no sistema.

<b> traceroute ip ou domínio </b>

Com traceroute podemos ver em tempo real todo o caminho que um pacote percorre até chegar ao seu destino.

![image](https://user-images.githubusercontent.com/89140035/196293244-1f5833c2-19b7-47df-a1de-99f357ca6f79.png)

<b> ss </b>

O comando ss serve para vocÊ verificar quais portas de rede estão abertas em seu Linux.

Opções: <br>
-r : resolve nomes dos hosts conectados a maquina <br>
-t : mostrar portas tcp <br>
-u : mostrar portas udp <br>
-l : mostrar portas que estão em escuta (prontas para aceitar conexões) <br>
-p : mostrar os processos que estão usando as portas <br>
-n : não resolve os nomes dos serviços (apresenta o serviço Linux e o ID) <br>
-4 : somente IPv4 <br>
-6 : somente IPv6 <br>

Exemplo: ss -tulpn

### Prática Redes Linux 🧑‍🚀

![image](https://user-images.githubusercontent.com/89140035/196009431-6547a9fe-7f8b-4f1d-99fe-edc85330cb4d.png)

OBJETIVO: <br>
1 - Definir a configuração das placas de rede das duas máquinas virtualizadas em modo interno. <br>
2 - Fazer as duas máquinas se comunicarem na rede classe A. <br>
3 - Fazer o teste de conexão entre as duas máquinas. <br>
4 - Responder a pergunta: As máquinas tem acesso a internet?

Primeira deixar as duas máquinas IP fixo através da edição do arquivos interfaces na pasta /etc/network.

![image](https://user-images.githubusercontent.com/89140035/196009548-7d5df001-461d-47b3-bf7f-e29ce985d656.png)

Verificando os números de IP das máquinas pelo comando "ip -4 a" após o comando "service networking restart"

![image](https://user-images.githubusercontent.com/89140035/196009597-f1e2eef0-ec2b-4e05-ba1a-dd195edac9ff.png)

Teste de ping da máquina 1 para a 2 e a máquina 2 para a 1

![image](https://user-images.githubusercontent.com/89140035/196009726-564ecc3f-18d6-4595-9c8a-fd2a256e9a48.png)

Como as duas máquinas estão especificadas em modo interno e também não houve configuração de gateway padrão não é possível pingar a um site externo.

Agora vamos adicionar outra interface na Máquina 1, fazendo a seguinte topologia:

![image](https://user-images.githubusercontent.com/89140035/196010168-30d2b763-084a-4ff7-985f-657176dc94d1.png)

Desta forma ficaremos com 3 interfaces

![image](https://user-images.githubusercontent.com/89140035/196010312-6b01c227-8d66-4be5-a124-64876f750f6a.png)

Por que a terceira interface não pegou IP mesmo colocando em modo bridge? No arquivo de interfaces não existe a configuração para a nova interface.

![image](https://user-images.githubusercontent.com/89140035/196010479-d8953db6-08f7-4801-88c3-570c210a63a7.png)

Com a configuração da terceira interface, vamos conferir se agora existe numero de IP

![image](https://user-images.githubusercontent.com/89140035/196010656-888ec9da-0c67-4e3e-9025-2923bf9b9d23.png)

Agora a maquina 1 consegue estabelecer conexão com a internet

![image](https://user-images.githubusercontent.com/89140035/196010714-1b56beaf-010c-4635-a11c-284e20388342.png)

### Servidor de Arquivos (SAMBA) 👋

Um <b> servidor de arquivos </b> é um computador conectado a uma rede que tem o objetivo principal de proporcionar um local para o armazenamento compartilhado de arquivos de computadores (como documentos, arquivos de som, fotografias, filmes, imagens, bases de dados, etc) <br>
No Linux, o servidro de arquivos é o Samba, um conjunto de programas de interoperabilidade padrão do Windows para Linux e Unix. <br>
O Samba é um Software Livre licenciado sob a GNU General Public License, o projeto Samba é um mombro da Software Freedom Conservancy. <br>
Desde 1992, o Samba fornece serviços de arquivos para todos os clientes que usam o protocolo <b> SMB (server Messege Block) / CIFS (Common Internet File System), </b> como todas as versões do DOS e Windows, OS/2, Linux e muitos outros. <br>
O Samba é um componente importante para integrar perfeitamente servidores e desktops Linux/Unix em ambientes do <b> Active Diretory </b>. Ele pode funcionar como um controlador de domínimio ou como um membro regular de domínio. <br>

* Quais são as vantagens de um servidor de arquivos? 

1 - Backup <br>
2 - Centralização da Infomação e Disponibilidade <br>
3 - Confidencialidade e Integridade da Informação <br><br>

O Linux tem a capacidade de agir como um servidor de arquivos. Para essa tarefa vamos utilizar os serviços do SAMBA que é um conjuntos de serviços que permite que máquinas Linux e Windows se comuniquem, compartilhando serviços de arquivos. 

Características:

1 - Compartilhamento de arquivos entre máquinas Linux e Windows. <br>
2 - Controle de acesso leitura/gravação por compartilhamento ou por usuário autenticado. <br>
3 - Possibilidade de definir compartilhamento público. <br>
4 - Permite ocultar o conteúdo de determinados diretórios que não quer que sejam exibidos na rede. <br>
5 - Permite montar unidades mapeadas de sistemas Windows ou outros servidores Linux como um diretório. <br>
6 - Permite a configuração de recursos simples atrvés de programas de configuração gráficos via web.

* <b> Instalação </b>

A instalação pode ser feita através do gerenciador de pacotes apt-get. Entre com o comando: <br>
<b> apt-get install samba smbclient cifs-utils </b> <br>

O pacote samba é o servidor samba e os pacotes smbclient e cifs-utils fazem parte dos aplicativos cliente.

Após a instalação, execute o comando: <br>
<b> service --status-all </b> <br>

![image](https://user-images.githubusercontent.com/89140035/196261662-20254d8b-27e0-4ce3-8313-27592b56d850.png)

Observe que o serviço do Samba estará aparecendo e com o sinal de + na frente, indicando que está ativo.

Pode se controlar o serviço com os comandos: <br>

* <b> service smbd status </b> <br>
* <b> service smbd start </b> <br>
* <b> service smbd stop </b> <br>
* <b> service smbd restart </b> <br> 

Toda a configuração do Samba, incluindo as configurações gerais do servidor, impressoras e todos os compartilhamentos, é feita em um único arquivo de configuração, o /etc/samba/smb.conf

![image](https://user-images.githubusercontent.com/89140035/196262169-9c570e27-04a4-49f6-98de-8bc7eeade8b0.png)

Por padrão, o arquivo <b> smb.conf </b> já vem com informações escritas e é possível ser personalizado, afim de estudos, renomeie o arquivo <b> smb.conf </b> para <b> smb.conf.original </b> dessa forma se você precisar para consulta de alguma informação do arquivo original ele ainda estará disponível. <br>
Crie um novo arquivo chamado <b> smb.conf </b> dentro do diretório <b> /etc/samba </b>.

![image](https://user-images.githubusercontent.com/89140035/196269893-152a1c55-b78c-45f9-86eb-34b8ef1b1473.png)

![image](https://user-images.githubusercontent.com/89140035/196270030-91695861-d88c-4c10-bbb6-82808355a3ec.png)



Com o arquivo <b> smb.conf </b> aberto, vamos adicionar as seguintes linhas, esse exemplo básico, cria um compartilhamento básico e público (sem autenticação nenhuma).

![image](https://user-images.githubusercontent.com/89140035/196264222-fa644186-7394-4776-bcd2-ddc13c0771b0.png)

O parâmetro <b> map to guest </b> mapeia usuários mal autenticados (sem autenticação) para a conta de convidado, portanto, basta adicionar o parâmetro <b> guest ok=yes </b> na sessão de compartilhamento. <br>
No nosso exemplo <b> [dados] </b>. Essa situação, cria um compartilhamento público chamado dados, sem a necessidade de autenticação. <br>

Os outros parâmetros no compartilhamento são: <br>
<b> Path </b> : é o parâmetro que indica o caminho do diretório a ser compartilhado. <br>
<b> Available </b> : é o parâmentro que indica se o compartilhamento está habilitado ou não. <br>
<b> Writable </b> : é o parâmetro que indica se o compartilhamento está com permissão de escrita. Aqui cabe uma observação, pois indicando <b> YES </b> o compartilhamento aceita gravação, colocando <b> NO </b> ele passa ser somente leitura, no caso de somente leitura, pode-se substituir pela opção <b> read only=yes. </b> <br>
<b> Browseable </b> : é o parâmentro que indica se o compartilhamento vai estar visível ou oculto para a sua rede. (OBS: Não use como quesito de segurança a ocultação de compartilhamento de rede, segurança por obscuridade não é totalmente eficaz.)

![image](https://user-images.githubusercontent.com/89140035/196268827-ad20f7fa-907d-4793-9c9c-b5e5200bdb0d.png)

_________________________________________________________________________________________________________________________________________________________
Criado o arquivo entramos com as seguintes instruções:

![image](https://user-images.githubusercontent.com/89140035/196271430-2c607665-ca4c-4fe7-a737-e0a9dea8be1c.png)

Criar o diretório dados na raiz /

![image](https://user-images.githubusercontent.com/89140035/196271987-b72f410c-ace0-4635-b573-62abe0650a3d.png)

É preciso dar permissão para o arquivo:

![image](https://user-images.githubusercontent.com/89140035/196272464-0990d81c-5ee9-4918-9662-dcb5b9a373a5.png)

Reinicinando e Confirmando o Status do Serviço:

![image](https://user-images.githubusercontent.com/89140035/196272800-e08aaa36-b913-41d8-9e18-837f8bc0af27.png)

Agora basta acessar a pasta "Dados" através da rede no Windows:

![image](https://user-images.githubusercontent.com/89140035/196279014-c571d8a8-4d30-467b-b395-3fb1da238271.png)

Mudando as configurações de permissões:

![image](https://user-images.githubusercontent.com/89140035/196280131-46cadc68-e185-464c-b915-51515c63343d.png)

Veja acima que com a nova opção o usuário verá a pasta vazia. No entanto, se o usuário souber o nome do compartilhamento e dar um "enter", ele terá acesso normalmente:

<b> \\192.168.0.20\dados </b>

Mundando agora o "writeable":

![image](https://user-images.githubusercontent.com/89140035/196281335-79a6e0e6-73b8-4c02-a232-b4e36582b6f0.png)

Veja que agora é possível visualizar a pasta, mas ao tentar criar, excluir qualquer arquivo dentro do diretório a permissão é negada.

OBS.: As últimas atualizações do Win10 estão impedindo que você acesso compartilhamento públicos (aqueles que não solicitem tanto o usuário quanto a senha), então é preciso desativar isso.

Para isso é preciso entrarmos no "Editor de Política de Grupo Local" ou Executar -> gpedit.msc <br>
Caso você esteja com a versão do Win10 Home, ele não é nativo, para instalar é preciso seguir os seguintes passos: <br>
1 - Em "Ativar ou Desativar Recursos do Windows" no Painel de Controle --> Desinstalar ou Alterar um Programa; <br>
2 - Selecione a Opção "Suporte para Compartilhamento de Arquivos SMB 1.0/CIFS" <br>
3 - Selecione a Opção ".NET Framework 3.5 (inclui .NET 2.0 e 3.0)", ao cliquer em OK, o sistema instalará automaticamente; <br>
4 - Entre no modo administrador do CMD e esvreva os comandos:<br>

<b> FOR %F IN ("%SystemRoot%\servicing\Packages\Microsoft-Windows-GroupPolicy-ClientTools-Package~*.mum") DO (DISM /Online /NoRestart /Add-Package:"%F") <br> <br>
FOR %F IN ("%SystemRoot%\servicing\Packages\Microsoft-Windows-GroupPolicy-ClientExtensions-Package~*.mum") DO (DISM /Online /NoRestart /Add-Package:"%F") </b> <br>

Com  isso você instalará o GPEDIT.MSC. Agora siga o caminho: <br>
Configuração do Computador --> Modelos Administrativos --> Rede --> Estação de Trabalho do LANMAN --> Habilitar logons de convidados não seguros <br>
Mude-o para "Habilitado"

Vamos agora criar mais um compartilhamento que solicite autenticação de usuário e senha. Vamos criar um compartilhamento chamado <b> TI </b>. <br>
Para isso, crie o diretório em sua disco chamado TI e de a permissão no <b> chmod </b>, para os teste vamos definir 777. Logo após abra o arquivo <b> smb.conf </b> e adicione os itens:

![image](https://user-images.githubusercontent.com/89140035/196292533-e37d5270-291d-43d2-b9bc-e04f3eb7f649.png)

Aqui, você pode observar que o compartilhamento <b> [TI] </b> foi criado e também foi apresentado o parâmetro <b> valid users </b>. <br>
Com isso ao tentar acessar o compartilhamento TI será solicitado um usuário e senha.

![image](https://user-images.githubusercontent.com/89140035/196293037-dda412e0-0de5-4e5b-a08a-1e472b1e5548.png)

* Criando os Usuários João e Maria

No Samba é preciso criar o usuário localmente no Linux, e para ele é preciso dar permissão para que ele possa acessar os compartilhamentos pela rede - permissão do smbd.

![image](https://user-images.githubusercontent.com/89140035/196294472-8393c218-cc4a-40c5-8951-234a313c82b9.png)

Adicionar permissões administrativas para acessar o compartilhamento:

![image](https://user-images.githubusercontent.com/89140035/196294764-962afcb8-794e-45d1-bdc3-0723d45eaccc.png)

Veja que é possível dar acesso de senha para o usário do sistema e outra senha apenas para acesso ao diretório SMB.

Agora é possível usar as credenciais do João para acesso a pasta TI, inclusive adicionar e remover arquivos.

* Criação de diretório com permissão de escrita para alguns usuários e somente leitura para outros usuários

![image](https://user-images.githubusercontent.com/89140035/196295799-27948a5d-b990-411e-80cd-b9533f307608.png)

Agora temos como opção de somente leitura o usuário João, e com permissão de escrita a usuária Maria.

Quando um usuário apaga um arquivo pela rede, este arquivo só não é deletado do compartilhamento, mas também do servidor. Não existe uma "lixeira" para arquivos apagados pelos compartilhamentos, o sistema operacional não faz esse tipo de gravação. Pensando nisso, o samba também tem a possibilidade de criação de uma lixeira para os arquivos e diretórios.

* <b> Criando uma Lixeira </b>

Em configurações globais, crie as linhas:

![image](https://user-images.githubusercontent.com/89140035/196297517-5b0159c9-a26d-4ef4-aa74-ce4b4bd83266.png)

Crie o diretório lixeira:

![image](https://user-images.githubusercontent.com/89140035/196297793-3859e35b-6c18-4822-94d3-c525636088bb.png)

Desta forma, se qualquer usuário deletar alguns arquivo, ele será mantido dentro do diretório <b> lixeira </b> no disco do servidor, até ser movido ou deletado permanentemente.

* <b> Bloquear determinados arquivos de gravação por usuários </b>

Tal situação pode ser necessário, pois com a permissão concedida é possível o usuário gravar qualquer tipo de arquivo, como video, musica, entre outros. <br>
Neste caso o Samba tem a opção de vetar arquivos.

![image](https://user-images.githubusercontent.com/89140035/196298727-c5235ff3-294e-4cea-aca1-a43d8f2a3ae8.png)


### Servidor DHCP 🖇️

O DHCP, Dynamic Host Configuration Protocol, é um protocolo de serviço TCP/IP que oferece configuração dinâmica de terminais, com concessão de endereços IP de host e outros parâmetros de configuração para clientes de rede. <br>
O DHCP usa um mode cliente-servidor, no qual o servidor DHCP mantém o <b> gerenciamento contralizado </b> dos endereços IP usados na rede. <br>
1 - <b> DHCPDISCOVER : </b> serve para encontrar quais servidores DHCP estão disponíveis. <br>
2 - <b> DHCPOFFER: </b> uma resposta do servidor para os pacotes DHCPDISCOVER que tem os primeiros parâmentros da conexão. <br>
3 - <b> DHCPREQUEST: </b> pedido do cliente para o aluguel do endereço IP. <br>
4 - <b> DHCPACK : </b> uma resposta do servidor com os parâmentros e o IP do computadpr do cliente.

A instalação é feita com o pacote isc-dhcp-server

<b> apt-get install isc-dhcp-server </b>

Como todo serviço, o DHCP pode ser iniciado, parado ou então reiniciado, para isso use os comandos:

<b> service isc-dhcp-server start, stop, restart, status </b>

Arquivo de configuração:<br>
<b> /etc/dhcp/dhcpd.conf </b>

![image](https://user-images.githubusercontent.com/89140035/196500201-5fef299f-3673-411e-82bc-8c0643749c41.png)

OBJETIVOS:

1 - Instalar o serviço de DHCP. <br>
2 - Configurar o serviço de DHCP para fornecer as configurações para a rede interna.<br>
3 - Testar com uma estação de trabalho na rede interna.

Após a instalação é verificado um status de erro, isso acontece pelo fato de não havar as configurações iniciais.

![image](https://user-images.githubusercontent.com/89140035/196501942-773c0c37-5fb9-41d7-b7e5-5f002f220be1.png)

Assim como feito no servidor de arquivos Samba, iremos mover o arquivo <b> dhcpd.conf </b>

![image](https://user-images.githubusercontent.com/89140035/196502872-e6ed1026-bf14-4b08-a354-cb96a8bfa21d.png)

Para VirtualBox: com duas interfaces de rede - duas placas de rede (Bridge e Interna), é preciso indicar para o Linux que servirá para configuração. O arquivo de configuração deverá ser encontrado na pasta: <br><br>

<b> /etc/default </b>

Arquivo : <b> isc-dhcp-server </b>

![image](https://user-images.githubusercontent.com/89140035/196505353-f62f3f75-33a8-4387-8de6-acd2bfc3a7f0.png)

Agora vamos configurar o arquivo de interfaces, na pasta network:

![image](https://user-images.githubusercontent.com/89140035/196506684-03ee5f14-c371-4af4-9dd7-70aecdb1a807.png)

![image](https://user-images.githubusercontent.com/89140035/196506986-e141ec19-b4d2-4248-92f9-0369f66c43fb.png)

* Configuração

A configuração do DHCP está dentro do <b> dhcpd.conf </b> na pasta <b> /etc/dhcp/dhcpd.conf </b>

![image](https://user-images.githubusercontent.com/89140035/196512141-54966e81-0693-4f12-910f-129ee4572be3.png)

![image](https://user-images.githubusercontent.com/89140035/196512614-fbb2cb20-a2f7-484e-9ad9-b9043c3e50ff.png)

* Consultar as Máquinas que estão conectadas no servidor DHCP

![image](https://user-images.githubusercontent.com/89140035/196514376-6a6d9300-b357-4515-bb52-de00f46a0301.png)

* Travar um endereço de uma máquina

As vezes é necessário que o DHCP entregue o mesmo endereço de IP para uma máquina mesmo que o tempo limite de entrega tenha expirado e outra máquina peça endereço para se conectar na rede. Ex.: compartilhamento de uma impressora instalada em uma máquina que está sendo compartilhada, montar um servidor de arquivos sem forçar que os usuários sempre tentem descobrir o novo endereço de IP, etc.

<b> /etc/dhcp vi dhcpd.conf </b>

![image](https://user-images.githubusercontent.com/89140035/196516915-e086a205-60fb-4345-8c4c-5b1b4edf6789.png)

* host: o nome do host, encontre pelo comando "hostname". <br>
* hardware ethernet: endereço MAC do host, encontre pelo comando "ip a". <br>
* fixed-address: endereço IP que queira que fique fixo.

Veja que agora o IP na máquina cliente está atribuido conforme fixado:

![image](https://user-images.githubusercontent.com/89140035/196517941-b48da986-432a-4bbc-bb50-38824ec80879.png)

### Compartilhando a Internet 📨

![image](https://user-images.githubusercontent.com/89140035/196755696-9ebede9f-4808-4fb8-b1f8-b5200484d998.png)

Objetivo: <br>
<b> Debian 10: </b> Habilitar o serviço de NAT, para que a conexão vinda das estações de trabalho vi enp0s8 sejam redirecionadas para a enp0s3. <br>
<b> Linux Mint: </b> Configurar Gateway Padrão 10.200.0.1 <br>

Essa configuração fará que possa ser compartilhado a internet para suas estações de trabalho. Transformando seu servidor Linux em um servidor de internet.

Para compartilhar a internet, seguimos os seguintes comandos:

<b> modprobe iptable_nat <br>
 echo 1 > /proc/sys/net/ipv4/ip_forward <br>
 iptables -t nat -A POSTROUTING -o enp0s3 -j MASQUERADE </b> <br> 
 
Onde:

modproble iptable_nat <br>
modprobe - carrega os módulos necessários <br>
iptable_nat - carrega os módulos de roteamento.

echo 1> /proc/sys/net/ipv4/ip_forward <br>
echo 1> - inicia um script <br>
/proc/sys/net/ipv4/ip_forward - ativa o "ip_forward", o módulo responsável pelo encaminhamento dos pacotes 

iptables -t nat -A POSTROUTING -o enp0s3 -j MASQUERADE

Cria uma regra de roteamento, que orienta o servidor

<b> Caso o comando iptables der não encontrado, entre com a instalação pelo comando apt-get install iptables </b>

![image](https://user-images.githubusercontent.com/89140035/196764249-1ba75ee4-884a-48b9-b314-eb46a2c6472d.png)

Esses comandos não criam um serviço de servidor de internet, ou seja, todas as vezes que a máquina com o Linux Debian reiniciar o serviço irá cair, e mesmo após ligar a máquina com o Linux Mint ficará sem conexão. Para desenvolver um serviço permanente de servidor de internet é necessária a criação de scritp. Siga os passos abaixo:

![image](https://user-images.githubusercontent.com/89140035/196777696-33682e8f-8e2f-4c81-a333-c9f3aa950557.png)

<b> cd /etc/init.d/ </b>

Nesta pasta indicada na imagem acima são encontrados os serviços de inicialização do Debian. Crie um arquivo "vi internet" e digite as mesmas funções abaixo:

![image](https://user-images.githubusercontent.com/89140035/196778752-ee68ab78-cbef-46a4-a868-fea865cf62bb.png)

Agora transforme esse arquivo de texto em um script, pelos comandos:

![image](https://user-images.githubusercontent.com/89140035/196779134-480d7431-18f3-4893-a270-a6ef994799a5.png)

![image](https://user-images.githubusercontent.com/89140035/196779370-d5009d98-2365-4be2-9879-589d65d1e9b7.png)

Para rodar o scricpt ao reiniciar o servidor basta entrar com o comando:

<b> service internet start </b>

### Servidor WEB (Apache2 + PhP) 🎏

Servidor web é um software responsável por aceitar pedidos em HTTP de clientes, geralmente os navegadores, e servi-los com resposta e HTTP. <br>
Isso inclui dados, que geralmente são páginas web, tais como documentos em HTML com objetos embutidos (imagens, etc.) <br>
O mais popular, e mais utilizado no mundo, é o servidor <b> Apache </b> (software livre). A Microsoft possui a sua própria solução denominada <b> IIS </b> (Internet Information Services). <br>
O servidor de web, é responsável por hospedar e publicar os recursos de HTTP e Banco de Dados, existem vários serviços e maneiras de realizar a publicação, normalmente se usa a combinação entre <b> Apache, MySQL e PHP </b>

* Apache

O Servidor Apache, é o servidor web libre criado em 1995 por *Rob McCool*. É a principal tecnologia da Apache Software Foundation, responsável por mais de uma dezena de projetos envolvendo tecnologias de transmissão via web, processamento de dados e execução de aplicativos distribuídos. <br>
É um servidor de protocolo HTTP e disponibilizado em versões para os sistemas operacionais Windows, Novell, OS/2 e outros do padrão POSIX IEEE 1003 (Unix, Linux, FreeBSD, etc.) <br>

<b> Instalação </b>

<b> apt-get install apache2 </b>

Durante a instalação do apache2 é criado um ficheiro de configuração localizado em:

<b> /etc/apache2/sites-availabble/000-default-conf. </b>

Reiniciar o servidor Apache2:

<b> service apache2 restart </b>

O Apache vem com um arquivo host virtual padrão chamado <b> 000-default.conf </b> que você pode usar como default. <br>
Caso seu servidor apacha tenha apenas um site, basta deixar o arquivo padrão e adicionar o seu site dentro do diretório <b> /var/www/html </b>

![image](https://user-images.githubusercontent.com/89140035/197076760-e3317e2b-77c1-4fc8-bac4-2c7827ed6a07.png)

Através do caminho <b> cat /var/log/apache2/access.log </b> será possível ver todos os acessos da página.

Através do caminho <b> cat /var/log/apache2/error.log </b> será possível ver todos os erros decorrentes do Apache, como configurações errada, serviço parado, entre outros.

![image](https://user-images.githubusercontent.com/89140035/197078275-d3cfe658-19c2-49fe-8886-417e67d2720b.png)

Veja que ao digitar o número de IP ele traz a página default do Apache

![image](https://user-images.githubusercontent.com/89140035/197078768-4ff1b2b8-7bed-42e9-a693-3e213e720c90.png)

Veja acima as informações da máquina que acessou a página padrão do Apache

Ao listar as portas pelo comando <b> ss -tl </b> já é possível ver a última linha <b> *:http </b> que é justamente a porta 80

![image](https://user-images.githubusercontent.com/89140035/197079231-536710e1-2aff-45d6-a9db-2344041e5d17.png)

![image](https://user-images.githubusercontent.com/89140035/197079815-2cb22673-a3c6-471f-9721-bad7682b704e.png)

* <b> index.html default </b>

![image](https://user-images.githubusercontent.com/89140035/197079979-de01ae5b-e06e-4603-9c0d-f5302278e7ef.png)

O index.html é a página padrão dentro dos diretórios nos servidores de websites que é carregada sempre que uma seja solicitada e não seja especificado o nome de um arquivos específico, neste caso o próprio servidor se encarrega de procurar pelo arquivo index.html e entregar para o visitante. <br>
A palavra index vem do inglês, que quer dizer Índice. Traduzindo para a internet, o arquivo index, seria a página principal, que guarda o índice (links) de todo o site.

Assim como os demais arquivos, vamos movê-lo e criar um novo.

![image](https://user-images.githubusercontent.com/89140035/197080860-7a8c41da-ac19-44c7-8dfe-6eba2562579f.png)

Edite o arquivo para teste

![image](https://user-images.githubusercontent.com/89140035/197081333-b173434b-b0ff-4ad9-b068-9a8a326967aa.png)

Ao carregar a página, o novo arquivo será visto pelo navegador

![image](https://user-images.githubusercontent.com/89140035/197081481-97e14bf8-0c91-4e43-a45f-0ab8f051a0b8.png)

Mas se seu servidor for hospedar mais páginas, será necessário trabalhar com arquivos de <b> host virtual </b>. <br>
Os arquivos do host virtual especificam a configuração real de nossos hosts virtuais e editam como o servidor da web Apache responderá a várias solicitações de domínio.

<b> Crie o diretório para o seu novo site: <br>
 Exemplos: <br>
 mkdir -p /var/www/teste.com.br/public_html <br>
 mkdir -p /var/www/zezinho.com.br/public_html </b> <br>
 
 ![image](https://user-images.githubusercontent.com/89140035/197087661-3d3c6c88-f51c-4fc9-bd12-97ea28aa27d6.png)
 
 Crie um novo <b> index.html </b>, exemplo de conteúdo: <br>
 
 ![image](https://user-images.githubusercontent.com/89140035/197087794-4c1a23c0-152e-4648-a420-508b09ae4b98.png)
 
 ![image](https://user-images.githubusercontent.com/89140035/197082478-a07486a6-749c-4509-ae48-26ead506afad.png)


Criar o arquivo de configuração dos sites:

O Apache vem com um arquivo host virtual padrão chamado <b> 000-default.conf </b> que você pode usar como ponto de partida. Copie este arquivo para o primeiro domínio:

<b> cp /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/teste.com.br.conf </b>

![image](https://user-images.githubusercontent.com/89140035/197088478-ed43c3b6-a34c-456d-80a6-27156416178e.png)

Após a cópia do arquivo, realizar as seguintes alterações:

![image](https://user-images.githubusercontent.com/89140035/197088741-2a36c5ad-a316-4b66-ada7-64e4fa123823.png)

Após as alterações é preciso ativar o site através do comando:

<b> a2ensite teste.com.br.conf </b>

Após a execução será retornado a seguinte mensagem:

Enabling site example.com. <br>
To active the new confuguration, you need to run: <br>
service apache2 reload <br>

Lembre-se de desativar o site padrão 000-default.conf pelo comando:

<b> a2dissite 000-default.conf </b>

Reinicie o apache pelo comando:

<b> service apache2 restart </b>

![image](https://user-images.githubusercontent.com/89140035/197088952-6ce68541-688d-41c4-b8ee-13f4ea78912a.png)

Comandos extras:

<b> apachectl -t </b>: verificar se a sintaxe do ficheiro de configuração está correta

<b> apache2 -v </b> : verificar versão Apache

<b> É necessário instalar os módulos (pacotes) de PHP para que possa rodar sites com essa tecnologia </b> <br>
Ao instalar a versão mais nova dos pacotes de PHP, ativeo, através dos comandos:

![image](https://user-images.githubusercontent.com/89140035/197091415-c2bb92b0-ad95-4572-9f24-e32cf1bf0402.png)

Consulte a versão pelo comando:

![image](https://user-images.githubusercontent.com/89140035/197091489-df6923ad-2a77-4240-9dd9-ee3300fe141b.png)

### MariaDB

<b> Banco de Dados </b>: São conjuntos de arquivos armazenados e relacionados através de tabelas. São coleções organizadas de dados que se relacionam de forma a criar algum sentido e dar mais eficiência durante uma pesquisa.

<b> SGBD </b>: Sistema Gerenciador de Banco de Dados são os softwares responsáveis pela criação, administração e armazenamento de um banco de dados.

<b> Tabelas </b>: São os locais lógicos onde os dados ficam armazenados de uma maneira organizada, uma tabela é formada por campos e registros. Os campos são os valores fixos de uma tabela, como nome, telefone, email... Já os registros são as informações adicionadas dentro da tabela.

A primeira versão do MySQL apareceu em 1995. Foi criada inicialmente para uso pessoal, mas em poucos anos evoluiu para um banco de dados de nível empresarial e se tornou o sotware de banco de dados relacional de código aberto mais popular do mundo.

Em janeiro de 2008, a Sun Microsystems comprou o MySQL por $1 bilhão. Logo depois, a Oracle adquiriu toda a Sun Microsystems após obter aprovação da Comissão Europeia no final de 2009.

Pro desconfiar da administração do MySQL pela Oracle, os desenvolvedores originais do MySQL criaram o <b> MariaDB </b> em 2009. Com o passar do tempo, o MariaDB substituiu o MySQL.

Instalar MySQL (MariaDB) <br>
<b> apt-install mariadb-server </b>

![image](https://user-images.githubusercontent.com/89140035/197275302-b2bffb01-f5a8-4696-ac26-393b27a79ba5.png)

Após a instalação, executar a configuração de segurança <br>
<b> mysql_secure_installation </b>

Para conectar no bando de dados <br>
<b> mariadb -u nome_do_usário </b>

![image](https://user-images.githubusercontent.com/89140035/197275827-9d381870-de85-486a-b71b-8f5f023aa2de.png)

1) <b>Show Databases</b>: Mostra quais bancos de dados possui no servidor

![image](https://user-images.githubusercontent.com/89140035/197276191-45ab1cab-8af8-4f0e-95e7-8796657934e0.png)

2) <b>create database nome</b>: Criar Banco de Dados

![image](https://user-images.githubusercontent.com/89140035/197276643-046f1f03-057a-4c1e-aeb5-c7c887bf933f.png)

3) <b> create table nome </b>: Criar uma tabela dentro do banco de dados

![image](https://user-images.githubusercontent.com/89140035/197277377-5e931bda-ad23-4f07-8fcc-1c4362701a4d.png)


4) <b> select * from cadastro </b> : Ver conteúdo da Tabela

![image](https://user-images.githubusercontent.com/89140035/197282437-e45afea4-75f1-48ed-ab16-b5ca417104e9.png)

Veja que pela imagem acima a tabela não possui dados.

5) <b> insert into cadastro (codigo, nome, email, endereco, nascimento, nacionalidade) <br>
 values (1, 'Eduardo Mogfores', 'eduardo_mogfores@yahoo.com.br', 'Rua y', 09091986, 'Brasileiro); </b> : Inserir dados
 
 ![image](https://user-images.githubusercontent.com/89140035/197283789-2f4b4315-4dc4-49b8-8c61-dd9f8a564d00.png)

6) <b> delete from cadastro where nome='Eduardo Mogfores'; </b> : excluir dados

![image](https://user-images.githubusercontent.com/89140035/197284165-a96a8ec2-c5b5-4e18-aa4b-1375920292bb.png)

7) <b> drop table cadastro </b> : apagar um banco de dados

![image](https://user-images.githubusercontent.com/89140035/197284493-588190e4-2bcb-4bb4-8179-dbdd12428b3c.png)

8) <b> exit </b> : sair do terminal

9) <b> drop database teste; </b> : apagar tabela teste

### WordPress - Instalando e Administrando 🗺️ (terminar)

WordPress é um sistema livre e aberto de gestão de conteúdo para internet (Content Management System - CMS), baseado em PHP com banco de dados MySQL. <br>
Executando em um servidor interpretador, voltado principalmente para a criação de páginas eletrônicas (sites) e blogs online. <br>
É uma das ferramentas mais utilizadas para conteúdo na web. <br>
É possível desenvolver sites de tipo comércio eletrônico, revistas, portfólio, gerenciador de projeto, agregador de eventos e, outros conteúdos devido a sua capacidade de extensão antravés de <b> plugins, API's (Application Programming Interface) temas e programação. </b>

<b> Instalação </b>

Pré-Requisitos:

O WordPress precisará de um <b> servidor web (APACHE), </b> um <b> banco de dados (MARIADB) </b> e o <b> PHP </b> para funcionar corretamente. A configuração de uma pilha LAMP (Linux, Apache, MariaDB, e PHP) atende a todos esses requisitos.

1) Criando um Banco de Dados MariaDB e um Usuário para o WordPress

<b> CREATE DATABASE wordpress DEFAULT CHARACTER SET utf8 COLLATE utf8_unicode_ci; </b>

... continuar

### Proxy Squid (terminar)

### Acesso Remoto 🪳

O SSH, para Secure Shell, é um protocolo de rede usado para operar logins remotos em máquinas distantes dentro de uma rede ou pela internet. As arquiteturas SSH normalmente incluem um servidor SSH usado pelos clientes SSH para conectar-se à máquina remota. O SSH é um protocolo Criptografado.

No Debian, o pacote de instação é o <b> openssh-server </b>

Com o comando <b> ss -tlpn | grep 22 </b> você irá ver a porta de conexão com o serviço de SSH.

![image](https://user-images.githubusercontent.com/89140035/197587844-dd6723a0-edee-4ed5-82ff-56f0a1ba1e76.png)

O arquivo de configuração é o /etc/ssh/sshd_config

<b> Lembrando que o usuário root é desativado por padrão </b>

Para o acesso ao seu servidor, podemos utilizar ferramentas como o PuTTY.

![image](https://user-images.githubusercontent.com/89140035/197590967-d7105fe0-3f42-4dac-bc7f-ab0551f1cb9d.png)

![image](https://user-images.githubusercontent.com/89140035/197591167-1ea3c97f-04bc-4657-acb3-ae8939320561.png)

Por padrão, como dito anteriormente, só será possível a conexão por usuário sem ser root, por questões de segurança.

![image](https://user-images.githubusercontent.com/89140035/197592017-a76488d4-483a-4ab9-ba11-6320145489c3.png)


### DNS - Bind Recursivo e Autoritativo

### Firewall - IPtables

Um firewall é um dispositivo de segurança de rede que monitora o tráfego de rede de entrada e saída e decide permitir ou bloquear tráfegos específicos de acordo com um conjunto definido de regras de segurança. <br>
Os firewalls têm sido a linha de frente da defesa na segurança de rede há mais de 25 anos. <br>
Eles colocam uma barreira entre redes internas protegidas e controladas que podem ser redes externas confiáveis ou não, como a internet. Um firewall pode ser um hardware, software ou ambos.<br>

![image](https://user-images.githubusercontent.com/89140035/197874634-861aaaed-692a-4fb1-800d-bcbe3ddaea47.png)

DMZ = rede pública.

<b> IPTABLES </b>

A função do Firewall é tomar conta das portas, verificar quem as está acessando e conforme as regras do usuário deixar ou não o acesso dos programas através das referidas portas. <br>
Para usuários Linux temos o <b> iptables </b>, configurado via scripts. <br>
As regras do iptables são compostas de uma Tabela, Opções, Chain, Dados e Ação.

<b> iptables [-t tabela] [opção] [chain] [dados] -j [ação] </b>

iptables <b> -t tabela </b> opção chain dados -j ação

<b> Tabelas: </b>

São os locais usados para armazenar os chains. <br>
As tabelas são referenciadas em uma regra iptables com a opção "-t tabela". <br>
Existem 3 tabelas discponíveis: <br>
<b> filter - </b> As regras contidas na tabela filter determinaram a aceitação (ou não) de um pacote. Dentro dessa tabela existem três cadeias: INPUT, OUTPUT, FORWARD. <br>
<b> nat - </b> usada quando há ocorrência de NAT (geração de outra conexão);
<b> mangle - </b> raramente usada, utilizada para alterações especiais de pacotes.

Se você deixar em branco [-t tabela], a tabela usada será a filter.

iptables -t tabela <b> opções </b> chain dados -j ação

<b> Opções: </b>

Representada por uma letra sempre escrita em maiúscula.

-A = acrescenta uma nova regra as exigentes; <br>
-L = lista as regras existentes; <br>
-F = apaga todas as regras; <br>
-I = insere uma nova regra;
-D = zera uma regra específica;

iptables -t tabela opções <b> chain </b> dados -j ação

<b> Chains: </b>

Com eles podemos especificar a situação do tratamento dos pacotes, seja qual tabela for.<br>
Exemplo: para tabelas <b> filter </b> temos as seguintes tipos de chains:

INPUT = consultado para dados que chegam ao computador; <br>
OUTPUT = consultado para dados que saem do computador; <br>
FORWARD = consultado para dados que são redirecionados para outra interface de rede ou outra máquina.

Já para as tabelas <b> nat </b> os chains possíveis são:

PREROUTING = consultado para os dados que precisam ser modificados logo que chegam (DNAT e redirecionamento de portas); <br>
POSTROUTING = consultado para dados que precisam ser modificados após o tratamento de roteamento (IP Masquerading); <br>
OUTPUT = consultado quando os dados gerados localmente precisam ser modificados antes de serem roteados (IPs locais).

iptables -t tabela opção chain <b> dados </b> -j ação

As opções de dados possíveis de inserção em uma regra iptables são:

-s <br>
Especifica a origem do pacote. Origem que pode ser informada como: <br>
- endereço IP completo (-s 192.168.1.1);
- hostname (-s ubuntu);
- endereço fqdn (-s www.ubuntu.com.br);
- par rede/máscara (-s 200.200.200.0/255.255.255.0 ou -s 200.200.200.0/24).

-d <br>
Especifica um destino para o pacote, com a mesma sintaxe descrita acima por -s.

-i <br>
Identifica a interface de entrada do pacote, podendo ser placa de rede, modem ou interface de conexão: <br>
-i eth0 <br>
-i enp0s3 <br>
-i wlan0 <br>

-o <br>
Identifica a interface de saída do pacote, com a mesma sintaxe descrita acima em -i.

-p <br>
Especifica o protocolo usado na regra, podendo ser: <br>
-p tcp <br>
-p udp <br>
-p icmp <br>

--sport ou --source-port <br>
Especifica uma porta ou faixa de portas de origem. Deve sempre ser acompanhado por -p tcp e -p udp.

--dport ou --destination-port <br>
Especifica uma porta ou faixa de portas de destino. Deve sempre ser acompanhado por -p tcp e -p udp.

! <br>
Exclui determinado argumento (exceção)

iptables -t tabela opção chain dados <b> -j ação </b>

<b> Ações : </b>

Sempre vem após o parâmetro -j e os mais usados são: <br>
ACCEPT = O pacote é aceito e o processamento das regras daquele chains é concluído; <br>
DROP = Rejeita o pacote sem nenhum aviso; <br>
REJECT = Rejeita o pacote, mas envia um aviso;

Mostrar regras

![image](https://user-images.githubusercontent.com/89140035/197902590-2111f9ac-8e31-4efa-a675-02eed6b89fbf.png)

Bloquear endereço IP

![image](https://user-images.githubusercontent.com/89140035/197902860-e0096d0b-1628-4d80-b127-f823ee7aeddc.png)

Apagar a regra

![image](https://user-images.githubusercontent.com/89140035/197903096-9e69c771-6586-4d65-bfa3-ccdcfe4cf443.png)

Fechar conexão com SSH

![image](https://user-images.githubusercontent.com/89140035/197903430-60281edf-6da8-4d39-baae-0b6f67927423.png)

Deixar bloqueado para todos com uma exceção

![image](https://user-images.githubusercontent.com/89140035/197904302-fc3bd1b9-dc4c-465c-a802-3417064e2e8b.png)

Bloquear comando do PING

![image](https://user-images.githubusercontent.com/89140035/197904554-4e5e2937-5bc8-4ce7-a177-3332af1154d0.png)

Bloquear comando do PING apenas para uma máquina

![image](https://user-images.githubusercontent.com/89140035/197905123-4c0aa87e-cad6-4f47-8891-42cd41156a36.png)




### Controlador de Domínio (SAMBA)

Um controlador de domínio, do inglês Domain Controller (DC), é um servidor que responde à requisições seguras de autenticação (login, verificação de permissões, etc) dentro de uma rede de computadores. <br>
Um domínio é um conceito introduzido no Windows NT em que um usuário pode ter acesso a uma série de recursos de computador com o uso de uma única combinação de nome de usuário e senha.<br>

- Usuário e senha
- Permissões na estação de trabalho
- Permissões de acesso na rede

Uma das funções do Samba também é atuar como controlador de domínio, esse recurso serve para controlar os usuário que podem acessar seus computadores e também definir permissões de uso. <br>
O Linux conta com o Samba que além de compartilhar arquivos, também pode ser o Domain Controller de uma rede. <br>
Para a configuração, será necessário a instalação dos pacotes de serviços:

<b> Samba, krb5-config, winbind e smbclient </b>

Deixando o IP do DC estático

![image](https://user-images.githubusercontent.com/89140035/198101972-f5b9bec8-0ce8-425a-b7ba-a0827385dff1.png)

Renomeando o arquivo smb.conf

![image](https://user-images.githubusercontent.com/89140035/198127072-c339a860-cbe9-47dc-a6a8-86c778318b3b.png)

Agora vamos iniciar a configuração. Para isso é preciso chamar o seguinte comando para configurar o arquivo smb.conf

![image](https://user-images.githubusercontent.com/89140035/198104681-619604be-da13-4391-9e4e-1603c7c9818b.png)

Realm = nome do domínio <br>
Domain [teste] = em branco <br>
Server Role [dc] = qual a função deste domínio?  = dc <br>
DNS backend = SAMBA_INTERNAL <br>
DNS forwarder = para quem as máquinas vão redirecionar as consultadas do domínio
Senha de Administrador = Teste22!

cat smb.conf

![image](https://user-images.githubusercontent.com/89140035/198127861-be7464f7-cca4-4112-8fdc-79e75bbff820.png)

Agora é preciso fazer uma cópia do arquivo do Kerperus, que esta dentro do diretório /var/lib diretamente para o diretório /etc

![image](https://user-images.githubusercontent.com/89140035/198128340-af5f91a2-e5ee-4737-83ec-0952269bd255.png)

Agora precisamos entrar com uns comandos para gerenciar os serviços

![image](https://user-images.githubusercontent.com/89140035/198129487-90612212-9380-44e6-a250-1307a0950948.png)

![image](https://user-images.githubusercontent.com/89140035/198130764-d3fe0885-5efd-4e15-b9e0-c7c803176e3c.png)

![image](https://user-images.githubusercontent.com/89140035/198131355-89beb238-d035-4880-9d6f-fd3c32ae0ed5.png)

![image](https://user-images.githubusercontent.com/89140035/198131493-281cdd0b-d469-4f96-bd70-3c0a4b800532.png)

![image](https://user-images.githubusercontent.com/89140035/198131846-154d6c6e-47ca-4426-ae15-7b4d7ae0286b.png)

Verificar os usuários existentes dentro do domínio

![image](https://user-images.githubusercontent.com/89140035/198385682-c9ff8664-5805-40f5-adfd-05adacfca59b.png)

Criar novo usuário

![image](https://user-images.githubusercontent.com/89140035/198385934-c7a2fe60-10df-4124-8bef-b8954b82d756.png)

Deletar usuário

![image](https://user-images.githubusercontent.com/89140035/198386104-0273b60c-d2cc-464f-ae69-f9d3b23b4a3e.png)

Resetar a senha do usuário

![image](https://user-images.githubusercontent.com/89140035/198386430-70bb6759-e79c-40cc-a454-4da53718ab67.png)

Definição de tempo para que o usuário expire no domínio

![image](https://user-images.githubusercontent.com/89140035/198386761-ce865814-54e7-4246-a446-0dbaf7cb1adf.png)

Desativar um usuário no domínio

![image](https://user-images.githubusercontent.com/89140035/198387076-7420f373-409c-4377-8f97-0f9b48b9fa58.png)

Ativar um usuário no domínio

![image](https://user-images.githubusercontent.com/89140035/198387288-1dfa6825-4964-445d-9d20-0cf442ae7191.png)

Criar ou deletar um grupo

![image](https://user-images.githubusercontent.com/89140035/198387712-87a1391f-1678-420c-9bda-ff105ba96ee2.png)

Listar grupos

<b> samba-tool group list </b>

Adicionar usuários a grupos criados. Obs: para adicionar mais usuários, basta inserir a vírgula (,) e ir colocando os nomes dos usuários

![image](https://user-images.githubusercontent.com/89140035/198388298-78409678-9efb-47c8-a349-af24f1995c44.png)

Listar os usuários dentro de um grupo

![image](https://user-images.githubusercontent.com/89140035/198388550-585fd228-3b93-4721-af90-fb86374f93c6.png)

Remover um usuário de um grupo

![image](https://user-images.githubusercontent.com/89140035/198388699-c7a600f2-a4b9-408d-9f81-e36465d4dc7a.png)

Consultar parâmetros de senha

![image](https://user-images.githubusercontent.com/89140035/198388910-6e10b8dc-e9c1-45dd-8047-82c0b2e86caa.png)

Alterar as configurações de senha (ex. mudar o tamanho miníno da senha)

![image](https://user-images.githubusercontent.com/89140035/198389645-3f94ca4f-9055-496c-8a82-fdb0c96b54c1.png)

Exibir menu de ajuda e possibilidades de alteração de sennha

<b> samba-tool domain passwordsettings set -h </b>

![image](https://user-images.githubusercontent.com/89140035/198391382-01829ea1-812c-4684-8c3d-19a7edd6a70d.png)

Ex.: desativar a complexidade da senha (não recomendado, caso desativado o usuário poderá incluir senha 12345 ou abcde por exemplo)

![image](https://user-images.githubusercontent.com/89140035/198391873-b5c08697-de27-41db-b0c3-e44fee181e88.png)

Ex.: Trocar o tempo mínimo de troca de senha

![image](https://user-images.githubusercontent.com/89140035/198392260-f8b85a53-70b3-4b08-b4b7-7f73f265ac3e.png)

<b> Controlador de Domínio (continuação) </b>

A Unidade Organizacional (OU) é um contêiner no domínio que pode conter objetos como grupos, comtas de usuário e computador. <br>
A OU é uma unidade administrativa na qual um administrador pode vincular objetos de Diretiva de Grupo e atribuir permissões a outro usuário. <br>
Portanto, podemos distinguir duas tarefas principais ao usar a OU, exceto para armazenar objetos do domínio: <br>
- Delegação de tarefas administrativas e de gerenciamento no domínio a outros administradores e usuários sem conceder a eles as permissões de administrador do domínio; <br>
- Vinculando diretivas de grupo (GPO) a todos os objetos (usuários e computadores) nesta OU.


