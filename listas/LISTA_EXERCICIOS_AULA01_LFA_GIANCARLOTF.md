# Lista de Exercícios — Aula 01

## Linguagens Formais e Autômatos

**Tema:** sintaxe, semântica e análise de código  
**Professor:** Murillo Edson de Carvalho Souza  
**Aluno(a):** Giancarlo Tabaczenski Fernandes  
**Turma:** ENGCDM3B **Data:** 07/08/2026

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
| 1 | “As flores são belas.” | A | Construção sintaticamente adequada |
| 2 | “As flores é bela.” | B | Apresenta um erro de concordância verbal (“é” em vez de “são”) e um erro de concordância nominal (“bela” em vez de “belas”) |
| 3 | “Vou corre hoje no parque.” | C | Apresenta um problema de flexão (“corre” em vez “correr”) |
| 4 | “Água bebeu José.” | B | Apresenta construção em ordem não usual, que pode ser interpretado como sintaticamente inválido |
| 5 | “O aluno acabou a prova.” | A | Construção sintaticamente adequada |

### Questões complementares

1. A sentença do item 4 é impossível em português ou apenas incomum na ordem mais frequente? Explique.

   **Resposta:**  
   A sentença não é impossível em português; porém, é incomum.  
   Interpretando “Água” como sujeito e “José” como objeto direto, observa-se que a estrutura sintática é válida. O estranhamento decorre da interpretação semântica, pois, no uso comum da língua, oespera-se que “José” seja o agente da ação de beber e que a “Água” seja o objeto.

2. Reescreva todas as sentenças problemáticas de maneira adequada ao português usual.

   **Resposta:**  
   “As flores são belas.”  
   “Vou correr hoje no parque.”  
   “José bebeu água.”

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

Classificação: S.

Justificativa:  
A atribuição está estruturalmente incorreta, pois um valor não pode ser atribuído a um literal numérico.

### Item 2

```text
então (a < 10) se;
```

Classificação: S.

Justificativa:  
A ordem dos elementos da estrutura condicional está errada.

### Item 3

```text
inteiro soma;
soma := 4.5;
```

Classificação: M.

Justificativa:  
Existe incompatibilidade entre os tipos, pois um valor `real` está sendo atribuído a uma variável do tipo `inteiro`.

### Item 4

```text
media := 10.0;
```

Considere que `media` não foi declarada anteriormente.

Classificação: M.

Justificativa:  
O uso de uma variável não declarada é tratado como erro semântico, uma vez que o compilador não consegue resolver o identificador na tabela de símbolos.

### Item 5

```text
real media;
media := 10.0;
```

Classificação: V.

Justificativa:  
O trecho é válido, pois segue as regras fornecidas.

### Item 6

```text
se a < 10 então
    a := a + 1;
```

Considere que `a` foi declarada como inteira.

Classificação: V.

Justificativa:  
O trecho é válido, pois segue as regras fornecidas.

---

## Exercício 3 — Ambiguidade e contexto

Explique a classe gramatical e o significado da palavra destacada em cada frase.

### Caso A — “caminho”

1. “Eu **caminho** todos os dias.”
2. “O **caminho** é longo.”

**Explicação:**  
1. Verbo. Indica a ação de andar ou percorrer a pé.  
2. Substantivo. Indica uma via ou extensão que se percorre.

### Caso B — “colher”

1. “Vou **colher** flores.”
2. “A **colher** caiu no chão.”

**Explicação:**  
1. Verbo. Indica a ação de pegar ou coletar algo, geralmente relacionado a plantas.  
2. Substantivo. Indica um utensílio de mesa/cozinha.

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
1. Variável do tipo inteiro e função, respectivamente.  
2. O compilador consulta a tabela de símbolos para obter as informações do identificador “soma”, como categoria, tipo e escopo em que foi declarado.

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
   Sim, o trecho não apresenta nenhuma discordância com as regras estabelecidas.

2. Há incompatibilidade de tipos ou uso de variável não declarada no trecho apresentado?

   **Resposta:**  
   Não, as variáveis “salario” e “novoSalario” foram declaradas como `real`, e a operação entre valores reais é compatível com o tipo declarado.

3. O programa realiza o objetivo proposto? Justifique.

   **Resposta:**  
   Não, pois o valor que deveria multiplicar o salário deveria ser `1.1` e não `11`.

4. Classifique o problema como erro sintático, erro semântico estático ou erro lógico.

   **Resposta:**  
   Erro lógico, porque o trecho é sintaticamente e semanticamente válido, mas a operação realizada não corresponde ao resultado esperado pelo programa.

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

1. análise léxica (*scanner*);
2. análise sintática (*parser*);
3. análise semântica.

### Parte B — O que cada etapa recebe e produz?

| Etapa | O que analisa? | Exemplo de problema detectado |
|---|---|---|
| Análise léxica | A sequência de caracteres do código-fonte | Detecção de símbolos ou palavras inválidas |
| Análise sintática | A organização dos tokens conforme as regras da linguagem | Detecção de ordem ou estrutura incorreta dos elementos |
| Análise semântica | O significado das estruturas | Detecção de uso de variável não declarada |

### Parte C — Fluxograma

Desenhe um fluxo contendo os seguintes elementos:

```text
Código-fonte → analisador léxico → tokens → analisador sintático → estrutura sintática
            → analisador semântico → código validado para as próximas etapas
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

- **Léxico** está relacionado à conversão da sequência de caracteres em tokens.
- **Sintaxe** está relacionada às regras de relação entre as palavras/tokens.
- **Semântica** está relacionada ao significado dos elementos e interpretação da sentença.
- **Erro lógico** ocorre quando o texto é aceito, mas o resultado não corresponde ao comportamento esperado.

