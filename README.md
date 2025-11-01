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
| NgRx (opcional) | Gerenciamento de estado |
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

## About Laravel

Laravel is a web application framework with expressive, elegant syntax. We believe development must be an enjoyable and creative experience to be truly fulfilling. Laravel takes the pain out of development by easing common tasks used in many web projects, such as:

- [Simple, fast routing engine](https://laravel.com/docs/routing).
- [Powerful dependency injection container](https://laravel.com/docs/container).
- Multiple back-ends for [session](https://laravel.com/docs/session) and [cache](https://laravel.com/docs/cache) storage.
- Expressive, intuitive [database ORM](https://laravel.com/docs/eloquent).
- Database agnostic [schema migrations](https://laravel.com/docs/migrations).
- [Robust background job processing](https://laravel.com/docs/queues).
- [Real-time event broadcasting](https://laravel.com/docs/broadcasting).

Laravel is accessible, powerful, and provides tools required for large, robust applications.

## Learning Laravel

Laravel has the most extensive and thorough [documentation](https://laravel.com/docs) and video tutorial library of all modern web application frameworks, making it a breeze to get started with the framework. You can also check out the [Laravel Bootcamp](https://laravel.com/learn), where you will be guided through building a modern Laravel application.

If you don't feel like reading, [Laracasts](https://laracasts.com) can help. Laracasts contains thousands of video tutorials on a range of topics including Laravel, modern PHP, unit testing, and JavaScript. Boost your skills by digging into our comprehensive video library.

## Laravel Sponsors

We would like to extend our thanks to the following sponsors for funding Laravel development. If you are interested in becoming a sponsor, please visit the [Laravel Partners program](https://partners.laravel.com).

### Premium Partners

- **[Vehikl](https://vehikl.com/)**
- **[Tighten Co.](https://tighten.co)**
- **[Kirschbaum Development Group](https://kirschbaumdevelopment.com)**
- **[64 Robots](https://64robots.com)**
- **[Curotec](https://www.curotec.com/services/technologies/laravel/)**
- **[DevSquad](https://devsquad.com/hire-laravel-developers)**
- **[Redberry International](https://redberry.international/laravel-development)**
- **[Active Logic](https://activelogic.com)**

## Contributing

Thank you for considering contributing to the Laravel framework! The contribution guide can be found in the [Laravel documentation](https://laravel.com/docs/contributions).

## Code of Conduct

In order to ensure that the Laravel community is welcoming to all, please review and abide by the [Code of Conduct](https://laravel.com/docs/contributions#code-of-conduct).

## Security Vulnerabilities

If you discover a security vulnerability within Laravel, please send an e-mail to Taylor Otwell via [taylor@laravel.com](mailto:taylor@laravel.com). All security vulnerabilities will be promptly addressed.

## License

The Laravel framework is open-sourced software licensed under the [MIT license](https://opensource.org/licenses/MIT).