
# Guia de Criação e Personalização de um Copilot

## Criar um Copilot

Para criar um copilot em branco, na página inicial, devemos escolher o ambiente correto e clicar em **"New agent"**.  
É recomendado usar o idioma inglês para criar o novo agente, já que em português pode não funcionar corretamente.

- **Inserir uma descrição detalhada**: A descrição é o que o nosso chatbot é responsável por fazer.
- **Inserir instrução**: A instrução é o prompt do agente. Use técnicas de engenharia de prompt para passar instruções bem definidas para o agente.
- **Configurações avançadas**: Defina a solução em que esse chatbot será armazenado. Isso facilita a exportação e importação para o ambiente de produção posteriormente.

---

## Customização de Tópicos

1. Vá até a aba **Tópicos** e adicione um novo tópico (em branco ou com base em uma descrição).
2. Se for um tópico em branco, adicione **frases de gatilho**, que orientarão o agente sobre diferentes formas que o usuário pode usar para abordar o tema. A linguagem natural cuida da interpretação baseada no **significado** e não em palavras exatas.
3. Adicione **ações**, como respostas generativas (na aba **Avançado**).
   - Configure o input para recuperar a pergunta do usuário através da variável de sistema **Activity.Text**.
   - Edite as propriedades e a fonte de dados das respostas generativas para melhor performance.
   - Finalize o tópico com uma mensagem indicando o encerramento do assunto.

> **Dica**: Sempre reinicie a conversa antes de executar um novo teste.

---

## Personalizar Mensagem de Erro no Tópico

Personalize mensagens de erro para evitar que o usuário receba respostas incoerentes ou irrelevantes.

- Edite o tópico de sistema **Conversational Boosting**:
  - Caso o copilot não encontre a resposta, ele utilizará este recurso para tentar responder com base em geração de linguagem.
  - Alternativamente, personalize o tópico de **Fallback**. Em caso de conflito, ele cairá no fallback; caso contrário, usará o conversational boosting.
- No **Conversational Boosting**:
  - Desabilite a opção de usar conhecimento geral (evita que o agente busque informações na internet).
  - Adicione uma mensagem personalizada, incluindo variáveis se necessário.
  - Também é possível disparar ações, como chamar um fluxo no Power Automate.

---

## Customizar Qualidade da Resposta com Respostas Generativas

- Dentro dos tópicos:
  - Personalize o **Conversational Boosting** e modifique as **fontes de dados** para usar apenas suas bases de conhecimento.
  - **Evite o uso de dados da internet/OpenAI** para manter o foco no tema desejado.

- Ao customizar as fontes de dados:
  - Defina o **nível de moderação de conteúdo** como **alto**.
  - Insira um prompt alternativo e a variável de entrada **Activity.Text**.
  - Limite da entrada: 8000 caracteres.

- Também é possível configurar o **nível de moderação de conteúdo** nas configurações do agente (nível global e não apenas por tópico).
