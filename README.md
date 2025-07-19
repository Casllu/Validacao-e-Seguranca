# Desafio: Validação e Segurança
## Descrição do Projeto
Este é um sistema de eventos e cidades que implementa um relacionamento N-1 entre entidades, onde múltiplos eventos podem estar associados a uma única cidade. O desafio consiste em implementar as funcionalidades necessárias para que todos os testes do projeto passem, com foco em validações de dados e controle de acesso baseado em roles.

## Estrutura do Sistema
### Entidades
- City (Cidade): Representa as cidades onde os eventos podem ocorrer
- Event (Evento): Representa os eventos que acontecem em determinadas cidades
- Relacionamento: N eventos para 1 cidade (N-1)
### Roles de Usuário
- Usuário Anônimo: Acesso apenas para leitura
- CLIENT: Pode ler dados e inserir novos eventos
- ADMIN: Acesso completo a todas as operações
## Regras de Controle de Acesso
### Rotas Públicas (sem autenticação)
- GET /events - Listar todos os eventos
- GET /events/{id} - Buscar evento por ID
- GET /cities - Listar todas as cidades
- GET /cities/{id} - Buscar cidade por ID
### Rotas para CLIENT e ADMIN
- POST /events - Inserir novo evento
### Rotas exclusivas para ADMIN
- POST /cities - Inserir nova cidade
- PUT /cities/{id} - Atualizar cidade existente
- DELETE /cities/{id} - Excluir cidade
- PUT /events/{id} - Atualizar evento existente
- DELETE /events/{id} - Excluir evento
## Regras de Validação
### Validações para City
- Nome: Campo obrigatório, não pode ser vazio ou nulo
### Validações para Event
- Nome: Campo obrigatório, não pode ser vazio ou nulo
- Data: Não pode ser uma data no passado
- Cidade: Campo obrigatório, deve estar associado a uma cidade válida
## Tecnologias Utilizadas
- Spring Boot
- Spring Security
- Spring Data JPA
- Bean Validation
- H2 Database (para testes)
- JUnit
## Como Executar
1. Clone o repositório
2. Execute ./mvnw clean install para instalar as dependências
3. Execute ./mvnw spring-boot:run para iniciar a aplicação
4. Execute ./mvnw test para rodar os testes
## Endpoints da API
### Cidades
- GET /cities - Lista todas as cidades (público)
- POST /cities - Cria nova cidade (apenas ADMIN)


### Eventos
- GET /events - Lista todos os eventos (público)
- POST /events - Cria novo evento (CLIENT e ADMIN)

## Estrutura de Autenticação
O sistema utiliza autenticação baseada em JWT (JSON Web Tokens) com as seguintes roles:
- ROLE_CLIENT
- ROLE_ADMIN
## Tratamento de Exceções
O sistema deve implementar tratamento adequado para:
- Validações de campo obrigatório
- Validações de data
- Controle de acesso não autorizado
- Recursos não encontrados
- Violações de integridade referencial
## Observações Importantes
- Todas as validações devem ser implementadas utilizando Bean Validation
- O controle de acesso deve ser configurado via Spring Security
- Os testes fornecidos devem passar sem modificações
- A estrutura do banco de dados já está definida e não deve ser alterada