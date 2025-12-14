# AlmoxApp - Infra

Este repositório contém a infraestrutura de desenvolvimento do AlmoxApp, incluindo configuração de containers, variáveis de ambiente e documentação.  
Ele integra os submódulos backend (NestJS) e frontend (NextJS), além do banco de dados PostgreSQL.

## Estrutura
```
almoxapp-infra/
├── docker-compose.yml
├── .env
├── docs/
├── backend/   → submodule (almoxapp-backend)
└── frontend/  → submodule (almoxapp-frontend)
```

## Pré-requisitos
- Git
- Docker e Docker Compose

## Clonando com submodules
```
git clone --recurse-submodules git@github.com:germanoricardi/almoxapp-infra.git
cd almoxapp-infra
```

Se já clonou sem recurse-submodules:
```
git submodule update --init --recursive
```

## Configuração
Crie o arquivo .env na raiz do almoxapp-infra:
```
POSTGRES_USER=almoxapp
POSTGRES_PASSWORD=almoxapp
POSTGRES_DB=almoxapp
```

## Rodando a aplicação
```
docker-compose up --build
```

Serviços disponíveis:
- Frontend → http://localhost:3000
- Backend → http://localhost:3001
- Postgres → localhost:5432

## Documentação
- Mockups e protótipos estão em docs/
- Histórico de alterações em CHANGELOG.md

## Fluxo de trabalho com submodules
Para atualizar código do frontend ou backend:
```
cd frontend (ou backend)
git add .
git commit -m "feat: ..."
git push
```

Depois volte ao infra e atualize a referência:
```
git add frontend backend
git commit -m "chore(submodules): update frontend and backend refs"
git push
```