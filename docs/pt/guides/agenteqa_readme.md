# 🧪 AgenteQA: Seu Especialista em Geração de Testes

**AgenteQA** é um modo projetado para auxiliá-lo na criação de testes de software. Ele ajuda a identificar casos de teste, gerar código para testes unitários, de integração (conceitualmente) e a definir cenários para testes de comportamento, garantindo que seu código funcione como esperado.

## 🎯 Objetivo Principal

O objetivo do AgenteQA é ajudá-lo a:

*   **Identificar Casos de Teste:** Descobrir cenários relevantes para testar seu código, incluindo o caminho feliz, casos de borda, entradas inválidas e condições de erro.
*   **Gerar Código de Testes Unitários:** Escrever o código necessário para testar unidades isoladas do seu software (funções, métodos, classes pequenas).
*   **Definir Testes de Integração:** Ajudar a conceituar como testar a interação entre diferentes componentes ou módulos.
*   **Esboçar Testes de Comportamento (BDD):** Ajudar a escrever cenários em formato Gherkin (Given-When-Then), se necessário.
*   **Promover Boas Práticas de Teste:** Fomentar a criação de testes claros, de fácil manutenção e eficazes.

## 💡 Quando Usá-lo?

Utilize o AgenteQA quando:

*   Você está desenvolvendo novas funcionalidades e quer garantir sua qualidade desde o início (TDD ou BDD).
*   Você precisa aumentar a cobertura de testes de um código existente.
*   Você quer verificar se uma refatoração não introduziu regressões.
*   Você não tem certeza de quais casos de teste são importantes para uma parte específica do código.
*   Você precisa de ajuda para escrever o "boilerplate" ou a estrutura dos seus arquivos de teste.

## ✅ Considerações Chave

*   **Frameworks de Teste:** O AgenteQA tentará se adaptar ao framework de teste que você especificar (ex: `pytest` para Python, `JUnit` para Java, `Jest` ou `Mocha` para JavaScript/TypeScript, etc.). Se você não especificar um, ele poderá perguntar ou usar um comum para a linguagem.
*   **Tipos de Teste:**
    *   **Unitários:** Foco principal. Testam a menor unidade de código de forma isolada.
    *   **Integração:** O AgenteQA pode ajudar a definir quais interações testar e como esses testes podem ser estruturados, mas a implementação completa pode exigir mais contexto do sistema.
    *   **E2E/Comportamento:** Pode ajudar a escrever os cenários (ex: em Gherkin), mas a automação desses testes geralmente depende de ferramentas específicas fora do alcance da simples geração de código.
*   **Cobertura vs. Qualidade:** O AgenteQA o ajudará a gerar testes, mas lembre-se que o objetivo não é apenas 100% de cobertura, mas ter testes significativos que realmente validem o comportamento esperado e os casos críticos.

## 🔧 Ferramentas Recomendadas (para plataformas como o Cursor)

*   **`Edit`**: Ativado. Essencial para que o AgenteQA escreva o código dos testes em seus arquivos.
*   **`Search`**: Opcional. Pode ser útil para entender dependências se estiver gerando testes para código que interage com outras partes do sistema.

## ⚙️ Modelo Padrão (Sugestão)

*   Um modelo com boa compreensão de código e conhecimento de diversos frameworks de teste é ideal. **Gemini Pro**, **GPT-4**, ou **Claude 3 Opus/Sonnet** são boas opções.

## 🗣️ Exemplo Básico de Interação (Teste Unitário Python com Pytest)

**Usuário:**
`AgenteQA, preciso gerar testes unitários para esta função em Python. Estou usando pytest.`
```python
# utils.py
def dividir(a, b):
    if b == 0:
        raise ValueError("Não se pode dividir por zero")
    return a / b
```
`Quero testar o caso normal e a divisão por zero.`

**AgenteQA (Resposta Esperada):**
```
---PENSAMENTO---
pt1. O usuário quer testes unitários para a função `dividir` em Python usando `pytest`.
pt2. Casos a cobrir: divisão normal e `ValueError` em divisão por zero.
pt3. Gerar um arquivo de teste `test_utils.py` com duas funções de teste.
---
🧪 Entendido! `AgenteQA` pronto para garantir a qualidade da sua função `dividir`. Vamos criar alguns testes com `pytest`.

🔍 **Análise da Função:**
# ... (resto do exemplo como no original) ...
```

## 🔗 System Prompt

Para instruções completas do sistema, consulte o arquivo `Prompt.md` no diretório principal do AgenteQA.
