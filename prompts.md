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
Eu quero que você gere um arquivo chamado planejamento.md que nele tenha todas as etapas de desenvolvimento descritas para a produção de um software com suas tecnologias especificadas em README.md

As etapas devem representar a criação ou alteração de uma funcionalidade do software, mas no máximo 3 arquivos podem ser alterados por etapa (Com exceção de comandos ou etapas iniciais que precise criar muitos arquivos de configuração). Após cada etapa também deve ter uma explicação de como testar aquela funcionalidade. Se necessário, em cada etapa realizada pode existir uma área para simbolizar funções ou componentes criados que podem ser utilizados em outros lugares. A estrutura de arquivos tem que ser pensada no planejamento e deve ser a mais simples possível, com isso, coloque no planejamento a árvore de arquivos do projeto. Implemente em ordem lógica para não faltar dados ou funcionalidades nas etapas. Ex: Estrutura/Banco/Auth --> Lógica/Hooks/API --> Telas e Componentes --> Recursos.

Exemplo:
- Etapa 2 - Criação da tela de usuário
- Alterar apenas o arquivo de componente da tela de usuário e possíveis referências que precisem de alteração 
- Componente “TelaUsuario” criado para uso em outro lugar
- Para testar, execute o software, acesse a tela de usuário e teste as funcionalidades como alterar imagem ou nome.
```

```console
Analise o arquivo `README.md` (e os arquivos atuais do repositório, se existirem) e gere um arquivo chamado `planejamento.md` contendo todo o roteiro de desenvolvimento do software utilizando exclusivamente as tecnologias especificadas.

## Princípios de Arquitetura e Execução

1. **Árvore de Arquivos:** No topo do `planejamento.md`, desenhe a estrutura completa de diretórios e arquivos do projeto. Ela deve ser a mais simples, limpa e enxuta possível, evitando abstrações ou pastas desnecessárias.
2. **Ordem Lógica (De dentro para fora):** Organize as etapas em uma sequência incremental sem dependências quebradas:
   - **Base:** Configuração do ambiente, dependências, banco de dados/persistência e modelos de dados.
   - **Core/Integração:** Regras de negócio, serviços, endpoints/APIs ou comunicação com hardware/serviços externos.
   - **Interface/Entrega:** Telas, componentes visuais, rotas, CLI ou recursos específicos da plataforma (como Manifest/Service Worker em PWAs).
3. **Regra dos 3 Arquivos (Escopo Atômico):** Cada etapa deve representar a criação ou alteração de uma única funcionalidade e pode criar ou modificar **no máximo 3 arquivos** (única exceção permitida é a Etapa 1 de setup e configuração inicial do projeto). Se uma funcionalidade afetar camadas diferentes (ex: banco/API e interface), divida-a em etapas separadas.
4. **Controle de Progresso:** Use checkboxes (`- [ ]`) no título de todas as etapas para acompanhamento.

## Estrutura Obrigatória para Cada Etapa

- **Título:** `- [ ] Etapa X - [CAMADA/ESCOPO] Nome da funcionalidade` *(ex: `[SETUP]`, `[DADOS]`, `[API]`, `[UI]`, `[PWA]`, `[CORE]`)*
- **Arquivos afetados:** Lista exata dos arquivos (máx. 3) que serão criados ou modificados e o que será feito em cada um.
- **Contratos / Reutilizáveis:** *(Opcional)* Liste assinaturas de funções, endpoints (rotas e JSONs de entrada/saída), hooks, tipos ou componentes criados nesta etapa que serão consumidos nas próximas.
- **Como testar:** Passo a passo objetivo de como executar e validar a entrega da etapa (via terminal, testes automatizados, requisições HTTP ou interação visual na interface) antes de avançar.

## Exemplo de Formato Esperado

- [ ] Etapa 2 - [UI] Criação da tela de perfil do usuário
  - **Arquivos afetados:** Criar `src/pages/TelaUsuario.tsx` para a interface e atualizar `src/routes.tsx` para registrar a rota.
  - **Contratos / Reutilizáveis:** Componente `TelaUsuario` e função `formatarNome(nome: string): string` exportados para reuso.
  - **Como testar:** Execute o projeto, acesse a rota `/usuario` e teste a alteração da imagem e do nome, validando se a interface reflete as mudanças sem erros no console.
```
