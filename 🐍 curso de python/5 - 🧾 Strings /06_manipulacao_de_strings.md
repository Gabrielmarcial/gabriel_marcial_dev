# Exercicios : Manipulação de strings


## Questões

### Questão 1

Escreva um Programa onde você entre com um nome e ele retorne a primeira letra em maiúscula e o restante em minúscula.

### Questão 2

Crie um programa em que o usuário digite uma palavra (ou uma frase) e esse retorne apenas as vogais e a quantidade de vogais da frase ou palavra.

### Questão 3

Crie um programa em que o usuário digite seu nome completo e o programa imprima seu último sobrenome, o número de letras do sobrenome e as vogais.

### Questão 4

Crie um programa em que seja lido a palavra "datamarte" e imprima apenas as letras que não se repetem

### Questão 5

Escreva um programa que Leia uma frase e imprima o total de vogais, o total de brancos e o total do resto.

### Questão 6

Um palíndromo é uma cadeia que pode ser lida de frente para trás e de trás parafrente.


Implemente um algoritmo palindromo. O programa deverá retornar True se for um palíndromo e False caso contrário.

---

## Resoluções

### Resolução 1

```python
n = str(input('Qual seu nome:'))
n = n.strip()
v =  [ ]

for c in range(0,len(n)):
    v.append(n[c])

for j in range(0,len(v)-1):

    if j == 0 :
        v[0] = v[0].upper()
        for k in range(j+1,len(v)):
            v[k] = v[k].lower()

    if v[j] == " ":
       v[j+1] = v[j+1].upper()


for i in range(0,len(v)):
    print(v[i], end= " " )
```

### Resolução 2

```python
frase = str(input('Entre com o texto: '))
vogais = ['a','e','i','o','u']
cont = 0
for letra in frase:
  if letra in vogais:
    cont+=1

print(cont)
```

### Resolução 3

```python
nome = str(input('Entre com seu nome: '))
nome = nome.strip()
vetor = nome.split(' ')

ultimo_sobrenome = vetor[len(vetor)-1]

# vogais
vogais = ['a','e','i','o','u']
cont = 0
for letra in ultimo_sobrenome:
  if letra in vogais:
    cont+=1

print(f'Último nome:{ultimo_sobrenome}')
print(f'Letras: {len(ultimo_sobrenome)} , Vogais: {cont}')
```

### Resolução 4

```python
frase = str(input('Entre com a Frase: '))

letras = []

for c in range(0,len(frase)):
  if c == 0:
    letras.append(frase[c])

  if frase[c] not in letras:
      letras.append(frase[c])

# letras q não se repetem
letras_n = []

for letra in letras:
  cont = 0
  for l in frase :
    if letra == l :
      cont += 1
  if cont == 1 :
    letras_n.append(letra)

print(letras_n)
```

### Resolução 5

```python
frase = str(input('Entre com a Frase: '))

vogais = ['a','e','i','o','u']
cont_vogais = 0
cont_branco = 0

for letra in frase:
  if letra in vogais:
    cont_vogais +=1
  if letra == " ":
    cont_branco += 1
resto = len(frase)-(cont_branco+cont_vogais)
print(f'Vogias: {cont_vogais}\nEspaços em Branco: {cont_branco}\nOutros:{resto}')
```

### Resolução 6

```python
frase = str(input('Entre com uma palavra:'))
frase = frase.strip().upper()
termos = frase.split()
junto = ''.join(termos)
tras_para_frente=''

for letra in range((len(junto)-1),-1,-1):
  tras_para_frente+= junto[letra]

if tras_para_frente == junto:
  print('True')

else :
  print('False')
```
