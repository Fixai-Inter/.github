# 🌳 Padrões Git

> Este documento define os padrões relacionados ao uso do **Git** e do **GitHub** adotados pela equipe.
>
> O objetivo dessas convenções é garantir um histórico organizado, facilitar revisões de código, automatizar processos e tornar o desenvolvimento mais previsível.

---

# Sumário

1. Repositórios
2. Branches
3. Commits
4. Pull Requests
5. Code Review
6. Merge Strategy
7. Versionamento (Semantic Versioning)
8. Releases
9. Fluxo Completo de Desenvolvimento

---

# 1. Repositórios

## Objetivo

Os repositórios devem possuir uma organização clara para facilitar a localização de projetos e reduzir ambiguidades.

## Convenções

| Regra                                 | Exemplo                      |
| ------------------------------------- | ---------------------------- |
| Utilizar sufixo segundo ou primeiro ano | `modelagem-de-dados-segundo-ano` |
| Utilizar nomes descritivos            | `banco-de-horas-segundo-ano` |
| Utilizar letras minúsculas            | ✅ `github-api`               |
| Separar palavras com hífen (`-`)      | ✅ `gestao-escolar-api`       |
| Evitar espaços e caracteres especiais | ❌ `Banco de Dados`           |

### Estrutura interna

Sempre que possível, organize o projeto em módulos.

Exemplo:

```text
banco-de-dados
│
├── tabelas/
├── procedures/
├── triggers/
├── views/
└── documentacao/
```

> ✅ **Boa prática**
>
> Um repositório deve possuir apenas uma responsabilidade principal. Evite utilizar um mesmo repositório para armazenar projetos diferentes.

---

# 2. Branches

## Estratégia de Branches

A equipe utiliza três branches permanentes.

| Branch | Finalidade                        |
| ------ | --------------------------------- |
| `dev`  | Desenvolvimento diário            |
| `hml`  | Homologação e validação integrada |
| `main` | Produção                          |

Cada branch representa um estágio de maturidade do software.
---

## Branches de trabalho

Toda nova atividade deverá ser criada a partir da branch `dev`.

Padrão:

```
tipo/nome-da-feature
```

Tipos permitidos:

| Tipo     | Exemplo               |
| -------- | --------------------- |
| feature  | feature/login-social  |
| bugfix   | bugfix/null-pointer   |
| hotfix   | hotfix/token-expirado |
| docs     | docs/guia-git         |
| refactor | refactor/auth-service |
| test     | test/github-api       |

> ⚠️ Nunca desenvolva diretamente nas branches `main` ou `hml`.

---

# 3. Commits

## Conventional Commits

Todos os commits devem seguir o padrão **Conventional Commits**.

Estrutura:

```text
tipo(escopo): descrição
```

Exemplo:

```text
feat(auth): adiciona login com GitHub
```

---

## Tipos permitidos

| Tipo     | Utilização          | Impacto na versão |
| -------- | ------------------- | ----------------- |
| feat     | Nova funcionalidade | MINOR             |
| fix      | Correção de bug     | PATCH             |
| docs     | Documentação        | Nenhum            |
| refactor | Refatoração         | Nenhum            |
| style    | Formatação          | Nenhum            |
| test     | Testes              | Nenhum            |
| perf     | Performance         | PATCH             |
| build    | Build               | Nenhum            |
| ci       | CI/CD               | Nenhum            |
| chore    | Manutenção          | Nenhum            |

---

## Breaking Changes

Mudanças incompatíveis devem utilizar `!`.

Exemplo:

```text
feat(api)!: remove endpoint legado
```

ou

```text
BREAKING CHANGE:
```

na descrição do commit.

Isso permitirá que ferramentas como o **Release Please** identifiquem automaticamente uma nova versão **MAJOR**.

> ℹ️ **Por que utilizar Conventional Commits?**
>
> Além de organizar o histórico do Git, esse padrão permite gerar Release Notes automaticamente e automatizar o versionamento do projeto.

---

# 4. Pull Requests

Toda alteração deverá ser enviada através de Pull Request.

## Requisitos obrigatórios

* Utilizar o template oficial.
* Referenciar a Issue relacionada.
* Explicar o objetivo da alteração.
* Informar como validar a mudança.

Exemplo:

```
Closes #25
```

---

## Recomendações

* Prefira Pull Requests pequenas.
* Evite alterações com centenas de arquivos.
* Atualize a documentação quando necessário.

> ✅ Pull Requests menores recebem revisões melhores.

---

## Draft Pull Requests

Caso o desenvolvimento ainda não tenha sido concluído, recomenda-se utilizar um **Draft Pull Request**.

Essa funcionalidade permite compartilhar o progresso sem solicitar revisão formal.

---

# 5. Code Review

O Code Review é obrigatório para garantir qualidade e compartilhamento de conhecimento.

Durante a revisão, verifique principalmente:

| Item          | Objetivo                        |
| ------------- | ------------------------------- |
| Legibilidade  | Código fácil de entender        |
| Arquitetura   | Respeita a estrutura do projeto |
| Segurança     | Evita vulnerabilidades          |
| Performance   | Evita desperdícios              |
| Duplicação    | Não replica lógica existente    |
| Testes        | Cobertura adequada              |
| Boas práticas | Segue os padrões definidos      |

> ✅ O objetivo do Code Review é melhorar o software, e não encontrar culpados.

---

# 6. Merge Strategy

## 6.1. Fluxo de Merge

Fluxo adotado pela equipe:

```mermaid
A[feature/*]
B[dev]
C[hml]
D[main]

A --> B
B --> C
C --> D
```

Processo:

1. Desenvolver em uma branch derivada de `dev`;
2. Abrir Pull Request para `dev`;
3. Consolidar entregas em `hml`;
4. Após homologação, promover para `main`.

> ⚠️ Nunca envie alterações diretamente para `main`.

## 6.2 Proteções do Repositório

As **Branch Protection Rules** são configurações do GitHub que impedem alterações indevidas nas branches protegidas e garantem que o fluxo de desenvolvimento da equipe seja seguido de forma consistente.

Seu principal objetivo é reduzir erros humanos, aumentar a qualidade das entregas e assegurar que nenhuma alteração seja integrada sem passar pelas validações definidas pelo time.

> ℹ️ **Por que utilizar Branch Protection Rules?**
>
> Embora os padrões definidos neste guia orientem como o desenvolvimento deve ser realizado, eles dependem da disciplina da equipe. As Branch Protection Rules transformam essas diretrizes em regras aplicadas automaticamente pelo GitHub, reduzindo a possibilidade de erros e aumentando a confiabilidade do processo.

---

## Branches protegidas

As branches permanentes do projeto deverão possuir regras de proteção configuradas no GitHub.

| Branch | Nível de proteção | Finalidade                                                       |
| ------ | ----------------- | ---------------------------------------------------------------- |
| `dev`  | Moderado          | Desenvolvimento contínuo e integração das funcionalidades.       |
| `hml`  | Alto              | Homologação das funcionalidades antes da publicação em produção. |
| `main` | Máximo            | Ambiente de produção e versões oficiais da aplicação.            |

---

## Configurações recomendadas

As configurações abaixo deverão ser aplicadas às branches protegidas sempre que possível.

| Configuração                                          | `dev` | `hml` | `main` | Objetivo                                                                               |
| ----------------------------------------------------- | :---: | :---: | :----: | -------------------------------------------------------------------------------------- |
| Bloquear push direto                                  |   ✅   |   ✅   |    ✅   | Garantir que toda alteração seja realizada através de Pull Request.                    |
| Exigir Pull Request antes do merge                    |   ✅   |   ✅   |    ✅   | Manter o histórico organizado e rastreável.                                            |
| Exigir pelo menos uma aprovação                       |   ❌   |   ✅   |    ✅   | Garantir que alterações críticas sejam revisadas por outro integrante.                 |
| Exigir aprovação da pipeline de CI                    |   ✅   |   ✅   |    ✅   | Impedir merges quando houver falhas de build, testes ou validações automatizadas.      |
| Exigir branch atualizada antes do merge               |   ❌   |   ✅   |    ✅   | Evitar conflitos e integrações baseadas em código desatualizado.                       |
| Exigir resolução de todas as conversas do Code Review |   ❌   |   ✅   |    ✅   | Garantir que todas as observações da revisão tenham sido tratadas antes da integração. |

> ✅ **Boa prática**
>
> As configurações da branch `dev` são propositalmente menos restritivas para permitir maior agilidade durante o desenvolvimento. Já as branches `hml` e `main` representam ambientes mais estáveis e, por isso, exigem validações adicionais.

---

## Fluxo protegido

Após a configuração das Branch Protection Rules, toda alteração seguirá automaticamente o fluxo abaixo:

```mermaid
A[Branch de Trabalho]
B[Pull Request]
C[Code Review]
D[Pipeline de CI]
E[Merge]
F[Branch Protegida]

A --> B
B --> C
C --> D
D --> E
E --> F
```

Esse fluxo garante que nenhuma alteração seja integrada às branches protegidas sem passar pelas etapas obrigatórias de validação.

---

## Benefícios

A utilização das Branch Protection Rules proporciona diversos benefícios ao processo de desenvolvimento:

* Reduz alterações acidentais em ambientes críticos;
* Garante que toda mudança seja revisada antes da integração;
* Impede merges quando a pipeline de integração contínua falhar;
* Mantém um histórico consistente de Pull Requests;
* Aumenta a confiabilidade das versões publicadas;
* Padroniza o fluxo de desenvolvimento entre todos os integrantes da equipe.

---

## Exceções

Em situações excepcionais, como correções críticas em produção (**Hotfixes**), poderá ser necessário acelerar o processo de revisão.

Mesmo nesses casos, recomenda-se manter o fluxo através de Pull Request, evitando alterações diretas nas branches protegidas sempre que possível.

> ⚠️ **Importante**
>
> As Branch Protection Rules não substituem o processo de Code Review nem a responsabilidade dos desenvolvedores. Elas representam uma camada adicional de segurança para garantir que o fluxo definido pela equipe seja seguido de forma consistente em todos os repositórios.

---

# 7. Versionamento

A equipe utiliza **Semantic Versioning (SemVer)**.

Formato:

```
MAJOR.MINOR.PATCH
```

| Tipo  | Quando utilizar          |
| ----- | ------------------------ |
| MAJOR | Alterações incompatíveis |
| MINOR | Novas funcionalidades    |
| PATCH | Correções                |

Exemplo:

| Versão | Significado             |
| ------ | ----------------------- |
| 1.0.0  | Primeira versão estável |
| 1.1.0  | Nova funcionalidade     |
| 1.1.1  | Correção                |
| 2.0.0  | Mudança incompatível    |

---

# 8. Releases

As Releases serão geradas automaticamente utilizando:

* GitHub Actions
* Release Please

O Release Please analisa todos os commits desde a última Release e determina automaticamente a próxima versão.

Exemplo:

```
feat(auth): login Google
fix(jwt): corrige validação
docs: atualiza README
```

Resultado:

```
Nova versão: MINOR
```

Exemplo:

```
fix(login): timeout
fix(api): null pointer
```

Resultado:

```
Nova versão: PATCH
```

Exemplo:

```
feat(api)!: remove endpoint antigo
```

Resultado:

```
Nova versão: MAJOR
```

---

# 9. Fluxo Completo

```mermaid
Issue --> Branch

Branch --> Commit

Commit --> PullRequest

PullRequest --> Review

Review --> MergeDev

MergeDev --> Homologacao

Homologacao --> Release

Release --> Main

Main --> Produção
```

---

# Erros comuns

| Evite                      | Motivo                    |
| -------------------------- | ------------------------- |
| Commit "Update"            | Não informa o que mudou   |
| Trabalhar na `main`        | Risco para produção       |
| PRs gigantes               | Revisões menos eficientes |
| Não utilizar template      | Perda de contexto         |
| Não atualizar documentação | Gera dívida técnica       |

---

# Referências

* Conventional Commits
* Semantic Versioning
* GitHub Flow
* Release Please
* GitHub Actions
* Keep a Changelog
