# [](#header-1) Sistemas operacionais : Gerência de atividades : Introdução


## [](#header-2) Introdução

[slide](./introduction.pdf)

[Capítulo 02 Gerência de tarefas](http://wiki.inf.ufpr.br/maziero/lib/exe/fetch.php?media=so:so-cap02.pdf) do livro [Sistemas Operacionais: Conceitos e Mecanismos](http://wiki.inf.ufpr.br/maziero/doku.php?id=so:livro_de_sistemas_operacionais)


### [](#header-3) Conceito base
"Um __programa__ (software, aplicativo, etc) é um conjunto de uma ou mais sequências de instruções escritas para resolver um problema específico, constituindo assim uma aplicação ou utilitário."

**Termo**: processo, atividade, tarefa

**Conceito**: é a execução, por um ou mais processadores, das sequências de instruções definidas em um programa para realizar seu objetivo

**Por que**? existe mais processos que número de processadores disponíveis



### [](#header-3) Hierarquia

comando ```pstree```



### [](#header-3) Processos IO ou CPU Bound


**io** input and output
```c
FILE * fp = fopen("exemplo", "w+");
int count = 1;
while (count++) {
  fprintf(fp, "%d ", count);
  printf("%d\n", count);
}
fclose(fp);
```

**cpu**
```c
int count = 1;
while (count++) { }
```


### [](#header-3) Sistemas mono e multi

1. Monotarefa
1. Multitarefa
   1. Preemptiva
   2. Cooperativa
1. Tempo compartilhado



## [](#header-2) Ciclo de vida

**Estados**

- Novo
- Pronto, Apto
- Executando
- Suspensa, Esperando
- Terminada

## [](#header-2) Tarefas leves ou Threads


