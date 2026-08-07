# Lista de Exercícios — Aula 01

## Linguagens Formais e Autômatos

**Tema:** sintaxe, semântica e análise de código  
**Professor:** Murillo Edson de Carvalho Souza  
**Aluno(a):** Eduardo Lima dos Santos  
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
| 1 | “As flores são belas.” | A | A frase está correta quanto à sintaxe, concordância e escrita. |
| 2 | “As flores é bela.” | B | Há erro de concordância verbal ("é" → "são") e nominal ("bela" → "belas"). |
| 3 | “Vou corre hoje no parque.” | C | A palavra "corre" foi escrita de forma inadequada. O correto é "correr". |
| 4 | “Água bebeu José.” | A | A estrutura sintática é válida, embora a ordem seja incomum. O sentido muda para indicar que "água" é o objeto bebido por José. |
| 5 | “O aluno acabou a prova.” | A | A construção está correta e é comum no português. |

### Questões complementares

1. A sentença do item 4 é impossível em português ou apenas incomum na ordem mais frequente? Explique.

   **Resposta:**  
   Não é impossível. A frase é apenas incomum na ordem mais frequente do português. A forma mais natural seria "José bebeu água." Na frase apresentada, ocorre inversão da ordem dos termos, recurso possível na língua.

2. Reescreva todas as sentenças problemáticas de maneira adequada ao português usual.

   **Resposta:**  
   - Item 2: “As flores são belas.” (concordância no plural)  
   - Item 3: “Vou correr hoje no parque.” (verbo principal no infinitivo)  
   - Item 4 (opcional, apenas para a ordem mais frequente): “José bebeu água.”

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

Classificação: **S**

Justificativa:  
O lado esquerdo de `:=` deve ser um destino de atribuição, ou seja, um identificador de variável. `45` é um literal inteiro e não pode ocupar essa posição, então a sequência de tokens não deriva da regra `variável := expressão`.  

### Item 2

```text
então (a < 10) se;
```

Classificação: **S**

Justificativa:  
A forma condicional definida é `se condição então comando`. Aqui as palavras reservadas aparecem em ordem invertida e não há comando após `então`, de modo que a sequência não corresponde a nenhuma produção da gramática.  

### Item 3

```text
inteiro soma;
soma := 4.5;
```

Classificação: **M**

Justificativa:  
As duas linhas seguem a gramática: há uma declaração bem formada e uma atribuição bem formada. O problema está na **compatibilidade de tipos**: `soma` foi declarada como `inteiro` e recebe o literal real `4.5`. 

### Item 4

```text
media := 10.0;
```

Considere que `media` não foi declarada anteriormente.

Classificação: **M**

Justificativa:  
A estrutura `identificador := literal ;` é sintaticamente perfeita; o analisador sintático a aceita sem qualquer problema. A violação é da regra “variáveis precisam ser declaradas antes do uso”, verificada por consulta à tabela de símbolos.  

### Item 5

```text
real media;
media := 10.0;
```

Classificação: **V**

Justificativa:  
A variável é declarada antes do uso, a atribuição respeita a forma `variável := expressão`, e o tipo do literal `10.0` (real) é compatível com o tipo declarado `real`. Não há violação sintática nem semântica frente às regras fornecidas.

### Item 6

```text
se a < 10 então
    a := a + 1;
```

Considere que `a` foi declarada como inteira.

Classificação: **V**

Justificativa:  
A construção segue exatamente a forma `se condição então comando`. A condição `a < 10` é uma comparação entre um inteiro e um literal inteiro, resultando em valor lógico — como esperado para uma condição. O comando `a := a + 1` atribui um inteiro a uma variável inteira. 

---

## Exercício 3 — Ambiguidade e contexto

Explique a classe gramatical e o significado da palavra destacada em cada frase.

### Caso A — “caminho”

1. “Eu **caminho** todos os dias.”
2. “O **caminho** é longo.”

**Explicação:**  
Em (1), **caminho** é **verbo** — 1ª pessoa do singular do presente do indicativo de “caminhar” — e significa a ação de andar a pé. O contexto que decide isso é o pronome “eu” antes dela e a ausência de determinante.  
Em (2), **caminho** é **substantivo** masculino e significa via, trajeto, percurso. O que sinaliza a classe é o artigo “o” antecedendo a palavra e o verbo “é” logo depois, que pede um sujeito nominal.  
Ou seja: a mesma sequência de caracteres (mesmo *token*, do ponto de vista léxico) tem classe e significado definidos apenas pelo **contexto sintático** em que aparece.

### Caso B — “colher”

1. “Vou **colher** flores.”
2. “A **colher** caiu no chão.”

**Explicação:**  
Em (1), **colher** é **verbo** no infinitivo, formando locução verbal com “vou”, e significa apanhar/recolher; “flores” é seu objeto direto.  
Em (2), **colher** é **substantivo** feminino, o utensílio de mesa; o artigo “a” e a função de sujeito do verbo “caiu” fixam essa leitura.  
Como no caso A, a desambiguação não vem da palavra isolada, mas dos elementos vizinhos — o analisador precisa da estrutura da frase, não apenas da cadeia de caracteres.

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
1.

No primeiro trecho, soma representa uma variável.

No segundo trecho, soma representa uma função.

2.

O compilador precisa consultar:

a tabela de símbolos;
o tipo do identificador;
o escopo onde ele foi declarado.

Assim consegue determinar se "soma" é uma variável, uma função ou outro identificador.

### Debate

Por que um compilador precisa considerar declarações, tipos e escopos para decidir se um código está correto?

**Anotações:**  
Porque apenas analisar a estrutura do código não é suficiente. O compilador precisa verificar se os identificadores foram declarados, se os tipos são compatíveis e se o uso respeita o escopo das declarações, garantindo que o programa faça sentido.

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
   Sim. O trecho está sintaticamente correto porque segue as regras da linguagem e pode ser analisado normalmente pelo compilador.

2. Há incompatibilidade de tipos ou uso de variável não declarada no trecho apresentado?

   **Resposta:**  
   Não. As variáveis foram declaradas corretamente e ambas possuem o tipo real, portanto não há incompatibilidade de tipos nem uso de variável não declarada.

3. O programa realiza o objetivo proposto? Justifique.

   **Resposta:**  
   Não. O objetivo era aumentar o salário em 10%, o que exige multiplicar por 1.1. Multiplicar por 11 faz o salário ficar onze vezes maior.

4. Classifique o problema como erro sintático, erro semântico estático ou erro lógico.

   **Resposta:**  
   Erro lógico.

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

1. Análise léxica (*scanner*)
2. Análise sintática (*parser*)
3. Análise semântica

### Parte B — O que cada etapa recebe e produz?

| Etapa | O que analisa? | Exemplo de problema detectado |
|---|---|---|
| Análise léxica | Recebe o código-fonte como uma sequência de caracteres e a agrupa em *tokens* (palavras reservadas, identificadores, números, operadores, delimitadores), descartando espaços e comentários. Produz a sequência de tokens. | Símbolo ou sequência que não forma nenhum token válido, como `@` fora de uma cadeia ou o número mal formado `12.3.4`. |
| Análise sintática | Recebe a sequência de tokens e verifica se sua **ordenação** deriva das regras da gramática. Produz a estrutura sintática (árvore sintática / árvore abstrata). | Ordem inválida na condicional, como `então (a < 10) se;` (Exercício 2, Item 2), ou `45 := a;`, ou um `;` faltando. |
| Análise semântica | Recebe a árvore sintática e verifica a **coerência** dos elementos, consultando a tabela de símbolos: declarações, tipos, escopos, número de argumentos. Produz a árvore anotada/validada para as próximas fases. | Uso de variável não declarada (`media := 10.0;`) ou incompatibilidade de tipos (`inteiro soma; soma := 4.5;`). |

### Parte C — Fluxograma

Desenhe um fluxo contendo os seguintes elementos:

```text
Código-fonte → análise léxica (scanner) → tokens → análise sintática (parser) → estrutura sintática
            → análise semântica → código validado para as próximas etapas
```

### Questão de reflexão

Por que a análise semântica normalmente depende dos resultados das análises léxica e sintática?

**Resposta:**  
Porque a análise semântica depende de uma estrutura sintática já construída. Primeiro o compilador identifica os tokens (análise léxica), depois verifica se eles estão organizados corretamente (análise sintática) e, somente então, consegue analisar o significado do programa, verificando tipos, declarações e escopos.

---

## Desafio opcional — Crie seus próprios exemplos

Crie três pequenos exemplos:

1. uma frase ou código com problema de escrita/tokenização;
2. uma construção com erro sintático;
3. um programa sintaticamente válido, mas com erro lógico.

Para cada exemplo, apresente a classificação e a justificativa.

### Exemplo 1 — Problema de escrita/tokenização

```text
real preç0 := 7..5;
```

**Classificação:** erro léxico.

**Justificativa:** dois problemas ocorrem antes de qualquer verificação de estrutura. `7..5` não corresponde a nenhum padrão de número da linguagem (um real admite um único ponto decimal), e `preç0` mistura um caractere não previsto na formação de identificadores. O *scanner* interrompe o processo por não conseguir produzir tokens válidos — a análise sintática nem chega a ser executada.

*Equivalente em língua natural:* “Eu xegei ontem.” — “xegei” não é uma palavra do léxico do português.

### Exemplo 2 — Erro sintático

```text
inteiro x;
se x > 0
    x := x - 1;
```

**Classificação:** erro sintático.

**Justificativa:** todos os tokens são válidos e o identificador `x` está devidamente declarado, mas falta a palavra reservada `então`, exigida pela forma `se condição então comando`. A sequência de tokens não deriva de nenhuma produção da gramática, e o erro é detectado pelo *parser* sem qualquer consulta a tipos ou declarações.

*Equivalente em língua natural:* “Os livro estão na mesa nova.” — palavras existentes, concordância/estrutura incorreta.

### Exemplo 3 — Sintaticamente válido, com erro lógico

```text
inteiro a;
inteiro b;
real media;

a := 8;
b := 6;
media := a + b / 2;
```

**Classificação:** erro lógico.

**Justificativa:** o trecho compila sem qualquer reclamação: todas as variáveis são declaradas antes do uso, a estrutura das atribuições é válida e os tipos são compatíveis. Porém a média não é calculada corretamente, porque a divisão tem precedência sobre a soma: o programa avalia `a + (b / 2)` = 8 + 3 = 11, em vez de `(a + b) / 2` = 7. A intenção do programador não é acessível ao compilador — o erro só aparece ao conferir o resultado.

**Correção:**

```text
media := (a + b) / 2;
```

---

## Síntese

Complete:

- **Léxico** está relacionado a **como os caracteres do código-fonte se agrupam em unidades mínimas com significado próprio, os *tokens* (palavras reservadas, identificadores, números, operadores); é a etapa que reconhece se cada “palavra” pertence ao vocabulário da linguagem**.
- **Sintaxe** está relacionada a **como esses tokens podem ser ordenados e combinados, isto é, às regras de estrutura (gramática) que definem quais sequências formam construções bem formadas, como `se condição então comando`**.
- **Semântica** está relacionada a **ao significado e à coerência das construções já reconhecidas: se os identificadores foram declarados, se estão no escopo correto, se os tipos são compatíveis e se as operações fazem sentido para os valores envolvidos**.
- **Erro lógico** ocorre quando **o programa é aceito pelo compilador e executa normalmente, mas produz um resultado diferente do pretendido, porque o que foi escrito não corresponde à intenção do programador (como usar `* 11` no lugar de `* 1.1`); só é revelado por testes, execução ou revisão do código**.
