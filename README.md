# Banco de Performance da API do Banco com K6

## Introdução
Este repositório contém testes de performance para a API do Banco (API educativa desenvolvida pelo Julio de Lima para a Mentoria de Teste de Software), utilizando JavaScript e a ferramenta K6. O objetivo é avaliar o desempenho da API sob diferentes condições de carga, garantindo que ela atenda aos requisitos de escalabilidade e confiabilidade.

## Tecnologias Utilizadas
- **JavaScript**: Linguagem usada para escrever os scripts de teste.
- **[K6](https://k6.io/)**: Ferramenta de teste de carga e performance para APIs, serviços web e sistemas distribuídos.
- Variáveis de ambiente para configuração dinâmica (ex: `BASE_URL`).

## Estrutura do Repositório
A estrutura do repositório está organizada da seguinte forma:
```
banco-api-performance-tests/
├── config/
│   ├── config.local.json
├── fixtures/
│   ├── postLogin.json
├── helpers/                
│   ├── autenticacao.js
├── tests/
│   ├── login.test.js
│   ├── transferencias.test.js
├── utils/
│   ├── variaveis.js
├── .gitignore
├── README.md
```
## Objetivo de Cada Grupo de Arquivos
- **config/**: Contém arquivos de configuração, como `config.local.json`, que armazena configurações específicas do ambiente de teste, como URLs e chaves de API.
- **fixtures/**: Armazena dados de exemplo ou payloads, como `postLogin.json`, utilizados como entrada para simular requisições na API durante os testes.
- **helpers/**: Inclui scripts de suporte, como `autenticacao.js`, que fornecem funções reutilizáveis para autenticação e outras operações comuns nos testes.
- **tests/**: Contém os scripts de teste escritos em JavaScript para o K6, como `login.test.js` e `transferencias.test.js`, cada um projetado para simular e medir o desempenho de cenários específicos da API.
- **utils/**: Armazena funções utilitárias, como `variaveis.js`, que auxiliam na manipulação de dados ou lógica compartilhada entre os scripts de teste.

## Modo de Instalação e Execução do Projeto
### Pré-requisitos
- **Node.js**: Versão 16 ou superior.
- **K6**: Instale o K6 seguindo as instruções oficiais em [k6.io](https://k6.io/docs/getting-started/installation/).
- **Git**: Para clonar o repositório.

### Instalação
- Clone o repositório:
   ```bash
   git clone https://github.com/matheuspnascimento/banco-api-performance-tests.git
   ```
- Acesse o diretório do projeto:
   ```bash
   cd banco-api-performance-tests
   ```
### Execução
- **Configuração da variável de ambiente BASE_URL**:
   Defina a variável de ambiente `baseUrl` no `config.local.json` com o endereço da API que será testada. Exemplo:
   ```bash
   {
    "baseUrl": "http://localhost:3000"
   }
   ```

Essas variáveis serão usadas dinamicamente nos testes para montar as requisições.

- **Executar um teste**
Para rodar um teste use o comando:
    ```bash
    k6 run tests/login.test.js -e BASE_URL=http://localhost:3000
    k6 run tests/transferencias.test.js -e BASE_URL=http://localhost:3000
    ```

- **Executar testes com o dashboard em tempo real**:
   Para rodar os testes e visualizar o dashboard web do K6 em tempo real (se tiver no Windows, utilize o Bash em vez do CMD):
   ```bash
   K6_WEB_DASHBOARD=true k6 run tests/login.test.js
   K6_WEB_DASHBOARD=true k6 run tests/transferencias.test.js
   ```

- **Executar testes com exportação de relatório HTML**:
   Para rodar os testes e gerar um relatório HTML com os resultados (se tiver no Windows, utilize o Bash em vez do CMD):
   ```bash
   K6_WEB_DASHBOARD=true K6_WEB_DASHBOARD_EXPORT=html-report.html k6 run tests/login.test.js
   K6_WEB_DASHBOARD=true K6_WEB_DASHBOARD_EXPORT=html-report.html k6 run tests/transferencias.test.js
   ```

   O arquivo `html-report.html` será gerado no diretório raiz do projeto e pode ser aberto em qualquer navegador para visualização detalhada dos resultados.

### Notas
- Certifique-se de que a variável `baseUrl` está configurada corretamente antes de executar os testes.
- O dashboard web do K6 estará disponível durante a execução (verifique a porta exibida no terminal).
- Para mais detalhes sobre as opções do K6, consulte a [documentação oficial](https://k6.io/docs/).
