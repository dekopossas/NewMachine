# NewMachine
Project dedicated to practice english and register new machine configuration process

Ok, first of all a little context, i bought a new computer and a i need to configurure it to work. So lets go on the steps


depois eu continuo escrevendo em ingls, não quero perder tempo, kkkkk mas comecei com ubunto 22.04, tive um problema desgraçado pra instalar ele, primeiro pq tava sem pendrive então tentei usar meu proprio ssd pra isso e nao consegui, então chamei um uber pra pegar meu pendrive na casa da mariana e boa.

então instalei o ubuntu com ventoy e tive um problema, meu teclado não foi identificado, nem por cabo, então tive q fazer uma GAMBIARRA MALUCA,
desmontei o pc tirei o ssd novo que tinha comprado so pra colocar o ubuntu, coloquei ele num notebook e tive o meu primeiro registro:

no passo a passo da intalação do ubunto, tinha a opção, apagar um disco e instalar o ubuntu, era a opção que eu queria, mas fiquei com medo de apagar meu ssd de windows então eu desliguei, abri o pc, tirei o ssd que nao queria apagar, pra depois ligar ele de novo so com o ssd novo então queria deixar registrado aqui que é de boa de fazer, não precisa ter medo existem varias confirmações antes de realmente apagar um ssd.

muito bem, instalei o ubuntu, e instalei o chrome, o brave e o vscode. Bem fácil até aqui.
então procurei o docker pra instalar, senti muita falta do *oh my zsh*, então quero deixar aqui os passos.

vc vai precisar do git pra instalar o *oh my zsh*

então usei esse passo a passo: https://www.digitalocean.com/community/tutorials/how-to-install-git-on-ubuntu-20-04-pt
obs:(pulei a parte "Como instalar o Git do código").

e o curl tbm: https://www.alura.com.br/artigos/curl-como-usar 

https://www.alura.com.br/artigos/oh-my-zsh-melhorando-produtividade-terminal
aqui vc pode encontrar o problema que eu acabei de encontrar que é o terminal não entrar com o zsh direto, esse problema acontece pq vc nao reiniciou o ubuntu, (minha suspeita)
Reiniciei aqui e era o que eu suspeitava mesmo, caso não seja o seu caso siga esse passo a passo: https://diolinux.com.br/sistemas-operacionais/como-alterar-o-terminal-padrao-bash-zsh.html

Pqp, instalar o zsh é dificil kkkkkkk, eu imagina descrever aqui, quase nada funciona direito, os videos estão velhos e os links atualizados então os processos são diferentes, mas eu vou fazer um passo a passo melhor aqui.
mas eu estou aqui para melhorar a sua vida!

siga esse tutorial ate começar a instalar os plugins: https://www.alura.com.br/artigos/oh-my-zsh-melhorando-produtividade-terminal

pula pra troca parte de troca de thema, dessa vez eu to usando o strug, mas to querendo olhar o meu ultimo, era bem bom. Acabei de consultar e usava o "refined"
ele é bem clean, bem bom, mas não mostra a maquina, por isso q troquei pro strug, quero ter noção de ql maquina eu estou mexendo quando estou dentro do git. Mas se vc so mexe de uma maquina, o refined é bem ótimo!

hoje eu to usando um windows e um linux, então no meu linux eu coloquei o omni, que muda as cores do terminal. É bem sutil mas faz diferença, pra quem gosta, só vai nesse link:
https://github.com/getomni/gnome-terminal/blob/main/INSTALL.md

desisti de colocar no teriminal do windows, justamente pq faz muita pouca diferença

logo em seguida para instalar os plugins vai para o zinit esse é o link para consulta, mas eu vou deixar os comandos aqui: https://github.com/zdharma-continuum/zinit

pra baixar: 

```git
bash -c "$(curl --fail --show-error --silent --location https://raw.githubusercontent.com/zdharma-continuum/zinit/HEAD/scripts/install.sh)"
```

pra instalar automaticamente: 

```git
zinit self-update
```

vc vai abrir o arquivo zshrc com o comando: sudo nano ~/.zshrc e vai colocar essas linhas no final tem q ficar +- assim
### End of Zinit's installer chunk (essa linha ja ta no arquivo)
zinit light zdharma/fast-syntax-highlighting

zinit light zsh-users/zsh-autosuggestions

zinit light zsh-users/zsh-completions


quando vc salvar e sair, ele vai baixar e instalar as extenções.

agora vamo pro docker.
eu to seguindo um tutorial da trybe.

1. Então começamos removendo versões anteriores com: 
```git 
sudo apt-get remove docker* containerd runc
```

Caso nenhum dos pacotes esteja instalado, esse comando retornará o erro E: Impossível encontrar o <nome-do-pacote>. Nesse caso, é só prosseguir com a instalação.

2. Instalando as dependências iniciais
Para habilitar a obtenção dos repositórios via HTTPS pelo apt-get, instale os pacotes listados abaixo. Nós precisamos disso para prosseguir a instalação:

```git
sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
```

3. Adicionando a chave pública do repositório Docker em nossa máquina
Para adicionar a chave GPG* oficial do repositório do Docker, execute o comando a seguir:

⚠️ Este passo é necessário pois precisamos obter uma chave pública dos servidores da empresa Docker Inc para garantir que qualquer pacote obtido através da Internet esteja assinado por esta chave, evitando assim possíveis ataques de segurança.

Copiar
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
Se tudo der certo, você não deve receber nenhum retorno visual.

4. Adicionando o repositório remoto na lista do apt
Para finalmente adicionar o repositório oficial do Docker no apt, execute o seguinte comando:

Copiar
echo \
  "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" \
  | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
Perceba que adicionamos o repositório stable (em $(lsb_release -cs) stable), isso significa que teremos somente o repositório com as versões estáveis do Docker.

Em distribuições baseadas no Ubuntu (como o Linux Mint), talvez você precise alterar o comando $(lsb_release -cs) para uma versão do Ubuntu que seja compatível com aquele sistema. Por exemplo: caso utilize o Linux Mint Tessa, você deve alterar o valor para bionic.

⚠️Importante: o Docker não garante seu funcionamento em sistemas fora dos requisitos de sistema operacional.

5. Instalando o Docker no Linux
Agora sim, vamos à instalação do Docker!

Primeiro, vamos garantir que os índices dos pacotes do apt estão atualizados, já que adicionamos um novo repositório:
Copiar
sudo apt-get update
Vamos instalar a última versão estável do Docker Engine - Community, que é uma versão mantida pela própria comunidade, já que o Docker é open source.
Para isso, execute no terminal:

Copiar
sudo apt-get install docker-ce docker-ce-cli containerd.io
6. Adicionando seu usuário ao grupo de usuários Docker
Para evitar o uso de sudo em todos os comandos Docker que formos executar, vamos dar as devidas permissões ao nosso usuário.

Primeiro crie um grupo chamado docker:
Copiar
sudo groupadd docker
Caso ocorra uma mensagem: groupadd: grupo 'docker' já existe, é só prosseguir.

Então, use o comando abaixo para adicionar seu usuário a este novo grupo:
Copiar
sudo usermod -aG docker $USER
⚠️ Execute o comando exatamente como ele está acima, considerando as letras maiúsculas e minúsculas.

Para ativar as alterações realizadas nos grupos, você pode realizar logout e login de sua sessão ou executar o seguinte comando no terminal:
Copiar
newgrp docker
⚠️ Se após esse comando você tiver algum problema, reinicie sua máquina. Depois de reiniciar siga para os próximos passos

7. Inicie o Daemon do Docker
O Daemon é um serviço que fica no background, ou seja, é um serviço que sempre está em execução e aguarda por comandos feitos por meio do CLI. Entretanto, para que este serviço fique sempre disponível, precisamos ativá-lo, até mesmo após reiniciarmos nosso computador.

Para consultar o status atual do daemon do Docker, execute o seguinte comando:
Copiar
sudo systemctl status docker
O comando anterior deve retornar algo como um pequeno relatório sobre o serviço, onde consta seu status de funcionamento:
Copiar
● docker.service - Docker Application Container Engine
     Loaded: loaded (/lib/systemd/system/docker.service; enabled; vendor preset: enabled)
     Active: inactive (dead) since Thu 2021-09-23 11:55:11 -03; 2s ago
TriggeredBy: ● docker.socket
       Docs: https://docs.docker.com
    Process: 2034 ExecStart=/usr/bin/dockerd -H fd:// --containerd=/run/containerd/containerd.sock (code=exited, status=0>
   Main PID: 2034 (code=exited, status=0/SUCCESS
Caso o parâmetro Active esteja como stop/waiting ou no nosso caso, como inactive, rode o comando start para iniciá-lo:
Copiar
sudo systemctl start docker
Ao consultar o status novamente, o processo deverá estar como start/running/active.

Agora, vamos habilitar o daemon do Docker para iniciar durante o boot:
Copiar
sudo systemctl enable docker
8. Valide a instalação
Para validar se tudo ocorreu como deveria na instalação, vamos executar o tão esperado hello world do Docker:

Copiar
docker run hello-world
O terminal deve retornar uma mensagem com dicas, conforme a seguir:

depois eu vou tentar formatar esse passo a passo, copiei ele todo pq é da trybe e eu nao vou ter o acesso pra sempre, esse passo a passo é muito bom!

gerando uma nova chave ssh, essa parte é tensa to pegando na trybe tbm:

Se vc precisar de links para o gui, tem sempre links do git como :
https://docs.github.com/pt/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent

mas começaremos gerando uma chave
```git
ssh-keygen -t ed25519 -C "your_email@example.com"
```
Nessa parte é MUITO IMPORTANTE vc ler e não fazer errado que vai te polpar muito tempo, a primeira pergunta é sobre o diretorio da chave!
eu recomendo vc não mudar nada e deixar o diretorio padrão, a mens q vc saiba o que esta fazendo, não mude o nome tbm, é apenas pro seu computador saber onde está o arquivo.

depois é senha, não tem, segredo.

Adicionar sua chave SSH ao ssh-agent 
```git
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
```

Esse é o comando pra mostrar a chave publica
```git
cat ~/.ssh/id_ed25519.pub
```
