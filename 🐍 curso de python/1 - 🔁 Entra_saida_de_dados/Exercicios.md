# Exercicios: Tipos e operações


## Questões

### Questão 1

***Faça um programa que leia o nome de uma pessoa e mostre uma mensagem de 'olá < nome_de_entrada > .***

### Questão 2

***Escreva um programa para somar dois números.***

### Questão 3

***Programa para somar dois números com entrada do usuário.***

### Questão 4

***Escreva um programa para multiplicar dois números com entrada do usuário.***

### Questão 5

***Escreva um programa para calcular a potência de dois números com entrada do usuário.***

### Questão 6

***Esrecva um programa que leia um Inteiro e mostre o seu sucessor e seu antecessor.***

### Questão 7

**Crie um programa que leia um número e mostre o seu dobro, triplo e sua raiz quadrada.**

### Questão 8

***Escreva um programa em python que leia a largura e altura de uma parede (em metros) e exiba a área da Parede.***

### Questão 9

***Escreva um programa em python que leia a largura e altura de uma parede (em metros), calcule a sua área e a quantidade de tinta necessária para pintá-la, sabendo que cada litro de tinta pinta uma área de 4 metros quadrados.***

### Questão 10

***Faça um código Python que leia duas notas de um aluno, calcule e exiba a média aritmética das notas.***

### Questão 11

***Programa Python para verificar se um número é positivo ou negativo.***

---

## Resoluções

### Resolução 1

```python
nome = input('Me diga seu nome: ')
print(f'Olá {nome}')
```

### Resolução 2

```python
a = 5
b = 6

soma = a+b

print(f'Soma de {a} com {b} é {soma}')
```

### Resolução 3

```python
n1 = float(input('Me diga o primeiro numero: '))
n2 = float(input('Me diga o segundo numero: '))

soma = n1 + n2

print(f'A soma de {n1} + {n2} = {soma}')
```

### Resolução 4

```python
n1 = int(input('Me diga o primeiro numero: '))
n2 = int(input('Me diga o segundo numero: '))

multiplicacao = n1*n2

print(f'A multiplicação entre {n1} x {n2} = {multiplicacao}')
```

### Resolução 5

```python
n1 = int(input('Me diga a base: '))
n2 = int(input('Me diga o expoente: '))

pot = n1**n2

print(f'o numero {n1} elevado ao {n2} é {pot}')
```

### Resolução 6

```python
n1 = int(input('Me diga um numero inteiro: '))

ante = n1-1
suce = n1+1

print(f'O seu antecessor é {ante} e seu sucessor é {suce} ')
```

### Resolução 7

```python
n = int(input('Entre com um número: '))

dobro = n*2
triplo = n*3
raiz = (float(n)) ** 0.5

print(f'O dobro de {n} é {dobro}, Seu triplo é {triplo} e sua raiz quadrada {round(raiz,2)}')
```

### Resolução 8

```python
largura = int(input('Digite a Largura: '))
altura = int(input('Digite a Altura: '))

area = largura * altura

print(f'A área da parede é de {area} m²')
```

### Resolução 9

```python
largura = int(input('Digite a Largura: '))
altura = int(input('Digite a Altura: '))

area = largura * altura
tinta = area/4

print(f'A área da parede é de {area} m²,será necessario um total de {tinta} l')
```

### Resolução 10

```python
nota1 = float(input('Primeira nota do aluno: '))
nota2 = float(input('Segunda nota do aluno: '))

media = (nota1 + nota2) / 2

print(f'A media do aluno é {media}')
```

### Resolução 11

```python
numero = float(input('Me diga um numero: '))

positivo = numero > 0

print(f'O numero {numero} é positivo? {positivo}')
```
