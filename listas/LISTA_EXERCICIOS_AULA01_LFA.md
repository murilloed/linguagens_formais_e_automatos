# Lista de Exercícios — Aula 01

## Linguagens Formais e Autômatos

**Tema:** sintaxe, semântica e análise de código  
**Professor:** Murillo Edson de Carvalho Souza  
**Aluno(a):** Paula Ribeiro Moreira de Souza  
**Turma:** ENGCDM3B **Data:** 06/08/2026

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
| 1 | “As flores são belas.” | A | a semântics e a gramática estão de acordo com a língua portuguesa |
| 2 | “As flores é bela.” | C | a semântica está correta, mas a gramática do verbo "é" não está de acordo com a língua portuguesa |
| 3 | “Vou corre hoje no parque.” | C | a semântica está correta, mas a gramática do verbo "corre" não está de acordo com a língua portuguesa |
| 4 | “Água bebeu José.” | B | a semântica está incorreta, dificultando o entendimento e a gramática está de acordo com a língua portuguesa |
| 5 | “O aluno acabou a prova.” | A | a semântica e a gramática estão de acordo com a língua portuguesa |

### Questões complementares

1. A sentença do item 4 é impossível em português ou apenas incomum na ordem mais frequente? Explique.

   **Resposta:**  
   A sentença não é impossível em português, já que ela está gramaticalmente correta, porém não possui sentido lógico, prejudicando a semântica e tornando-a não adequada ao português usual

2. Reescreva todas as sentenças problemáticas de maneira adequada ao português usual.

   **Resposta:**  
   2. As flores são belas
   3. Vou correr hoje no parque
   4. José bebeu água

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

Classificação: M

Justificativa:  
erro na semântica, já que 45 é um valor constante e não pode receber o conteúdo de a

### Item 2

```text
então (a < 10) se;
```

Classificação: S

Justificativa:  
erro na sintaxe, já que a ordem está invertida

### Item 3

```text
inteiro soma;
soma := 4.5;
```

Classificação: M

Justificativa:  
a variável soma foi declarada como inteiro, mas recebeu um valor numérico

### Item 4

```text
media := 10.0;
```

Considere que `media` não foi declarada anteriormente.

Classificação: M

Justificativa:  
a variável media não foi declarada antes do uso

### Item 5

```text
real media;
media := 10.0;
```

Classificação: V

Justificativa:  
a variável media foi declarada como real e recebeu o valor 10.0, que também é real. Não há erro sintático nem semântico.

### Item 6

```text
se a < 10 então
    a := a + 1;
```

Considere que `a` foi declarada como inteira.

Classificação: V

Justificativa:  
a condição segue a estrutura se condição então comando, e a variável a foi declarada como inteira. A atribuição a := a + 1 também é compatível com o tipo da variável.
---

## Exercício 3 — Ambiguidade e contexto

Explique a classe gramatical e o significado da palavra destacada em cada frase.

### Caso A — “caminho”

1. “Eu **caminho** todos os dias.”
2. “O **caminho** é longo.”

**Explicação:**  
1. é um verbo
2. é um substantivo

### Caso B — “colher”

1. “Vou **colher** flores.”
2. “A **colher** caiu no chão.”

**Explicação:**  
1. é um verbo
2. é um substantivo

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
1. No primeiro trecho, o nome soma representa uma variável do tipo inteiro, que recebe o valor 10.

No segundo trecho, o nome soma representa uma função que recebe dois números inteiros e retorna a adição entre eles.

2. O compilador precisa consultar as declarações, os tipos dos elementos e o escopo em que o nome está sendo utilizado. Assim, ele consegue identificar se soma representa uma variável ou uma função em cada contexto.

### Debate

Por que um compilador precisa considerar declarações, tipos e escopos para decidir se um código está correto?

**Anotações:**  
Porque essas informações determinam como cada elemento deve ser interpretado. As declarações indicam quais variáveis e funções existem, os tipos mostram quais valores e operações são permitidos, e os escopos definem em quais partes do programa cada nome pode ser utilizado.

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
   Sim. O trecho está sintaticamente correto porque as declarações e a atribuição seguem a estrutura definida pela pseudolinguagem.

2. Há incompatibilidade de tipos ou uso de variável não declarada no trecho apresentado?

   **Resposta:**  
   Não. As variáveis salario e novoSalario foram declaradas como reais, e a operação de multiplicação também produz um valor real.

3. O programa realiza o objetivo proposto? Justifique.

   **Resposta:**  
   Não. O objetivo era conceder um aumento de 10%, mas o código multiplica o salário por 11. Isso faz o resultado ser onze vezes o salário original, em vez de representar um aumento de apenas 10%.

4. Classifique o problema como erro sintático, erro semântico estático ou erro lógico.

   **Resposta:**  
   O problema é um erro lógico, pois o código é aceito pelo compilador e executado, mas produz um resultado diferente do objetivo proposto.

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

1. análise léxica
2. análise sintática 
3. análise semântica

### Parte B — O que cada etapa recebe e produz?

| Etapa | O que analisa? | Exemplo de problema detectado |
|---|---|---|
| Análise léxica | Analisa os caracteres do código e os organiza em tokens. | Palavra ou símbolo que não pode ser reconhecido como token válido. |
| Análise sintática | Analisa a ordem e a estrutura dos tokens conforme a gramática da linguagem. | Comando escrito em ordem incorreta, como então condição se. |
| Análise semântica | Analisa o significado das estruturas, as declarações e a compatibilidade de tipos. | Utilização de variável não declarada ou atribuição de valor real a uma variável inteira. |

### Parte C — Fluxograma

Desenhe um fluxo contendo os seguintes elementos:

```text
Código-fonte → análise léxica → tokens → análise sintática → estrutura sintática
            → análise semântica → código validado para as próximas etapas
```

### Questão de reflexão

Por que a análise semântica normalmente depende dos resultados das análises léxica e sintática?

**Resposta:**  
A análise semântica depende das análises léxica e sintática porque, antes de verificar o significado do código, o compilador precisa reconhecer os tokens e organizar esses tokens em uma estrutura válida. Somente depois disso ele consegue verificar declarações, tipos, escopos e compatibilidade entre os elementos.

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

- **Léxico** está relacionado ao reconhecimento dos caracteres, palavras, símbolos e tokens da linguagem.
- **Sintaxe** está relacionada à ordem e à estrutura dos elementos conforme as regras da linguagem.
- **Semântica** está relacionada a ao significado das estruturas, às declarações, aos tipos e aos escopos.
- **Erro lógico** ocorre quando o código é aceito e executado, mas produz um resultado diferente do esperado.

