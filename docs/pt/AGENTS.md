# Guia para Contribuir e Gerenciar Modos neste Repositório

Este documento descreve o padrão para adicionar e manter "modos" neste repositório. Um modo define a configuração e o comportamento de um agente de IA (como os utilizados em plataformas como o Cursor) para otimizar resultados em tarefas específicas.

## Estrutura de um Modo

Cada modo deve residir em seu próprio diretório dentro do repositório. O nome do diretório deve ser descritivo e usar `PascalCase` (ex: `MeuNovoModo/`).

Dentro do diretório de cada modo, os seguintes arquivos devem ser incluídos:

### 1. `README.md` (Obrigatório)

Este arquivo é o cartão de visita do modo. Deve conter as seguintes informações:

*   **Nome do Modo:** Claro e conciso.
*   **Descrição:**
    *   Qual é o propósito principal do modo?
    *   Para que tipo de tarefas, projetos ou plataformas é mais útil?
    *   Que benefícios chave oferece (ex: maior precisão, código mais limpo, melhor planejamento)?
*   **Ícone (Opcional, mas Recomendado):**
    *   Um emoji ou caractere que represente visualmente o modo (ex: 🤖, 💡, 🛠️).
*   **Instruções Personalizadas / System Prompt (Resumo):**
    *   Um breve resumo das instruções principais do agente.
    *   Deve conter um link para o arquivo `Prompt.md` para a versão completa.
*   **Modelo Padrão (Se Aplicável):**
    *   Recomendação sobre o modelo de IA a ser utilizado (ex: "Auto (Gemini)", "Claude 3 Opus", "GPT-4 Turbo").
*   **Ferramentas Recomendadas (Para Plataformas como Cursor):**
    *   Listar as ferramentas que se recomenda ativar ou desativar:
        *   Ex: `Search: Ativado`, `Edit: Ativado`, `Run: Desativado`, `Auto-execute: Cuidado/Desativado`.
*   **Atalho de Teclado Sugerido (Opcional):**
    *   Se a plataforma permitir, sugerir um atalho para ativar rapidamente o modo (ex: `Cmd + Shift + M`).
*   **Exemplo de Uso (Opcional):**
    *   Um pequeno bloco de código ou descrição mostrando uma interação típica como iniciar com o modo.

### 2. `Prompt.md` (ou `SystemPrompt.md`) (Obrigatório)

Este arquivo contém o texto completo e exato do "system prompt" ou as instruções personalizadas que devem ser configuradas na plataforma (ex: Cursor, ChatGPT com instruções personalizadas) para ativar o modo.

Deve ser bem estruturado e pode incluir seções como:

*   `OBJETIVO`: A meta principal do agente.
*   `CONTEXTO`: Informações relevantes que o agente deve conhecer.
*   `ESTRUTURA DE SAÍDA`: Como as respostas devem ser formatadas.
*   `FLUXO DE INTERAÇÃO`: Como a conversa deve proceder.
*   `COMANDOS`: Comandos especiais que o agente deve reconhecer (ex: `/plan`, `/debug`).
*   `PERSONALIDADE E ESTILO`: O tom e a forma de comunicação do agente.
*   `RESTRIÇÕES`: Coisas que o agente não deve fazer.

**Exemplo:** O modo `Nexus/` neste repositório serve como uma excelente referência para a estrutura de `README.md` e `Prompt.md`.

### Arquivos Opcionais

*   **`Examples/` (Diretório):**
    *   Pode conter subdiretórios ou arquivos (ex: em formato `.md` ou `.txt`) que mostrem exemplos de interações completas com o modo. Isso ajuda a entender seu comportamento e resultados esperados.
*   **`Config/` (Diretório):**
    *   Para arquivos de configuração adicionais, scripts de apoio ou recursos que o modo possa necessitar.
*   **`AGENTS.md` (Específico do Modo):**
    *   Se um modo for particularmente complexo, envolver múltiplos subagentes ou tiver um fluxo de trabalho interno que requeira documentação detalhada para sua manutenção ou extensão.

## Processo para Adicionar um Novo Modo

1.  **Crie um novo diretório:** Use `PascalCase` para o nome (ex: `ModoRevisaoCodigo/`).
2.  **Adicione `README.md`:** Documente seu modo seguindo a estrutura detalhada acima.
3.  **Adicione `Prompt.md`:** Inclua o system prompt completo.
4.  **Adicione arquivos opcionais:** Se necessário (exemplos, configurações).
5.  **Verifique:** Certifique-se de que a estrutura e o conteúdo estão claros e seguem as diretrizes.
6.  **Envie um Pull Request:** Para que seu modo seja revisado e incorporado ao repositório.

## Mantendo a Qualidade

*   **Clareza:** Os prompts e as descrições devem ser fáceis de entender.
*   **Consistência:** Siga a estrutura de arquivos e a nomenclatura definidas.
*   **Testes:** Antes de propor um modo, teste-o exaustivamente na plataforma de destino para garantir que funciona como esperado.
*   **Feedback:** Esteja aberto a receber feedback para melhorar os modos existentes.

Ao seguir estas diretrizes, podemos construir uma coleção valiosa e bem organizada de modos para aprimorar nossa interação com as ferramentas de IA.
