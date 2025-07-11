# 🕵️ AgenteSherlock: Seu Detetive de Bugs

**AgenteSherlock** é um modo especializado para ajudá-lo a identificar, analisar e resolver bugs em seu código. Ele atua como um detetive metódico, guiando-o passo a passo para encontrar a causa raiz dos problemas e propor soluções eficazes.

## 🎯 Objetivo Principal

O objetivo do AgenteSherlock é auxiliá-lo no processo de depuração de código de maneira estruturada. Ele o ajudará a:

*   Esclarecer o problema: entender o comportamento anômalo versus o esperado.
*   Formular hipóteses sobre a causa do erro.
*   Sugerir passos concretos de depuração (inspeção de variáveis, logging, etc.).
*   Propor modificações no código para corrigir os bugs.

## 💡 Quando Usá-lo?

Use o AgenteSherlock quando você enfrentar:

*   Erros explícitos (exceções, mensagens de erro).
*   Comportamento inesperado do seu código.
*   Necessidade de uma segunda opinião especializada para rastrear um bug difícil.
*   Bloqueios onde você não sabe como continuar com a depuração.

## 🔧 Ferramentas Recomendadas (para plataformas como o Cursor)

*   **`Edit`**: Ativado. O AgenteSherlock o usará para sugerir alterações em seu código.
*   **`Run`**: Usar com cautela. O AgenteSherlock pode sugerir a execução de código para testar hipóteses. Certifique-se de fazê-lo em um ambiente seguro e controlado.
*   **`Search`**: Opcional. Pode ser útil se o bug envolver múltiplos arquivos, mas o agente se concentrará principalmente no código fornecido.

## ⚙️ Modelo Padrão (Sugestão)

*   Recomenda-se um modelo com boas capacidades de raciocínio lógico e compreensão de código, como **Gemini Pro**, **GPT-4**, ou **Claude 3 Sonnet/Opus**. "Automático" geralmente é uma boa escolha se a plataforma o gerenciar bem.

## 🗣️ Exemplo Básico de Interação

**Usuário:**
`/start_debug AgenteSherlock, tenho um problema com esta função Python. Ela deveria somar dois números, mas às vezes retorna um resultado incorreto.`
```python
def soma(a, b):
  return a + b + 1 # Ops, um bug intencional
```
`Quando chamo soma(2, 2), obtenho 5 em vez de 4.`

**AgenteSherlock (Resposta Esperada):**
```
---PENSAMENTO---
pt1. O usuário forneceu o código, o resultado obtido e o esperado.
pt2. O bug parece estar na linha `return a + b + 1`.
---
🕵️: Entendido. Parece que há uma operação extra na sua função `soma`.

🔍 **Análise do Problema:**
A função `soma` é definida como `def soma(a, b): return a + b + 1;`.
Quando você a chama com `soma(2, 2)`:
1. `a` é `2`.
2. `b` é `2`.
3. A operação `a + b` resulta em `4`.
4. Em seguida, um `1` adicional é somado, resultando em `5`.

O comportamento esperado para `soma(2, 2)` é `4`.

💡 **Hipótese:**
O `+ 1` adicional na declaração de retorno é a causa do bug.

🛠️ **Sugestão de Correção:**
Para que a função retorne a soma correta de `a` e `b`, sugiro modificar a linha de retorno.

Gostaria que eu mostrasse como a linha corrigida deveria ficar?
```

## 🔗 System Prompt

Para instruções completas do sistema, consulte o arquivo `Prompt.md` no diretório principal do AgenteSherlock. (Este link idealmente apontaria para o `Prompt.md` original, já que não é traduzido).
