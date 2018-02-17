# Sistemas operacionais : Gerência de atividades



## Introdução



### Conceito base
"Um __programa__ (software, aplicativo, etc) é um conjunto de uma ou mais sequências de instruções escritas para resolver um problema específico, constituindo assim uma aplicação ou utilitário."

**Termo**: processo, atividade, tarefa

**Conceito**: é a execução, por um ou mais processadores, das sequências de instruções definidas em um programa para realizar seu objetivo

**Por que**? existe mais processos que número de processadores disponíveis



### Hierarquia


comando ```pstree```




### Processos IO ou CPU Bound


```c
FILE * fp = fopen("exemplo", "w+");
int count = 1;
while (count++) {
  fprintf(fp, "%d ", count);
  printf("%d\n", count);
}
fclose(fp);
```

```c
int count = 1;
while (count++) { }
```


### Sistemas mono e multi

1. Monotarefa
1. Multitarefa
   1. Preemptiva
   2. Cooperativa
1. Tempo compartilhado



## Ciclo de vida

**Estados**

- Novo
- Pronto, Apto
- Executando
- Suspensa, Esperando
- Terminada



## Gerenciador de processos


### Escalonador : Algoritmos

### Troca de contexto
