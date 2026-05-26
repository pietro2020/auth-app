<!-- Badges -->
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![PHP](https://img.shields.io/badge/PHP-8.0%2B-blue)](https://www.php.net/)
[![Laravel](https://img.shields.io/badge/Laravel-10-red)](https://laravel.com)
[![Tests](https://img.shields.io/badge/tests-PHPUnit-orange)](#running-tests)

# Nome do Projeto

Auth App — Sistema de autenticação e gestão de usuários

Breve descrição
: Um projeto base em Laravel para autenticação, autorização e gerenciamento de usuários, pronto para ser usado como ponto de partida para aplicações SaaS ou sistemas internos.

✨ Funcionalidades

- Autenticação (registro, login, logout) ✅
- Perfil de usuário e edição de dados ✅
- CRUD de Posts e Categorias (exemplo de recursos) ✅
- Upload de imagens para posts
- Sistema de permissões/roles (esqueleto para políticas)
- Endpoints RESTful para consumo por SPA/Mobile
- Testes automatizados básicos (Feature/Unit)

🛠 Tecnologias Utilizadas

- **Framework:** Laravel
- **Linguagem:** PHP
- **Gerenciador de pacotes:** Composer
- **Banco de dados:** [coloque aqui] (ex: MySQL, PostgreSQL)
- **Frontend:** Blade + Tailwind CSS (Vite)
- **Cache / Sessões:** Redis (opcional)
- **Filas / Jobs:** Laravel Queues (Redis/Database) (opcional)
- **Docker:** (opcional — instruções abaixo)

📦 Instalação

1. Clone o repositório

```bash
git clone https://github.com/seu-usuario/seu-repo.git
cd seu-repo
```

2. Instale dependências PHP e JS

```bash
composer install
npm install
```

3. Configure o ambiente

```bash
cp .env.example .env
# Edite .env conforme necessário (DB, CACHE, QUEUE, etc.)
```

4. Gere a APP_KEY

```bash
php artisan key:generate
```

5. Rode migrations e seeders

```bash
php artisan migrate
# Se houver seeders
php artisan db:seed
```

6. Rode build front-end e servidor local

```bash
npm run dev
php artisan serve --host=127.0.0.1 --port=8000
```

⚙️ Configuração (.env)

Principais variáveis que você deve revisar:

| Variável | Descrição | Exemplo |
|---|---:|---|
| `APP_NAME` | Nome da aplicação | My App |
| `APP_ENV` | Ambiente | local, production |
| `APP_DEBUG` | Debug ativo? | true/false |
| `APP_URL` | URL base | http://localhost:8000 |
| `DB_CONNECTION` | Driver do banco | mysql/postgres/sqlite |
| `DB_HOST` | Host do banco | 127.0.0.1 |
| `DB_PORT` | Porta do banco | 3306 |
| `DB_DATABASE` | Nome do banco | auth_app |
| `DB_USERNAME` | Usuário do banco | root |
| `DB_PASSWORD` | Senha do banco | secret |
| `CACHE_DRIVER` | Cache (opcional) | redis/file |
| `QUEUE_CONNECTION` | Filas (opcional) | database/redis |
| `REDIS_HOST` | Host do Redis | 127.0.0.1 |

Adapte conforme o seu ambiente (Docker, VPS, CI).

🚀 Executando o Projeto

- Ambiente local (desenvolvimento):

```bash
composer install
cp .env.example .env
php artisan key:generate
php artisan migrate --seed
npm install && npm run dev
php artisan serve
```

- Ambiente produção (exemplo básico):

```bash
composer install --no-dev --optimize-autoloader
php artisan config:cache
php artisan route:cache
php artisan view:cache
npm ci && npm run build
```

- Docker (se o projeto trouxer `docker-compose.yml`):

```bash
docker-compose up -d --build
docker-compose exec app composer install
docker-compose exec app php artisan migrate --seed
```

🧪 Testes

- Rodar suíte PHPUnit:

```bash
./vendor/bin/phpunit
# ou, se presente, pelo composer script
composer test
```

- Rodar testes específicos (ex.: apenas Feature):

```bash
./vendor/bin/phpunit --testsuite=Feature
```

- Cobertura (exemplo com Xdebug & phpunit.xml configurado):

```bash
./vendor/bin/phpunit --coverage-text
```

📁 Estrutura do Projeto (principais pastas)

- `app/` — Lógica do domínio (Models, Controllers, Policies, Requests)
- `config/` — Arquivos de configuração
- `routes/` — Rotas (`web.php`, `api.php`, `auth.php`)
- `resources/views/` — Views Blade
- `resources/js/` — Entrada JS (Vite)
- `database/migrations/` — Migrations
- `database/seeders/` — Seeders
- `tests/` — Testes Feature / Unit
- `public/` — Arquivos públicos (assets, uploads)

🔐 Autenticação & Segurança

- Autenticação: implemente com `Laravel Breeze`, `Sanctum` (API tokens) ou `Passport` (OAuth), conforme necessidade.
- Proteção CSRF: habilitada por padrão no middleware `VerifyCsrfToken`.
- Validações: Requests customizados (`FormRequest`) são usados para garantir entrada segura.
- Permissões e Roles: use `Gates/Policies` ou bibliotecas como `spatie/laravel-permission` para controle fino.

📡 API

O projeto expõe endpoints RESTful em `routes/api.php` seguindo convenções JSON:

- Autenticação: `POST /api/login`, `POST /api/register`, `POST /api/logout`
- Usuários: `GET /api/users`, `GET /api/users/{id}`
- Posts: `GET /api/posts`, `POST /api/posts`, `PUT /api/posts/{id}`, `DELETE /api/posts/{id}`

Exemplo de request (token Bearer):

```bash
curl -H "Accept: application/json" \
  -H "Authorization: Bearer <TOKEN>" \
  https://api.seuapp.com/api/posts
```

🐳 Docker

Se houver `Dockerfile` e `docker-compose.yml`, os contêineres recomendados são:

| Serviço | Função |
|---|---|
| app | PHP-FPM + Composer + Artisan |
| web | Nginx ou Apache (proxy) |
| db | MySQL / PostgreSQL |
| redis | Cache / Queue |

Comandos úteis:

```bash
docker-compose up -d --build
docker-compose exec app composer install
docker-compose exec app php artisan migrate --seed
docker-compose logs -f
```

☁️ Deploy

- VPS: configure webserver (Nginx), PHP-FPM, supervisor para filas, certificados TLS (Let's Encrypt).
- Forge: integrar deploy automático via GitHub/Bitbucket.
- Docker: subir imagens para registry e orquestrar (Docker Compose, Kubernetes).
- CI/CD: use GitHub Actions/GitLab CI para rodar testes e deploy automático.
- Variáveis de ambiente: configure `APP_KEY`, `DB_*`, `QUEUE_CONNECTION`, `REDIS_*`, `MAIL_*` no ambiente de produção.

🤝 Contribuição

Por favor siga estas regras ao contribuir:

1. Abra uma Issue para discutir mudanças grandes.
2. Crie branches com nomes claros: `feature/`, `fix/`, `chore/`.
3. Escreva testes para novas funcionalidades.
4. Execute `composer test` antes de submeter PR.
5. Mantenha estilo PSR-12 e rode `php-cs-fixer`/`larastan` quando aplicável.

Adicione um `CONTRIBUTING.md` se desejar regras mais detalhadas.

📄 Licença

Este projeto é licenciado sob a licença MIT — veja o arquivo `LICENSE`.

🛠 Troubleshooting — Erros Comuns

- Erro: "No application encryption key has been specified." — Rode `php artisan key:generate`.
- Erro: Conexão com o banco — Verifique `DB_HOST`, `DB_PORT`, `DB_DATABASE`, `DB_USERNAME`, `DB_PASSWORD` no `.env`.
- Problemas com permissões de storage — Rode `php artisan storage:link` e ajuste permissões em `storage/` e `bootstrap/cache/`.
- Filas não processam — Verifique `queue:work`/`supervisor` e `QUEUE_CONNECTION`.

❓ FAQ

- P: Qual DB devo usar em produção?
  - R: MySQL ou Postgres são recomendados; escolha com base em operação e backup.
- P: O projeto tem autenticação por token?
  - R: Suporte a tokens via `Sanctum` é recomendado para APIs.
- P: Como habilitar Redis?
  - R: Instale/rode o contêiner `redis` e ajuste `CACHE_DRIVER` e `QUEUE_CONNECTION` para `redis`.

🛣 Roadmap

- [ ] Integração completa com `spatie/laravel-permission` para roles
- [ ] Autenticação via OAuth2 (Passport)
- [ ] Suporte a Social Login (Google, GitHub)
- [ ] Tests coverage > 80%
- [ ] CI/CD com testes e deploy automático

---

Se quiser, posso também:

- Adicionar exemplos reais de `.env` para MySQL/Postgres
- Integrar `Sanctum` e mostrar exemplos de tokens
- Criar `CONTRIBUTING.md` e `CODE_OF_CONDUCT.md`

Obrigado — se quiser, atualizo o README com valores reais (DB, objetivo, público e features).
# 📰 Laravel Blog System

Sistema de blog desenvolvido com Laravel Fullstack, permitindo gerenciamento completo de posts e categorias, autenticação de usuários e upload de imagens. O projeto foi construído utilizando Blade, TailwindCSS e MySQL, seguindo boas práticas de desenvolvimento web moderno.

---

## ✨ Funcionalidades

* 🔐 Sistema de autenticação de usuários
* 📝 CRUD completo de posts
* 📂 CRUD completo de categorias
* 🖼️ Upload e gerenciamento de imagens
* 🎨 Interface responsiva com TailwindCSS
* ⚡ Aplicação Fullstack utilizando Laravel + Blade
* 🗄️ Banco de dados MySQL
* 📋 Validação de formulários
* 🔎 Organização de posts por categorias

---

## 🛠️ Tecnologias Utilizadas

* PHP
* Laravel
* Blade
* TailwindCSS
* MySQL
* XAMPP

---

## 📁 Estrutura do Projeto

```bash
app/
database/
public/
resources/
 ├── views/
 ├── css/
 └── js/
routes/
storage/
```

---

## ⚙️ Instalação e Configuração

### 1. Clone o repositório

```bash
git clone https://github.com/seu-usuario/seu-repositorio.git
```

### 2. Acesse a pasta do projeto

```bash
cd nome-do-projeto
```

### 3. Instale as dependências do PHP

```bash
composer install
```

### 4. Instale as dependências do frontend

```bash
npm install
```

### 5. Configure o arquivo `.env`

Copie o arquivo de exemplo:

```bash
cp .env.example .env
```

Configure as informações do banco de dados:

```env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=nome_do_banco
DB_USERNAME=root
DB_PASSWORD=
```

---

## 🔑 Gere a chave da aplicação

```bash
php artisan key:generate
```

---

## 🗄️ Execute as migrations

```bash
php artisan migrate
```

---

## 🖼️ Configure o armazenamento das imagens

```bash
php artisan storage:link
```

---

## 🚀 Inicie o projeto

### Servidor Laravel

```bash
php artisan serve
```

### Compilar assets

```bash
npm run dev
```

---

## 📸 Upload de Imagens

O sistema permite upload de imagens para posts, utilizando o sistema de armazenamento do Laravel.

As imagens ficam disponíveis através do diretório:

```bash
storage/app/public
```

---

## 🔐 Autenticação

O projeto possui sistema de login para gerenciamento do conteúdo do blog, permitindo acesso restrito às funcionalidades administrativas.

---

## 📚 Funcionalidades Administrativas

### Posts

* Criar posts
* Editar posts
* Excluir posts
* Upload de imagens
* Organização por categorias

### Categorias

* Criar categorias
* Editar categorias
* Excluir categorias

---

## 🎨 Interface

A interface foi desenvolvida utilizando TailwindCSS, garantindo:

* Responsividade
* Design moderno
* Melhor experiência do usuário
* Componentização visual

---

## 📌 Objetivo do Projeto

Este projeto foi desenvolvido com foco em aprendizado e prática de desenvolvimento Fullstack com Laravel, aplicando conceitos de:

* Arquitetura MVC
* CRUD completo
* Relacionamentos entre tabelas
* Upload de arquivos
* Autenticação
* Integração frontend/backend

---

## 📄 Licença

Este projeto está sob a licença MIT.

---

## 👨‍💻 Desenvolvedor

Desenvolvido utilizando Laravel Fullstack com Blade, TailwindCSS e MySQL.
