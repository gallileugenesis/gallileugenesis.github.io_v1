---
layout: post
title:  "qual lâmpada comprar?"
date:   2022-03-31 
category: ciência de dados
icon: www
keywords: tag1, tag2, tag3
image: lampadas.jpg
preview: 0
---

Imaginem a seguinte situação: uma empresa está se preparando para comprar uma grande quantidade de lâmpadas para um de seus novos empreendimentos. 

Essa empresa recebe então os dados do tempo de duração, em horas,  de lâmpadas de dois fabricantes diferentes, A e B, como mostra a tabela abaixo. 

![df.png](https://github.com/gallileugenesis/qual_lampada_comprar/blob/main/figuras/df.png?raw=true,style=centerme)

Ao todo, o banco de dados contém 40 entradas com os respectivos tempos de duração das lâmpadas A e B. 

A questão que se levanta é: qual a melhor opção de compra para a empresa, levando-se em conta somente os dados de tempo de tempo de duração, mostrados acima?

Bem, uma análise estatística do conjunto de dados pode trazer informações valiosas para responder essa questão.  Para realizar essa análise, existem diversas ferramentas, como o tradicional excel, o software R, diversas bibliotecas Python. Nesse exemplo, vamos trabalhar com essa última opção, cujo código está disponível [aqui](https://github.com/gallileugenesis/qual_lampada_comprar). 

Bem, vamos começar com uma descrição estatística básica dos dados:

|       |      A      |      B      |
| :---: | :---------: | :---------: |
| count |  40.000000  |  40.000000  |
| mean  | 909.650000  | 1018.350000 |
|  std  |  94.305165  |  96.901364  |
|  min  | 684.000000  | 819.000000  |
|  25%  | 857.250000  | 949.750000  |
|  50%  | 916.500000  | 1015.500000 |
|  75%  | 971.250000  | 1085.500000 |
|  max  | 1093.000000 | 1230.000000 |

O que esses dados nos dizem? Bom, primeiro, a média de duração da lâmpada A é de 909,65 horas, ao passo que a lâmpada B dura, em média, 1018,35 horas, como também está mostrado na figura abaixo. Isso significa que, para esse conjunto de dados,  as lâmpadas do tipo B duram em média, 12% a mais do que as lâmpadas A.  

![tempo_medio.png](https://github.com/gallileugenesis/qual_lampada_comprar/blob/main/figuras/tempo_medio.png?raw=truestyle=centerme)

Então devemos escolher a lâmpada B, não é? Bem... Não tão depressa. A média é uma medida que pode te enganar em algumas ocasiões. Ela, por si só, embora as vezes deem indicações corretas, não deve embasar jamais suas decisões.

Um outro ponto a se destacar é que os tempos de duração das duas lâmpadas tem desvios padrão bem parecidos, com valores de 94,3 e 96,9, para A e B, respectivamente. Isso equivale a uma diferença de apenas 2%. Ou seja, a variabilidade das medições em torno de suas respectivas médias são semelhantes. 

Sigamos com a análise e olhemos agora para os valores mínimos observados. No caso de A, o menor tempo de duração observado é de 684 horas, enquanto, para B, esse dado foi de 819 horas (quase 20% maior!!). Já para os maiores valores observados, tivemos em A 1093 horas, e em B, 1230 horas (12,5% a mais). Com esses dados podemos calcular a amplitude dos dados, uma medida estatística dada pela diferença entre os valores máximo e mínimo no conjunto de dados. Logo, para esse caso, temos que a amplitude de A é de 409 horas, e a amplitude de B é de 411 horas (4% maior). Percebam que, apesar da grande diferença entre os valores mínimo e máximo observados nos dados conjuntos de dados, suas amplitudes não mostraram uma grande variação. 

Para analisar melhor os quartis, vamos recorrer ao boxplot desses dados.

![boxplot.png](https://github.com/gallileugenesis/qual_lampada_comprar/blob/main/figuras/boxplot.png?raw=truestyle=centerme)

A figura do boxplot ilustra o que já temos discutido com relação a média, desvio padrão, valores máximos e mínimos. Até aqui, todos os indícios nos levam a crer que a Lâmpada B é a melhor opção. Mas, sigamos com a análise.

Pode-se notar que, para a lâmpada A, 25% das amostram tem tempo de duração de no máximo 857 horas (1º quartil), 50% duram até 916 (2º quartil ou mediana) e, por fim, 75% tem duração de até 971 horas (3º quartil). Já para a lâmpada B, esses valores são de 950,1015 e 1085, respectivamente. Ou seja, as estatísticas absolutas da lâmpada B são melhores do que as de A. 

Para finalizar essa análise gráfica, vamos dar uma olhada no histograma dos dados. 

![hist.png](https://github.com/gallileugenesis/qual_lampada_comprar/blob/main/figuras/hist.png?raw=truestyle=centerme)

O que vemos é que o histograma de B está deslocado para a direita, em relação a A, como já indicavam as análises anteriores. Isso indica que a média de duração das lâmpadas desse fabricante é maior. A dispersão dos dados são semelhantes, como já citado. Os dados também seguem uma distribuição aproximadamente normal. 

As  maiores frequências do tempo de duração das lâmpadas do fabricante A estão ente 850 e 900 (10) e 900 e 950 (12) horas. Já no caso das lâmpadas B, ocorrem frequências parecidas entre 900 e 1150 (7 , 8 e 9). 

Bem, até aqui tudo indica que a escolha das lâmpadas do fabricante B seria a opção mais plausível, dadas todas as informações expostas até o momento. No entanto, como lembrou [Nassim Taleb](https://en.wikipedia.org/wiki/Nassim_Nicholas_Taleb) em [Skin in the Game](https://www.amazon.com.br/Skin-Game-Hidden-Asymmetries-English-ebook/dp/B075HYVP7C/ref=sr_1_1?__mk_pt_BR=%C3%85M%C3%85%C5%BD%C3%95%C3%91&crid=23MXAOK3O8NFO&keywords=Skin+in+the+Game&qid=1648564544&s=digital-text&sprefix=%2Cdigital-text%2C244&sr=1-1), essas medidas estatísticas sem intervalos de confiança não dizem muita coisa, uma vez que são estimativas pontuais dos parâmetros populacionais e não nos informam nada sobre a incerteza associada aos seus valores (o quão distante esse valor está verdadeiro parâmetro populacional). 

O intervalo de confiança (IC) é calculado a partir das estatísticas dos dados observados e constitui uma faixa de valores que provavelmente contém um parâmetro populacional (média, mediana, etc) com um determinado nível de confiança. Pode-se entender também o IC como sendo à probabilidade de um parâmetro populacional cair entre um conjunto de valores por uma certa proporção de vezes. Desse modo, os IC medem o grau de incerteza ou certeza em um método de amostragem.

Comumente se usa intervalos de confiança de 99% e 95%.  Por exemplo, quando dizemos que um intervalo de confiança é de 95%, queremos dizer que, se tomarmos um certo número de amostras aleatórias da população, calcularmos o intervalo a cada vez, então o verdadeiro parâmetro populacional analisado estará em 95% desses intervalos.

Quando não conhecemos nada a respeito do comportamento de uma dada população, ou seja, quando não conhecemos os parâmetros populacionais, e dispomos somente das amostras de uma população, como é o caso na maioria das aplicações práticas e também no nosso exemplo a respeito do tempo de duração das lâmpadas, precisamos recorrer a   [Distribuição t de Student](https://pt.wikipedia.org/wiki/Distribuição_t_de_Student) para encontrar o intervalo de confiança. 

Desse modo, para uma população com média $\mu$ e desvio padrão $\sigma$ desconhecidos, um intervalo de confiança, com um nível de confiança $C$, para a média populacional, com base em uma amostra aleatória simples (simple random sample, SRS) de tamanho $n$, é dado por,


$$
IC = \overline{x} \pm t^*\dfrac{s}{\sqrt n}
$$
onde $\overline{x}$ e $s$ são a média e desvio padrão amostral, respectivamente, e $t^*$ é igual a $(1-C)/2$ e é denominado valor crítico superior para a distribuição $t$ com $n-1$ graus de liberdade, $t(n-1)$.

![confdiag.gif](https://github.com/gallileugenesis/qual_lampada_comprar/blob/main/figuras/confdiag.gif?raw=true)

Vamos então encontrar os intervalos de confiança para a médias das amostras A e B,  com um nível de confiança de 95%. Nesse caso, temos os seguintes resultados:

Para as lâpadas do fabricante A, espera-se, com 95% de confiança, que a média esteja entre 879.49 e 939.81.

Já para as lâmpadas do fabricante B, esse intervalo está entre 987.36 e 1049.34, para o mesmo nível de confiança.

Percebemos que o limite inferior de B é maior que o limite superior de A. Logo, agora com um maior nível de segurança, podemos afirma que a melhor opção de compra são as lâmpadas do fabricante B!

Muito obrigado por ler esse artigo. 

Caso tenha interesse, você pode me encontrar no [GitHub](https://github.com/gallileugenesis) e [Linkedin](https://www.linkedin.com/in/gallileugenesis/).







