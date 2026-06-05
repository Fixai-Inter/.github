# 📖 Guia de Contribuição e Padrões do Time

Este repositório centraliza os padrões de trabalho do time: templates de issues, templates de pull requests e as convenções que devem ser seguidas por todos os integrantes. Leia com atenção antes de começar a contribuir.

---

## 📋 Sumário

- [Registro de Horas](#-registro-de-horas)
- [Templates de Issue](#-templates-de-issue)
- [Templates de Pull Request](#-templates-de-pull-request)
- [Fluxo do Board](#-fluxo-do-board)
- [Boas Práticas Gerais](#-boas-práticas-gerais)

---

## ⏱️ Registro de Horas

O registro de horas é feito diretamente nos **comentários das issues** no GitHub. Esse padrão é fundamental para o funcionamento do sistema de análise automática que consolida os dados de tempo trabalhado pelo time.

### Formato obrigatório

```
[horas: 2.5] - Descrição do que foi feito
```

### Regras do formato

- O campo `[horas: X]` deve vir sempre no início do comentário
- O valor deve ser um número decimal usando ponto como separador. Use `1.5` para uma hora e meia, `0.5` para trinta minutos, `2.0` para duas horas exatas
- A descrição após o traço é obrigatória e deve resumir o que foi feito naquele período
- Cada comentário deve representar uma sessão de trabalho. Se trabalhou em momentos diferentes do dia, faça comentários separados

### Exemplos corretos

```
[horas: 1.5] - Implementação do endpoint de autenticação
[horas: 0.5] - Code review do PR #42
[horas: 3.0] - Correção do bug de timeout na integração com o serviço de pagamento
[horas: 2.5] - Reunião de refinamento e atualização da documentação técnica
```

### Exemplos incorretos

```
[hora: 1,5] - Uso de vírgula no lugar de ponto
2.5h - Implementação - Formato fora do padrão
[hora: 2.5] implementação sem o traço separador
```

> ⚠️ Comentários fora do formato padrão não serão reconhecidos pelo sistema de análise automática e as horas não serão contabilizadas.

---

## 🗂️ Templates de Issue

Ao clicar em **New Issue** dentro de qualquer repositório da organização, você verá a tela de seleção com os templates disponíveis. Escolha sempre o template mais adequado para o que está sendo registrado.

---

### ✨ Feature Request

**Quando usar:** para registrar ou sugerir uma nova funcionalidade no sistema, seja ela solicitada pelo cliente, definida pelo produto ou identificada pelo próprio time técnico.

Este template é o mais estratégico do fluxo. Além de descrever o que será feito, ele pede a motivação por trás da funcionalidade, quem se beneficia, o que está fora do escopo e os critérios de aceitação. Preencher essas informações com cuidado evita retrabalho e garante que todo o time entenda o real valor da entrega antes de começar.

**Label aplicada automaticamente:** `feature`

---

### 🐛 Bug Report

**Quando usar:** para reportar qualquer comportamento inesperado, erro ou falha no sistema, seja encontrado em produção, homologação ou durante o desenvolvimento.

Um bom bug report precisa ser detalhado o suficiente para que qualquer pessoa consiga reproduzir o problema sem precisar perguntar nada a quem abriu. Por isso o template pede o passo a passo de reprodução, o comportamento esperado, o comportamento atual e informações do ambiente. Quanto mais completo, mais rápida será a correção.

**Label aplicada automaticamente:** `bug`

---

### 📌 Task

**Quando usar:** para tarefas técnicas internas que não se encaixam como feature nem como bug. Exemplos comuns são criar uma integração com um serviço externo, configurar um ambiente, implementar um script, realizar uma migração de dados ou qualquer trabalho técnico que precisa ser rastreado no board.

**Label aplicada automaticamente:** `task`

---

### 📚 Documentation

**Quando usar:** para registrar a necessidade de criar ou atualizar documentação, seja ela técnica ou de produto. Exemplos incluem documentar uma API, atualizar o README de um repositório, escrever um guia de onboarding ou registrar decisões arquiteturais.

Times maduros tratam documentação como parte do trabalho, não como algo opcional. Toda funcionalidade entregue sem documentação adequada gera dívida para o time no futuro.

**Label aplicada automaticamente:** `documentation`

---

### ⚡ Performance

**Quando usar:** para registrar problemas ou oportunidades de melhoria relacionados a desempenho, como tempo de resposta lento, alto consumo de memória, queries demoradas, bundle grande ou qualquer situação onde o sistema está funcionando corretamente mas de forma ineficiente.

Este template pede métricas atuais e esperadas justamente para que a melhoria seja objetiva e mensurável, e não apenas subjetiva.

**Label aplicada automaticamente:** `performance`

---

### 🔒 Security

**Quando usar:** para registrar vulnerabilidades, falhas de segurança ou dependências com CVEs conhecidos identificados no sistema.

> ⚠️ **Atenção:** se a vulnerabilidade for crítica e ainda não estiver corrigida, **não detalhe publicamente como explorá-la** nesta issue. Reporte primeiro ao responsável técnico via canal privado e só então abra o registro com o nível de detalhe adequado.

**Label aplicada automaticamente:** `security`

---

### 🧪 Test

**Quando usar:** para registrar a necessidade de escrever ou melhorar testes em partes do sistema que estão sem cobertura ou com cobertura insuficiente. Pode ser motivado por um bug recorrente em uma área sem testes, por uma feature nova crítica ou por um débito técnico identificado durante o desenvolvimento.

**Label aplicada automaticamente:** `test`

---

## 🔀 Templates de Pull Request

Ao abrir um Pull Request, utilize o template correspondente ao tipo de mudança que está sendo entregue. Cada PR deve ter um tipo bem definido para facilitar o processo de revisão e manter o histórico organizado.

Os links abaixo abrem o PR já com o template correto selecionado. Salve esta página ou adicione esses links aos seus favoritos.

| Template | Quando usar | Link direto |
|---|---|---|
| ✨ Feature | Nova funcionalidade implementada | [Abrir PR de Feature](?template=feature_pull_request_template.md) |
| 🐛 Bug Fix | Correção de um problema existente | [Abrir PR de Bug Fix](?template=bugfix_pull_request_template.md) |
| 🚨 Hotfix | Correção urgente para produção | [Abrir PR de Hotfix](?template=hotfix_pull_request_template.md) |
| 🔧 Refactoring | Melhoria de código sem alteração de comportamento | [Abrir PR de Refactoring](?template=refactoring_pull_request_template.md) |
| 🔩 Chore | Manutenção, dependências, configurações | [Abrir PR de Chore](?template=chore_pull_request_template.md) |

---

### ✨ Feature

Para PRs que entregam uma nova funcionalidade. O template pede a descrição do que foi implementado, a issue relacionada, como testar e o registro de horas. Todo PR de feature precisa estar vinculado a uma issue de Feature Request existente.

---

### 🐛 Bug Fix

Para PRs que corrigem um problema existente. O diferencial deste template em relação ao de feature é a seção de reprodução do bug antes da correção, que ajuda o revisor a entender o contexto sem precisar buscar a issue original.

---

### 🚨 Hotfix

Para correções urgentes que precisam ir para produção rapidamente. O template inclui uma seção de impacto em produção e de risco da mudança, que são informações críticas para quem vai revisar e aprovar com agilidade. Todo hotfix deve ser revisado por ao menos um integrante sênior antes do merge.

---

### 🔧 Refactoring

Para PRs que melhoram a estrutura interna do código sem alterar nenhum comportamento externo. O ponto mais importante neste template é a confirmação explícita de que nenhuma funcionalidade foi adicionada, removida ou alterada. O revisor precisa dessa garantia para focar na qualidade do código.

---

### 🔩 Chore

Para tarefas de manutenção como atualização de dependências, ajustes em configurações, mudanças em pipelines de CI/CD e outros trabalhos que não afetam diretamente o produto. É o template mais simples, mas importante para manter o histórico de mudanças organizado e rastreável.

---

## 📊 Fluxo do Board

O board do projeto segue os seguintes estados. Cada integrante é responsável por manter o status das suas issues atualizado ao longo do dia.

| Estado | Descrição |
|---|---|
| **Backlog** | Issue criada e registrada, ainda não priorizada para a sprint atual |
| **Ready** | Issue priorizada, refinada e pronta para ser iniciada |
| **In Progress** | Alguém está trabalhando ativamente nessa issue agora |
| **In Review** | O PR foi aberto e está aguardando revisão do time |
| **Done** | Issue concluída, PR mergeado e entrega validada |

---

## ✅ Boas Práticas Gerais

**Sobre issues:**
- Toda issue deve ter ao menos um assignee definido antes de ir para In Progress
- Critérios de aceitação precisam estar preenchidos antes do desenvolvimento começar
- Registre as horas ao longo do trabalho, não apenas no final. Isso garante mais precisão nos dados

**Sobre pull requests:**
- Todo PR deve referenciar a issue relacionada usando `Closes #número` na descrição
- PRs não devem ficar abertos sem revisão por mais de um dia útil
- Não faça merge do próprio PR sem ao menos uma aprovação de outro integrante, exceto em casos de hotfix urgente previamente alinhado

**Sobre o registro de horas:**
- Registre sempre que pausar ou encerrar uma sessão de trabalho em uma issue
- Inclua tempo de reuniões, code reviews e pesquisa quando estiverem relacionados a uma issue específica
- Em caso de dúvida sobre o formato, consulte a seção de Registro de Horas neste documento
