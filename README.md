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
