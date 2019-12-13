# Refactoring

## O que é refatoração

Resumindo é a maneira de alterar a estrutura do código sem alterar o comportamento. Quem não gosta de uma casa limpa e organizada? Viver em um ambiente sujo e bagunçado causa stress, não achamos as coisas que gostariamos e vergonha de trazer alguém para tomar um café. Assim tem que ser com o nosso trabalho: limpo e organizado. Trabalhar com código fonte que é bagunçado e sujo nos causa efeitos parecidos como no exemplo acima. Só que com alguns agravantes, nosso dinheiro depende disso, a empresa depende disso, os nossos clientes dependem disso. Bagunça não encontramos as coisas fáceis, bugs se escondem no meio da sujeira que ficam difíceis de encontrar mesmo depois de inspecionar por horas (debugging) no meio do caos.

## Porque refatorar

* Menos stress.
* Design simples e elegante.
* Tempo para focar em produto e não em bugs.
* Agilidade no entendimento do código.

## Requisitos para refatorar

Os requisitos serão mapeados por níveis de importância para a refatoração de *Indispensável* a *Descartável*, são eles:

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

### Ferramenta de análise estática - Altamente recomendável

Ferramentas ajudam no apoio a encontrar vulnerabilidades, code smells, cobertura de testes automatizados, checagem de padrão e entre outos; Atuando como revisores de código automatizado e gerando relatórios sobre o resultado da revisão. Essas ferramentas podem atuar integrado a IDE, editor de texto ou como uma etapa da esteira de código. Nessa última podendo atuar como guardião e impedindo a publicação caso alguma regra definida pela equipe é violada.

### Programação em par - Recomendável

Programação em par ajuda na transmissão de conhecimento, na coletividade do código-fonte e na revisão de código feita durante o processo. Refatorar é uma prática que requer entendimento técnico de boas práticas, trade-offs que podem surgir e visão arquitetural para atender o produto no futuro, todas essas decisões ganham quando há troca de experiências entre os pareados. Não acredito que precisa ser pareado durante todo o ciclo de vida da refatoração, a pessoa que está a frente do desafio que precisa sentir a necessidade e do ganho do valor de ter outro desenvolvedor na empreitada.

### Dedicação a refatoração - Descartável

Refatoração tem que estar no *modus operandi* da equipe, fazer parte do processo de baixo nível do trabalho, atrelado as tarefas do dia-a-dia como incluir novas funcionalidades ou trabalhar em algum bug; Ao se deparar com o código fora do padrão, sem testes, ou remover trade-offs que não fazem mais sentido, deve-se refatorar (lembre-se de realizar commits separado da tarefa, facilita a rastreabilidade e a separação de contexto). Se for visível que o esforço de deixá-lo limpo é maior que o tempo disponível, não se preocupe em finalizar o trabalho, deixe para resolver nas próximas tarefas que atingir o código.

### Avisar o gestor - Descartável

Não avisamos o gestor as estratégias que tomamos em usar algum design pattern específico ou se vamos utilizar composição ao invés de hierarquia entre classes, por que avisar sobre refatoração? Nosso trabalho é entregar produto de qualidade, e qualidade significa manter o código simples, testado, livre de bugs o máximo possível e atendendo as expectativas, caso ele ou ela esteja impedindo, no mínimo estará se comportando de maneira não profissional e amadora.

## Níveis de refatoração

O ideal é que refatoração seja sempre feito de maneira **pequena**/**média**, mesmo em grandes pedaços de código ruim ou arquitetura antiquada, usando técnica de *baby steps* como é feito no TDD. O código chegará no grau esperado através do tem po que aquela estrutura é visitada por um programador. Isso também é conhecido como **Regra do escoteiro** que diz que: *Deixe o local que visitou um pouco melhor que o encontrou*.

## Técnicas de refatoração

### Guideline para refatoração

### Exemplos de alto nível
* Entrangulamento

Estrangulamento, ou como já ouvi alguns dizendo morte por inanição para o mesmo objetivo, é uma técnica aconselhável para remover uma parte do sistema em detrimento de outra, seja por troca de tecnologia, seja pelo avançado estágio de podridão do código. Com ela também é possível a organização de bordas de módulos.

* Feature toggle
* Log de acesso
* Decomposição por objetos.
* Clean code

### Exemplos de baixo nível (Abordar?)
* Extração de método.
* Extração constante.
* Extração de classe.
* Extração de variável.
* Obsessão por tipos primitivos.
