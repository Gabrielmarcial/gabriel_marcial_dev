# Exercicios : Tuplas,Listas e dicionários


## Questões

### Questão 1

Crie um programa em python que permita verificar se 2 vetores são iguais.

### Questão 2

Faça um programa em python que leia 4 notas, mostre as notas e a média na tela.

### Questão 3

Faça um Programa que leia um vetor de 5 números inteiros, mostre a soma, a multiplicação e os números.

### Questão 4

Faça um Programa que leia um vetor de 10 caracteres, e diga quantas consoantes foram lidas. Imprima as consoantes.

### Questão 5

Faça um Programa que leia um vetor de 10 números reais e mostre-os na ordem
inversa.

### Questão 6

Crie um algoritmo para ler uma letra do alfabeto e verificar se é vogal ou consoante.

### Questão 7

Faça um Programa em python que leia 20 números e armazene-os num vetor. Armazene os números pares no vetor PAR e os números IMPARES no vetor impar. Imprima os três vetores.

### Questão 8

Faça um Programa que leia um vetor A com 10 números inteiros, calcule e mostre a soma dos quadrados dos elementos do vetor.

### Questão 9

Foram anotadas as idades e alturas de 30 alunos. Faça um Programa que determine quantos alunos com mais de 13 anos possuem altura inferior à média de altura desses alunos.

### Questão 10

Faça um programa em python que leia seis valores numéricos atribuindo-os a duas variáveis do tipo lista com três elementos cada. Cada variável irá representar um vetor, calcule o produto escalar e o produto vetorial destes vetores.

### Questão 11

Escreva um programa que leia um número N. Em sequência, ele deve ser N números e armazená-los em uma lista.

### Questão 12

Escreva um programa em python que peça um vetor de 16 posições e troque as 8 primeiras posições pelas 8 últimas posições. Imprima o vetor original e o vetor trocado.

### Questão 13

Crie um algoritmo que leia uma quantidade de números N localizados em um intervalo entre x e y verifique se ele é primo e caso seja adicione ele a um vetor. Imprima a soma resultante dos elementos de dentro desse vetor.

### Questão 14

Crie um programa que permita somar todos os elementos de uma lista.

### Questão 15

Em uma fazenda existem 90 animais. Cada animal tem preso em seu pescoço um cartão
contendo seu número de identificação e seu peso. Crie um programa em python que escreva o
número e peso do maior e menos animal.

### Questão 16

Ler um vetor de 30 posições. Depois, ler um número inteiro n,imprimir quantas vezes o número n aparece no vetor.

### Questão 17

Com duas listas numéricas, A e B, crie um algoritmo que permita determinar o produto interno dessas listas.
exemplo :
 - lista_A = [ 2 , 4 , 5 ]
 - lista_B = [ 4 , 0 , 7 ]
 - Produto = [ 8 , 0 , 35 ]

### Questão 18

Escreva um programa para converter números inteiros, menores do que 4000 em algarismos arábicos, para romanos.

### Questão 19

Leia um vetor de 40 posições e conte quantos elementos pares se encontram no vetor

---

## Resoluções

### Resolução 1

```python
vet1 = [2,3,4,5]
vet2 = [2,3,4,5]

if vet1 == vet2:
  print('São iguais')
else:
  print('Não são iguais')
```

### Resolução 2

```python
notas = []
soma = 0
for c in range(4):
  n = float(input('Entre com a nota:'))
  notas.append(n)

for nota in notas:
  soma += nota

media = soma / len(notas)

print(notas)
print(f'Média:{media}')
```

```python
notas = []

for c in range(4):
  n = float(input('Entre com a nota:'))
  notas.append(n)

media = sum(notas) / len(notas)

print(notas)
print(f'Média:{media}')
```

### Resolução 3

```python
numeros = []

for c in range(5):
  n = int(input('Entre com o número:'))
  numeros.append(n)

# soma
soma = sum(numeros)

# multiplição
produto = 1
for numero in numeros:
  produto = produto*numero


print(f'''
Números:{numeros}
Soma:{soma}
Produto:{produto}
''')
```

```python
import numpy as np

numeros = []

for c in range(5):
  n = int(input('Entre com o número:'))
  numeros.append(n)

# soma
soma = np.sum(numeros)

# multiplição
produto = np.prod(numeros)


print(f'''
Números:{numeros}
Soma:{soma}
Produto:{produto}
''')
```

### Resolução 4

```python
vogal = ['a','e','i','o','u']
consoantes = []
for c in range(10):
  letra = input('Entre com uma letra:')
  letra = letra.lower()
  if letra not in vogal:
    consoantes.append(letra)

print(consoantes)
print(f'Quantidade:{len(consoantes)}')
```

### Resolução 5

```python
numeros = []
inverso = []
for c in range(10):
  n = int(input('Entre com o número:'))
  numeros.append(n)

for c in range(len(numeros)-1,-1,-1):
  inverso.append(numeros[c])

print(numeros)
print(inverso)
```

### Resolução 6

```python
vogal = ['a','e','i','o','u']

letra = input('Entre com uma letra:')
letra = letra.lower()

if letra not in vogal:
  print('É consuante')
else :
  print('Não é consuante')
```

### Resolução 7

```python
import random

vetor = []
par = []
impar = []

for c in range(20):
  num = random.randint(0,100)
  vetor.append(num)
  if num%2 == 0:
    par.append(num)
  else:
    impar.append(num)

print(vetor)
print(par)
print(impar)
```

### Resolução 8

```python
vetor = []
quadrados = []

for c in range(10):
  num = int(input('Entre com um número:'))
  vetor.append(num)

for c in vetor:
  num_2 = c**2
  quadrados.append(num_2)

print(vetor)
print(quadrados)
```

### Resolução 9

```python
import random


# entrada / criando os dados
idades = [ ]
alturas = [ ]

for c in range(30):
  idade = random.randint(8,18)
  altura = random.uniform(1.0,2.0)

  idades.append(idade)
  alturas.append(round(altura,2))

# calculando a media
media  = sum(alturas)/len(alturas)
media = round(media,2)

# verificar os alunos com idade maior q 13
cont = 0

for x,y in zip(idades,alturas):
  if x > 13 :
    if y < media :
      cont += 1


# saida
print('Idades:',idades)
print('Alturas:',alturas)
print('Alunos com idade maior que 13 anos e com altura acima da média:',cont)
```

### Resolução 10

```python
import numpy as np

vetor_1 = []
vetor_2 = []

for c in range(6):
  if c < 3 :
    n = int(input('Entre com o valor do  Vetor 1 : '))
    vetor_1.append(n)
  else:
    n = int(input('Entre com o valor do  Vetor 2 : '))
    vetor_2.append(n)

produto_vetorial = np.cross(vetor_1,vetor_2)
produto_escalar = vetor_1[0]*vetor_2[0]+vetor_1[1]*vetor_2[1]+vetor_1[2]*vetor_2[2]

print(f'Vetor 1 : {vetor_1}, Vetor 2 : {vetor_2}')
print(f'Produto Vetorial : V1xV2 = {produto_vetorial}')
print(f'Produdo Escalar : V1.V2 = {produto_escalar}')
```

### Resolução 11

```python
n = int(input('Entre com quantos números deseja armazenar:'))
v = []

for c in range(n):
  num = float(input(f'Entre com o Número {c+1}:'))
  v.append(num)

print(f'Números : {v}')
```

### Resolução 12

```python
import random
vetor = []
for c in range(16):
  vetor.append(random.randint(0,100))

print(f'Vetor Original:{vetor}')

for pos in range(8):
  num = vetor[pos]
  vetor[pos] = vetor[15-pos]
  vetor[15-pos] = num

print(f'Vetor Alterado:{vetor}')
```

### Resolução 13

```python
x = int(input('Entre com o primeiro número: '))
y = int(input('Entre com o último número: '))
soma = 0
vetor = []

for c in range(x+1,y):
  print(c)
  divi = 0

  for i in range(1,c+1):

    if c % i == 0 :
      divi += 1

  if divi == 2 :
     vetor.append(c)

for i in vetor:
  soma += i

print('Números:',vetor,'\nsoma:',soma)
```

### Resolução 14

```python
import random

# gerando uma lista aleatoria
lista = []
for c in range(10):
  lista.append(random.randint(0,10))
print(lista)

# somando
soma = 0
for elemento in lista :
  soma += elemento

print(f'Soma: {soma}')
```

### Resolução 15

```python
import random
animais = {}
maior = 0
menor = 0

for c in range (0, 90):
    id = 100000 + c
    peso = random.randint(0,1000)
    animais[peso] = id

    if c == 0 :
        maior = peso
        menor = peso

    elif peso > maior:
       maior = peso

    elif peso < menor:
        menor = peso

print(f'O Maior Animal : {animais[maior]} com {maior}kg')
print(f'O Menor Animal : {animais[menor]} com {menor}kg')
```

### Resolução 16

```python
import random
cont = 0
vetor = []
for c in range(30):
  vetor.append(random.randint(0,10))

print(vetor)

x = int(input('Qual valor deseja verificar :'))

for i in vetor:
  if i == x:
    cont+=1

print(f'O número n = {x} aparece {cont} Vezes no Vetor')
```

### Resolução 17

```python
lista1 = []
lista2 = []
produto = []
# gerando uma lista aleatoria
for c in range(5):
  lista1.append(random.randint(0,10))
  lista2.append(random.randint(0,10))

# produto
if len(lista1) == len(lista2):
  for c in range(0,len(lista1)):
      produto.append(lista1[c]*lista2[c])

  print(f'Lista_A :{lista1}\nLista_B:{lista2}\nProduto:{produto}')

else:
  print('Impossivel fazer operação : Listas com tamanhos diferentes')
```

### Resolução 18

```python
numero = int(input('Entre com um valor inteiro entre(0,4000):'))

arabico = [1000, 900, 500, 400, 100, 90, 50, 40, 10, 9, 5, 4, 1]
romano = ['M', 'CM', 'D', 'CD','C', 'XC','L','XL','X','IX','V','IV','I']
num_romano = []

for i in range(len(arabico)):
    alg = int(numero / arabico[i])
    num_romano.append(romano[i] * alg)
    numero -= arabico[i] * alg

result = ''
for roman in num_romano:
  result += roman

print(result)
```

### Resolução 19

```python
import random
cont = 0
vetor = []
for c in range(40):
  vetor.append(random.randint(0,10))

for i in vetor:
  if i%2 == 0:
    cont+=1

print(f'O Vetor:{vetor} \nTem {cont} números Pares')
```
