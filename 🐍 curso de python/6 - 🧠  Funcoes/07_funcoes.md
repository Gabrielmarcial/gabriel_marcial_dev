# Exercicios : Funções


## Questões

### Questão 1

Crie uma função pot que receba dois números(base e expoente) e calcule a potência.

### Questão 2

Crie uma função __par_impar__ que verifique se um numero n é par ou Impa.

### Questão 3

Crie uma função determinar o maior numero de um vetor com n valores:

### Questão 4

Escreva um programa em python para converter números escritos em algarismos romanos (menores que 4000) para arábicos.(uerj)
- [Conversão de Números Romanos](https://wiki.python.org.br/NumerosRomanos)

### Questão 5

Escreva uma função fatoracao_primo(num) que decompõe um numero em fatores primos.

- Exemplo: 56475768481089153821883027 = ['3^33', '7^4', '11^4', '17^2']

### Questão 6

Desenvolva um programa que apresente um menu com as opções abaixo, e execute a função associada com cada opção.

Menu:
- Cırculo : Cálculo de Circunferência e Área
- Quadrado : Cálculo de Perımetro e Area
- Vetor : Leitura e apresentação de dados de um vetor, menor e maior elemento
Sair

### Questão 7

Crie um programa que tenha uma função fatorial() que será mostrado na tela o processo de cálculo do fatorial.

### Questão 8

Implemente a função area_triangulo(matriz). O parâmetro matriz é uma matriz 3x2
que contém as coordenadas x e y de pontos do triângulo. Utilize fórmula de Heron para
calcular a área.
Onde s é o semiperímetro do triângulo e a, b e c são os comprimento dos lados do
triângulo.

---

## Resoluções

### Resolução 1

```python
def pot(base:int,exp:int):

  num = base**exp

  return num

print(pot(2,4))
print(pot(3,5))
```

### Resolução 2

```python
def par_impar(n:int)-> str:
  if n%2 == 0:
    valor = 'Par'
  else :
    valor = 'Impar'

  return valor

print(par_impar(2))
print(par_impar(4))
print(par_impar(7))
print(par_impar(123467))
```

### Resolução 3

```python
def maior(vet:list):
  maior = vet[0]
  for valor in vet:
    if valor > maior:
      maior = valor
  print(vet)
  return maior


import random
vetor = []
for c in range(0,100):
  vetor.append(random.randint(0,1000))


maior(vetor)
```

### Resolução 4

```python
def romano(numero):
     '''o a variavel numero
        deve ser um valor entre 0 e 40000 '''

     arabico = [1000, 900, 500, 400, 100, 90, 50, 40, 10, 9, 5, 4, 1]
     romano = ['M', 'CM', 'D', 'CD','C', 'XC','L','XL','X','IX','V','IV','I']
     num_romano = []

     for i in range(len(arabico)):
         alg = int(numero / arabico[i])
         num_romano.append(romano[i] * alg)
         numero -= arabico[i] * alg
     return ''.join(num_romano)

print(romano(15))
print(romano(10))
print(romano(3050))
```

### Resolução 5

```python
def fatoracao_primo(n):
  num = n
  lista = []
  divisor =  2
  while n != 1:
      # conta o tamanho do expoente
      exp = 0;
      while n%divisor == 0:
          n = n / divisor;
          exp = exp + 1;

      # imprime a multiplicade do fator
      if exp != 0:
          lista.append(f"{divisor}^{exp}")

      divisor +=  1
  return f"{num}={lista}"

print(fatoracao_primo(2224))
print(fatoracao_primo(258))
print(fatoracao_primo(87))
```

### Resolução 6

```python
def circulo(r):
    comprimento_circulo = 2 * (3.14) * r
    area = (3.14) * (r ** 2)
    print(f'O comprimento do Circulo de Raio {r} m é {comprimento_circulo} m e sua área é {area} m²')


def quadrado(l):
    perimetro = 4 * l
    area = l ** 2
    print(f'O Perimetro do Quadrado de lado {l} m é {perimetro} m e sua área é {area} m²')


def valores():
    v = []
    n = int(input('quantos valores deseja ?'))
    for c in range(0, n):
        num = input(f'numero {c+1} : ?')
        v.append(num)
    max = ''
    for valor in v:
        if max == '':
            max = valor
        elif valor > max:
            max = valor
    print(f'O valor máximo é {max}.')
    min = ''
    for valor in v:
        if min == '':
            min = valor
        elif valor < min:
            min = valor
    print(f'O valor mínimo é {min}.')


n = 0
while n != 4:
    print("""
        Menu - Elementos da Prova 3

        Escolha uma opção :
        [1] - Cálculo da Circunferência e da Área de um Circulo
        [2] - Cálculo do Perımetro e da Área de um Quadrado
        [3] - O mair e menor valor de uma lista de valores
        [4] - Sair

      """)
    n = int(input('Qual a opção desejada:'))

    if n == 1:
        raio = float(input('Entre com o valor do raio :'))
        circulo(raio)

    if n == 2:
        lado = float(input('Entre com o Valor do lado:'))
        quadrado(lado)

    if n ==3:
        valores()
```

### Resolução 7

```python
def fatorial(numero):
  fat = 1
  proces = ''

  for c in range(1,numero+1):
    fat = fat*c
    if c == numero:
      proces += f'{c}='
    else :
      proces += f'{c}x'

  result =  f'{proces} {fat}'

  return result

print(fatorial(8))
print(fatorial(10))
```

### Resolução 8

```python
def semi_perimetro(matriz):
  ''' Dado uma matriz = [[x1,y1],[x2,y2],[x3,y3]] com os pontos de um triangulo
      a = (((x1-x2)**2)+((y1-y2)**2))**(1/2)
      b = (((x1-x3)**2)+((y1-y3)**2))**(1/2)
      c = (((x2-x3)**2)+((y2-y3)**2))**(1/2)
      e retorna o semi - perimetro s e os lados
  '''

  a = (((matriz[0][0]-matriz[1][0])**2)+((matriz[0][1]-matriz[1][1])**2))**(1/2)
  b = (((matriz[0][0]-matriz[2][0])**2)+((matriz[0][1]-matriz[2][1])**2))**(1/2)
  c = (((matriz[1][0]-matriz[2][0])**2)+((matriz[1][1]-matriz[2][1])**2))**(1/2)

  s = (a+b+c)/2

  return s,a,b,c


def area_triangulo(m):
    '''Função que retorna a área de um triangulo com  a formula de Heron
      area = (s * (s - a) * (s - b) * (s - c))**(1/2)
    '''
    s,l1,l2,l3 = semi_perimetro(m)

    area = (s*(s - l1)*(s - l2)*(s - l3))**(1/2)

    return area




tri1 = [[3, 3], [6, 3],[3, 5]]
tri2 = [[0, 0], [8, 0],[0, 8]]


print(area_triangulo(tri1))
print(area_triangulo(tri2))
```
