<p align="center"><a href="https://laravel.com" target="_blank"><img src="https://raw.githubusercontent.com/laravel/art/master/logo-lockup/5%20SVG/2%20CMYK/1%20Full%20Color/laravel-logolockup-cmyk-red.svg" width="400" alt="Laravel Logo"></a></p>

<p align="center">
<a href="https://github.com/laravel/framework/actions"><img src="https://github.com/laravel/framework/workflows/tests/badge.svg" alt="Build Status"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/dt/laravel/framework" alt="Total Downloads"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/v/laravel/framework" alt="Latest Stable Version"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/l/laravel/framework" alt="License"></a>
</p>

# 🧠 Smart Service Hub

**Centralize e automatize atendimentos de múltiplas empresas com inteligência e eficiência.**

## 📋 Visão Geral

O **Smart Service Hub** é uma plataforma SaaS desenvolvida com **Laravel 11** (PHP 8.5 LTS) e **Angular**, que permite a centralização de atendimentos de clientes (via chat, e-mail ou API externa) em um único painel administrativo.

Cada empresa (tenant) possui:

- Suas próprias configurações de atendimento
- Usuários com diferentes papéis (admin, atendente)
- Um histórico de conversas e dashboard de performance
- Regras personalizadas (ex: horários de atendimento, tags, status)

## 🎯 Objetivos do Projeto

- Mostrar domínio completo do desenvolvimento full-stack com Laravel e Angular.
- Demonstrar arquitetura multi-tenant e boas práticas de isolamento de dados.
- Implementar API RESTful documentada, segura e performática.
- Apresentar um front-end moderno e responsivo com dashboard interativo.
- Servir como portfólio público, com foco técnico e visual para recrutadores.

## ⚙️ Stack Técnica

### 🔹 Backend

| Tecnologia | Finalidade |
|------------|------------|
| Laravel 11 (PHP 8.5 LTS) | Framework principal do backend |
| Sanctum / JWT | Autenticação e controle de acesso |
| PostgreSQL | Banco relacional multi-tenant |
| Redis (opcional) | Filas e cache |
| Laravel Queues | Mensageria assíncrona |
| Docker (dev opcional) | Ambiente isolado |
| Laravel Herd | Servidor local otimizado (uso atual) |

### 🔹 Frontend

| Tecnologia | Finalidade |
|------------|------------|
| Angular 18+ | Interface do painel administrativo |
| TailwindCSS | Estilização moderna e rápida |
| Signal (opcional) | Gerenciamento de estado |
| Chart.js / ApexCharts | Gráficos e relatórios |
| Axios / HttpClient | Comunicação com a API |

## 🧩 Principais Módulos do Sistema

### 1. Autenticação e Controle de Acesso

- Cadastro e login com Laravel Sanctum/JWT.
- Perfis: Admin, Atendente, Supervisor.
- Multi-empresa (cada tenant com domínio/subdomínio ou token único).

### 2. Gestão de Empresas (Tenants)

- CRUD completo de empresas.
- Cada empresa tem seus próprios usuários, atendimentos e regras.
- Middleware de isolamento por tenant_id.

### 3. Gestão de Atendimentos

- CRUD de tickets/conversas.
- Campos: cliente, canal (chat/email/API), status, tags, prioridade.
- Histórico de mensagens armazenado por empresa.

### 4. Mensageria e Processos Assíncronos

- Fila para processar eventos de chat simulados (ex: novas mensagens).
- Redis para enfileiramento (ou database driver local).

### 5. Dashboard e Relatórios

- Total de atendimentos por dia, status e canal.
- Taxa de resolução e tempo médio de resposta.
- Exibição via gráficos no front-end.

### 6. Integração Simulada com API Externa

- Endpoint que simula recebimento de mensagens via webhook.
- Pode ser adaptado depois para integrações reais (Twilio, Meta, etc).

## 🗂️ Estrutura Inicial do Repositório

```
smart-service-hub/
├── backend/
│   ├── app/
│   ├── bootstrap/
│   ├── config/
│   ├── database/
│   │   ├── migrations/
│   │   ├── seeders/
│   ├── routes/
```

🧠 Arquitetura Geral
Angular App  →  Laravel API  →  PostgreSQL
                        ↓
                      Redis (queues)


Cada requisição é autenticada via Bearer Token (JWT/Sanctum).

Middleware de tenant detection baseado no token.

Laravel processa lógica de negócios, fila, e serve dados para o front-end.

O Angular consome via REST, exibe dashboards e formulários.

💾 Modelagem Inicial (Banco de Dados)

Tabelas principais:

Tabela	Descrição
tenants	Empresas (nome, domínio, chave de API, plano)
users	Usuários do sistema (vinculados a um tenant)
tickets	Conversas/atendimentos
messages	Mensagens de cada ticket
tags	Etiquetas configuráveis por empresa
settings	Configurações gerais de cada tenant
🧰 Requisitos de Desenvolvimento
Pré-requisitos

PHP 8.5 (via Laravel Herd)

Composer 2.x

Node.js 20+

PostgreSQL 14+

Git

(Opcional) Redis

Comandos iniciais
composer create-project laravel/laravel backend
cd backend
php artisan serve


Frontend (posterior):

ng new frontend --style=css --routing=true
cd frontend
ng serve

🚀 Futuras Extensões (para roadmap público)

Autenticação OAuth (Google, GitHub)

Tema dark/light no front

Módulo de notificações push

Suporte real à API do WhatsApp (Twilio ou Meta)

## 🚢 Deploy gratuito

### Render

```bash
# Configuração para Render
# Backend (Laravel)
git push render main
```

| Configuração | Valor |
|--------------|-------|
| Type | Web Service |
| Build Command | `composer install && npm ci && npm run build` |
| Start Command | `php artisan serve --host 0.0.0.0 --port $PORT` |
| Environment | PHP |

### Railway

```bash
# Configuração para Railway
# Arquivo railway.json na raiz
{
  "build": {
    "builder": "nixpacks",
    "buildCommand": "composer install && php artisan migrate --force"
  },
  "deploy": {
    "startCommand": "php artisan serve --host 0.0.0.0 --port $PORT",
    "healthcheckPath": "/",
    "healthcheckTimeout": 90
  }
}
```

### Vercel

```bash
# Configuração para Vercel
# Arquivo vercel.json na raiz
{
  "version": 2,
  "framework": null,
  "functions": {
    "api/index.php": {
      "runtime": "vercel-php@0.6.0"
    }
  },
  "routes": [
    { "src": "/(.*)", "dest": "/api/index.php" }
  ],
  "env": {
    "APP_ENV": "production",
    "APP_DEBUG": "false",
    "APP_URL": "https://yourproductionurl.com",
    "DB_CONNECTION": "pgsql"
  }
}
```

## 🔧 Instalação e Configuração

### Requisitos do Sistema

- PHP 8.5+
- Composer 2.x
- Node.js 20+
- PostgreSQL 14+
- (Opcional) Redis

### Passos para Instalação

1. Clone o repositório
```bash
git clone https://github.com/seu-usuario/smart-service-hub.git
cd smart-service-hub
```

2. Instale as dependências do backend
```bash
composer install
cp .env.example .env
php artisan key:generate
```

3. Configure o banco de dados no arquivo .env
```
DB_CONNECTION=pgsql
DB_HOST=127.0.0.1
DB_PORT=5432
DB_DATABASE=smart_service_hub
DB_USERNAME=seu_usuario
DB_PASSWORD=sua_senha
```

4. Execute as migrações e seeders
```bash
php artisan migrate --seed
```

5. Inicie o servidor de desenvolvimento
```bash
php artisan serve
```

6. (Opcional) Instale e configure o frontend Angular
```bash
cd frontend
npm install
ng serve
```

## 👥 Contribuição

Contribuições são bem-vindas! Para contribuir:

1. Faça um fork do projeto
2. Crie uma branch para sua feature (`git checkout -b feature/nova-funcionalidade`)
3. Commit suas mudanças (`git commit -m 'Adiciona nova funcionalidade'`)
4. Push para a branch (`git push origin feature/nova-funcionalidade`)
5. Abra um Pull Request
