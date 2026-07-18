# 📖 Introdução

> Este documento apresenta os princípios, objetivos e escopo do **Guia de Engenharia de Software** da equipe. Antes de iniciar qualquer contribuição em um projeto, recomenda-se a leitura completa desta documentação.

---

# 1. Objetivo

O Guia de Engenharia de Software tem como objetivo definir um conjunto de padrões e boas práticas para o desenvolvimento dos projetos da equipe.

Ao centralizar essas diretrizes em um único local, buscamos garantir que todos os integrantes desenvolvam software de forma consistente, independente do projeto ou da tecnologia utilizada.

Este guia existe para:

* Padronizar o fluxo de desenvolvimento;
* Facilitar a colaboração entre os integrantes;
* Reduzir retrabalho causado por falta de padronização;
* Melhorar a qualidade do código entregue;
* Aumentar a previsibilidade das entregas;
* Automatizar processos através das ferramentas do GitHub;
* Facilitar o onboarding de novos integrantes.

> ℹ️ **Por que isso é importante?**
>
> Em equipes de desenvolvimento, a ausência de padrões faz com que cada integrante trabalhe de uma maneira diferente. Isso aumenta o tempo de revisão, dificulta a manutenção do código e torna o crescimento da equipe mais complexo. A padronização reduz essas diferenças e permite que qualquer desenvolvedor compreenda rapidamente o funcionamento dos projetos.

---

# 2. Escopo

Este guia é aplicável a **todos os repositórios mantidos pela equipe**, independentemente da linguagem de programação, framework ou tecnologia utilizada.

As convenções descritas nesta documentação abrangem:

* Organização dos repositórios;
* Fluxo de desenvolvimento utilizando Git e GitHub;
* Gerenciamento de atividades;
* Processo de revisão de código;
* Estratégia de versionamento;
* Organização do trabalho utilizando GitHub Projects;
* Boas práticas de documentação.

Sempre que um novo projeto for iniciado, recomenda-se que ele siga estas diretrizes desde o início.

> ⚠️ **Importante**
>
> Caso um projeto necessite de exceções às regras descritas neste guia, essas exceções devem ser documentadas no próprio repositório do projeto para evitar ambiguidades.

---

# 3. Princípios de Engenharia

Os padrões apresentados neste guia são baseados em princípios amplamente utilizados pela indústria de software. Mais do que seguir regras, buscamos adotar práticas que aumentem a qualidade e a sustentabilidade dos projetos ao longo do tempo.

## 3.1 O código pertence à equipe

Todo código desenvolvido é um ativo da equipe, e não de um único desenvolvedor.

Isso significa que qualquer integrante deve ser capaz de compreender, revisar e evoluir uma funcionalidade sem depender exclusivamente de quem a implementou.

> ✅ **Boa prática**
>
> Escreva código pensando na próxima pessoa que precisará mantê-lo — que pode ser você mesmo no futuro.

---

## 3.2 Clareza acima de complexidade

Soluções simples costumam ser mais fáceis de manter, testar e evoluir.

Antes de optar por uma implementação complexa, avalie se existe uma alternativa mais simples que resolva o mesmo problema.

Sempre priorize:

* Legibilidade;
* Simplicidade;
* Organização;
* Facilidade de manutenção.

---

## 3.3 Consistência acima de preferência pessoal

Cada desenvolvedor possui seu próprio estilo de programação. Entretanto, dentro de uma equipe, a consistência é mais importante do que preferências individuais.

Seguir padrões comuns facilita a leitura do código e reduz o tempo necessário para revisões e manutenção.

---

## 3.4 Automação sempre que possível

Processos manuais tendem a ser mais lentos e suscetíveis a erros.

Sempre que possível, devemos utilizar automações para:

* Execução de testes;
* Validação de código;
* Geração de Releases;
* Versionamento;
* Integração contínua (CI);
* Publicação de artefatos (CD).

A automação aumenta a confiabilidade das entregas e reduz atividades repetitivas.

---

## 3.5 Documentação faz parte da entrega

Uma funcionalidade não é considerada totalmente concluída quando apenas o código foi implementado.

Sempre que uma alteração impactar o funcionamento do sistema, sua documentação também deverá ser atualizada.

Isso inclui:

* README;
* Guias técnicos;
* Diagramas;
* Documentação de APIs;
* Decisões arquiteturais (quando aplicável).

> ✅ **Boa prática**
>
> Um projeto bem documentado reduz o tempo de onboarding, facilita a manutenção e preserva o conhecimento técnico da equipe.

---

## 3.6 Qualidade antes de velocidade

Entregar rapidamente é importante, mas entregar com qualidade é essencial.

Código com baixa qualidade gera retrabalho, aumenta a incidência de bugs e dificulta futuras evoluções do sistema.

Por esse motivo, toda alteração deve passar pelos processos definidos neste guia antes de ser incorporada ao projeto.

---

# 4. Fluxo Geral de Desenvolvimento

O processo de desenvolvimento adotado pela equipe segue um fluxo padronizado, desde a criação de uma atividade até sua disponibilização em produção.

```mermaid

A[Issue]
B[Branch]
C[Desenvolvimento]
D[Commits]
E[Pull Request]
F[Code Review]
G[Homologação]
H[Release]
I[Produção]

A --> B
B --> C
C --> D
D --> E
E --> F
F --> G
G --> H
H --> I
```

Cada uma dessas etapas é detalhada nos próximos documentos desta documentação.

---

# 5. Organização da Documentação

A documentação foi dividida em arquivos independentes para facilitar a manutenção e a consulta.

| Documento                | Conteúdo                                              |
| ------------------------ | ----------------------------------------------------- |
| `introducao.md`          | Objetivos, escopo e princípios de engenharia.         |
| `padroes-git.md`         | Padrões relacionados ao Git, GitHub e versionamento.  |
| `organizacao-projeto.md` | Organização das atividades, Issues e GitHub Projects. |
| `templates.md`           | Templates oficiais utilizados pela equipe.            |
| `exemplos.md`            | Exemplos completos dos padrões adotados.              |

---

# 6. Referências

Os padrões apresentados neste guia são inspirados em práticas amplamente adotadas pela indústria de software e adaptados às necessidades da equipe.

Entre as principais referências utilizadas estão:

* GitHub Engineering
* Google Engineering Practices
* Conventional Commits
* Semantic Versioning (SemVer)
* GitHub Flow
* GitHub Projects
* Release Please (Google)
* Keep a Changelog

Essas referências servem como base para a evolução contínua deste guia e poderão ser complementadas conforme novos processos forem incorporados pela equipe.
