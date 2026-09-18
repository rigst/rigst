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
| 04 | [Sistema Orçamentos](https://orcamentos.stolben.com) | Cadastro de clientes, catálogo de itens e montagem de orçamentos do rascunho ao documento final | [sistema_orcamentos](https://github.com/rigst/sistema_orcamentos) | AGPL-3.0 |
| 05 | [Sistema Finanças](https://financas.stolben.com) | Lançamentos por categoria com saldo e histórico mês a mês | [sistema_financas](https://github.com/rigst/sistema_financas) | AGPL-3.0 |
| 06 | [Estudo por Questões](https://questoes.stolben.com) | Importe PDFs de provas, aplique IA sobre as questões e gere relatórios de estudo | [sistema_questoes](https://github.com/rigst/sistema_questoes) | AGPL-3.0 |
| 07 | [Sistema Vetorial](https://vetorial.stolben.com) | Editor visual de modelos em PDF e geração em lote de certificados e documentos a partir de planilhas | [sistema_vetorial](https://github.com/rigst/sistema_vetorial) | AGPL-3.0 |
| 08 | [Dojo](https://dojo.stolben.com) | Mentoria de programação passo a passo: a IA monta o plano em etapas, guia o que fazer e por quê, e revisa o código sem escrever por você | [dojo](https://github.com/rigst/dojo) | AGPL-3.0 |
| 09 | [Dracma](https://dracma.stolben.com) | Assistente financeira no Telegram: conte o gasto por texto, áudio, foto ou PDF e ela categoriza, registra, divide a conta da casa e avisa antes de o limite estourar | [dracma](https://github.com/rigst/dracma) | AGPL-3.0 |

---

## Stack

**Back-end e dados**

![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![Django](https://img.shields.io/badge/Django-092E20?style=flat&logo=django&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat&logo=postgresql&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=flat&logo=redis&logoColor=white)
![Celery](https://img.shields.io/badge/Celery-37814A?style=flat&logo=celery&logoColor=white)
![HTMX](https://img.shields.io/badge/htmx-3366CC?style=flat&logo=htmx&logoColor=white)

**Infraestrutura**

![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat&logo=linux&logoColor=black)
![Nginx](https://img.shields.io/badge/Nginx-009639?style=flat&logo=nginx&logoColor=white)
![Gunicorn](https://img.shields.io/badge/Gunicorn-499848?style=flat&logo=gunicorn&logoColor=white)
![systemd](https://img.shields.io/badge/systemd-30B980?style=flat&logo=systemd&logoColor=white)

**CI/CD e observabilidade**

![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-2088FF?style=flat&logo=githubactions&logoColor=white)
![SonarQube Cloud](https://img.shields.io/badge/SonarQube%20Cloud-126ED3?style=flat&logo=sonarqubecloud&logoColor=white)
![Codecov](https://img.shields.io/badge/Codecov-F01F7A?style=flat&logo=codecov&logoColor=white)
![Grafana](https://img.shields.io/badge/Grafana-F46800?style=flat&logo=grafana&logoColor=white)
![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?style=flat&logo=prometheus&logoColor=white)
![Loki](https://img.shields.io/badge/Loki-F46800?style=flat&logo=grafana&logoColor=white)

**IA**

![Claude](https://img.shields.io/badge/Claude-Anthropic-D97757?style=flat)
![faster-whisper](https://img.shields.io/badge/faster--whisper-local-5A5A5A?style=flat)

**Mensageria**

![Telegram Bot API](https://img.shields.io/badge/Telegram%20Bot%20API-26A5E4?style=flat&logo=telegram&logoColor=white)

---

## Infraestrutura

Os sistemas rodam em VPS Linux com deploy próprio. Nginx, Gunicorn, HTTPS, domínios e processos todos sob meu controle. Cuido de toda a operação: do primeiro deploy à manutenção do dia a dia.

---

## Integração contínua

Os projetos compartilham um único pipeline de CI, em [rigst/ci](https://github.com/rigst/ci) — cada repositório tem um arquivo de dez linhas que o chama, em vez de uma cópia divergente. Ajuste feito lá vale para todos de uma vez.

A cada push, em paralelo: lint e formatação (`ruff`), tipos (`mypy` com `django-stubs`), testes com cobertura (`pytest`), análise de segurança do código (`bandit`), auditoria de CVE nas dependências (`pip-audit`), varredura de segredos em todo o histórico (`gitleaks`), `check --deploy` e verificação de migrações pendentes do Django, e agregação no SonarQube Cloud.

Há um segundo bloco, que nasce desligado e entra projeto a projeto: conferência de **licenças** (`liccheck`, com a política partindo do fato de que os projetos são AGPL-3.0), **SBOM** em CycloneDX sobre o ambiente resolvido, **integridade das dependências** (lock com hashes, instalado sob `--require-hashes`), testes **ponta a ponta** com Playwright num navegador real e **acessibilidade** com `axe-core`, reprovando por impacto e não por contagem.

Cobertura publicada no Codecov; bugs, code smells e duplicação no SonarQube Cloud. A adoção é gradual por projeto: cada etapa entra reportando e passa a bloquear quando o passivo dela zera.

O que o pipeline aprendeu na prática está escrito. O README do `rigst/ci` tem uma seção de **armadilhas conhecidas** — cada uma custou uma sessão de depuração e está lá com sintoma, causa e correção, de `ruff --fix` desligando signals do Django a renomear branch no GitHub sem que o SonarQube perceba, deixando o job verde e a análise parada.

---

## Entrega contínua

Quando o CI conclui com sucesso na `main`, o deploy dispara sozinho. O repositório compartilhado entrega só a mecânica — SSH, `concurrency`, comando forçado e retry; a lógica de deploy de cada app fica versionada e revisável no próprio projeto, em `deploy/cd-deploy.sh`.

No servidor, o deploy tem usuário próprio, chave restrita a um comando forçado e uma linha de `sudoers` que autoriza reiniciar exatamente a unidade daquele app. Nada além disso.

O script prefere `reload` — recarrega os workers sem derrubar o processo mestre, e o usuário não vê nada. Mas `reload` não troca o binário que já está carregado, então um upgrade do próprio Gunicorn passaria verde sem entrar em produção. Por isso a decisão entre `reload` e `restart` faz duas perguntas ao servidor: a versão instalada mudou neste `pip install`, e o pacote em disco é mais novo que o processo que o carregou. A segunda pergunta pega também o resíduo deixado por um deploy anterior.

Os timeouts de SSH que aparecem de vez em quando — fora do host, e que somem sozinhos — são absorvidos por um retry com espera crescente. Erro real do script não é repetido: se o deploy quebrou, ele quebra alto.

---

## Observabilidade

Um agente [Grafana Alloy](https://grafana.com/docs/alloy/) no servidor envia métricas e logs para o Grafana Cloud.

**Métricas:** host (`node_exporter`), PostgreSQL, Redis e sondas HTTP externas (`blackbox`) contra os domínios públicos.
**Logs:** journal do systemd e log de acesso do nginx, consultáveis por LogQL no Loki.

Os alertas cobrem host sem reportar, disco abaixo de 15% livre, Postgres e Redis fora do ar, unidade systemd inativa, sonda HTTP falhando e certificado TLS a menos de 14 dias do vencimento.

Dois deles se sobrepõem de propósito. A unidade `active` diz que o processo existe; a sonda HTTP diz que o site responde. É a segunda que pega app vivo devolvendo 500, nginx mal configurado, TLS quebrado e DNS — coisas que o processo, do lado de dentro, considera normais.

Cada alerta carrega na anotação o que fazer quando ele disparar: o comando de diagnóstico, o de correção e, quando existe, o incidente que o originou. Alerta que chega às três da manhã sem dizer o próximo passo é só barulho.

Uma nota de privacidade: o endereço do visitante é **mascarado no caminho de saída** para o Grafana Cloud. O arquivo local guarda o IP inteiro, que é o que cumpre o art. 15 do Marco Civil; o que sobe para o serviço externo já vai truncado. A obrigação legal continua atendida em disco sem que o dado pessoal saia do servidor.

---

## Contato

- Site: [stolben.com](https://stolben.com)
- E-mail: rodrigo@stolben.com
