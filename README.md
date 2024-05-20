<h1 style="text-align: center;">CAPÍTULO 9</h1>

>**Capítulo 9 - Estruturas Avançadas de Lógica**

## POR QUE EU PRECISO DE REPETIÇÕES?

### Problema

Imagine um arquivo de texto no formato csv (comma separated values) contento informações de alunos. Munido desta lista, você deve disparar um e-mail para todos os alunos menores de idade.

>O que fazer? Verificar linha a linha?

Em um cálculo rápido, se o arquivo tiver 10.000 linhas, você precisará de 10.000 `if` para verificar se cada aluno em cada uma das linhas é menor de idade.

```
se <condição para a 1ª linha> então
    //o que ocorrerá se o aluno for menor
fim_se
se <condição para a 2ª linha> então
    //o que ocorrerá se o aluno for menor
fim_se
se <condição para a 2ª linha> então
    //o que ocorrerá se o aluno for menor
fim_se
...
se <condição para a 10.000ª linha> então
    //o que ocorrerá se o aluno for menor
fim_se
```

Além de ser contraproducente fazer a inserção manual, o programa fica suscetível a falhas.

### Solução

Um **loop** é uma estrutura que permite indicar a repetição de uma tarefa em um determinado número de vezes.

```
para linha de 1 até 10000 passo 1 faça
    se <condição para linha> então
        //o que acontecerá se o aluno for menor
    fim_se
fim_para
```

## TIPOS DE LAÇOS EXISTENTES NA PROGRAMAÇÃO

| CONTADOR | PRÉ-CONDICIONAL | PÓS-CONDICIONAL |
|:--------:|:---------------:|:---------------:|
|  `for`   |     `while`     |      `do`       |

> Não existe `do` em PYTHON.

### Contador

Bloco de código será executado um número específico de vezes.

```Python
# PYTHON
for count in range(5):
    print(f'Count is: {count}')
```

### Pré-condicional

Há uma verificação **ANTES** de executar o bloco de código.

```Python
# PYTHON
while <condição>:
    <bloco de código>
```

### Pós-condicional

Há uma verificação **APÓS** a execução do bloco de código.

>Não existem em **PYTHON**

```Java
// Java

int count = 0;

do {
    System.out.println("Count is: " + count);
    count++;
} while (count < 5);
```

## ENQUANTO FOR VERDADE VAMOS REPETIR

>Laço pré-condicional `while`

Sintaxe em pseudocódigo:

```
Enquanto <condição> Faça
    <Bloco de Repetição>
Fim_enquanto
```

A visualização gráfica (fluxograma) e a codificação (pseudocódigo ou **Python**) requer algum cuidado.

Sintaxe no **Python** (while):

```Python
while <condição>:
    <Bloco de Repetição>
```

A caracterização de blocos em **Python** é definida pela **identação** do código.

A característica mais importante do laço, que os diferencia dos demais, é o fato de ele ser uma laço ``0, N``.<br>Ele tem a característica de executar o bloco de repetição no mínimo nenhuma (*zero*) vez e no máximo várias (N).

Isso significa que o laço é mais bem utilizado em situações em que há a possibilidade de um *bloco de repetição* não ser executado.

### Exemplo

```Python
resp = input("Digite [S]im ou [N]ão: ")
while resp != 'S' and resp != 'N':
    print("Opção inválida! Digite [S]im ou [N]ão.")
    resp = input()
print("Você digitou a letra válida", resp)
```

O **Python**, por ser uma linguagem dinâmica e flexível, permite executar as mesmas ações de maneiras diferentes.

```Python
resp = input("Digite [S]im ou [N]ão: ")
while resp not in ('S', 'N'):
    print("Opção inválida! Digite [S]im ou [N]ão.")
    resp = input()
print("Você digitou a letra válida", resp)
```