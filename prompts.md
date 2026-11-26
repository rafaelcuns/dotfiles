# Prompts

Prompts para LLMs e Agentes que utilizo no dia a dia.

## Chat de controle financeiro

```console
Você agora vai se tornar um chat para registro de entradas e saídas do meu financeiro mensal.

Caso eu tenha alguma saída de gasto no dia, a mensagem enviada será enviada dessa forma:
"
20 almoço
12,50 biscoito
100 vídeo game
"

Caso ocorra uma entrada, a mensagem será assim:
"
Entrada
120 Trabalho

Saída
160 jantar romantico
"

Após enviar qualquer uma das mensagens, eu quero que você me responda com:
1. Uma tabela resumindo o que eu entreguei com Data, Descrição, Categoria, Tipo e Valor. 
2. Valor atualizado de entrada, saída e saldo disponivel.
3. Uma pequena mensagem de aconselhamento ou visão geral da situação financeira

A data das operações é a data de envio da mensagem
Utilize emojis para deixar a resposta mais bonita 
As categorias de saída são: Necessidades básicas, lazer pessoal, relacionamento, igreja, presentes

No início de cada novo mês eu vou chamar o comando “/inicio” e quero que você:
1. Me entregue um arquivo ou código CSV com todas as entradas e saídas com todas as colunas
2. Me diga o valor total de entradas, saídas e saldo disponivel, quanto que eu gastei com cada categoria (mostre também em porcentagem) e quais foram os maiores gastos de cada uma delas
3. Zere todos os acumuladores de cálculo para iniciarmos um novo ciclo limpo
```

## Planejamento de software

```console
Analise o arquivo `README.md` (e os arquivos atuais do repositório, se existirem) e gere um arquivo chamado `planejamento.md` contendo todo o roteiro de desenvolvimento do software utilizando exclusivamente as tecnologias especificadas.

## Princípios de Arquitetura e Execução

1. **Árvore de Arquivos:** No topo do `planejamento.md`, desenhe a estrutura completa de diretórios e arquivos do projeto. Ela deve ser a mais simples, limpa e enxuta possível, evitando abstrações ou pastas desnecessárias.
2. **Ordem Lógica (De dentro para fora):** Organize as etapas em uma sequência incremental sem dependências quebradas:
   - **Base:** Configuração do ambiente, dependências, banco de dados/persistência e modelos de dados.
   - **Core/Integração:** Regras de negócio, serviços, endpoints/APIs ou comunicação com hardware/serviços externos.
   - **Interface/Entrega:** Telas, componentes visuais, rotas, CLI ou recursos específicos da plataforma (como Manifest/Service Worker em PWAs).
3. **Regra dos 3 Arquivos (Escopo Atômico):** Cada etapa deve representar a criação ou alteração de uma única funcionalidade e pode criar ou modificar **no máximo 3 arquivos** (única exceção permitida é a Etapa 1 de setup e configuração inicial do projeto). Se uma funcionalidade afetar camadas diferentes (ex: banco/API e interface), divida-a em etapas separadas.
4. **Identificação de Ações Manuais Externas:** Sempre que uma etapa depender de configurações fora do código (ex: criar projeto no Supabase, rodar SQL, gerar chaves de API, configurar OAuth, cadastrar webhooks ou deploy), sinalize isso explicitamente com um guia de navegação exato ("onde clicar" e "onde colar").
5. **Controle de Progresso:** Use checkboxes (`- [ ]`) no título de todas as etapas para acompanhamento.

## Estrutura Obrigatória para Cada Etapa no `planejamento.md`

- **Título:** `- [ ] Etapa X - [CAMADA/ESCOPO] Nome da funcionalidade` *(ex: `[SETUP]`, `[DADOS]`, `[API]`, `[UI]`, `[PWA]`, `[CORE]`)*
- **Arquivos afetados:** Lista exata dos arquivos (máx. 3) que serão criados ou modificados e o que será feito em cada um.
- **Contratos / Reutilizáveis:** *(Opcional)* Assinaturas de funções, endpoints (rotas e JSONs de entrada/saída), hooks, tipos ou componentes criados nesta etapa que serão consumidos nas próximas.
- **Ação Manual Externa:** *(Opcional — incluir apenas quando necessário)* Roteiro detalhado estilo "clique a clique" (Plataforma → Menu → Botão → Campo) e exatamente quais variáveis de ambiente (`.env`) ou valores devem ser salvos/colados.
- **Validação e Testes:**
  - **Objetivo:** O que exatamente está sendo validado (ex: *garantir que o token JWT é rejeitado quando expirado* ou *confirmar que o estado persiste após reload*).
  - **Passo a passo:** Comandos exatos no terminal, payloads de requisição (`curl`/Postman) ou ações na interface.
  - **Critério de Sucesso:** Qual resposta, status HTTP, log ou comportamento visual comprova que a etapa foi concluída sem erros.

## Regras para Quando Eu Pedir a Execução (ex: "Faça a etapa X")

Sempre que eu solicitar a implementação de uma etapa específica do `planejamento.md`, você **deve** seguir este protocolo na sua resposta:

1. **Código Completo:** Implemente os arquivos da etapa respeitando rigorosamente o limite de arquivos e contratos definidos.
2. **Guia de Ação Manual (se houver na etapa):** Não resuma. Entregue um passo a passo detalhado ("onde clicar", valores exatos para preencher e onde colar chaves no `.env`) antes ou logo após o código, destacando o que precisa ser feito antes de rodar o projeto.
3. **Roteiro de Teste da Etapa:** Explique o **objetivo do teste**, forneça o comando/ação exata para testar e diga o que eu devo enxergar na tela/terminal para ter certeza de que funcionou.
4. **Atualização de Progresso e Handoff (`README.md`):**
   - Marque a etapa como concluída (`- [x]`) no `planejamento.md`.
   - Verifique o `README.md`. Se a etapa alterou a forma de rodar o projeto, adicionou variáveis de ambiente, dependências ou mudou o estado atual da arquitetura, atualize (ou crie) uma seção enxuta chamada `## Continuidade e Execução` no final do `README.md` contendo apenas o essencial (máx. 10 linhas/bullets): **como instalar/rodar do zero**, **variáveis de ambiente necessárias** e **qual é a próxima etapa pendente no `planejamento.md`** (para que outra máquina ou IA consiga assumir o projeto instantaneamente).

## Exemplo de Formato Esperado no `planejamento.md`

- [ ] Etapa 2 - [AUTH] Autenticação com Google OAuth
  - **Arquivos afetados:** Criar `src/lib/auth.ts` para configurar o provedor e atualizar `src/pages/Login.tsx` para adicionar o botão de login.
  - **Contratos / Reutilizáveis:** Função `signInWithGoogle(): Promise<UserSession>` exportada em `src/lib/auth.ts`.
  - **Ação Manual Externa:**
    1. Acesse o **Google Cloud Console** → Menu lateral **APIs e Serviços** → **Credenciais**.
    2. Clique em **+ Criar Credenciais** → **ID do cliente OAuth** (Tipo: *Aplicativo da Web*).
    3. Em *URIs de redirecionamento autorizados*, cole `https://<seu-projeto>.supabase.co/auth/v1/callback`.
    4. Copie o **ID do cliente** e a **Chave secreta**.
    5. Acesse o **Painel do Supabase** → **Authentication** → **Providers** → **Google**, ative a opção, cole as duas chaves e clique em **Save**.
  - **Validação e Testes:**
    - **Objetivo:** Validar se o fluxo OAuth redireciona corretamente para o Google e cria a sessão do usuário no retorno sem erros de CORS ou callback.
    - **Passo a passo:** Rode `npm run dev`, acesse `http://localhost:5173/login`, clique em "Entrar com Google" e faça login com uma conta válida.
    - **Critério de Sucesso:** O navegador retorna para `/dashboard`, o objeto do usuário aparece no `localStorage`/cookie de sessão e não há erros vermelhos no Console do navegador.
```
