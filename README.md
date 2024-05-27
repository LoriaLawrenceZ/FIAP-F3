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

O **Python**, por ser uma linguagem dinâmica e flexível, permite executar as mesmas ações de maneiras diferentes.

```Python
resp = input("Digite [S]im ou [N]ão: ")
while resp != 'S' and resp != 'N':
    print("Opção inválida! Digite [S]im ou [N]ão.")
    resp = input()
print("Você digitou a letra válida", resp)
```

```Python
resp = input("Digite [S]im ou [N]ão: ")
while resp not in ('S', 'N'):
    print("Opção inválida! Digite [S]im ou [N]ão.")
    resp = input()
print("Você digitou a letra válida", resp)
```
A linha com a instrução `while resp not in ('S', 'N')` pode ser traduzida como `Equanto resp não for 'S' ou 'N'`.

## CONTINUANDO

O loop `while` serve exatamente para esse tipo de situação: não temos um número definido de repetições, nem mesmo um limite para isso. Temos apenas uma **condição** que permite ao loop continuar ou parar.

Ou seja, ele é um laço de repetição baseado em condição.

O algorítmo fica semelhante a:

```
Variáveis:
    resposta: alfanumérico
Início
    resposta = “0”
    Enquanto (resposta != “42”) faça
        Escreva “Qual é a resposta para a vida, o universo e tudo mais?”
        Leia resposta
    Fim_enquanto
    Escreva “Parabéns, você acertou!”
Fim
```

Esse mesmo algorítmo em **Python**:

```Python
# Criação da variável com um valor inicial
resposta = "0"
# Enquanto a resposta não for 42, a repetição ocorre
while (resposta != "42"):
    # Para cada uma das repetições, o usuário vai submeter uma resposta
    resposta = input("Qual a resposta para a vida, o universo e tudo mais?")
# Quanto o laço terminar, a mensagem é exibida
print("Parabéns, você acertou!")
```

É necessario se atentar à condição criada, pois é passível do loop se tornar infinito.

## VAMOS REPETIR ENQUANTO FOR VERDADE

Laço pós-condicional *Faça-Enquanto*. Ele não existe no Python.

Representação do laço pós-condicional em pseudocódigo:

```
Faça
    Bloco de Repetição
Enquanto Condição
```

Laço tem característica `1, N`; ou seja, executa ao menos uma vez o bloco de repetição e executa no máximo N vezes.

### Como fazer em **Python** se ele não existe?

Pode-se colocar um laço `while` com uma condição que sempre será verdadeira e, dentro do bloco de repetição, colocar uma condição que, se for verdadeira, interrompe o laço.

```Python
somatoria = 0
print("Digite números ou 0 para finalizar...")
while True:
    num = float(input())
    somatoria = somatoria + num
    if num == 0:
        break # Força a saída do laço
print(f"Somatoria = {somatoria}")
```

Assim, contemplamos o **conceito** do laço pós-condicional no **Python**. Foi executado ao menos uma vez o bloco e a condição de saída ou continuidade do laço foi colocada no final da estrutura de repetição.

### Como fazer para controlar quantas repetições serão realizadas?

É aí que entra em cena a figura da `variável contadora`. Ela nada mais é do que uma variável que será usada como condição do loop, sendo incrementada a cada "volta" realizada.

Exemplo para ter uma repetição de 10 voltas:

```
Variáveis:
    i: inteiro
Início
    i = 0
    Enquanto (i<10) faça
        Escreva “Mais uma mensagem, com i valendo: ”, i
        i = i + 1
    Fim_enquanto
Fim
```

A cada volta é feito o incremento da variável `i` (`i = i + 1`), aumentando seu valor para que, eventualmente, ela atinja o limite estipulado

```Python
# Criação da variável com um valor inicial
i = 0
# Enquanto a variável contadora não chegar ao limite
while (i<10):
    # Para cada uma das repetições uma mensagem é exibida
    print("Mais uma mensagem, com i valendo: {}".format(i))
    i = i + 1
```

Da mesma forma que foi realizado um **incremento**, seria possível realizar um **decremento**.

## PARA LÁ E PARA CÁ

Quando há um problema que exige um *número determinado* de repetições, há uma estrutura mais apropriada que o loop `while` aliado ao contador: o laço de repetição `for`.

A ideia de funcionamento do laço `for` é baseada em determinar um ponto inicial e um ponto final para a repetição, sendo que a própria estrutura se encarregará de controlar o número de voltas.

Estrutura no laço `for` em pseudocódigo:

```
para <contadora> de <valor inicial> até <valor final> passo <incremento> faça
    //instruções que serão repetidas
fim_para
```

Se quisermos uma repetição de 10 vezes em **Python**, podemos fazer uso de uma função chamada `range()` que definirá um intervalo de valores para a nossa variável contadora assumir.

```Python
# A variável contadora deverá assumir valores no intervalo entre 0 e 9
for x in range(10):
    # Para cada um desses valores, vamos printar o valor da variável
    print(x)
```

> Pode-se ler como *"para a variável x no intervalo entre 0 e 9, faça:"*

Mas e se quiser controlar o valor inicial da variável?

Isso é possível alterando a função `range()` com a inclusão de outro argumento. Se escrever `range(1, 10)`, por exemplo, o valor inicial será **1** e o valor final será **9**.

```Python
# A variável contadora deverá assumir valores no intervalo entre 1 e 9
for x in range(1,10):
    # Para cada um desses valores, vamos printar o valor da variável
    print(x)
```

Mas e para controlar o incremento?

Basta adicionar um argumento na função `range()`! Se escrever `range(1, 10, 2)`, o valor inicial será 1, o valor final será 9 e o incremento será de 2 em 2.

