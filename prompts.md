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

As etapas devem representar a criação ou alteração de uma funcionalidade do software, mas no máximo 3 arquivos podem ser alterados por etapa. Após cada etapa também deve ter uma explicação de como testar aquela funcionalidade. Se necessário, em cada etapa realizada pode existir uma área para simbolizar funções ou componentes criados que podem ser utilizados em outros lugares. A estrutura de arquivos tem que ser pensada no planejamento e deve ser a mais simples possível

Exemplo:
- Etapa 2 - Criação da tela de usuário
- Alterar apenas o arquivo de componente da tela de usuário e possíveis referências que precisem de alteração 
- Componente “TelaUsuario” criado para uso em outro lugar
- Para testar, execute o software, acesse a tela de usuário e teste as funcionalidades como alterar imagem ou nome.
```