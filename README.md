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
