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
\forall x, \,\, p(x) \geq 0
$$

$$
\forall x, \,\, p(-x) = p(x)
$$

Para todo tripla ortonormal $x,y,z \in \mathbb{S}^2$, $p(x)+p(y)+p(z)=1$. 

Um modelo para esta teoria é justamente a esfera $\mathbb{S}^2$. O que se faz agora é adicionar uma nova sentença ao modelo

Existe um estado $p$ tal que $\forall x, \,\, p(x)=0 \lor p(x)=1$.

Como das três primeiras sentenças segue que $p$ deve ser contínua, ao adicionar essa última sentença temos uma contradição. Logo, não existe modelo para esta teoria. A não existência de modelo significa que os elementos do domínio (que neste caso são as direções em $\mathbb{S}^2$) não satisfazem, simultaneamente, as quatro proposições anunciadas. Logo, pela compacidade lógica, deve existir um subconjunto finito de direções violando alguma dessas sentenças. Sabemos, graças a Kochen-Specker, que existem tais conjuntos finitos violando a última sentença.
