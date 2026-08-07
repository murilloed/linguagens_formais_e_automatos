# Lista de Exercícios — Aula 01

## Linguagens Formais e Autômatos

**Tema:** sintaxe, semântica e análise de código  
**Professor:** __________________________________________  
**Aluno(a):** Aluisio Veloso Silva Carvalho______________  
**Turma:** matutino **Data:** 07/08/26

---

## Objetivos

Ao concluir esta lista, você deverá ser capaz de:

- diferenciar sintaxe e semântica;
- reconhecer problemas de escrita, concordância e ordenação;
- classificar erros básicos em trechos de código;
- explicar como o contexto altera o significado;
- distinguir um erro detectado pelo compilador de um erro lógico;
- ordenar as etapas iniciais do processamento realizado por um compilador.

## Orientações

1. Leia cada enunciado com atenção.
2. Não apresente apenas a classificação: escreva uma justificativa curta.
3. Nos exemplos de programação, considere a seguinte pseudolinguagem:
   - `inteiro`, `real` e `lógico` representam tipos;
   - `:=` é o operador de atribuição;
   - variáveis precisam ser declaradas antes do uso;
   - a forma condicional é `se condição então comando`.
4. Quando mais de uma classificação for defensável, indique o critério utilizado.

> **Nota conceitual:** na língua natural, um problema como “vou corre” é mais precisamente um erro gramatical ou de forma verbal. Na análise de compiladores, **erro léxico** possui um sentido técnico: ocorre quando uma sequência de caracteres não pode ser reconhecida como um token válido.

---

## Exercício 1 — Classificação em linguagem natural

Classifique cada sentença utilizando uma das categorias:

- **A — Adequada:** construção sintaticamente adequada no português usual;
- **B — Problema sintático:** problema de ordem, concordância ou estrutura;
- **C — Problema de formação/escrita:** palavra escrita ou flexionada de forma inadequada para o contexto.

| Item | Sentença | Classificação | Justificativa |
|---:|---|:---:|---|
| 1 | “As flores são belas.” | A | a sintaxe e formacao da frase estao corretas |
| 2 | “As flores é bela.” | B | a concoradncia verbal esta incorreta o correto seria: as flores sao belas ou a flor e bela |
| 3 | “Vou corre hoje no parque.” | C | erro na flexao do verbo correr a palvra corre deveria ser correr  |
| 4 | “Água bebeu José.” | A | a sintaxe e formacao da frase estao corretas a frase e apenas incomum (isso depende do contexto desde que nao seja literal)  |
| 5 | “O aluno acabou a prova.” | A | a sintaxe e formacao da frase estao corretas |

### Questões complementares

1. A sentença do item 4 é impossível em português ou apenas incomum na ordem mais frequente? Explique.

   **Resposta:**  
   nao e impossivel a frase e apenas incomum pode ser usada como fihura de expressao ou piada ela nao quebra nenhuma regra da lingua portuguesa

2. Reescreva todas as sentenças problemáticas de maneira adequada ao português usual.

   **Resposta:**  
   2: as flores sao belas ou a flor e bela
   3: vou correr hoje no parque

---

## Exercício 2 — Sintaxe e semântica na programação

Analise os trechos abaixo. Classifique o problema predominante como:

- **S — Sintático:** a estrutura não segue a gramática da pseudolinguagem;
- **M — Semântico:** a estrutura pode ser reconhecida, mas seus elementos não são válidos ou compatíveis;
- **V — Válido:** não há erro considerando apenas as regras fornecidas.

> Alguns compiladores podem classificar determinadas situações em fases diferentes. Considere as regras da pseudolinguagem apresentadas no início da lista.

### Item 1

```text
45 := a;
```

Classificação: S

Justificativa:  := e um sinal de atribuicao o que significa que a variavel do lado esquerdo recebe o valor do lado direito ja que o 45 e uma integral e nao uma variavel isso esta incorreto


### Item 2

```text
então (a < 10) se;
```

Classificação: S

Justificativa:  a ordem das palavras reservadas estao invertidas e nao ha comando apos entao


### Item 3

```text
inteiro soma;
soma := 4.5;
```

Classificação: M

Justificativa:  
na compatibilidade dos tipos tem um problema ja que a soma foi declarada que seria um inteiro porem recebeu um 4.5

### Item 4

```text
media := 10.0;
```

Considere que `media` não foi declarada anteriormente.

Classificação: M

Justificativa:  
as variaveis sempre devem ser declaradas antes do uso

### Item 5

```text
real media;
media := 10.0;
```

Classificação: V

Justificativa:  
o trecho esta sintaticamente e semanticamente perfeito 

### Item 6

```text
se a < 10 então
    a := a + 1;
```

Considere que `a` foi declarada como inteira.

Classificação: V

Justificativa:  
o trecho esta sintaticamente e semanticamente perfeito 

---

## Exercício 3 — Ambiguidade e contexto

Explique a classe gramatical e o significado da palavra destacada em cada frase.

### Caso A — “caminho”

1. “Eu **caminho** todos os dias.”
2. “O **caminho** é longo.”

**Explicação:**  
em 1:
Classe gramatical: verbo .

Significado: ação de andar, deslocar-se a pé, dar passos.

em 2:
Classe gramatical: substantivo masculino comum.

Significado: via, estrada, trajeto ou percurso a ser seguido (tanto físico quanto figurado).

### Caso B — “colher”

1. “Vou **colher** flores.”
2. “A **colher** caiu no chão.”

**Explicação:**  
em 1:
Classe gramatical: verbo (infinitivo impessoal do verbo colher).

Significado: ação de apanhar, arrancar ou tirar (frutos, flores, legumes) da planta onde nascem; também pode significar obter ou recolher.

em 2:
Classe gramatical: substantivo feminino comum.

Significado: utensílio doméstico (talher) com cabo e uma concavidade na extremidade, usado para levar alimentos à boca ou para servir.

### Caso C — programação

Observe os trechos:

```text
inteiro soma;
soma := 10;
```

```text
função soma(inteiro a, inteiro b)
    retorne a + b;
fim
```

1. O que o nome `soma` representa em cada trecho?
2. Que informações o compilador precisa consultar para interpretar corretamente esse nome?

**Resposta:**  
1:

primeiro trecho:O nome soma representa uma variável do tipo inteiro. Ela armazena um valor (no caso, o número 10) que pode ser modificado durante a execução do programa.

segundo trecho:O nome soma representa uma função (ou sub-rotina). Ela recebe dois parâmetros inteiros (a e b) e retorna um valor inteiro resultante da adição entre eles.

2:
O compilador precisa consultar a tabela de símbolos (ou contexto de declaração) para obter as seguintes informações:

Categoria sintática

Tipo de dado

Escopo (contexto): onde esse nome foi declarado (bloco, função, programa global)

Assinatura (se for função)

Contexto de uso

### Debate

Por que um compilador precisa considerar declarações, tipos e escopos para decidir se um código está correto?

**Anotações:**  
O compilador precisa de declarações, tipos e escopos porque a sintaxe (ordem das palavras) só garante estrutura, não significado. Sem declarações, ele não sabe se soma é variável (reservar memória) ou função (gerar chamada). Sem tipos, não sabe o tamanho dos dados nem qual instrução de CPU usar (ADD para inteiros, FADD para flutuantes). Sem escopos, não resolve conflitos de nomes nem controla visibilidade e tempo de vida. Essas verificações semânticas evitam que o programa gere código de máquina inválido ou execute operações proibidas, prevenindo crashes e comportamentos indefinidos em tempo de execução.
---

## Exercício 4 — Validade e erros lógicos

Um aluno desenvolveu um programa para conceder **10% de aumento** ao salário de um funcionário. O código deveria multiplicar o salário por `1.1`, mas foi escrito assim:

```text
real salario;
real novoSalario;

novoSalario := salario * 11;
```

O programa é aceito pelo compilador e executado normalmente.

Responda:

1. O trecho está sintaticamente correto? Justifique.

   **Resposta:**  
    Sim. A atribuição, os identificadores e o ponto e vírgula respeitam a gramática da linguagem (o compilador reconheceu a estrutura).

2. Há incompatibilidade de tipos ou uso de variável não declarada no trecho apresentado?

   **Resposta:**  
   Não. Ambas são real; multiplicar real por 11 (literal inteiro) é aceito como real, e todas as variáveis foram declaradas.

3. O programa realiza o objetivo proposto? Justifique.

   **Resposta:**  
   Não. O objetivo é aumento de 10% (multiplicar por 1,1), mas * 11 resulta em 1.100% do salário (um aumento de 1.000%).

4. Classifique o problema como erro sintático, erro semântico estático ou erro lógico.

   **Resposta:**  
   Erro lógico (semântico de execução), pois o programa compila e roda, mas produz um resultado matematicamente errado.

5. Corrija a linha responsável pelo problema.

```text
novoSalario := salario * 1.1;

```

---

## Exercício 5 — Ordem de processamento

Organize as etapas abaixo na ordem didática mais comum de um compilador:

- análise semântica;
- análise léxica (*scanner*);
- análise sintática (*parser*).

### Parte A — Lista numerada

1. Análise léxica (scanner)
2. Análise sintática (parser)
3. Análise semântica

### Parte B — O que cada etapa recebe e produz?

| Etapa | O que analisa? | Exemplo de problema detectado |
|---|---|---|
| Análise léxica | Caracteres do código-fonte, agrupando-os em tokens (palavras-chave, identificadores, números, operadores, símbolos). | Caractere inválido (ex.: @ ou # fora de string). |

| Análise sintática | Sequência de tokens, verificando se obedece à gramática da linguagem (estrutura hierárquica). | Falta de ponto e vírgula, parênteses não fechados, if sem then. |

| Análise semântica | Significado do programa: declarações, tipos, escopos e regras de coerência. | Variável não declarada, atribuir texto a inteiro, função chamada com parâmetros errados. |

### Parte C — Fluxograma

Desenhe um fluxo contendo os seguintes elementos:

```text
Código-fonte → Análise Léxica → tokens → Análise Sintática → estrutura sintática → Análise Semântica → código validado para as próximas etapas
```

### Questão de reflexão

Por que a análise semântica normalmente depende dos resultados das análises léxica e sintática?

**Resposta:**  
A análise semântica precisa dos tokens (gerados pela léxica) para saber quais são os nomes, valores e operadores envolvidos, e precisa da estrutura hierárquica (árvore sintática, gerada pelo parser) para saber relações de precedência, escopo e aninhamento (ex.: qual bloco contém qual variável). Sem os tokens, não há elementos para verificar; sem a árvore, não se sabe o contexto estrutural necessário para aplicar regras de tipo e declaração corretamente.

---

## Desafio opcional — Crie seus próprios exemplos

Crie três pequenos exemplos:

1. uma frase ou código com problema de escrita/tokenização;
2. uma construção com erro sintático;
3. um programa sintaticamente válido, mas com erro lógico.

Para cada exemplo, apresente a classificação e a justificativa.

---

## Síntese

Complete:

- **Léxico** está relacionado a _______________________________________________.
- **Sintaxe** está relacionada a ______________________________________________.
- **Semântica** está relacionada a ____________________________________________.
- **Erro lógico** ocorre quando _______________________________________________.

