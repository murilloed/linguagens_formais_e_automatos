# Lista de Exercícios — Aula 01

## Linguagens Formais e Autômatos

**Tema:** sintaxe, semântica e análise de código  
**Professor:** Murillo Edson de Carvalho Souza
**Aluno(a):** João Pedro Alves dos Santos Reis  
**Turma:** MDC078 **Data:** 07/08/2026

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
| 1 | “As flores são belas.”   | A | Adequada | A construção sintática está adequada no português usual.|
| 2 | “As flores é bela.” | C | Problema de formação/escrita| A palavra escrita ou flexionada de forma inadequada para o contexto, pois não há flexão do verbo "é" (singular) para "São" (plural).|
| 3 | “Vou corre hoje no parque.” | C | Problema de formação/escrita| A palavra escrita ou flexionada de forma inadequada para o contexto, pois não há flexão do verbo "correr" no infinitivo. |
| 4 | “Água bebeu José.” | B | Problema sintático| Problema de ordem, concordância ou estrutura, a frase não faz sentido e sua ordem e estrutura não fazem sentido.|  
| 5 | “O aluno acabou a prova.” | A | Adequada | A construção sintática está adequada no português usual.|

### Questões complementares

1. A sentença do item 4 é impossível em português ou apenas incomum na ordem mais frequente? Explique.

   **Resposta:**  
  É possível, mas estaria errado de acordo com a norma padrão da língua portuguesa.

2. Reescreva todas as sentenças problemáticas de maneira adequada ao português usual.

   **Resposta:**  
   2) "As flores são belas"
   3) "Vou correr hoje no parque"
   4) "José bebeu água"
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
Reconhecemos a estrutura de que há uma igualdade entre dois valores, mas não é compatível ou válido, pois há comparação de um número inteiro com uma variável.

### Item 2

```text
então (a < 10) se;
```

Classificação: S

Justificativa:  
Pois, a estrutura correta, seria se (a < 10) então. Por isso pode ser reconhecida, mas está errada.

### Item 3

```text
inteiro soma;
soma := 4.5;
```

Classificação: V

Justificativa:  
Não há erro, pois a variável é declarada e comparada com o valor corretamente.

### Item 4

```text
media := 10.0;
```

Considere que `media` não foi declarada anteriormente.

Classificação: M

Justificativa:  
A estrutura é reconhecida, mas está incorreta, pois não há declaração da variável media e sendo assim não há declaração do valor 10 pra media, pois ele não foi declarado antes.

### Item 5

```text
real media;
media := 10.0;
```

Classificação: V

Justificativa:  
Correto, pois dessa vez a variável media foi declarada corretamente.

### Item 6

```text
se a < 10 então
    a := a + 1;
```

Considere que `a` foi declarada como inteira.

Classificação: V

Justificativa:  
Correta, pois a variável #a foi declarada corretamente antes de ser comparada com o valor.

---

## Exercício 3 — Ambiguidade e contexto

Explique a classe gramatical e o significado da palavra destacada em cada frase.

### Caso A — “caminho”

1. “Eu **caminho** todos os dias.”
2. “O **caminho** é longo.”



**Explicação:**  
Na primeira frase a palavra caminho é um verbo, "caminhar". Já na segunda frase, o caminho é substantivo.

### Caso B — “colher”

1. “Vou **colher** flores.”
2. “A **colher** caiu no chão.”

**Explicação:**  
Na primeira frase a palavra colher é um verbo, no infinitivo. Na segunda a palavra colher é substantivo.

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
1) No primeiro, o soma é uma variável que é relacionado ao valor 10. Na segunda parte o soma é uma função que soma o inteiro a e o inteiro b.
2) No primeiro, ele vê a declaração de #soma como inteiro e após isso #soma com o valor 10. Na segunda a soma agora é uma função e

### Debate

Por que um compilador precisa considerar declarações, tipos e escopos para decidir se um código está correto?

**Anotações:**  
Para assim ter uma regra ou norma para ser seguida, para que assim diga o que está certo ou errado no código, assim como na língua portuguesa.

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
   Sim, pois a estrutura está correta e até por isso foi também compilada.

2. Há incompatibilidade de tipos ou uso de variável não declarada no trecho apresentado?

   **Resposta:**  
  Não, pois na lógica de estrutura das variáveis elas estão sendo feitas e declaradas corretamente
  
3. O programa realiza o objetivo proposto? Justifique.

   **Resposta:**  
  Não, pois o que é pedido é tanto um aumento de 1,1 no salário, mas no código há uma multiplicação com 11, não 1,1, sendo assim um valor maior que o pedido. 

4. Classifique o problema como erro sintático, erro semântico estático ou erro lógico.

   **Resposta:**  
   Erro semântico, pois há estrutura reconhecida, mas seus elementos são compatíveis.

5. Corrija a linha responsável pelo problema.

```text
real salario;
real novoSalario;

novoSalario := salario * 1.1;
```
---

## Exercício 5 — Ordem de processamento

Organize as etapas abaixo na ordem didática mais comum de um compilador:

- análise semântica;
- análise léxica (*scanner*);
- análise sintática (*parser*).

### Parte A — Lista numerada

1. Análise Léxica
2. Análise Sintática
3. Análise Semântica

### Parte B — O que cada etapa recebe e produz?

| Etapa | O que analisa? | Exemplo de problema detectado |
|---|---|---|
| Análise léxica | Entrada de caractere por caractere e as unidades básicas de significado | Caracteres inválidos e tokens não reconhecidos |
| Análise sintática | Se a sequência de tokens da análise léxica, está certa  | Erros na estrutura gramatical e operadores em locais inesperados |
| Análise semântica | O significado e a lógica por trás da estrutura sintática | Variáveis não declaradas e incompatibilidades de tipos (multiplicar um inteiro por string). |

### Parte C — Fluxograma

Desenhe um fluxo contendo os seguintes elementos:

```text
Código-fonte → Análise léxica → tokens → Análise Sintática → estrutura sintática
            → Análise Semântica → código validado para as próximas etapas
```

### Questão de reflexão

Por que a análise semântica normalmente depende dos resultados das análises léxica e sintática?

**Resposta:**  
Pois ela utiliza árvores sintáticas, geradas pelas análises sintáticas e para verificar as coerência lógica dos programas.

---

## Desafio opcional — Crie seus próprios exemplos

Crie três pequenos exemplos:

1. uma frase ou código com problema de escrita/tokenização;
2. uma construção com erro sintático;
3. um programa sintaticamente válido, mas com erro lógico.

Para cada exemplo, apresente a classificação e a justificativa.

1) Isso seria um problema de Analise Léxica. EX: String nome = "Maria;
2) Isso seria um problema de Analise Sintática. EX: int a = 5 + ;
3) Isso seria um problema de Analise Semântica. EX: 45:= a;

## Síntese

Complete:

- **Léxico** está relacionado a escrita  e tokens .
- **Sintaxe** está relacionada a se os tokens ou escritas estão certos.
- **Semântica** está relacionada a significado e lógica da estrutura sintática.
- **Erro lógico** ocorre quando é executado com sucesso, mas o resultado não está correto ou é o esperado.

---------------------------------------------
**Prompt usado**

Pode me dar exemplos de erros de análises léxicas, sintáticas e semânticas.
