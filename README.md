# Refactoring

## O que é refatoração

Resumindo é a maneira de alterar a estrutura do código sem alterar o comportamento.

## Porque refatorar

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

### Ferramenta de análise estática - Altamente recomendável

### Integração contínua - Altamente recomendável

### Programação em par - Recomendável

### Dedicação a refatoração - Descartável

Refatoração tem que estar no *modus operandi* da equipe, fazer parte do processo de baixo nível do trabalho, atrelado as tarefas do dia-a-dia como incluir novas funcionalidades ou trabalhar em algum bug; Ao se deparar com o código fora do padrão, sem testes, ou remover trade-offs que não fazem mais sentido, deve-se refatorar (lembre-se de realizar commits separado da tarefa, facilita a rastreabilidade e a separação de contexto). Se for visível que o esforço de deixá-lo limpo é maior que o tempo disponível, não se preocupe em finalizar o trabalho, deixe para resolver nas próximas tarefas que atingir o código.

### Avisar o gestor - Descartável

## Níveis de refatoração

O ideal é que refatoração seja sempre feito de maneira **pequena**/**média**, mesmo em grandes pedaços de código ruim ou arquitetura antiquada, usando técnica de *baby steps* como é feito no TDD. O código chegará no grau esperado através do tem po que aquela estrutura é visitada por um programador. Isso também é conhecido como **Regra do escoteiro** que diz que: *Deixe o local que visitou um pouco melhor que o encontrou*.

## Técnicas de refatoração

### Guideline para refatoração

### Exemplos de alto nível
* Entrangulamento
* Log de acesso
* Decomposição por objetos.
* Clean code

### Exemplos de baixo nível (Abordar?)
* Extração de método.
* Extração constante.
* Extração de classe.
* Extração de variável.
* Obsessão por tipos primitivos.
