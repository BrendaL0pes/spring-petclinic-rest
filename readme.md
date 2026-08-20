# Experimentos de Testes de Desempenho - Spring Petclinic REST

Este repositório é um *fork* (ou cópia) do projeto original [Spring Petclinic REST](https://github.com/spring-petclinic/spring-petclinic-rest), criado pela comunidade Spring.

**O objetivo deste repositório não é o desenvolvimento da aplicação em si, mas sim utilizá-la como um ambiente alvo (sandbox) para a aplicação e estudo de testes de desempenho e de API.**

---

## 🛠️ Aplicação de Testes

Abaixo estão detalhadas as ferramentas e abordagens utilizadas neste experimento para avaliar a qualidade, performance e confiabilidade da aplicação Petclinic:

### 1. Testes de Performance com JMeter (`src/test/jmeter/`)
Utilizado para avaliar a escalabilidade da API REST por meio de injeção de carga e estresse.
- **Como funciona**: O plano de teste (`petclinic-jmeter-crud-benchmark.jmx`) e outros scripts (`petclinic_jmeter.jmx`) simulam o comportamento de múltiplos usuários simultâneos acessando os endpoints de operações CRUD (Criar, Ler, Atualizar, Deletar) para entidades como *Owners* e *Pets*.
- **Objetivo**: Obter métricas cruciais como tempo de resposta, vazão (throughput) e identificar possíveis gargalos na API sob alta concorrência.
- **Relatórios**: Os resultados são exportados e analisados em relatórios HTML detalhados (ex: `relatorio_html_ct05`).

### 2. Testes de API com Postman + Newman (`src/test/postman/`)
Focado na validação funcional e testes de não-regressão dos endpoints.
- **Como funciona**: Coleções de requisições configuradas no Postman cobrem os principais fluxos de negócio. Esses testes são executados automaticamente via linha de comando utilizando o **Newman**.
- **Objetivo**: Garantir que as respostas da API (status code, payload JSON, headers) estão retornando exatamente o esperado, prevenindo que alterações quebrem funcionalidades existentes.

### 3. Testes de Carga com Gatling (`src/test/gatling/`)
Outra abordagem para testes de performance utilizando a ferramenta Gatling.
- **Como funciona**: Scripts em código definem cenários de acesso concorrente aos serviços da aplicação.
- **Objetivo**: Comparar resultados de estresse com o JMeter ou validar abordagens diferentes de scriptagem de performance.

### 4. Testes Unitários e de Integração (Java)
A base de testes automatizados inerente ao ecossistema Spring (com JUnit e Mockito) também se encontra presente para validações a nível de código.

---

> **Nota:** Para instruções sobre como rodar a aplicação Spring Petclinic (via Maven, Docker, etc.), consulte o [repositório original oficial](https://github.com/spring-petclinic/spring-petclinic-rest).
