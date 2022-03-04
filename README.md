### Primeiros passos para criar chave ssh do GitHub no Git:







Para começar, o meu objetivo é de criar um repositório no Git Hub, e para isso é preciso seguir alguns passos.

primeiro abri o Git Bash e digitei o comando : ssh-keygen -t ed 25519 -C "@meuemail", primeiro passo que segui para gerar a chave ssh.  

Após isso, foi gerado o número da Key fingerprint.

Feito isso, executei um comando para verificar na pasta ssh se as chaves (privada e publica) estão disponíveis.O comando para tal é cd /c/Users/"UsuarioPC"/.ssh/. Em seguida "ls", para listar as chaves. 

Agora para a atividade no Git Hub usei a chave publica, e para isso executei o comando "cat id25519.pub". 

Após o enter, foi gerado o código, a chave pública. 

Após gerada, apenas fiz login no Git Hub/settings//SSH and GPG keys/ copiei e colei o código no espaço destinado, e adicionei o nome da chave,logo acima. 



**A etapa seguinte é entregar a chave privada ao SSH-AGENT, entidade a qual irá lidar com as chaves:** 

Dentro da pasta ".ssh/" digitei "eval $(ssh-agent -s)", lembrando que esse código gera um número "agente pid ****". Após isso, usei o comando "ls" para listar as 

chaves, e em seguida, para entregá-las ao agente, executei "ssh-add ed25519".



*Etapas da criação do token de acesso pessoal:



Primeira etapa, acessar o Git Hub/Settings/Developer settings/Personal Acess Tokens.

em Seguida, cliquei em generate new token, preenchi o campo "What’s this token for?", depois determinei o tempo de duração, ou quando expirará, e após isso, marquei a 

opção "repo", e em seguida cliquei "Generate token".
copiei o número do meu novo token pessoal, e o guardei em segurança.







#### Iniciando repositório GIT (GIT INIT)



Agora que já obtive a chave pública,e o token pessoal, o próximo passo foi criar o arquivo, e a pastas que mais tarde compuseram o meu repositório. Para isso, abri o explorador de  arquivos, e ao localizar a pasta **Disco Local (C)**, criei uma pasta dentro dela com o nome **"workspace" ** , e é nela onde tudo foi feito. 


Agora, abrindo o Git Bash novamente,  digitei  **"cd workspace"**, para assim abrir a pasta **"workspace"**.



Dentro dessa pasta criei outra pasta, de nome **"inicio"**, e para adicioná-la executei o código **"mkdir inicio"**, esse código é usado para criar diretórios intermediários em um caminho especificado. 


Feito isso, executei **"ls"** para ver listada a pasta nova criada.


Agora indo para a pasta **“inicio”** onde usei um comando para iniciar o “git” e possibilitá-lo a gerenciar e subvencionar o nosso código.Com o comando:   **“git init“**.


Depois para visualizar as pastas OCULTAS com uma flag:  **“ is -a “**  podendo assim visualizar a estrutura da pasta **/.git**.

Após isso, configurei o meu email e user name apartir dos seguintes comandos : **git config --global user.name "Meu Nome"** e **git config --global user.mail "meuemail@gmail.com"**



##### criando arquivo markdown na pasta **"inicio"** :

criei um arquivo no bloco de notas, e salvei em formato **"md"**, e o salvei na pasta **"inicio"**. 

no git bush abri a pasta **"inicio"** com o comando **"cd inicio"** e listei, usando "ls" ,para assim expor o meu recém-criado arquivo md chamado **"Minhas-anotações.md"

Após isso, usei o comando **"git add * "**e depois **"git commit -m commit inicial"** para comitar o meu arquivo e iniciar o versionamento.

nota:
O Comando "git add *"  move os arquivos para a fase **"staged"**, enquanto **" git commit -m "mensagem" "** toma os arquivos em staged,e envia para a fase commit, com uma 

mensagem envelopada.

 



### ciclo de vida dos arquivos:

`untracked` : É o arquivo que acaba de ser criado, o qual o Git não conhece.

`tracked-unmodified`: São todos os arquivos que ainda não foram, de forma alguma, modificados.

`tracked- modified`: É o arquivo que foi modificado, portanto já fora um arquivo untracked, mas por uma alteração,desde a mais simples à mais elaborada irá fazê-lo 

modificado. Essa informação é dada a partir do sha1 do arquivo, que se altera de imediato, denunciando assim qualquer mudança ocorrida em seu código. 

 

`tracked - staged`: São arquivos que saem da fase "modified! para a fase "staged".

`staged`: São arquivos que já estão prontos para fazer parte de um agrupamento, ou commit. Depois de se tornarem commit, voltam a ser unmodified.





###  Dando vida ao repositório:


Por ter adicionado por arquivo untracked - qual o git não conhecia - tive de usar o comando git add* para que ele fosse movido para "staged". Para monitorar o status
do  meu arquivo (untracked, staged, modified, unmodified) usei o seguinte comando : "git status", e assim, pude me orientar melhor. 

Feito isso, o git me retornou "on branch master nothing to commit, working tree clean", ou seja,  não havia nada para comitar ,e a árvore de trabalho está limpa. 

Sendo assim, criei outra pasta, dentro da pasta "inicio", de nome "notas" (mkdir notas), e movi meu arquivo  "Minhas-anotações" para ela. 
Primeiro listei "ls" o que tinha dentro da pasta "inicio",e só tinha o arquivo md. Então depois usei o código "mv Minhas-anotações.md ./notas" . Então o arquivo foi movido com sucesso!!!


Feito isso, usei "cd .." para voltar para a pasta "inicio". Executei o "git status" e ele acusou que o arquivo "Minhas-anotações.md" foi excluido, mas não foi! Apenas mudou de pasta. Porém, o Git não reconhece.

Para regularizar isso, fiz o seguinte: incluí esse novo arquivo md em "staged", da seguinte forma : "git add Minhas-anotações.md notas/"

por fim, executando o comando "git status", verifiquei que agora o Git reconhece o arquivo e a nova pasta, pelo falo de que ambos estão na Staged, aguardando para serem commitados. Se eu quisesse reverter a situação para o estado anterior, bastava digitar "git restore", mas não ´foi esse o meu objetivo. 


Seguindo a diante, com o objetivo de commitar ese arquivo, executei o comando **"git commit -m "msg"**

criei um arquivo chamado **README.md** digitando o seguinte código: **"echo > README.md"** . Listei "ls" para verificar se deu tudo certo, e depois executei "git status". Com essa ação pude perceber que esse arquivo foi detectado como **untracked** , já que acabou  de ser criado, e não foi versionado. Por isso, abri o arquvo no Typora, e o modifiquei. (modifiquei adicionando minhasanotações, estas mesmas, em README.md, e cá estão elas.).
Feito assim, executei "git status" para ver se mudou o status,e executei "git add *" para adicionar tudo que foi modificadio em "staged".

Agora que está em "staged", fui commita-lo, usando "git commit -m "adiciona index" " e então o arquivo foi commitado!!



#### Enfim criando o repositório no Git Hub: 



#### acessei a aba create a new   repository

Adicionando o nome da pasta "inicio", e tornando público, finalizei a solicitação do repositório. 

É perceptível no processo que é criado um link https logo abaixo dos dados da solicitação. e é esse código que usamos para lincar nossas pastas do projeto ao Git Hub. 

Após copiado, joguei ele no git bash, e rodei. feito isoso, executo o código **"git remote -v"**, e logo após executo "git status", e não há nada pra commitar com o comando: (  git status.  ).

sendo assim, executei “ git push origin master” para autenticar com o GitHub!!
