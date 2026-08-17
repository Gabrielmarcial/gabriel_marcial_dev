# Exercicios : Estruturas de repetição(For-while-Break-continue-pass)


## Questões

### Questão 1

Escreva um programa em python que imprima todos os números inteiros de 0 a 50.

### Questão 2

Escreva um programa em python que imprima todos os números inteiros do intervalo fechado de
1 a 100.

### Questão 3

Escreva um programa que imprima todos os números inteiros de 100 a 1 (em ordem decrescente).

### Questão 4

Escreva um programa em python que imprima todos os números inteiros de 100 a 200.

### Questão 5

Escreva um programa em python que imprima todos os números inteiros de 200 a 100 (em ordem decrescente).

### Questão 6

Escreva um programa em python que imprima todos os números múltiplos de 5, no intervalo fechado de 1 a 500.

### Questão 7

Escreva um programa em python que imprima todos os números pares do intervalo fechado de 1 a 100.

### Questão 8

Escreva um programa em python que imprima os 100 primeiros números ímpares.

### Questão 9

Escreva um programa que imprima o quadrado dos números no intervalo fechado de 1
a 20.

### Questão 10

Escreva um programa em python que receba 5 números e mostre a metade de cada número.

### Questão 11

Escreva um programa em python que receba 5 números e mostre o quadrado de cada número.

### Questão 12

Criar um programa em python que mostre todos os números de 1 até 100 e a soma deles.

### Questão 13

Escreva um programa em python que leia 5 números inteiros positivos e informe a soma e a média dos números.

### Questão 14

Criar um programa que leia um número (N), e depois leia N números inteiros e imprima o maior deles.

### Questão 15

Criar um programa que leia dez números inteiros e imprima o maior e o menor número da lista.

### Questão 16

Escreva um programa em python, que leia um conjunto de 10 fichas, cada uma contendo, a altura
e o código do sexo de uma pessoa (1 para masculino e 2 para feminino), mostre:
  - a maior e a menor altura;
  - a média de altura das mulheres;
  - a média de altura da turma.

### Questão 17

Crie um algoritmo que escreva os N primeiros termos de uma progressão
aritmética e imprima sua soma.

### Questão 18

Nota: De que forma você poderia modificar o código acima implementando: *print(list(range(a,a+n*r,r)))* ?

18. Escreva um programa em python que leia uma quantidade de números inteiros até que seja digitado o valor 0. O programa deve calcular e escrever a quantidade de números pares e ímpares e a média aritmética dos números pares. e o número zero não deve ser considerado.

### Questão 19

Calcule 8! usando a estrutura while.

### Questão 20

Calcule 8! usando a estrutura for.

### Questão 21

Escreva um programa python que calcule o valor do fatorial de um número n qualquer.

### Questão 22

Escreva um programa em python que utilizando a estrutura while determine a soma dos números pares da Série de Fibonacci até um termo n (natural) digitado pelo usuário.

### Questão 23

Escreva um programa python (utilizando a estrutura for) para determinar o somatório e o produtório de n números reais digitados pelo usuário. Ainda, o programa deve determinar a média dos números, o valor máximo e o mínimo.

### Questão 24

Escreva um programa python que (com a estrutura while) imprima n números inteiros começando no -5.

### Questão 25

Escreva um programa python que determine a soma dos números primos entre 0 e um número inteiro positivo n.

### Questão 26

Escreva um programa que leia 2 números inteiros positivos, A e B, e que calcule a soma de todos os números compreendidos entre(sem considera A E B) eles. Se A for maior que B deve ser enviada a mensagem:"soma não será realizada".

### Questão 27

Crie um algoritmo que apure os votos de uma eleição, numa cidade com 20.000 eleitores, onde concorreram quatro candidatos. Um servidor da Justiça Eleitoral digitará cada voto individualmente. Cada voto equivale a um número inteiro. Os votos válidos podem ser 1, 2, 3 e 4, e estão relacionados aos seguintes candidatos:
1 – Gabriel
2 – José
3 – Maria
4 – Romel
Votos com o valor 0 são votos em branco, e votos com qualquer outro valor (além de 0, 1, 2, 3 e 4), são votos nulos.Calcule e escreva o total de votos de cada candidato, o total de votos brancos e o total de votos nulos.

### Questão 28

Crie um algoritmo de caixa eletrônico que lê a quantidade de dinheiro a ser sacado e imprime a menor quantidade de notas a ser dada ao usuário. A sua máquina de saque eletrônico é carregada com notas de 100, 50, 20, 10, 5 e 1 cada. Imprimir também a quantidade de cada nota a ser dada ao usuário.

### Questão 29

Escreva um programa que entre com os valores de a, b e c de uma eq do segundo grau e retorne suas raízes reais e complexas.

### Questão 30

Desenvolva um algoritmo que leia três números e determine o maior e o menor.

### Questão 31

Faça um programa que fatore um número.

### Questão 32

# **Estrutura de dados II**

---

## Resoluções

### Resolução 1

```python
for a in range(0, 51):
  print(a)
```

### Resolução 2

```python
for a in range(1, 101):
  print(a)
```

### Resolução 3

```python
for a in range(100, 0, -1):
  print(a)
```

### Resolução 4

```python
for a in range(100, 201):
  print(a)
```

### Resolução 5

```python
for a in range(200, 99, -1):
  print(a)
```

### Resolução 6

```python
for a in range(5, 501, 5):
  print(a)
```

### Resolução 7

```python
for a in range(1, 101):
  if a % 2 == 0:
    print(a)
```

### Resolução 8

```python
for a in range(1, 201):
  if a % 2 != 0:
    print(a)
```

### Resolução 9

```python
for a in range(1, 21):
  print(a ** 2)
```

### Resolução 10

```python
for a in range(1, 6):
  n = int(input('Digite um numero: '))
  n = n/2
  print(n)
```

### Resolução 11

```python
for a in range(1, 6):
  n = int(input('Digite um numero: '))
  n = n ** 2
  print(n)
```

### Resolução 12

```python
soma = 0

for a in range(1, 100+1):
  soma += a
  print(a)

print(f'A soma de todos esses numeros é {soma}')
```

### Resolução 13

```python
soma = 0
for c in range(1, 5+1):
    n = int(input('Me diga um numero inteiro: '))
    soma += n
print(f'a média desses numeros é de {soma/5}')
```

### Resolução 14

```python
maior = 0
N = int(input('Me diga a quantidade de numeros inteiros que você deseja ler: '))
for c in range(1, N+1):
    num = int(input('Me diga um numero: '))

    if c == 1:
        maior = num

    else:
        if num > maior:
            maior = num

print(f'O maior valor desses números é {maior}')
```

### Resolução 15

```python
maior = menor = 0
for c in range(1, 11):
    num = int(input('Me diga um numero: '))

    if c == 1:
        maior = menor = num

    else:
        if num > maior:
            maior = num

        if num < menor:
            menor = num

print(f'O maior e menor valor desses numeros digitados foram {maior} e {menor}')
```

### Resolução 16

```python
quant = maior = menor = soma2 = soma= 0

for c in range(1, 11):

    altura = float(input('Me diga sua altura: '))
    sexo = int(input('Digite seu sexo: [1]masculino | [2]feminino: '))
    soma += altura

    if sexo == 2:
        quant += 1

    if c == 1:
        maior = menor = altura

    else:
        if altura > maior:
            maior = altura

        if altura < menor:
            menor = altura

print('---'*20)
print(f'A maior altura dessas fichas é {maior} e a menor altura é {menor}')
print(f'A media de altura da turma é {soma/10}')
print(f'A media de altura das mulheres é {soma/ quant}')
```

### Resolução 17

```python
a = int(input("Digite o primeiro termo da P.A: "))
r = int(input("Digite a razão da P.A: "))
n = int(input("Quantos termos tem a P.A: "))

print('Sua progressão aritimética será de:', end=' ')

lista = []

for c in range (a, a + n*r, r):
    print(c,end=', ')
    lista.append(c)

print(end='\n')
print('E sua soma será de: ', end=' ' )
print(sum(lista))
```

### Resolução 18

```python
num_par = 0
num_impar = 0
soma_par = 0

while True :
  n = float(input('Entre com o número: '))

  if n == 0 :
    break

  if n % 2 == 0 :
    num_par += 1
    soma_par = soma_par + n

  else :
    num_impar += 1

media = soma_par/num_par

print(f'{num_par} Pares \n{num_impar} Impar \nMédia dos Pares {media} ')
```

### Resolução 19

```python
cont = 8
fat = 1

while cont != 0 :
  fat = fat*cont
  cont = cont - 1

print(f'Fatorial de 8 é {fat}')
```

### Resolução 20

```python
n = 1
for c in range(1,9):
   n = n*c

print(f'Fatorial de 8 é {n}')
```

### Resolução 21

```python
print('-------------------------Calculando Fatorial de um Número-------------------------')
num = int(input('Entre com o Número:'))
fat = 1
cont = num

while cont != 0 :
  fat = fat*cont
  cont = cont - 1

print(f'Fatorial de {num} é {fat}')
```

### Resolução 22

```python
n = int(input('Entre com o Número:'))
cont=1
a=1
b=c=soma=0

while cont<=n :
    print(a)

    # verificando se é par
    if a % 2 == 0:
        soma = soma + a

    #arrumando os termos
    c = a
    a += b
    b = c

    cont = cont+1

print(f"soma = {soma}")
```

### Resolução 23

```python
n = int(input('Entre com quantidade de Números:'))
soma = 0
produto = 1
max  = 0
min  = 0

for c in range(n):
  num = float(input('Entre com o número: '))

  # Verificando Máximo e Mínimo
  if c == 0 :
    max = num
    min = num

  if num > max :
    max = num

  if num < min:
    min = num

  # Produto e soma dos numeros
  soma += num
  produto = produto*num

media = soma / n
print('---'*10)
print(f' Somatório: {soma}\n Produtório:{produto}\n Média:{media} \n Máximo:{max}\n Mínimo:{min}')
print('---'*10)
```

### Resolução 24

```python
n = int(input('Entre com a quantidade de números:'))
cont =-5

while n != 0 :
  print(cont)
  cont += 1
  n += -1
```

### Resolução 25

```python
n = int(input('Entre com a quantidade de números: '))
soma = 0

for c in range(1,n+1):
  divi = 0

  for i in range(1,c+1):
    if c % i == 0 :
      divi += 1

  if divi == 2 :
     soma+=c


print(soma)
```

### Resolução 26

```python
a = float(input('Entre com A:'))
b = float(input('Entre com B:'))

soma = 0

if a > b :
  print('Soma não será realizada')

else :

  for c in range(int(a+1),int(b)):
    print(f'  {c}')
    soma += c
print('+___')
print(f'  {soma}')
```

### Resolução 27

```python
import random
cand_1 = cand_2 = cand_3 = cand_4 = branco = nulo  = 0

for c in range(20000):
  voto = random.randint(0,10)

  if voto == 1 :
    cand_1 += 1
  elif voto == 2 :
    cand_2 += 1
  elif voto == 3 :
    cand_3 += 1
  elif voto == 4 :
    cand_4 += 1
  elif voto == 0 :
    branco += 1
  else :
    nulo += 1


print(f'''
       ---------------------------
       |    APURAÇÃO DOS VOTOS : |
       |-------------------------|
       | 1 – Gabriel      : {cand_1} |
       | 2 – José         : {cand_2} |
       | 3 – Maria        : {cand_3} |
       | 4 – Romel        : {cand_4} |
       | Votos em Branco  : {branco} |
       | Votos Nulos      : {nulo}|
       --------------------------
       ''')
```

### Resolução 28

```python
valor = float(input("Quanto deseja sacar:"))
valor = int(valor)
desejo = input(f'o valor a ser sacado será de {valor}. Deseja continuar ? sim [1] não[2]'))

if desejo == 1:
  valor50= valor//50
  valor%=50
  valor20= valor//20
  valor%=20
  valor5= valor//5
  valor%=5
  valor1= valor//1

  print("{} notas de 50 reais".format(valor50))
  print("{} notas de 20 reais".format(valor20))
  print("{} notas de 5 reais".format(valor5))
  print("{} notas de 1 real".format(valor1))

else :
  print('Obriado por usar nosso serviços')
```

### Resolução 29

```python
# raizes
a = float(input('Digita o valor de a: '))
b = float(input('Digita o valor de b: '))
c = float(input('Digita o valor de c: '))

#determinante
D = (b**2 - 4*a*c)

#calculo das raizes5
if D >=0:
    x1 = (-b + D**(1/2)) / (2*a)
    x2 = (-b - D**(1/2)) / (2*a)
    print('x1 = {}'.format(x1))
    print('x2 = {}'.format(x2))

if D < 0 :
    print(f'x1 = {(-b)/(2*a)}+{((D*(-1)) ** (1 / 2))/(2*a)}i ')
    print(f'x1 = {(-b)/(2*a)}-{((D*(-1)) ** (1 / 2))/(2*a)}i ')
```

### Resolução 30

```python
max = 0
min = 0
a = 0
for c in range(3):
  a = float(input("entre com o número "))
  if c == 1 :
    max = a
    min = a
  if a > max :
    max = a
  if a < min :
    min = a

print(max ,min)
```

### Resolução 31

```python
  n = int(input("Digite um número: "))

  print('Fatores------------')
  divisor =  2
  while n != 1:
      # conta o tamanho do expoente
      exp = 0;
      while n%divisor == 0:
          n = n / divisor;
          exp = exp + 1;

      # imprime a multiplicade do fator
      if exp != 0:
          print(f"{divisor}^{exp}")

      divisor +=  1
  print('-------------------')
```

### Resolução 32

*(sem código associado)*
