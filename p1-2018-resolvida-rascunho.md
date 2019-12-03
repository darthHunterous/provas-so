# Resolução P1 2018 SO

Esta prova tem duas partes. A primeira parte contém 32 afirmações, você deve selecionar 12 destas que estão ERRADAS. Sua folha de resposta deve conter as questões erradas NA ORDEM com uma justificativa do porquê estão erradas. A justificativa deve ter apenas uma sentença (curta, não deve ter mais que 3 linhas). Respostas sem justificativa não serão consideradas. Cada resposa vale 1 ponto. Não serão consideradas mais que 14 respostas. A segunda parte tem três questões dissertativas, que devem ser respondidas no espaço alocado. Cada questão vale 2 pontos.

## PARTE I

**1. Um processo pode estar em 4 estados diferentes: rodando, pronto, bloqueado e suspenso.**

R: FALSO 1, também existem suspenso pronto e suspenso bloqueado e suspenso pronto em alguns sistemas.

**2. Na multiprogramação cada programa tem o monopólio da CPU até seu término, mas o Sistema Operacional pode decidir a ordem do escalonamento de alto nível do processo (decidir qual a ordem em que eles serão executados).**

R: FALSO 2, a troca de programa normalmente ocorre antes do final da execução.

**3. No Minix existem apenas 3 maneiras dos processos se comunicarem, todas síncronas: arquivos, pipes e mensagens.**

R: FALSO 3, também existem os sinais, interrupções de hardware assíncronas.

**4. Os processos em Minix são organizados de maneira hierárquica, com o processo INIT no topo da árvore.**

R: VERDADEIRO

**5. Pipes são tratados como arquivos no MINIX.**

R: VERDADEIRO

**6. Na versão que utilizamos do Minix o SO é dividido em 4 camadas, sendo que as duas inferiores compartilham o espaço de endereçamento e nas outras os processos rodam com memorias independentes.**

R: FALSO 4, Só o kernel compartilha o espaço de endereçamento, todas as outras camadas são separadas.

**7. Em Minix, chamadas de sistemas não são realmente “chamadas”. A biblioteca do sistema transforma a chamada de procedimentos no envio de mensagens síncronas.**

R: VERDADEIRO

**8. Todos os processos em Minix, inclusive os do Kernel (System Task e Clock Task) funcionam de maneira síncrona, com um loop de recebimento de mensagens.**

R: VERDADEIRO

**9. O funcionamento do Minix com envio de mensagens torna o sistema menos seguro.**

R: FALSO 5, aumenta a segurança pois isola o kernel.

**10. A única maneira de se criar um processo em Minix é pela chamada de sistema `fork()`.**

R: VERDADEIRO

**11. As duas maneiras de se criar um processo em Minix são a chamada de sistema `fork()` e a chamada de sistema `execve()`.**

R: FALSO 6, `execve()` não cria um novo processo, apenas troca o código que é executado.

**12. A rotina `malloc()`, deve utilizar diretamente a chamada de sistema `brk()`. Desta maneira, a rotina `free()` libera memória apenas quando a região liberada está no limite da área de dados do processo.**

R: VERDADEIRO

**13. A chamada `open()` é necessária apenas para verificar as permissões do arquivo.**

R: FALSO 7, também é necessária para abrir um arquivo novo.

**14.O Minix tem apenas dois tipos de arquivo: de bloco e de caractere. O primeiro oferece acesso aleatório pela manipulação do ponteiro de leitura. O segundo provê apenas acesso sequencial.**

R: (???)

**15. Para CRIARMOS um pipe no Minix precisamos utilizar não somente a chamada `pipe()` mas também a chamada `close()`.**

R: VERDADEIRO

**16. Quando queremos redirecionar entrada e saída, utilizamos a chamada `dup()`.**

R: VERDADEIRO

**17. O comando `chroot()` é muito útil para usuários uma vez que permite mudar o diretório corrente de um processo, simplificando referencias a arquivos no mesmo diretório.**

R: FALSO 8, o comando para realizarmos isso é `chdir()`.

**18. A chamada `setuid()` é muito útil para a segurança do sistema Minix, uma vez que permite que um processo chamado por um usuário rode com privilégios de superusuário.**

R: VERDADEIRO

**19. Tabelas de processo são essenciais para o multiprocessamento. Elas guardam todas as informações de um processo e permitem o restauro de seu estado quando ele voltar a executar.**

R: VERDADEIRO

**20. No Minix, assim como no UNIX , o Kernel é responsável pela manutenção da tabela de processos. Chamadas ao System Task permitem que os programas obtenham os dados que precisam para tomar decisões de escalonamento.**

R: VERDADEIRO

**21. Interrupções são comunicações assíncronas do hardware para o Kernel do sistema. Quando ocorrem, o hardware consulta uma tabela de endereços. Estes endereços se referem a procedimentos do System Task que são então ativados.**

R: VERDADEIRO

**22. Em muitos sistemas operacionais, processos que trabalham em conjunto compartilham alguma memória em comum. O uso compartilhado dessa memória cria “condições de corrida”, o que implica que o uso deste recurso precisa ser coordenado. As regiões do programa que acessam a memória comum são chamadas de “regiões criticas”.**

R: VERDADEIRO

**23. São 3 as condições para uma boa solução para o problema da exclusão mútua:**
  **i. Só um processo deve entrar na região crítica de cada vez.**
  **ii. Não deve ser feita nenhuma hipótese sobre a velocidade relativa dos processos.**
  **iii. Nenhum processo executando fora de sua região crítica deve bloquear outro processo.**

R: VERDADEIRO

**24. O código abaixo resolve o problema dos filósofos comilões:**

```C
#define N 5

void Philosopher(int i) {
	int I;
	think();
	take_chopstick(i);
	take_chopstick((i+1) % N);
	eat();
	put_chopstick(i);
	put_chopstick(i+1);
}
```

R: FALSO (9), ele não verifica se os pauzinhos estão disponíveis, o que pode causar um erro.

**25. Existe uma equivalência entre semáforos, monitores e mensagens. Qualquer um destes esquemas pode ser implementado usando o outro.**

R: VERDADEIRO (???)

**26. São 3 os níveis de escalonamento de processos:**
  **i. alto nível onde se decide quais processos entram na disputa por recursos;**
  **ii. nível médio, usado para balanceamento de carga;**
  **iii. baixo nível, onde se decide quão dos processos prontos deve ter o controle da CPU.**

R: VERDADEIRO

**27. Em sistemas preemptivos, o relógio é desligado e o processo decide quando deve ceder a CPU. Isso pode gerar o travamento do sistema.**

R: FALSO (10), em sistemas preemptivos o sistema determina um tempo máximo de execuçãopara cada processo e o interrompe ao final desse tempo.

**28. No sistema de multi-level feeback queues, existem várias filas de prioridade e cada processo é alocado a uma desde o início de sua execução. Desta maneira a alocação desta prioridade é essencial para o bom desempenho do sistema. Uma maneira de fazer isso são as “prioridades compradas”, onde se delega ao usuário decidir em que fila seu processo rodará.**

R: VERDADEIRO, em sistemas mobile isso é comum.

**29. Um processo em uma fila de menor prioridade sempre demorará mais para rodar que um processo numa fila de maior prioridade.**

R: FALSO (11), uma fila de menor prioridade implica numa maior "prioridade real", ou seja, que o processo irá rodar mais rápido.

**30. No EP1, para que os comandos rodados com `rode()` ou `rodeveja()` recebessem argumentos, é necessário criar um vetor de strings com os argumentos que seria passado para a chamada de sistema `execve()`.**

R: VERDADEIRO

**31. No EP2, a execução da chamada de sistemas `chpriority()` exige que a tabela de processo seja modificada no Kernel (por meio do System Task), no Process Manager e no File System.**

EP ANTIGO

**32.No EP2, um processo pode alterar a prioridade de execução de qualquer outro processo existente no sistema.**

EP ANTIGO

## PARTE II

**1.(2 pontos) O Minix possui processos de usuário que fazem várias funções tradicionalmente atribuídas ao kernel de um SO. Desenhe as camadas de processos do Minix com seus principais representantes e explique como se dá a comunicação entre elas. Quais as vantagens do microkernel do Minix sobre o kernel monolítico de outros SOs?**

```C
|-------------------------------------------------------|
| Init  | User Process | User Process |User Process|... | > User Processes
|-------------------------------------------------------|
|  Process  | 	 File	 | 	Info  | Network |   ....	| > Server
|  Manager  | 	System	 | Server |  Server |   ....	|	Processes
|-------------------------------------------------------|
| Disk Driver | TTY Driver | Ethernet Driver | ... 		| > Device Drivers
|-------------------------------------------------------|
|		Kernel		 | 	System Task	 | 	Kernel Task     | > Kernel
|-------------------------------------------------------|
```

Vantagens: Controle maior da comunicação entre os processos e o Kernel, além de gerar independência entre as camadas. Facilita manutenção e modificações.

**2. (2 pontos) A solução abaixo para o problema dos filósofos está errada. Porque?**

```C
#define N 5
Philosopher(i){
int I;
think();
take_chopstick(i);
while (!take_chopstick((i+1) % N){
	put_chopstic(i);
	wait(random);
	take_chopstick(i);
}
eat();
put_chopstick(i);
put_chopstick(i+1);
}

```

Pode ocorrer adiamento indefinido, como a espera é aleatória, pode nunca ocorrer uma situação em que os dois pauzinhos estão disponíveis.
