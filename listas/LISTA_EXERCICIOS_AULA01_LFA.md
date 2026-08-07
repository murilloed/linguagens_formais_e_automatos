# Lista de Exercícios — Aula 01

## Linguagens Formais e Autômatos

**Tema:** sintaxe, semântica e análise de código  
**Professor:** __________________________________________  
**Aluno(a):** ___________________________________________  
**Turma:** ___________________ **Data:** ____/____/________

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
| 1 | “As flores são belas.” | A | Estrutura correta e concordância adequada.|
| 2 | “As flores é bela.” | B | Erro de concordância de número (plural/singular).|
| 3 | “Vou corre hoje no parque.”| C | Palavra mal flexionada; falta o "r" no infinitivo (correr)|
| 4 | “Água bebeu José.”| A | Ordem invertida (Objeto-Verbo-Sujeito), mas gramaticalmente aceita.|
| 5 | “O aluno acabou a prova.” | A | Estrutura padrão (Sujeito-Verbo-Objeto) correta. |

### Questões complementares

1. A sentença do item 4 é impossível em português ou apenas incomum na ordem mais frequente? Explique.

   **Resposta:**  
R = É apenas incomum. A ordem padrão do português é Sujeito-Verbo-Objeto, mas a flexibilidade da língua permite a ordem Objeto-Verbo-Sujeito por estilo ou ênfase.

2. Reescreva todas as sentenças problemáticas de maneira adequada ao português usual.

   **Resposta:**  
R = Item 2: "As flores são belas." | Item 3: "Vou correr hoje no parque."
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

Classificação: ____S____

Justificativa:  
R = O lado esquerdo de uma atribuição deve ser um identificador (variável), não um valor literal. A ordem estrutural está errada.

### Item 2

```text
então (a < 10) se;
```

Classificação: ___S_____

Justificativa:  
R = As palavras reservadas estão fora da ordem estabelecida pela gramática (espera-se se condição então comando).

### Item 3

```text
inteiro soma;
soma := 4.5;
```

Classificação: ____M____

Justificativa:  
R = Incompatibilidade de tipos. Tenta-se atribuir um valor real (4.5) a uma variável declarada como inteira.

### Item 4

```text
media := 10.0;
```

Considere que `media` não foi declarada anteriormente.

Classificação: ___M_____

Justificativa:  
R = A variável media foi utilizada na atribuição sem ter sido previamente declarada na memória.

### Item 5

```text
real media;
media := 10.0;
```

Classificação: ___V_____

Justificativa:  
R = A variável foi declarada corretamente e recebe um valor numérico compatível com seu tipo.

### Item 6

```text
se a < 10 então
    a := a + 1;
```

Considere que `a` foi declarada como inteira.

Classificação: ____V____

Justificativa:  
R = A estrutura segue as regras do condicional e a atribuição aritmética usa uma variável previamente declarada e de tipo compatível.

---

## Exercício 3 — Ambiguidade e contexto

Explique a classe gramatical e o significado da palavra destacada em cada frase.

### Caso A — “caminho”

1. “Eu **caminho** todos os dias.”
2. “O **caminho** é longo.”

**Explicação:**  
R = Na frase 1, "caminho" é um verbo (ação de andar). Na frase 2, é um substantivo (lugar por onde se anda, trajeto).

### Caso B — “colher”

1. “Vou **colher** flores.”
2. “A **colher** caiu no chão.”

**Explicação:**  
R = Na frase 1, "colher" é um verbo (ação de retirar da terra). Na frase 2, é um substantivo (o utensílio de mesa).

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
R = No primeiro trecho, representa uma variável (espaço na memória). No segundo, representa o nome de uma função.

### Debate

Por que um compilador precisa considerar declarações, tipos e escopos para decidir se um código está correto?

**Anotações:**  
R = O compilador consulta a Tabela de Símbolos, verificando escopo e declarações anteriores para saber como tratar o nome.

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
R = Sim. O trecho obedece à estrutura gramatical de atribuição da linguagem (identificador :=     expressao).
2. Há incompatibilidade de tipos ou uso de variável não declarada no trecho apresentado?

   **Resposta:**  
R = Não. Ambas as variáveis são reais e a operação de multiplicação é válida para esse tipo.

3. O programa realiza o objetivo proposto? Justifique.

   **Resposta:**  
  R = Não. Multiplicar por 11 aumenta o valor em 1000%, e não em 10% (que seria 1.1).

4. Classifique o problema como erro sintático, erro semântico estático ou erro lógico.

   **Resposta:**  
   ___R =_Erro lógico ______________________________________________________________________

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

1. R = Análise léxica (scanner).
2. R = Análise sintática (parser).
3. R = Análise semântica.

### Parte B — O que cada etapa recebe e produz?

| Etapa | O que analisa? | Exemplo de problema detectado |
|---|---|---|

| Análise léxica | Agrupamento de caracteres em tokens (palavras) | Identificador com caractere inválido (ex: 2var)|

| Análise sintática | Ordem e estrutura dos tokens (gramática). | Falta de parênteses ou então após um se. |

| Análise semântica | Significado, escopo e tipagem das instruções. | Operação entre variável tipo texto e tipo numérico. |

### Parte C — Fluxograma

Desenhe um fluxo contendo os seguintes elementos:

```text
Código-fonte → __________ → tokens → __________ → estrutura sintática
            → __________ → código validado para as próximas etapas
```

### Questão de reflexão

Por que a análise semântica normalmente depende dos resultados das análises léxica e sintática?

**Resposta:**  
R = Porque a semântica avalia o significado de uma frase inteira estruturada. Não é possível checar o significado de algo que sequer forma uma palavra válida (léxica) ou uma frase com sentido gramatical (sintaxe).

---

## Desafio opcional — Crie seus próprios exemplos

Crie três pequenos exemplos:

1. uma frase ou código com problema de escrita/tokenização;
2. uma construção com erro sintático;
3. um programa sintaticamente válido, mas com erro lógico.

Para cada exemplo, apresente a classificação e a justificativa.

R(1) = Léxico/Escrita: inteiro @num := 5; (Justificativa: O caractere @ geralmente é inválido na formação de identificadores).

R(2) = Sintático: se (x > 5) x := 1; (Justificativa: Falta a palavra reservada então exigida pela gramática da nossa pseudolinguagem).

R(3) = Lógico: area := base + altura; (Justificativa: Sintaxe e tipos válidos, mas a fórmula de área retangular correta exige multiplicação *, não soma +).

## Síntese

Complete:

- **Léxico** está relacionado a formação de palavras válidas (tokens) a partir de caracteres.
- **Sintaxe** está relacionada a estrutura, ordem e gramática das instruções.
- **Semântica** está relacionada a significado, regras de tipo, declaração e escopo.
- **Erro lógico** ocorre quando o código compila e executa, mas produz um resultado incorreto devido a falha no raciocínio ou no algoritmo.


