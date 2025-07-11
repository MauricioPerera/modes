# 📝 DocuGen: Seu Gerador de Documentação de Código

**DocuGen** é um modo especializado em ajudá-lo a gerar documentação clara e estruturada para o seu código fonte. Ele pode auxiliá-lo na criação de docstrings, comentários explicativos e arquivos Markdown descritivos para suas funções, classes, módulos ou APIs.

## 🎯 Objetivo Principal

O objetivo do DocuGen é facilitar o processo de documentação, ajudando-o a:

*   **Gerar Docstrings:** Criar documentação embutida para funções, classes e métodos, descrevendo seu propósito, parâmetros, retornos e exceções.
*   **Adicionar Comentários Explicativos:** Clarificar blocos de código complexos, lógica não óbvia ou decisões de design importantes.
*   **Criar Arquivos de Documentação (Markdown):** Gerar descrições para módulos, APIs ou projetos completos em formato Markdown, incluindo seções como visão geral, uso, configuração, etc.
*   **Adaptar-se a Formatos Comuns:** Tentar gerar documentação em formatos padrão como JSDoc, reStructuredText (para Sphinx), Google Style Python Docstrings, JavaDoc, etc., conforme especificado.

## 💡 Quando Usá-lo?

Utilize o DocuGen quando:

*   Você está escrevendo novo código e quer documentá-lo dinamicamente.
*   Você tem código existente que carece de documentação adequada.
*   Você precisa gerar uma visão geral em Markdown para um componente ou API.
*   Você quer garantir consistência no estilo de documentação do seu projeto.
*   Você precisa de ajuda para lembrar os campos padrão de um formato de docstring específico.

## 📖 Formatos Suportados (ou a Especificar)

O DocuGen tentará gerar documentação no formato que você indicar. Alguns formatos comuns com os quais ele pode ajudar incluem (mas não se limitam a):

*   **Python:** Google Style Docstrings, reStructuredText (Sphinx), NumPy/SciPy docstrings, Epytext.
*   **JavaScript/TypeScript:** JSDoc, TSDoc.
*   **Java:** JavaDoc.
*   **C#:** XML Documentation Comments (usado por DocFX, Sandcastle).
*   **PHP:** PHPDoc.
*   **Markdown Genérico:** Para descrições de alto nível de módulos, APIs ou projetos.

Se você não especificar um formato, o DocuGen poderá perguntar ou usar um padrão comum para a linguagem do código fornecido.

## 🔧 Ferramentas Recomendadas (para plataformas como o Cursor)

*   **`Edit`**: Ativado. Essencial para que o DocuGen insira a documentação diretamente no seu código ou crie novos arquivos `.md`.
*   **`Search`**: Opcional. Pode ser útil se a documentação exigir o entendimento do contexto de outras partes do código.

## ⚙️ Modelo Padrão (Sugestão)

*   Um modelo com boa capacidade de compreensão de código e geração de texto estruturado é ideal. **Gemini Pro**, **GPT-4**, ou **Claude 3 Opus/Sonnet** são boas escolhas.

## 🗣️ Exemplo Básico de Interação (Docstring Python)

**Usuário:**
`DocuGen, preciso de uma docstring no estilo Google para esta função Python:`
```python
# calculadora.py
def somar_operandos(op1, op2):
    """
    Esta função ainda não tem uma boa docstring.
    """
    if not isinstance(op1, (int, float)) or not isinstance(op2, (int, float)):
        raise TypeError("Ambos os operandos devem ser números (int ou float).")
    return op1 + op2
```

**DocuGen (Resposta Esperada):**
```
---PENSAMENTO---
pt1. O usuário quer uma docstring estilo Google para a função `somar_operandos` em Python.
pt2. Analisar parâmetros (op1, op2), o tipo de retorno (número), e a exceção (`TypeError`).
pt3. Gerar a docstring com as seções Args, Returns, Raises.
---
📝 Entendido! `DocuGen` ao resgate para documentar sua função `somar_operandos` com uma docstring estilo Google.

🔍 **Análise da Função:**
A função `somar_operandos(op1, op2)`:
- Recebe dois operandos, `op1` e `op2`.
- Verifica se ambos são `int` ou `float`.
- Lança `TypeError` se não forem numéricos.
- Retorna a soma de `op1` e `op2`.

🛠️ **Docstring Estilo Google Sugerido:**
# ... (como no README.md do DocuGen) ...
```

## 🔗 System Prompt

Para instruções completas do sistema, consulte o arquivo `Prompt.md` no diretório principal do DocuGen.
*(Este link idealmente apontaria para o `Prompt.md` original do agente DocuGen, já que os prompts não são traduzidos como parte deste plano).*
