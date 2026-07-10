# _Resoluções dos Exercicios_

1. Programa Python para verificar se um número é positivo.

```python
numero = float(input('Digite um número: '))
if numero >= 0:
    result = f'O numero {numero} Positivo'
else:
    result = f'O numero {numero} é negativo'

print(result)
```

2. Programa Python para verificar se um número é par.

```python
numero = float(input('Digite um número: '))

if (numero % 2) == 0:
    result = f'O Numero {numero} é Par!'

else:
    result = f'O Numero {numero} impar!'

print(result)
```

3. Faça um Programa que peça dois números e imprima o maior deles. Caso sejam iguais nada deverá ser exibido.

```python
n1 = float(input('Digite um número: '))
n2 = float(input('Digite outro número: '))

if n1 > n2:
    result = f'O número {n1} é Maior que {n2}'

elif n1 == n2:
    result = ' '
else:
    result = f'O número {n2} é Maior que {n1}'

print(result)
```

4. Faça um Programa que verifique se uma letra digitada é "F" ou "M". Conforme a letra escrever: F - Feminino, M – Masculino

```python
sexo = str(input('Digite (F) para Feminino e (M) para Masculino: '.upper()))

if sexo.upper() == 'F':
    print('Feminino')

elif sexo.upper() == 'M':
    print('Masculino')

else:
    print()
```

5. Faça um programa que leia um nome de usuário e a sua senha e não aceite a senha igual ao nome do usuário, mostrando uma mensagem de erro. 

```python
nome = input('Digite o nome de usario: ')
senha = input('Digite a senha: ')

if nome.upper() == senha.upper():
  result = 'Erro, A sua senha não pode ser a mesma do nome de usuario!'

else:
    result = f'Usuario cadastrado com sucesso'

print(result)
```

6. Faça um programa para a leitura de duas notas parciais de um aluno. O programa deve calcular a média alcançada por aluno e apresentar:
        
        ◦ A mensagem "Aprovado", se a média alcançada for maior ou igual a sete;
        ◦ A mensagem "Reprovado", se a média for menor do que sete;

```python
nota1 = float(input('Digite a primeira nota: '))
nota2 = float(input('Digite a segunda nota: '))

media = (nota1 + nota2) / 2

if media >= 7:
    print(f'Você teve a Média igual a {media}')
    print('Parabens, você foi Aprovado!!!')

else:
    print(f'Você teve a Média igual a {media}')
    print('Eu lamento dizer, você foi Reprovado!')
```

7. Uma empresa resolveu dar um aumento de salário aos seus colaboradores e deseja te contratar para desenvolver o programa que calculará os reajustes. O programa deve receber, via teclado, o salário de um colaborador. O percentual de reajuste é dado segundo os critérios abaixo:
        ◦ salários até R$ 1500,00 (incluindo) : aumento de 20%
        ◦ salários entre R$ 1500,01 e R$ 2700,00 : aumento de 15%
        ◦ salários entre R$ 2700,01 e R$ 3500,00 : aumento de 10%
        ◦ salários de R$ 3500,01 em diante : aumento de 8% 
	Após o cálculo do reajuste, informe na tela:
        ◦ o salário antes do reajuste;
        ◦ o percentual de reajuste aplicado;
        ◦ o valor do aumento;
        ◦ o novo salário, após o reajuste.

```python
salario = float(input('Entre com o salário:'))

salario_pos = 0
percentual = 0
valor_aumento = 0

if salario <= 1500:
  percentual = 20/100
  valor_aumento = salario*percentual
  salario_pos = salario + valor_aumento

elif 1500.1 < salario <= 2700:
  percentual = 15/100
  valor_aumento = salario*percentual
  salario_pos = salario + valor_aumento

elif 2700.1 < salario <= 3500:
  percentual = 10/100
  valor_aumento = salario*percentual
  salario_pos = salario + valor_aumento

elif 3500.1 < salario :
  percentual = 8/100
  valor_aumento = salario*percentual
  salario_pos = salario + valor_aumento

print(f'''
◦ o salário antes do reajuste : {salario}
◦ o percentual de reajuste aplicado : {percentual}
◦ o valor do aumento : {valor_aumento}
◦ o novo salário, após o reajuste : {salario_pos}
''')

```

8. Faça um programa que lê as duas notas parciais obtidas por um aluno numa disciplina ao longo de um semestre, e calcule a sua média. A atribuição de conceitos obedece à tabela abaixo:
  
       Média de Aproveitamento           Conceito
       Entre 9.0 e 10.0        	         A
       Entre 7.5 e 8.9        	          B
       Entre 6.0 e 7.4         	         C
       Entre 4.0 e 5.9         	         D
       Entre 3.9  e zero        	        E
O algoritmo deve mostrar as notas, a média, o conceito correspondente e a mensagem “APROVADO” se o conceito for A, B ou C ou “REPROVADO” se o conceito for D ou E.

```python
nota1 = float(input('Digite a primeira nota: '))
nota2 = float(input('Digite a segunda nota: '))

media = (nota1 + nota2) / 2

if 9.0 <= media <= 10.0:
    result = f'Sua média no semestre foi de {media}, você ficou com A e foi APROVADO!'

elif 7.5 <= media <= 8.9:
    result = f'Sua média no semestre foi de {media}, você ficou com B e foi APROVADO!'

elif 6.0 <= media <= 7.4:
    result = f'Sua média no semestre foi de {media}, você ficou com C e foi APROVADO!'

elif 4.0 <= media <= 5.6:
    result = f'Sua média no semestre foi de {media}, você ficou com D e foi REPROVADO!'
else:
    result = f'Sua média no semestre foi de {media}, você ficou com E e foi REPROVADO!'

print(result)
```

9. Faça um programa que liste para o usuário um menu com quatro opções, sendo cada uma referente à uma operação matemática básica. Após o usuário ter escolhido a opção, leia dois valores e realize a operação selecionada.

```python
n1 = float(input('ENTRE COM O PRIMEIRO NÚMERO:'))
n2 = float(input('ENTRE COM O SEGUNDO NÚMERO:'))
n = int(input('''
Entre com uma opção :
[1] - SOMA (+)
[2] - SUBTRAÇÃO (-)
[3] - DIVISÃO (X)
[4] - MULTIPLICAÇÃO (/)
'''))

result = None

if n == 1:
  result = n1+n2

elif n == 2 :
  result = n1-n2

elif n == 3 :
  result = n1*n2

elif n == 4 :
  result = n1/n2

else:
  print('ESCOLHA UMA OPÇAO VALIDA !!!')

print(f'O resultado da operação é {result}'.upper())
```

10. Desenvolva um algoritmo que leia três números e determine o maior e o menor.

```python
n1 = float(input('Entre com o primeiro numero:'))
n2 = float(input('Entre com o segundo numero:'))
n3 = float(input('Entre com o terceiro numero:'))

maior = None
menor = None

# primeiro
maior = n1
menor = n1

# segundo
if n2 > maior:
  maior = n2

if n2 < menor :
  menor = n2

# terceiro
if n3 > maior:
  maior = n3

if n3 < menor :
  menor = n3

print(f'O maior é {maior}')
print(f'O menor é {menor}')
```

11. Desenvolva um algoritmo que determine, utilizando um menu, à área de um quadrado ou de um retângulo, de acordo com a escolha do usuário.

```python
n = int(input('Entre com área desejada : [1] -  Quadrado [2] - Retângulo :'))

if n == 1:
   lado = float(input('Entre com o Lado do Quadrado:'))
   area_quadrado = lado*lado
   print(f'Área:{area_quadrado}')

if n == 2:
  comprimento = float(input('Entre com o Comprimento do Retângulo :'))
  largura = float(input('Entre com a Largura do Retângulo :'))
  area_reatangulo = comprimento*largura
  print(f'Área:{area_reatangulo}')
```

12. Desenvolva um algoritmo que determine, utilizando um menu, o volume de um cubo, de um paralelepípedo e de uma esfera, de acordo com a escolha do usuário.

```python
n = int(input('''
Entre com uma opção :
[1] cubo
[2] Paralelepípado
[3] Esfera
'''))

if n == 1 :
  n1 = float(input('entre com a aresta do cubo: '))
  volume = n1**3
  print(f'meu cubo tem volume de {volume} m³')

elif n == 2 :
  n1 = float(input('entre com a base: '))
  n2 = float(input('entre com a largura: '))
  n3 = float(input('entre com a altura: '))
  volume = n1 * n2 *n3
  print(f'meu paralelepípado tem volume area de {volume} m³')

elif n == 3:
  n1 = float(input('entre com o valor do raio: '))
  volume = (4/3)*(3.14*(n1**3))
  print(f'minha esfera tem volume de {volume:.2f} m³')

else:
  print('Entre com um valor valido')
```

13. Desenvolva um algoritmo que utilizando a estrutura if-else, leia três números reais e determine se formam um triângulo. 
DICA : Três lados formam um triângulo quando a soma de quaisquer dois lados for maior que o terceiro;

```python
a = float(input('Entre com o Primeiro Lado: '))
b = float(input('Entre com o Segundo Lado: '))
c = float(input('Entre com o Terceiro Lado: '))

if a < b + c and b < a + c and c < a + b :
  print('Triângulo Existe')

else:
  print('Esses lados não formam um triângulo')
```

14. Faça um Programa que peça os 3 lados de um triângulo. O programa deverá informar se os valores podem ser um triângulo. Indique, caso os lados formem um triângulo, se o mesmo é: equilátero, isósceles ou escaleno.
Dicas:
        ◦ Três lados formam um triângulo quando a soma de quaisquer dois lados for maior que o terceiro;
        ◦ Triângulo Equilátero: três lados iguais;
        ◦ Triângulo Isósceles: quaisquer dois lados iguais;
        ◦ Triângulo Escaleno: três lados diferentes;

```python
a = float(input('Primeiro lado: '))
b = float(input('Segundo  lado: '))
c = float(input('Terceiro lado: '))

if (a + b < c) or (a + c < b) or (b + c < a):
  print('Nao é um triangulo')

elif (a == b == c) :
  print('Equilatero')

elif (a==b) or (a==c) or (b==c):
  print('Isósceles')

else:
  print('Escaleno')
```

15. Faça um programa que calcule as raízes de uma equação do segundo grau, na forma ax2 + bx + c. O programa deverá pedir os valores de a, b e c e fazer as consistências, informando ao usuário nas seguintes situações:
        
        ◦ Se o usuário informar o valor de a igual a zero, a equação não é do segundo grau e o programa não deve fazer pedir os demais valores, sendo encerrado;
        
        ◦ Se o delta calculado for negativo, a equação não possui raízes reais. Informe ao usuário e encerre o programa;
        
        ◦ Se o delta calculado for igual a zero a equação possui apenas uma raiz real; informe-a ao usuário;
        
        ◦ Se o delta for positivo, a equação possui duas raízes reais; informe-as ao usuário;

```python
a = float(input('Entre com o valor de a:'))
if a == 0:
  print('Essa eq não é do segundo grau')
else:
  b = float(input('Entre com o valor de b:'))
  c = float(input('Entre com o valor de c:'))
  delta = b**2 - 4*a*c

  if delta < 0:
    print('Não existe raizes reais')

  elif delta == 0 :
    print('Só tem um araiz real')

  else:
    print('Essa eq tem duas raizes reais')
```

16. Faça um Programa que peça um número correspondente a um determinado ano e em seguida informe se este ano é ou não bissexto.
        ◦  São bissextos todos os anos múltiplos de 400, p.ex: 1600, 2000, 2400, 2800...
        ◦ São bissextos todos os múltiplos de 4, exceto se for múltiplo de 100 mas não de 400, p.ex: 1996, 2000, 2004, 2008, 2012, 2016, 2020...

```python
ano = int(input('Entre com o Ano: '))
if (ano%4==0 and ano%100!=0) or (ano%400==0):
    result = 'Bissexto'
else:
    result = 'Não é bissexto'
```