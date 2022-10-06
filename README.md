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
* <b> Use su -lou su -para iniciar o shell raiz com um ambiente semelhante a um shell de 'login' normal. </b>


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







