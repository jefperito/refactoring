# Refactoring

Esse é um material resultante de uma compilação de minhas experiências, livros, apresentações e blogs de gurus da área de desenvolvimento como [Sandro Mancuso](https://twitter.com/sandromancuso), [Uncle Bob Martin](https://twitter.com/unclebobmartin), [Martin Fowler](https://twitter.com/martinfowler), [Elliotte Harold](https://twitter.com/elharo) e [Michael Feathers](https://twitter.com/mfeathers).

## O que é refatoração

Resumindo é a maneira de alterar a estrutura do código sem alterar o comportamento. Quem não gosta de uma casa limpa e organizada? Viver em um ambiente sujo e bagunçado causa stress, não achamos as coisas que gostariamos e vergonha de trazer alguém para tomar um café. Assim tem que ser com o nosso trabalho: limpo e organizado. Trabalhar com código fonte que é bagunçado e sujo nos causa efeitos parecidos como no exemplo acima. Só que com alguns agravantes, nosso dinheiro depende disso, a empresa depende disso, os nossos clientes dependem disso. Bagunça não encontramos as coisas fáceis, bugs se escondem no meio da sujeira que ficam difíceis de encontrar mesmo depois de inspecionar por horas (debugging) no meio do caos.

## Porque refatorar

* Menos stress.
* eliminar problemas de código legado.
* Design simples e elegante.
* Tempo para focar em produto e não em bugs.
* Agilidade no entendimento do código.

## O que é código legado.

* Medo de alterar.
* Falta de testes automatizados.

## Requisitos para refatorar

Os requisitos serão mapeados por níveis de importância para a refatoração de *Indispensável* a *Descartável*, esses níveis foram mapeados de acordo com a minha experiência, caso você não concorde com alguma classificação, não tem problema! Siga seu feeling profissional, segue a lista:

* **Indispensável**
Não é possível refatorar de maneira efetiva sem esse requisito.

* **Altamente recomendável**
Sem o requisito, é passível de gerar baixa performance, entrega com menor valor, etc...

* **Recomendável**
O requisito pode dar apoio em decisão ou gerar dados, mas é possível de ter uma entrega satisfatória sem ele.

* **Descartável**
Esse requisito não faz sentido para a refatoração, avalie 2 vezes antes de utilizar.

### Testes automatizados - Indispensável

Não tem como ter garantia sem testes automatizados, há muita coisa para perder para depender de testes manuais, além de que testes manuais são caros de executar e seres humanos são passíveis de diversas variáveis externas como problemas familiares, financeiros, etc... que podem degradar a qualidade do teste. Teste de unidade se encaixa muito bem pelo baixo nível de teste que se propõe além de ser extremamente barato de executá-lo, milhares de testes são executados em poucos segundos.

### Integração contínua - Indispensável

CI/CD dá a confiança que o sistema continua funcionando mesmo com a limpeza sendo feita, você pode visualizar os passos da pipeline sendo executada, os testes automatizados e deploy nos ambientes de homologação/produção, mesmo caso esqueça de rodar os testes na máquina local, não tem como publicar uma nova versão sem passar todas as etapas sem erro, pois a deploy está automatizado e é o único ponto de publicação.

### IDE - Indispensável

IDEs modernas possuem diversas funcionalidades de refatoração como extração de estrutura: variável, método, classe, constante, etc..., buscar dependência, sugerir melhorias e warning, trabalho que fazendo manualmente podendo adicionar bug ao projeto, IDEs estáveis dá garantia que ao executar alguma ferramenta de refatoração, o comportamento não foi alterado e os testes continuam passando.
Editores de texto como Sublime Text, Visual Studio, VIM, etc... não conheço se possui essas funcionalidades que executam com tanta confiabilidade, se você consegue chegar no mesmo nível de IDEs continue com o seu editor de texto, caso contrário, estude em utilizar uma IDE.

### Ferramenta de análise estática - Altamente recomendável

Ferramentas ajudam no apoio a encontrar vulnerabilidades, code smells, cobertura de testes automatizados, checagem de padrão e entre outos; Atuando como revisores de código automatizado e gerando relatórios sobre o resultado da revisão. Essas ferramentas podem atuar integrado a IDE, editor de texto ou como uma etapa da esteira de código. Nessa última podendo atuar como guardião e impedindo a publicação caso alguma regra definida pela equipe é violada.

Lembre-se que cobertura de código é uma ferramenta de apoio ao desenvolvimento e não uma métrica de gerenciamento, 95% de cobertura de cõdigo significa software bem testado? livre de bugs? não necessariamente, é possível criar testes de unidade que passem pelas linhas descobertas sem que gere asserções adequadas. Caso seja "vendido" essa métrica para a gerência e ocorra um bug, é possível que a gerência pergunte: "Esse bug foi gerado nos 5% sem cobertura?" Qual seria a resposta? Caso seja verdadeiro, haverá uma pressão de adicionar cobertura nesses 5% mesmo que a equipe já tenha adicionado cobertura no bug que foi corrigido, locais virtualmentes inalcançáveis, getters e setters onde o valor é muito pequeno, precisem receber teste de unidade.

Mas o pior caso é caso a resposta seja negativa, a métrica cai por terra, não haverá uma confiabilidade, já que havia testes na linha que apresentou o problema, apesar de que não foram bem escritos, a gerência colocará de escanteio.

### Programação em par - Recomendável

Programação em par ajuda na transmissão de conhecimento, na coletividade do código-fonte e na revisão de código feita durante o processo. Refatorar é uma prática que requer entendimento técnico de boas práticas, trade-offs que podem surgir e visão arquitetural para atender o produto no futuro, todas essas decisões ganham quando há troca de experiências entre os pareados. Não acredito que precisa ser pareado durante todo o ciclo de vida da refatoração, a pessoa que está a frente do desafio que precisa sentir a necessidade e do ganho do valor de ter outro desenvolvedor na empreitada.

### Padrão para arquitetura de testes - Recomendável

### Dedicação a refatoração - Descartável

Refatoração tem que estar no *modus operandi* da equipe, fazer parte do processo de baixo nível do trabalho, atrelado as tarefas do dia-a-dia como incluir novas funcionalidades ou trabalhar em algum bug; Ao se deparar com o código fora do padrão, sem testes, ou remover trade-offs que não fazem mais sentido, deve-se refatorar (lembre-se de realizar commits separado da tarefa, facilita a rastreabilidade e a separação de contexto). Se for visível que o esforço de deixá-lo limpo é maior que o tempo disponível, não se preocupe em finalizar o trabalho, deixe para resolver nas próximas tarefas que atingir o código.

### Avisar o gestor - Descartável

Não avisamos o gestor as estratégias que tomamos em usar algum design pattern específico ou se vamos utilizar composição ao invés de hierarquia entre classes, por que avisar sobre refatoração? Nosso trabalho é entregar produto de qualidade, e qualidade significa manter o código simples, testado, livre de bugs o máximo possível e atendendo as expectativas, caso ele ou ela esteja impedindo, no mínimo estará se comportando de maneira não profissional e amadora.

## Antes de refatorar

* Na refatoração de método, ir no galho mais profundo pois precisa menos contexto e ir subindo. em outros casos pode precisar ler o método completo.
* Ferramentas boas para refatorar.

Análise estática para gerar insights.
Equipes que tem baixa experiência podem focar em atingir metas quantificativas (obtidos através de ferramentas que geram métricas como violação de regras e padrões), essas mesmas ferramentas apoiam a equipe na evolução sendo um guia para um melhor software. Metas qualificativas como muitas técnicas do clean code, possui um grau de complexidade maior de análise, ferramentas tem maior dificuldade em suportar e precisa um pouco mais de experiência do desenvolvedor em código limpo e a capacidade de fazer trade offs em decisões que serão tomadas.

* Ciclo por refatoração: refatora -> rodar testes -> caso verde: refatora -> caso vermelho: ctrl/cmd + z.


### Medições de código

* Dependência entre estruturas.
  * Design structure matrix (DSM).
  * "Martin’s metrics".

* Complexidade de algoritmo.
  * Cyclomatic complexity.


## Níveis de refatoração (Rever isso)

O ideal é que refatoração seja sempre feito de maneira **pequena**/**média**, mesmo em grandes pedaços de código ruim ou arquitetura antiquada, usando técnica de *baby steps* como é feito no TDD. O código chegará no grau esperado através do tem po que aquela estrutura é visitada por um programador. Isso também é conhecido como **Regra do escoteiro** que diz que: *Deixe o local que visitou um pouco melhor que o encontrou*.

## Software totalmente legado
* 1o passo é focar testes de unidade no core do sistema.
* 2o passo no caminho principal da aplicação.
* 3o camminhos de borda/periférico.

Focar testes automatizados em abrangência e não em detalhes.
Aumentar a suite de testes ao quebrar os grandes testes de unidade e especializá-los, com suporte de novos testes para outros galhos especialistas.

Comece pequeno, não abrace o mundo. Escreva um teste por vez e pequenas refatorações, haverá muita aprendizagem nessa jornada e não faça BDUF, não no inicio pelo menos.

## Estratégia de refatoração

Estratégias adotadas para problemas recorrentes, seguindo por um problema definido e técnicas para resolvê-lo, porém existe algumas técnicas "genéricas" que pode/deve ser aplicada para qualquer tipo de problemas como:

* Clean code

### Módulos altamente acoplados

* Façade

Façade é um design pattern que significa em criar uma interface que simplifica e padroniza a comunicação entre os componentes sob o façade e o mundo externo. Isso possibilita uma serie de vantagens como único ponto de acesso (quando isolado), esconde complexidade, esconde componentes que não precisam expor ao cliente e facilita a configuração na utilização.

Estrangulamento, ou como já ouvi alguns dizendo morte por inanição para o mesmo objetivo, é uma técnica aconselhável para remover uma parte do sistema em detrimento de outra, seja por troca de tecnologia, seja pelo avançado estágio de podridão do código. Com ela também é possível a organização de bordas de módulos.

Caso seja uma reescrita, é possível manter as duas versões rodando em paralelo, intercambeando entre as versões em tempo de execução através de feature toggle, assim, poderá executar testes manuais e executar em cliente com alguma garantia de caso apareça algo inesperado, troque a chave para a utilização do módulo antigo.

### Complexidade de classes

* SRP
* Decomposição por objetos.

### Feature envy/Entidades anêmicas

* Encapsulamento.

Feature envy e entidades anêmicas tem problemas similares, apenas em locais diferente, enquanto entidade anêmica se concentra problema no domínio do sistema, feature envy é mais focado em todo o resto.

Eg. Imagine uma entidade profissional que possui apenas atributos e seus métodos de encapsulamento desses atributos, isso é conhecido como entidade anêmica, anêmica de **lógica de domínio**! Quando ela não controla e conhece o seu próprio comportamento e são outras classes ou funções que o fazem. Ao invés de eu perguntar para profissional se o seu cargo é um cargo de diretoria, preciso carregar um serviço (ProfissionalService como exemplo) ou qualquer outro tipo de estrutura de uma camada que não seja de domínio. Os pontos negativos desse problema é lógica de domínio espalhada em camadas fora do domínio, alto acoplamento: caso precise utilizar uma entidade, terá que carregar todo os serviços em volta dessa entidade e o pior pode acontecer, pode acabar duplicando lógica de domínio caso acabe não encontrando algo que já foi implementando julgando que não exista.
No caso de feature envy o problema é parecido, é possível identificar quando uma classe X acaba executando diversos métodos de uma classe Y para obter um determinado resultado, todas as essas operações a classe Y poderia abstrair e a classe X apenas perguntaria pelo resultado. Mais informações sobre feature envy nesses links: <Links> e anemic entities nesses links: <links>
 
Para resolver esses problemas basta mover ou criar métodos para as classes que deve ser responsável pela lógica.

---

* Feature toggle (talvez não precise, apenas para novas funcionalidades e reescrita).
* Log de acesso (talvez não precise, apenas para monitoramento).

### Exemplos de baixo nível (Abordar?)
* Extração de método.
* Extração constante.
* Extração de classe.
* Extração de variável.
* Obsessão por tipos primitivos.
