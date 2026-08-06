# Lista de Exercícios — Aula 01

## Linguagens Formais e Autômatos

**Tema:** sintaxe, semântica e análise de código  
**Professor:** Murillo Edson de Carvalho Souza  
**Aluno(a):** Giancarlo Tabaczenski Fernandes  
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
| 1 | “As flores são belas.” | A |  |
| 2 | “As flores é bela.” | B |  |
| 3 | “Vou corre hoje no parque.” | C |  |
| 4 | “Água bebeu José.” | B |  |
| 5 | “O aluno acabou a prova.” | A |  |

### Questões complementares

1. A sentença do item 4 é impossível em português ou apenas incomum na ordem mais frequente? Explique.

   **Resposta:**  
   ____________________________________________________________________________  
   ____________________________________________________________________________

2. Reescreva todas as sentenças problemáticas de maneira adequada ao português usual.

   **Resposta:**  
   “As flores são belas.”  
   “Vou correr hoje no parque.”  
   “José bebeu Água.”

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

Justificativa:  
____________________________________________________________________________  
____________________________________________________________________________

### Item 2

```text
então (a < 10) se;
```

Classificação: S

Justificativa:  
____________________________________________________________________________  
____________________________________________________________________________

### Item 3

```text
inteiro soma;
soma := 4.5;
```

Classificação: M

Justificativa:  
____________________________________________________________________________  
____________________________________________________________________________

### Item 4

```text
media := 10.0;
```

Considere que `media` não foi declarada anteriormente.

Classificação: M

Justificativa:  
____________________________________________________________________________  
____________________________________________________________________________

### Item 5

```text
real media;
media := 10.0;
```

Classificação: V

Justificativa:  
____________________________________________________________________________  
____________________________________________________________________________

### Item 6

```text
se a < 10 então
    a := a + 1;
```

Considere que `a` foi declarada como inteira.

Classificação: V

Justificativa:  
____________________________________________________________________________  
____________________________________________________________________________

---

## Exercício 3 — Ambiguidade e contexto

Explique a classe gramatical e o significado da palavra destacada em cada frase.

### Caso A — “caminho”

1. “Eu **caminho** todos os dias.”
2. “O **caminho** é longo.”

**Explicação:**  
1) Verbo.  
2) Substantivo.

### Caso B — “colher”

1. “Vou **colher** flores.”
2. “A **colher** caiu no chão.”

**Explicação:**  
1) Verbo.  
2) Substantivo.

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
1) Variável e função, respectivamente.  
2) 

### Debate

Por que um compilador precisa considerar declarações, tipos e escopos para decidir se um código está correto?

**Anotações:**  
____________________________________________________________________________  
____________________________________________________________________________  
____________________________________________________________________________

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
   __________________________________________________________________________  
   __________________________________________________________________________

2. Há incompatibilidade de tipos ou uso de variável não declarada no trecho apresentado?

   **Resposta:**  
   __________________________________________________________________________  
   __________________________________________________________________________

3. O programa realiza o objetivo proposto? Justifique.

   **Resposta:**  
   __________________________________________________________________________  
   __________________________________________________________________________

4. Classifique o problema como erro sintático, erro semântico estático ou erro lógico.

   **Resposta:**  
   __________________________________________________________________________

5. Corrija a linha responsável pelo problema.

```text


```

---

## Exercício 5 — Ordem de processamento

Organize as etapas abaixo na ordem didática mais comum de um compilador:

- análise semântica;
- análise léxica (*scanner*);
- análise sintática (*parser*).

### Parte A — Lista numerada

1. análise léxica (*scanner*);
2. análise sintática (*parser*);
3. análise semântica.

### Parte B — O que cada etapa recebe e produz?

| Etapa | O que analisa? | Exemplo de problema detectado |
|---|---|---|
| Análise léxica |  |  |
| Análise sintática |  |  |
| Análise semântica |  |  |

### Parte C — Fluxograma

Desenhe um fluxo contendo os seguintes elementos:

```text
Código-fonte → __________ → tokens → __________ → estrutura sintática
            → __________ → código validado para as próximas etapas
```

### Questão de reflexão

Por que a análise semântica normalmente depende dos resultados das análises léxica e sintática?

**Resposta:**  
____________________________________________________________________________  
____________________________________________________________________________  
____________________________________________________________________________

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

