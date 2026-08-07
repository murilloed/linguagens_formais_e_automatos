# Respostas — Lista de Exercícios da Aula 01

## Linguagens Formais e Autômatos

**Tema:** sintaxe, semântica e análise de código 
**Professor:** Murillo Edson de Carvalho Souza
**Aluno(a):** Pedro Henrique Alves Castello Branco - 2412082057
**Turma:** Matutino **Data:** 07/08/2026

---

## Exercício 1 — Classificação em linguagem natural

| Item | Sentença | Classificação | Justificativa |
|---:|---|:---:|---|
| 1 | “As flores são belas.” | **A** | A sentença apresenta ordem usual e concordância correta entre artigo, substantivo, verbo e predicativo. |
| 2 | “As flores é bela.” | **B** | Há erro de concordância: o sujeito está no plural, portanto o verbo e o predicativo também devem ficar no plural. |
| 3 | “Vou corre hoje no parque.” | **C** | Depois do verbo auxiliar “vou”, deve-se usar o infinitivo “correr”, e não a forma “corre”. É um problema de flexão verbal. |
| 4 | “Água bebeu José.” | **B** | Adotando como critério a ordem mais comum do português, a frase está fora da ordem usual sujeito–verbo–objeto. A forma esperada é “José bebeu água”. Em um contexto literário ou de topicalização, porém, a ordem apresentada pode ser interpretada. |
| 5 | “O aluno acabou a prova.” | **A** | A sentença tem estrutura adequada e concordância correta. |

### Questões complementares

1. **A sentença do item 4 é impossível em português ou apenas incomum?**

   Ela não é impossível. É uma construção incomum na fala cotidiana, pois apresenta o objeto antes do verbo e o sujeito depois dele. Dependendo do contexto e da entonação, pode haver topicalização ou efeito literário. Na ordem mais frequente do português, seria “José bebeu água”.

2. **Reescrita das sentenças problemáticas:**

   - Item 2: “As flores são belas.”
   - Item 3: “Vou correr hoje no parque.”
   - Item 4: “José bebeu água.”

---

## Exercício 2 — Sintaxe e semântica na programação

### Item 1

```text
45 := a;
```

**Classificação: M — Semântico.**

**Justificativa:** a instrução tem a aparência de uma atribuição, mas o lado esquerdo deveria indicar um local que possa receber e armazenar um valor, como uma variável. O literal `45` é um valor constante e não pode receber o conteúdo de `a`. O critério adotado considera a possibilidade de atribuição como uma restrição semântica. Se a gramática da linguagem exigir explicitamente um identificador no lado esquerdo, um compilador também poderá apontar o problema durante a análise sintática.

### Item 2

```text
então (a < 10) se;
```

**Classificação: S — Sintático.**

**Justificativa:** os elementos não estão na ordem definida pela pseudolinguagem. A estrutura esperada é `se condição então comando`.

### Item 3

```text
inteiro soma;
soma := 4.5;
```

**Classificação: M — Semântico.**

**Justificativa:** `soma` foi declarada como inteira, mas `4.5` é um valor real. A estrutura da atribuição está correta, porém os tipos são incompatíveis, desconsiderando qualquer conversão implícita que não foi definida no enunciado.

### Item 4

```text
media := 10.0;
```

**Classificação: M — Semântico.**

**Justificativa:** a atribuição tem estrutura reconhecível, mas `media` é usada sem ter sido declarada, contrariando uma regra da pseudolinguagem.

### Item 5

```text
real media;
media := 10.0;
```

**Classificação: V — Válido.**

**Justificativa:** a variável foi declarada antes do uso e o valor real `10.0` é compatível com seu tipo.

### Item 6

```text
se a < 10 então
    a := a + 1;
```

**Classificação: V — Válido.**

**Justificativa:** considerando que `a` foi declarada como inteira, a condição compara valores compatíveis e o comando soma e atribui valores inteiros. A estrutura também segue a forma condicional apresentada no enunciado.

---

## Exercício 3 — Ambiguidade e contexto

### Caso A — “caminho”

1. Em “Eu **caminho** todos os dias”, `caminho` é um **verbo**, a primeira pessoa do singular do presente do indicativo do verbo *caminhar*. Significa praticar a ação de andar.
2. Em “O **caminho** é longo”, `caminho` é um **substantivo**. Significa uma via, trajeto ou percurso.

O artigo `o`, o pronome `eu`, a posição da palavra e sua relação com os outros termos permitem identificar a classe gramatical e o significado adequado em cada contexto.

### Caso B — “colher”

1. Em “Vou **colher** flores”, `colher` é um **verbo no infinitivo**. Significa retirar ou apanhar flores.
2. Em “A **colher** caiu no chão”, `colher` é um **substantivo**. Refere-se ao utensílio usado para comer ou servir alimentos.

O verbo auxiliar `vou` seleciona o infinitivo no primeiro caso, enquanto o artigo `a` indica o uso como substantivo no segundo.

### Caso C — programação

1. No primeiro trecho, `soma` é o nome de uma **variável inteira**, que recebe o valor `10`. No segundo, `soma` é o nome de uma **função**, que recebe dois parâmetros inteiros e retorna a adição deles.
2. Para interpretar o nome corretamente, o compilador precisa consultar a **tabela de símbolos** e verificar a declaração associada ao identificador, sua categoria (variável ou função), seu tipo, seus parâmetros, seu escopo e o ponto do programa em que ele é usado.

### Debate

Um compilador precisa considerar declarações, tipos e escopos porque a forma do código, sozinha, não determina se cada uso é válido. As declarações informam quais nomes existem; os tipos determinam quais operações e atribuições são compatíveis; e os escopos indicam qual declaração está visível em determinado ponto. Essas informações permitem detectar, por exemplo, variável não declarada, atribuição incompatível, chamada de função com argumentos incorretos ou referência à declaração errada.

---

## Exercício 4 — Validade e erros lógicos

Código apresentado:

```text
real salario;
real novoSalario;

novoSalario := salario * 11;
```

1. **O trecho está sintaticamente correto?**  
   Sim. As declarações e a atribuição obedecem às formas da pseudolinguagem, e os operadores estão em posições válidas.

2. **Há incompatibilidade de tipos ou uso de variável não declarada?**  
   Não. `salario` e `novoSalario` foram declaradas como reais. Multiplicar um valor real pelo número inteiro `11` produz um valor numérico que pode ser atribuído a `novoSalario`.

3. **O programa realiza o objetivo proposto?**  
   Não. Multiplicar por `11` produz um valor igual a onze vezes o salário original, e não um salário com aumento de 10%. Para acrescentar 10%, o fator correto é `1.1`.

4. **Classificação do problema:**  
   É um **erro lógico**. O código é aceito e executado, mas o cálculo implementado não corresponde ao objetivo desejado.

5. **Linha corrigida:**

```text
novoSalario := salario * 1.1;
```

---

## Exercício 5 — Ordem de processamento

### Parte A — Lista numerada

1. Análise léxica (*scanner*).
2. Análise sintática (*parser*).
3. Análise semântica.

### Parte B — O que cada etapa recebe e produz?

| Etapa | O que analisa? | O que produz? | Exemplo de problema detectado |
|---|---|---|---|
| Análise léxica | A sequência de caracteres do código-fonte, agrupando-a em unidades válidas | Uma sequência de *tokens* | Caractere ou sequência que não forma um token válido da linguagem |
| Análise sintática | A sequência de *tokens* e sua organização segundo a gramática | Uma estrutura sintática, normalmente uma árvore | Palavras-chave em ordem inválida, como `então condição se` |
| Análise semântica | A estrutura sintática em conjunto com declarações, tipos e escopos | Uma estrutura anotada e validada para as próximas etapas | Variável não declarada ou atribuição entre tipos incompatíveis |

### Parte C — Fluxograma

```text
Código-fonte
     ↓
Análise léxica (scanner)
     ↓
   tokens
     ↓
Análise sintática (parser)
     ↓
estrutura sintática
     ↓
Análise semântica
     ↓
código validado para as próximas etapas
```

### Questão de reflexão

A análise semântica depende das etapas anteriores porque primeiro é necessário reconhecer os caracteres como *tokens* e organizar esses *tokens* em uma estrutura gramatical. Somente com essa estrutura é possível saber o papel de cada elemento e então verificar declarações, tipos, escopos e compatibilidade das operações. Se os *tokens* ou a estrutura não forem reconhecidos, não há uma interpretação confiável sobre a qual aplicar as regras semânticas.

---

## Desafio opcional — Exemplos

1. **Problema de escrita/tokenização**

   ```text
   inteiro total@;
   ```

   **Classificação:** erro léxico.  
   **Justificativa:** considerando que `@` não pertence ao alfabeto permitido para identificadores nem representa outro token da linguagem, o analisador léxico não consegue formar um token válido com `total@`.

2. **Erro sintático**

   ```text
   se então x < 5 x := x + 1;
   ```

   **Classificação:** erro sintático.  
   **Justificativa:** os componentes não seguem a ordem `se condição então comando`.

3. **Programa válido com erro lógico**

   ```text
   real base;
   real altura;
   real area;
   area := base + altura;
   ```

   **Classificação:** erro lógico.  
   **Justificativa:** as variáveis estão declaradas, os tipos são compatíveis e a atribuição é sintaticamente válida, mas a área de um retângulo deveria ser calculada por `base * altura`, não por uma soma.

---

## Síntese

- **Léxico** está relacionado ao reconhecimento dos caracteres e à formação de *tokens* válidos.
- **Sintaxe** está relacionada à organização dos *tokens* conforme as regras gramaticais da linguagem.
- **Semântica** está relacionada ao significado das construções e à validade de declarações, tipos, escopos e operações.
- **Erro lógico** ocorre quando o programa é sintática e semanticamente aceito, mas produz um resultado diferente do objetivo pretendido.

