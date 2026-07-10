
# Redução de dimensionalidade aplicada a imagens multiespectrais


**Autor:** Gabriel Marcial de Paiva¹

¹ Instituto de Computação — Universidade Federal Fluminense (UFF), Trabalho de Álgebra Linear Computacional 26.1

---

### Resumo

A segmentação de imagens multiespectrais constitui um importante problema de Álgebra Linear aplicada, uma vez que cada imagem pode ser representada por uma matriz cujas linhas correspondem aos pixels e cujas colunas representam as bandas espectrais. Devido à elevada dimensionalidade e à presença de redundâncias decorrentes da correlação entre bandas, torna-se necessária a utilização de técnicas de redução de dimensionalidade capazes de preservar as informações mais relevantes dos dados. Neste trabalho, emprega-se a Decomposição em Valores Singulares (SVD) como ferramenta para obter uma representação compacta das imagens, identificando e preservando as direções de maior variabilidade espectral e descartando componentes pouco informativas, como ruídos e redundâncias. A partir da truncagem da decomposição nos *k* maiores valores singulares, os pixels são projetados em um espaço de menor dimensão por meio de uma aproximação de baixo posto, reduzindo o custo computacional e mantendo a maior parte da informação espectral original. Em seguida, a representação reduzida é utilizada como entrada para um algoritmo de segmentação, responsável por agrupar os pixels de acordo com suas características espectrais. Esse processo permite a identificação e a diferenciação de objetos presentes na imagem, como edifícios, ruas e áreas vegetadas, podendo ser empregado tanto para a determinação de suas localizações quanto para a geração de dados de treinamento destinados a modelos de redes neurais.

**Palavras-chave:** SVD, k-means, segmentação, Sensoriamento-remoto.

---

## 1. Introdução

A segmentação de imagens multiespectrais (Figura 1) (em que cada pixel é caracterizado por um vetor de intensidades ao longo de múltiplas bandas espectrais) é, em sua essência, um problema de álgebra linear aplicada. Cada imagem com n bandas e m pixels pode ser representada como uma matriz $A\in \mathbb{R}^{m \times n}$, na qual cada linha corresponde a um pixel e cada coluna a uma banda espectral. Esse tipo de representação, embora simples, frequentemente carrega redundância entre bandas (correlação espectral), o que motiva o uso de técnicas de redução de dimensionalidade antes de qualquer etapa de classificação ou agrupamento.

**Figura 1** — Exemplo - imagem multiespectral.

![Exemplo de imagem multiespectral](/imagens/img_mult.png)

*Fonte: Autor.*

Neste trabalho, utilizaremos a Decomposição em Valores Singulares (SVD) para tratar um problema de redução de dimensionalidade, uma das fatorações mais importantes da Álgebra Linear. A SVD expressa uma matriz $A$ como o produto $A = U\Sigma V^{T}$, em que $U$ e $V$ são matrizes ortogonais cujas colunas formam bases para os espaços dos pixels e das bandas, respectivamente, enquanto $\Sigma$ é uma matriz diagonal que contém os valores singulares, grandezas que medem a magnitude (ou energia) de cada direção capturada pela decomposição. Geometricamente, a SVD identifica os eixos ortogonais ao longo dos quais os dados apresentam maior variabilidade, ordenando-os de acordo com sua importância, em ordem decrescente.

O objetivo é aplicar a SVD neste projeto para obter uma representação compacta de cada pixel, preservando as direções de maior energia espectral e descartando componentes pouco informativos, como ruídos e redundâncias entre as bandas. Ao truncar a decomposição nos $k$ primeiros valores singulares e calcular $U_k\Sigma_k$, projeta-se cada pixel em um espaço de dimensão reduzida, mantendo a maior parte da informação espectral relevante por meio de uma aproximação de baixo posto. Essa etapa reduz o custo computacional do processo de segmentação, ao mesmo tempo em que preserva as características mais importantes da matriz original.

A representação reduzida obtida por meio da SVD é utilizada como entrada para um algoritmo de segmentação, que particiona os pixels em diferentes grupos. O objetivo dessa segmentação é diferenciar e identificar objetos, como edifícios, ruas e árvores, a fim de determinar suas localizações ou gerar dados de treinamento para um modelo de rede neural.

## 2. Fundamentação teórica

### 2.1 Autovalores, autovetores e decomposição espectral

Para uma matriz $A \in K^{n \times n}$, um vetor não nulo $v$ associado a um autovalor $\lambda$ satisfaz a equação $Av=\lambda v$ [Lopes, 2026a]. Quando $A$ possui $n$ autovetores linearmente independentes, é possível organizá-los nas colunas de uma matriz $V$, enquanto seus respectivos autovalores são dispostos na diagonal de uma matriz $\Lambda$. Dessa forma, obtém-se a relação

$$AV=V\Lambda.$$

Como $V$ é inversível, pode-se escrever a *decomposição espectral* como:

$$A=V\Lambda V^{-1}.$$

As matrizes que admitem essa fatoração são chamadas de *diagonalizáveis*, pois são semelhantes a uma matriz diagonal.

No caso das matrizes reais simétricas, pode-se demonstrar que toda matriz $A \in \mathbb{R}^{n \times n}$ simétrica possui apenas autovalores reais e admite uma base ortonormal de autovetores. Consequentemente, a matriz $V$, formada por esses autovetores, é ortogonal, de modo que $V^{-1}=V^{T}$. Assim, a decomposição espectral assume a forma:

$$A = V\Lambda V^{T} = \sum_{j=0}^{n-1} \lambda_j v_j v_j^{T}.$$

Essa forma da decomposição espectral, com produtos externos ponderados por $\lambda$, é a ideia principal que conecta a decomposição espectral com aproximações de baixo posto, truncando essa soma nos $k$ primeiros valores de $\lambda_j$. No entanto, isso vale somente para matrizes quadradas simétricas.

Para generalizar esse problema para qualquer $A \in \mathbb{R}^{m \times n}$, e não apenas para matrizes quadradas, buscamos uma aproximação $\tilde{A}$ de posto $k$ que minimize $\|A-\tilde{A}\|_F^2$. Para o caso de posto $1$, o problema se resume a encontrar um vetor unitário $v$ que maximize $\|Av\|^2$. Esse valor está associado ao maior autovalor de $A^{T}A$, que é uma matriz simétrica positiva definida. Definindo $\sigma=\|Av\|$ e $u=Av/\sigma$, a melhor aproximação de posto $1$ é $\tilde{A}=\sigma uv^{T}$.

Generalizando para posto $k$, os $k$ vetores $v_j$ que resolvem o problema são os $k$ primeiros autovetores de $A^{T}A$, ordenados pelos maiores autovalores. Com isso, obtemos a melhor aproximação dada por $\tilde{A}=U\Sigma V^{T}$.

### 2.2 Decomposição em Valores Singulares (SVD)

A Decomposição em Valores Singulares (SVD) é fundamentada no Teorema de Eckart–Young [Lopes, 2026b], que estabelece que a melhor aproximação $\tilde{A}$ de posto $k < \operatorname{rank}(A)$ para uma matriz $A \in \mathbb{R}^{m \times n}$ é aquela que minimiza a norma de Frobenius do erro, ou seja, $\|A-\tilde{A}\|_F^2$.

$$A \approx \tilde{A} = U\Sigma V^{T},$$

onde

$$U \in \mathbb{R}^{m \times k}, \qquad \Sigma \in \mathbb{R}^{k \times k}, \qquad V^{T} \in \mathbb{R}^{k \times n},$$

com $\Sigma$ sendo uma matriz diagonal.

Além disso:

1. $V$ é formado pelos $k$ primeiros autovetores de $A^{T}A$, correspondentes aos maiores autovalores.

2. A matriz dos valores singulares é dada por

$$\Sigma = \operatorname{diag}\left(\|Av_0\|, \|Av_1\|, \ldots, \|Av_{k-1}\|\right).$$

3. A matriz dos vetores singulares à esquerda é calculada por

$$U = AV\Sigma^{-1}.$$

A SVD é, portanto, uma extensão natural da decomposição espectral. Em vez de diagonalizar diretamente a matriz $A$, ela aplica o Teorema Espectral à matriz simétrica $A^{T}A$, contornando as restrições de que $A$ seja simétrica e quadrada. Dessa forma, a Decomposição em Valores Singulares pode ser aplicada a qualquer matriz $A \in \mathbb{R}^{m \times n}$.

Quando consideramos uma decomposição em que $k=\operatorname{rank}(A)$, obtemos a chamada *SVD econômica*. Nessa decomposição, a matriz $A$ é representada exatamente, porém utilizando apenas os vetores singulares associados aos valores singulares não nulos, reduzindo a quantidade de informações armazenadas em relação à SVD completa.

Diferentemente da SVD completa, em que

$$A=\tilde{U}\tilde{\Sigma}\tilde{V}^{T},$$

as matrizes $\tilde{U}$ e $\tilde{V}$ contêm bases ortonormais completas de $\mathbb{R}^{m}$ e $\mathbb{R}^{n}$, respectivamente. Na SVD econômica, são mantidas apenas as colunas correspondentes aos valores singulares não nulos, reduzindo as dimensões das matrizes sem perda de informação.

## 3. Metodologia

A metodologia deste trabalho será dividida em quatro etapas. Na primeira etapa, as imagens multiespectrais serão lidas e suas bandas serão convertidas para um formato matricial. Na segunda etapa, com as matrizes já construídas, será aplicada a Decomposição em Valores Singulares (SVD) para reduzir a dimensionalidade dos dados. Na terceira etapa, após a redução da dimensionalidade, os pixels serão classificados por meio de um algoritmo de clusterização. Por fim, na quarta etapa, os resultados obtidos serão avaliados.

### 3.1 Representação Matricial dos dados

Neste trabalho serão utilizadas imagens aéreas do município do Rio de Janeiro, disponibilizadas pelo Instituto Pereira Passos (IPP). Essas imagens possuem o formato ilustrado na Figura 2, sendo compostas por três bandas espectrais convencionais (RGB) e uma banda adicional no infravermelho próximo (NIR).

**Figura 2** — Reorganização dos dados.

![Reorganização dos dados](/imagens/reshape.png)

*Fonte: Autor.*

Após a leitura, cada imagem é representada por um arranjo tridimensional de dimensões $n_b \times n_l \times n_c$, em que $n_b$ representa o número de bandas, $n_l$ o número de linhas e $n_c$ o número de colunas. Para aplicar a Decomposição em Valores Singulares (SVD), é necessário reorganizar esses dados por meio de uma operação de *reshape*, de forma que cada pixel seja tratado como uma observação independente. Assim, parte-se de um arranjo $I \in \mathbb{R}^{n_b \times n_l \times n_c}$ para obter uma matriz $A \in \mathbb{R}^{m \times n_b}$, em que $m=n_l \cdot n_c$.

Caso essa conversão não fosse realizada, seria necessário separar cada banda e processá-las individualmente. No contexto do sensoriamento remoto, entretanto, é comum organizar os dados nesse formato matricial, pois ele preserva as informações espectrais de cada pixel e possibilita a aplicação de técnicas de redução de dimensionalidade e classificação multiespectral.

### 3.2 Redução de dimensionalidade via SVD

Na etapa de redução de dimensionalidade, utiliza-se a matriz de pixels $A \in \mathbb{R}^{m \times n_b}$, sobre a qual é aplicada a Decomposição em Valores Singulares (SVD), dada por $A=U\Sigma V^{T}$, por meio da função `numpy.linalg.svd` da biblioteca NumPy. Após a decomposição, são avaliados os $k$ primeiros componentes principais, com $k < n_b$. A representação reduzida de cada pixel é obtida por

$$X_{\mathrm{red}} = U_k\Sigma_k \in \mathbb{R}^{m \times k},$$

descartando-se a matriz $V^{T}$, uma vez que ela descreve a relação entre as bandas espectrais, e não entre os pixels. Dessa forma, $X_{\mathrm{red}}$ preserva a maior parte da variância espectral presente nos dados para a dimensão $k$ escolhida, funcionando como uma compressão que reduz a redundância entre as bandas e mantém as informações mais relevantes para as etapas subsequentes de processamento.

### 3.3 Agrupamento via K-Means

Sobre $X_{\mathrm{red}}$, aplica-se o algoritmo *k-means*, utilizando a implementação da biblioteca *scikit-learn* (`sklearn.cluster.KMeans`), para particionar os pixels em quatro classes fixas. O algoritmo busca minimizar a soma das distâncias euclidianas quadráticas entre cada ponto e o centróide do cluster ao qual ele pertence. Ao final do processo, obtém-se um vetor de rótulos, que é reorganizado para o formato espacial original da imagem, de dimensões $n_l \times n_c$.

### 3.4 Visualização e interpretação

Por fim, são comparados diferentes valores de $k$ e os tamanhos de suas respectivas reduções de dimensionalidade, com o objetivo de identificar os melhores resultados. O mapa de classes obtido é sobreposto à imagem original para permitir uma inspeção visual da segmentação. Em seguida, cada classe é analisada isoladamente, possibilitando associar cada *cluster* a um tipo de cobertura ou objeto presente no terreno, como vegetação, construções, vias e corpos d'água.

## 4. Resultados

A Tabela 1 mostra que a compressão cresce à medida que o número de componentes ($k$) é reduzido, variando de 0% ($k = 4$) a 75% ($k = 1$). Embora a imagem utilizada neste trabalho seja relativamente pequena, o objetivo é analisar esse problema em um cenário de maior escala, como ocorre em imagens multiespectrais, que frequentemente possuem 13 ou mais bandas espectrais. As Figuras 3, 4 e 5 permitem avaliar se essa compressão preserva as informações relevantes para o processo de segmentação.

**Tabela 1** — Redução do tamanho da imagem em função do número de componentes mantidos.

| Nº de Componentes (K) | Original (MB) | Reduzido (MB) | Mantido (%) | Redução (%) |
|:----------------------:|:--------------:|:---------------:|:-------------:|:--------------:|
| 1 | 22.96 | 5.74  | 25.00  | 75.00 |
| 2 | 22.96 | 11.48 | 50.00  | 50.00 |
| 3 | 22.96 | 17.22 | 75.00  | 25.00 |
| 4 | 22.96 | 22.96 | 100.00 | 0.00  |

A partir de $k = 2$ (Figura 3b, segmentação com K = 2), com uma redução de 50% do tamanho da imagem original, já é possível observar uma melhora significativa na análise visual. As copas das árvores tornam-se mais bem delimitadas, e surgem detalhes mais finos que estavam ausentes para $k = 1$, como a diferenciação entre telhados e vegetação. Esse ganho provavelmente está associado à preservação da banda do infravermelho próximo (NIR), que é altamente sensível à presença de vegetação e corpos d'água.

Entre $k = 2$, $k = 3$ e $k = 4$, as diferenças visuais são pequenas. Essa observação sugere que a maior parte da informação (ou energia espectral) da imagem está concentrada nos dois primeiros componentes principais. Embora $k = 4$ preserve todas as características da imagem original e, consequentemente, seja a representação mais completa para a classificação, nota-se que $k = 2$ já constitui uma boa aproximação para tarefas como a identificação de áreas vegetadas, conforme ilustrado nas Figuras 4 e 5.

Esses resultados evidenciam uma aplicação promissora da Decomposição em Valores Singulares (SVD) em problemas de maior escala, envolvendo imagens com dimensões da ordem de gigabytes. A truncagem da SVD para um pequeno número de componentes reduz significativamente o custo computacional do processamento, preservando as informações mais relevantes para a realização da segmentação e de outras análises espectrais.

**Figura 3** — Comparação entre a imagem original e os resultados de classificação.

| Imagem original (RGB) | Segmentação com K = 1 | Segmentação com K = 2 |
|:---:|:---:|:---:|
| ![Original](/imagens/original.png) | ![Segmentação K1](/imagens/segmentacao/segmentacao_k1.png) | ![Segmentação K2](/imagens/segmentacao/segmentacao_k2.png) |

| Segmentação com K = 3 | Segmentação com K = 4 |
|:---:|:---:|
| ![Segmentação K3](/imagens/segmentacao/segmentacao_k3.png) | ![Segmentação K4](/imagens/segmentacao/segmentacao_k4.png) |

**Figura 4** — Comparação entre a imagem original e os resultados de classificação.

| Imagem original (RGB) | Segmentação com K = 1 | Segmentação com K = 2 |
|:---:|:---:|:---:|
| ![Original](/imagens/original.png) | ![Classe K1](/imagens/classe_destacada/class_k1.png) | ![Classe K2](/imagens/classe_destacada/class_k2.png) |

| Segmentação com K = 3 | Segmentação com K = 4 |
|:---:|:---:|
| ![Classe K3](/imagens/classe_destacada/class_k3.png) | ![Classe K4](/imagens/classe_destacada/class_k4.png) |

**Figura 5** — Comparação entre a imagem original e os resultados de classificação.

| Imagem original (RGB) | Segmentação com K = 1 | Segmentação com K = 2 |
|:---:|:---:|:---:|
| ![Original](/imagens/original.png) | ![Classe destacada K1](/imagens/classe_destacada/class_destac_k1.png) | ![Classe destacada K2](/imagens/classe_destacada/class_destc_k2.png) |

| Segmentação com K = 3 | Segmentação com K = 4 |
|:---:|:---:|
| ![Classe destacada K3](/imagens/classe_destacada/class_destac_k3.png) | ![Classe destacada K4](/imagens/classe_destacada/class_destac_k4.png) |

## 5. Conclusão

Este trabalho mostrou que a Decomposição em Valores Singulares (SVD) é uma técnica eficaz de pré-processamento para a segmentação de imagens multiespectrais. Os resultados confirmam a hipótese central de que, com $k = 2$, é possível obter uma redução de 50% dos dados sem perda perceptível de qualidade na segmentação, enquanto $k = 1$ preserva apenas as macroclasses, deixando de representar detalhes como telhados e pequenos corpos d'água. Esses resultados indicam que poucas componentes concentram a maior parte da informação espectral relevante, validando o uso da SVD como uma ferramenta prática para redução de dimensionalidade, inclusive em fluxos modernos de aprendizado de máquina.

As principais limitações deste trabalho estão relacionadas à escolha do valor de $k$, realizada por inspeção visual, sem a utilização de um critério quantitativo. Além disso, o número de clusters foi fixado em quatro classes, sem a realização de experimentos com diferentes valores. Outra análise que poderia ter sido realizada seria a comparação das classificações obtidas para $k = 2$, $k = 3$ e $k = 4$ em nível de pixel, permitindo quantificar as diferenças entre os mapas gerados. Entretanto, essa avaliação não foi possível devido ao tempo disponível para o desenvolvimento do trabalho.

Como trabalhos futuros, sugere-se a seleção automática do valor de $k$ com base na energia acumulada dos valores singulares, bem como a comparação da SVD com outras técnicas de redução de dimensionalidade e diferentes algoritmos de clusterização. Também é recomendável a utilização de imagens de maiores dimensões, tanto em resolução espacial quanto em número de bandas espectrais. Por fim, os resultados da segmentação podem ser validados e corrigidos por um processo manual e utilizados para a construção de conjuntos de dados destinados ao treinamento de modelos de redes neurais voltados à classificação de elementos como rodovias, áreas vegetadas e edificações.

## Código

O código que acompanha este relatório pode ser encontrado neste Google Colab: [link colab](https://colab.research.google.com/drive/1_e83gKZqDCEU6yc-CtPGyuQxlA4TOHG1?usp=sharing)

## Referências

- Lopes, Pedro Cortez Fetter. *Álgebra Linear Computacional: Aulas 19 e 20 — Autovalores e Autovetores*. Universidade Federal Fluminense, 2026. Notas de aula da disciplina Álgebra Linear Computacional.
- Lopes, Pedro Cortez Fetter. *Álgebra Linear Computacional: Aulas 21 e 22 — Decomposição de Valores Singulares*. Universidade Federal Fluminense, 2026. Notas de aula da disciplina Álgebra Linear Computacional.
