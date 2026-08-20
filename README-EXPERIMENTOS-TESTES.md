# Experimentos de Testes - Spring Petclinic REST

Este documento explica os experimentos de testes configurados neste repositório. O projeto possui diferentes suítes de testes para garantir a qualidade, performance e funcionamento correto da API REST.

## Estrutura de Testes

Os testes estão organizados no diretório `src/test/`. Eles são divididos nas seguintes categorias:

### 1. Testes de Performance com JMeter (`src/test/jmeter/`)
Contém scripts para testes de carga e estresse na aplicação.
- **Arquivos JMX**: Contêm as configurações de requisições, número de usuários simultâneos (threads) e tempo de execução (ramp-up).
- **Como executar**: Pode ser executado via interface gráfica do JMeter ou via linha de comando:
  ```bash
  jmeter -n -t src/test/jmeter/petclinic_jmeter.jmx -l resultado.jtl -e -o relatorio_html
  ```
- **Relatórios**: Os resultados geram arquivos `.jtl` (ex: `resultado_ct05.jtl`) e podem ser visualizados em formato HTML na pasta `relatorio_html_ct05`.

### 2. Testes de API com Postman (`src/test/postman/`)
Contém coleções do Postman para testar os endpoints da API de forma automatizada e manual.
- **Como executar**: Podem ser importados no Postman ou executados via **Newman** na linha de comando:
  ```bash
  newman run src/test/postman/sua-collection.json
  ```
Há também um script `postman-tests.sh` na raiz do projeto para facilitar essa execução.

### 3. Testes de Carga com Gatling (`src/test/gatling/`)
Outra ferramenta utilizada para testes de performance e carga.
- **Como executar**: Utilizando o plugin do Maven para Gatling:
  ```bash
  mvn gatling:test
  ```

### 4. Testes Unitários e de Integração (Java)
A aplicação também possui testes padrão em Java utilizando JUnit e Mockito.
- **Como executar**:
  ```bash
  ./mvnw test
  ```

## Resumo do Experimento (JMeter)
Observou-se a execução de testes como o `petclinic-jmeter-crud-benchmark.jmx`, onde os endpoints de operações CRUD (Criar, Ler, Atualizar, Deletar) de entidades como *Owners* e *Pets* foram testados para obter métricas de tempo de resposta, vazão (throughput) e possíveis gargalos da API em situações de alta concorrência.
