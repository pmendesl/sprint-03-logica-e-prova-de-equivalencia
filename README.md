## Relatório da Sprint 03: Lógica Digital Aplicada

### 1. Modelagem da Lógica do Projeto Atualizado

**Cenário:**
Foi modelada a lógica de um sistema de alarme residencial simplificado. O alarme deve ser ativado (`S = 1`) se alguma das seguintes condições for verdadeira:

*   A **porta principal (`P`)** está aberta E o **sistema está ativado (`A`)**.
*   Uma **janela (`J`)** está aberta E o **sistema está ativado (`A`)**.
*   O **sensor de movimento (`M`)** detecta movimento E o **sistema está ativado (`A`)**.
*   O **botão de pânico (`B`)** é pressionado (independentemente do estado do sistema).

**Variáveis de Entrada:**
*   `A`: Sistema de alarme ativado (1) / desativado (0)
*   `P`: Porta principal aberta (1) / fechada (0)
*   `J`: Janela aberta (1) / fechada (0)
*   `M`: Movimento detectado (1) / nenhum movimento (0)
*   `B`: Botão de pânico pressionado (1) / não pressionado (0)

**Saída:**
*   `S`: Alarme disparado (1) / não disparado (0)

**Expressão Booleana Original:**
Com base nas condições descritas, a expressão booleana que representa a lógica atual completa do sistema é:

`S_original = (P . A) + (J . A) + (M . A) + B`

**Objetivo da Lógica:**
O objetivo desta lógica é garantir que o alarme dispare em situações de intrusão (porta, janela ou movimento detectado com o sistema ativado) ou em caso de emergência (botão de pânico pressionado). O sistema ativado (`A`) funciona como um habilitador para os sensores de porta, janela e movimento, enquanto o botão de pânico (`B`) tem prioridade e dispara o alarme independentemente do estado do sistema ou dos outros sensores.

### 2. Construção de um Modelo Simplificado da Lógica

**Expressão Original:**
`S_original = (P . A) + (J . A) + (M . A) + B`

**Método de Simplificação Utilizado:**
Foi utilizada a **Álgebra Booleana**, especificamente a **Propriedade Distributiva**, que afirma que `X . Y + X . Z = X . (Y + Z)`.

**Simplificação:**
Observando que o termo `A` é comum nos três primeiros produtos da expressão original, aplicamos a propriedade distributiva:

`S_simplificada = A . (P + J + M) + B`

**Justificativa das Simplificações:**
A aplicação da Propriedade Distributiva permite fatorar o termo comum `A` de uma soma de produtos. No contexto de circuitos lógicos, essa simplificação reduz o número de portas lógicas necessárias. Em vez de três portas AND separadas para `(P . A)`, `(J . A)` e `(M . A)`, e uma porta OR para somar seus resultados, a expressão simplificada requer apenas uma porta OR para `(P + J + M)` e uma única porta AND com `A`. Isso resulta em um circuito mais eficiente, com menor complexidade e custo de hardware.

**Expressão Simplificada:**

`S_simplificada = A . (P + J + M) + B`

### 3. Prova de Equivalência entre o Modelo Original e o Modelo Simplificado

Para provar a equivalência entre a expressão original e a simplificada, foi construída uma tabela verdade abrangendo todas as 32 combinações possíveis das 5 variáveis de entrada (`A`, `P`, `J`, `M`, `B`).

**Tabelas Verdade Comparativas (Original × Simplificado):**

| A | P | J | M | B | S_Original | S_Simplificada | Equivalente |
|---:|---:|---:|---:|---:|-----------:|---------------:|:------------|
| 0 | 0 | 0 | 0 | 0 | 0 | 0 | Sim |
| 0 | 0 | 0 | 0 | 1 | 1 | 1 | Sim |
| 0 | 0 | 0 | 1 | 0 | 0 | 0 | Sim |
| 0 | 0 | 0 | 1 | 1 | 1 | 1 | Sim |
| 0 | 0 | 1 | 0 | 0 | 0 | 0 | Sim |
| 0 | 0 | 1 | 0 | 1 | 1 | 1 | Sim |
| 0 | 0 | 1 | 1 | 0 | 0 | 0 | Sim |
| 0 | 0 | 1 | 1 | 1 | 1 | 1 | Sim |
| 0 | 1 | 0 | 0 | 0 | 0 | 0 | Sim |
| 0 | 1 | 0 | 0 | 1 | 1 | 1 | Sim |
| 0 | 1 | 0 | 1 | 0 | 0 | 0 | Sim |
| 0 | 1 | 0 | 1 | 1 | 1 | 1 | Sim |
| 0 | 1 | 1 | 0 | 0 | 0 | 0 | Sim |
| 0 | 1 | 1 | 0 | 1 | 1 | 1 | Sim |
| 0 | 1 | 1 | 1 | 0 | 0 | 0 | Sim |
| 0 | 1 | 1 | 1 | 1 | 1 | 1 | Sim |
| 1 | 0 | 0 | 0 | 0 | 0 | 0 | Sim |
| 1 | 0 | 0 | 0 | 1 | 1 | 1 | Sim |
| 1 | 0 | 0 | 1 | 0 | 1 | 1 | Sim |
| 1 | 0 | 0 | 1 | 1 | 1 | 1 | Sim |
| 1 | 0 | 1 | 0 | 0 | 1 | 1 | Sim |
| 1 | 0 | 1 | 0 | 1 | 1 | 1 | Sim |
| 1 | 0 | 1 | 1 | 0 | 1 | 1 | Sim |
| 1 | 0 | 1 | 1 | 1 | 1 | 1 | Sim |
| 1 | 1 | 0 | 0 | 0 | 1 | 1 | Sim |
| 1 | 1 | 0 | 0 | 1 | 1 | 1 | Sim |
| 1 | 1 | 0 | 1 | 0 | 1 | 1 | Sim |
| 1 | 1 | 0 | 1 | 1 | 1 | 1 | Sim |
| 1 | 1 | 1 | 0 | 0 | 1 | 1 | Sim |
| 1 | 1 | 1 | 0 | 1 | 1 | 1 | Sim |
| 1 | 1 | 1 | 1 | 0 | 1 | 1 | Sim |
| 1 | 1 | 1 | 1 | 1 | 1 | 1 | Sim |

**Breve Explicação da Equivalência:**
Conforme demonstrado na tabela verdade acima, as colunas `S_Original` e `S_Simplificada` apresentam exatamente os mesmos valores de saída para todas as 32 combinações possíveis das variáveis de entrada (`A`, `P`, `J`, `M`, `B`). A coluna `Equivalente` confirma que, em todos os cenários, as saídas são idênticas. Isso prova que a expressão simplificada `S_simplificada = A . (P + J + M) + B` é logicamente equivalente à expressão original `S_original = (P . A) + (J . A) + (M . A) + B`. A simplificação foi bem-sucedida em reduzir a complexidade da expressão sem alterar a funcionalidade lógica do sistema de alarme.

### Referências

*   [1] FIAP. *AULA_05__Teorema_de_DeMorgan.pdf*. Material didático de Ciência da Computação, Prof. Mauricio Neto. (Referência ao documento fornecido pelo usuário)
