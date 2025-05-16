# Aprendendo SSH, WSL e simulação de VPS
Instalei o WSL com Ubuntu padrão via PowerShell (como administrador):  
`wsl --install`  
Abri o Ubuntu pelo menu iniciar e configurei o sistema. Agora tenho um terminal Linux dentro do Windows.

Criei uma chave SSH com:  
`ssh-keygen`  
Pressionei ENTER para aceitar os padrões e gerei a fingerprint da chave.

Atualizei os pacotes do sistema:  
`sudo apt update`  

Instalei o servidor SSH:  
`sudo apt install openssh-server`  

Tive problemas de rede (provavelmente por causa da VPN). Reiniciei o WSL:  
`wsl --shutdown`  

Desativei a VPN, abri o Ubuntu como administrador e reinstalei o openssh-server.  
Iniciei o servidor SSH com:  
`sudo service ssh start`  

Descobri o IP local do Ubuntu (WSL):  
`hostname -I`  

No PowerShell do Windows, me conectei via SSH:  
`ssh user@ip_do_ubuntu`  
Após digitar a senha, acessei a máquina Linux via SSH.

Criei um arquivo de texto na máquina Linux com:  
`echo "Hello, World!" > hello.txt`  
(echo imprime texto; o símbolo `>` redireciona a saída para um arquivo)

Verifiquei o conteúdo do arquivo com:  
`cat hello.txt`  
(cat exibe o conteúdo de arquivos no terminal)

Copiei o arquivo da máquina Ubuntu (WSL) para o Windows com:  
`scp user@ip_do_ubuntu:/home/user/hello.txt "local"`  
(scp copia arquivos de forma segura via SSH)

Enviei o arquivo de volta do Windows para o Ubuntu com:  
`scp "local" user@ip_do_ubuntu:/home/user/`
