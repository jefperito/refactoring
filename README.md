# refactoring

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

### Avisar o gestor - **Descartável**

## Níveis de refatoração

O ideal é que refatoração seja sempre feito de maneira pequena, mesmo em grandes pedaços de código ruim ou arquitetura antiquada, usando técnica de *baby steps* como é feito no TDD. O código chegará no grau esperado através do tem po que aquela estrutura é visitada por um programador. Isso também é conhecido como **Regra do escoteiro** que diz que: *Deixe o local que visitou um pouco melhor que o encontrou*.

### Pequeno

O esforço de fazer é mínimo e leva poucos minutos para executar. Técnica de alto nível não é possível aplicar pois precisa de um custo razoável de análise, costuma não ser mais de 2 ou 3 técnicas, extrações de métodos, constantes, variáveis, renomear coisas, etc... tudo que encaixar no tempo para resolver em minutos. 

### Médio

### Grande

### Épico

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
