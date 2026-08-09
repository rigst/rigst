# Rodrigo Stölben

Sistemas web em Python e Django, do código à operação.

Parto do problema real, modelo o fluxo, a estrutura de dados e as regras de negócio, e só então começo a construir. Prefiro menos peças, bem escolhidas, a empilhar ferramenta sobre ferramenta. E como sou eu quem opera os sistemas depois do deploy, cada decisão de código é tomada pensando em quem vai mantê-los estáveis em produção.

---

## Projetos publicados

| # | Projeto | Descrição | Código | Licença |
|---|---------|-----------|--------|---------|
| 01 | [Trilhas de Estudo](https://trilhas.stolben.com) | IA monta trilha completa: níveis, conteúdo sob demanda, exercícios e avaliações corrigidas automaticamente | [sistema_trilhas](https://github.com/rigst/sistema_trilhas) | AGPL-3.0 |
| 02 | [A.R.Q.](https://arq.stolben.com) | Gestão para escritórios de arquitetura: briefing, proposta, contrato, fases, agenda e financeiro num fluxo só | [sistema_arq](https://github.com/rigst/sistema_arq) | AGPL-3.0 |
| 03 | [Divisor de PDF](https://divisor.stolben.com) | Envie PDFs, comprima e divida em partes menores: download em PDF único ou ZIP | [divisor_pdf](https://github.com/rigst/divisor_pdf) | AGPL-3.0 |
| 04 | [Sistema de Orçamentos](https://orcamentos.stolben.com) | Cadastro de clientes, catálogo de itens e montagem de orçamentos do rascunho ao documento final | [sistema_orcamentos](https://github.com/rigst/sistema_orcamentos) | AGPL-3.0 |
| 05 | [Sistema Finanças](https://financas.stolben.com) | Lançamentos por categoria com saldo e histórico mês a mês | [sistema_financas](https://github.com/rigst/sistema_financas) | AGPL-3.0 |
| 06 | [Estudo por Questões](https://questoes.stolben.com) | Importe PDFs de provas, aplique IA sobre as questões e gere relatórios de estudo | [sistema_questoes](https://github.com/rigst/sistema_questoes) | AGPL-3.0 |

---

## Stack

**Back-end e dados**

![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![Django](https://img.shields.io/badge/Django-092E20?style=flat&logo=django&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat&logo=postgresql&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=flat&logo=redis&logoColor=white)
![Celery](https://img.shields.io/badge/Celery-37814A?style=flat&logo=celery&logoColor=white)

**Infraestrutura**

![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat&logo=linux&logoColor=black)
![Nginx](https://img.shields.io/badge/Nginx-009639?style=flat&logo=nginx&logoColor=white)
![Gunicorn](https://img.shields.io/badge/Gunicorn-499848?style=flat&logo=gunicorn&logoColor=white)

**IA**

![Claude](https://img.shields.io/badge/Claude-Anthropic-D97757?style=flat)

---

## Infraestrutura

Os sistemas rodam em VPS Linux com deploy próprio. Nginx, Gunicorn, HTTPS, domínios e processos todos sob meu controle. Cuido de toda a operação: do primeiro deploy à manutenção do dia a dia.

---

## Qualidade

Os projetos compartilham um único pipeline de CI, em [rigst/ci](https://github.com/rigst/ci) — cada repositório tem um arquivo de dez linhas que o chama, em vez de uma cópia divergente. Ajuste feito lá vale para todos de uma vez.

A cada push, em paralelo: lint e formatação (`ruff`), testes com cobertura (`pytest`), análise de segurança do código (`bandit`), auditoria de CVE nas dependências (`pip-audit`), varredura de segredos em todo o histórico (`gitleaks`), `check --deploy` e verificação de migrações pendentes do Django, e agregação no SonarQube Cloud.

Cobertura publicada no Codecov; bugs, code smells e duplicação no SonarQube Cloud. A adoção é gradual por projeto: cada etapa entra reportando e passa a bloquear quando o passivo dela zera.

---

## Contato

- Site: [stolben.com](https://stolben.com)
- E-mail: rodrigo@stolben.com
