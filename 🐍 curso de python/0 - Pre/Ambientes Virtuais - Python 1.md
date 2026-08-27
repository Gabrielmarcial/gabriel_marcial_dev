

Tags : [[Python]]  | [[Ambiente Virtuais]] | 



--- 
# AMBIENTE VIRTUAL


### Criando Ambientes virtuais

- [criando-ambientes-virtuais](https://www.treinaweb.com.br/blog/criando-ambientes-virtuais-para-projetos-python-com-o-virtualenv/)
- [Ambiente virtual Python no Windows (usando venv e VS Code)](https://www.youtube.com/watch?v=m1TYpvIYm74)

### Linux:

**instalando o virtualenv:**

```python
sudo apt-get install python3-venv
```

**Criando ambiente virtual:**

```python
python3 -m venv venv
```

**Ativando o Ambiente:**

```python
source venv/bin/activate
```

**Desativando o Ambiente:**

```python
 deactiva
```

**Para instalar Pacotes:**

```python
 pip3 install <nome do pacote>
```

### windows :

**instalando o venv:**

```python
pip install venv
```

**Criando ambiente virtual:**

```python
python -m venv venv
```

**Ativando o Ambiente:**

```python
cmd
.\venv\Scripts\Activate.bat
```

**Desativando o Ambiente:**

```python
deactivate
```

**Para instalar Pacotes:**

```python
pip install <nome do pacote>
```

## Requirements:

**Verificando oque está instalado:**

```python
pip freeze
```

**Salvando as bibliotecas instaladas:**

```python
pip freeze > requirements.txt
```

**Instalando :**

```python
pip install -r requirements.txt
```

```python
pip freeze > requirements.txt
```