## Compacidade lógica

O objetivo dessa seção é explicar brevemente o que é o Teorema da Compacidade lógica, como ele se aplica a Sistemas lógicos de Primeira Ordem e como Hrushovski e Pitowsky aplicaram esse teorema [neste artigo](docs/hrushovski2004generalizations) para obter alguns resultados relacionados ao Teorema de Gleason para conjuntos finitos de projetores.

Esta seção baseia-se fortemente No artigo [First-order Model Theory](https://plato.stanford.edu/entries/modeltheory-fo/#Thms) na *Stanford Encyclopedia of Philosophy*. Devo começar dizendo que este teorema é mais um resultado sobre "metamatemática" do que matemática em si. Parece geral demais para ser aplicado à demonstração de um mero lema, mas ao longo dessa seção, darei alguns exemplos que encontrei na literatura, majoritariamente no artigo do Hrushovski e Pitowsky, ou mesmo [neste artigo do Pitowsky sozinho](pitowsky1998infinite.md). 

## Model Theory

As poucas referências que encontrei sobre Compacidade Lógica invariavelmente citam Model Theory (Teoria Modal em PT-BR?). Em poucas palavras, Model Theory é o estudo sobre a interpretação de uma linguagem, formal ou natural, utilizando estruturas de teoria de conjuntos. É razoável esperar que, com uma definição tão abrangente, tenha várias interseções entre Model Theory e Lógica.

Algumas noções básicas de Model Theory:

Os elementos básicos são sentenças S. Na linguagem natural, sentenças nem sempre podem ter um valor de verdadeiro/falso atribuido a elas, porque usualmente alguma informação não está presente na sentença. No português é mais difícil encontrar um exemplo assim, mas na matemática poderiamos dizer "É maior que 3". Essa é uma sentença verdadeira para o número 4, falsa para 2. Poderíamos completar essa sentença especificando um número e ela passsaria a ter um valor de verdadeiro/falso válido para ela. Essa informação faltante é chamada de *interpretação* de S. 

Se uma intepretação I de S faz com que S seja verdadeira, então I é chamada de *a model for* S (daí o nome model theory). Na linguagem mais comum da matemática, dizemos simplesmente que I satisfaz S (por exemplo, 4 satisfaz a sentença "é maior que 3"). A notação formal para isso é $I\models S$. 

Podemos colecionar todos os modelos para uma sentença S em um conjunto que denotamos $Mod(S)$. Na realidade, se temos um conjunto de sentenças $T$, onde $S\in T$, podemos construir o conjunto $Mod(T)$. Os elementos de $Mod(T)$ são a coleção de todas as interpretações que são, simultaneamente, modelos para todas as possíveis sentenças em $T$. Quando um conjunto de sentenças $T$ é usado para definir um conjunto dessa forma, é comum chamar $T$ de uma *Teoria* ou *conjunto de axiomas*. Portanto, nessa linguagem, $T$ *axiomatiza* $Mod(T)$.

Por exemplo, considera o seguinte conjunto de sentenças

$$
\forall x,y,z, \,\, (x+y)+z = x + (y+z), \quad x+0 = x, \quad x+(-x) = 0, \quad x+y = y+x.
$$

O conjunto de modelos possíveis para estas sentenças (ou seja, interpretações que as tornem verdadeiras) é justamente o conjunto dos grupos Abelianos.



## First Order Model Theory

Model Theory de primeira ordem se preocupa em estudar a relação entre teorias formadas a partir de sentenças construidas por Lógica de Primeira Ordem (ou lógica Clássica) e seus respectivos candidatos a modelos (ou interpretações). Não vou me estender muito aqu porque Lógica Clássica é como praia de tombo, o raso todo mundo conhece, é chato e entediante, enquanto que o fundo é muito fundo e o risco de afogamento é alto. O que é importante ter em mente é que uma linguagem de primeira ordem normalmente é construida em cima de conectivos lógicos $\lor, \land, \neg, \implies, \iff$, além de quantificadores existêncial $\exists$ e universal $\forall$. Todo modelo tem um domínio e em linguagens de primeira ordem, estes conectivos atuam diretamente sobre os elementos deste domínio, que são chamadas *variáveis* (ou *variáveis de primeira ordem*).

*Variáveis de segunda ordem* se estendem sobre propriedades, conjuntos, classes, relações ou funções sob o domínio das variáveis de primeira ordem. Assim, por exemplo, no caso dos grupos abelianos, a sentença $\forall x, x+0=x$ é uma sentença de primeira ordem, pois refere-se diretamente às variáveis do domínio do modelo (neste caso, elementos do grupo abeliano que satisfaz esta e as outras sentenças, simultaneamente). Por exemplo, se escrevessemos

$$
\forall x, x+0=x \,\, \land \,\, \forall f, f(x)=0,
$$
esta seria uma expressão em segunda ordem para a teoria dos grupos abelianos, pois há uma referência clara à funções das variáveis do modelo.

Teoria de Linguagens é uma toca de coelho. Por hora, basta restingirmo-nos ao máximo em sentenças de primeira ordem (isto é, evitar sentenças que envolvam variáveis de segunda ordem sobre modelos) e trabalhar diretamente com as variáveis de primeira ordem.


## Teorema da Compacidade

Com tudo o que já foi definido, podemos enunciar o Teorema da Compacidade da seguinte forma:

*Se T é uma teoria de primeira ordem e cada sub-conjunto finito de T possui um modelo, então T possui um modelo*.

Obviamente, os casos mais extremos são aqueles em que T é infinito, enumerável ou não-enumerável. Aparentemente, o Teorema vale em ambos os casos (veja [Alfred Tarski's Work in Model Theory](https://www.jstor.org/stable/2273900?seq=2) página 2).

Esse Teorema é muito forte. Não faço ideia e não tenho fôlego intelectual para ir atrás das provas feitas pelo Tarski  e de A. Mal'ce para entender porque ele vale. Ao invés disso, vou dedicar o restante dessa seção para mostrar como Pitowsky usou esse teorema de lógica para estudar contextualidade de Kochen-Specker e derivar várias consequências do teorema de Gleason.

## Conjuntos KS finitos via Compacidade

Primeiro, é necessário colocar o Teorema de Gleason em uma forma que conseguimos reconhecer como uma teoria de primeira ordem. [Hrushovski e Pitwosky](hrushovski2004generalizations) fazem isso enunciado o seguinte modelo:

$$
\mathrm{G1:}\,\, \forall x, \,\, p(x) \geq 0
$$

$$
\mathrm{G2:}\,\,\forall x, \,\, p(-x) = p(x)
$$

Para todo tripla ortonormal $\mathrm{G3:}\,\, x,y,z \in \mathbb{S}^2$, $p(x)+p(y)+p(z)=1$. 

Um modelo para esta teoria é justamente o conjunto de todas as direções possíveis em $\mathbb{R}^3$, ou seja, a esfera $\mathbb{S}^2$. O que se faz agora é adicionar uma nova sentença à teoria:

F1: Existe uma frame function $p$ tal que $\forall x, \,\, p(x)=0 \lor p(x)=1$.

Como das três primeiras sentenças G1-G3 segue que $p$ deve ser contínua (esse é um dos reusltados necessários para o teorema de Gleason, que segue de G1-G3 como Hrushovski e Pitowsky mostram no artigo), ao adicionar essa última sentença F1, temos uma contradição. Logo, não existe modelo para esta nova teoria formada por G1-G3 + F1. A não existência de modelo significa que os elementos do domínio (que anteriormente eram as direções em $\mathbb{S}^2$) não satisfazem, simultaneamente, as quatro proposições anunciadas. Logo, pela compacidade lógica, deve existir um subconjunto finito de direções violando esta nova teoria formada por G1-G3+F1, ou seja, violando alguma (ou mais de uma) dessas proposições. Sabemos, graças a Kochen-Specker, que existem tais conjuntos finitos e são os conhecidos "conjuntos de Kochen-Specker", que violam justamente F1.

O Teorema da Compacidade deve ser tomado com certo cuidado aqui. Primeiro, poderiamos pensar que o último axioma viola a condição de ser de primeira ordem, já que contém uma sentença do tipo "existe um estado...". Mas isso não é verdade, pois se fosse, invalidaria o resultado obtido por Hrushovski. O que ocorre é que não se está exatamente quantificando sobre funções, pois $p$ foi adicionado à linguagem, assim como as operações $+,\times$ naturalmente foram assumidas como constituintes da linguagem.

Ou seja, "Existe um estado p$ não é formalmente equivalente à $\exists p$, pois a linguagem possui apenas um símbolo $p$. No próprio artigo, eles mencionam

*Add to this first order theory a function symbol* $p:\mathbb{S}^2 \rightarrow \mathbb{R}$.

A verdade é que o axioma F1 está mal escrito e causa essa ambiguidade. Devemos interpretar $p$ como alguma frame function, que apesar de arbitrária, está fixa como operação adicionada ao modelo. Na realidade, devemos fazer uma distinção entre o símbolo $p$, que é linguístico, de um modelo que satisfaça $p$, que de fato seria uma frame function. 

Um exemplo concreto é o seguinte. Considere a teoria dos grupos abelianos que citei anteriormente. De forma implicita, o símbolo $+$ foi inserido na linguagem, de forma a fazer sentido os axiomas de grupo Abeliano. De maneira concreta, qualquer grupo abeliano satisfaz estes axiomas. Porém, a operação $+$ terá diferentes interpretações, de acordo com cada grupo. Poderíamos então pensar em todos as as interpretações possíveis para o símbolo $+$. Um deles é a adição de números reais, outro é a multiplicação de matrizes diagonais, etc. Poderiamos então formular uma frase do tipo "Existe uma operação +...", ao espírito do axioma F1, sem querer dizer $\exists +$, mas sim "Existe uma interpretação para +...". Essa seria uma sentença de primeira ordem.

Reformulando o axioma F1 sob essas considerações, ele fica melhor enunciado assim:

F1: Existe uma interpretação para a frame function $p$ tal que $\forall x, \,\, p(x)=0 \lor p(x)=1.$

Essa é a prova não-construtiva de que conjuntos KS devem existir, a partir do teorema de Gleason.







