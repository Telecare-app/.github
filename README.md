# 🏥 TeleCare — Cuidado conectado

Sistema Laravel para gestão de pacientes, profissionais, especialidades, prontuários,
agenda e autenticação com recuperação de senha por e-mail.

## Funcionalidades disponíveis

- Login, cadastro e recuperação/redefinição de senha.
- Cadastro e edição de pacientes.
- Cadastro de médicos e secretários.
- Cadastro e seleção de especialidades durante o cadastro do médico.
- Agenda e prontuários.

## Telas principais

### Login

<img width="722" height="876" alt="image" src="https://github.com/user-attachments/assets/c1d9594d-fa1a-4b7f-9e86-a39352d625ed" />


### Criar conta

<img width="722" height="876" alt="image" src="https://github.com/user-attachments/assets/2cda6a54-793f-45c5-a4bf-d174a08fa89b" />


### Recuperar senha

<img width="722" height="876" alt="image" src="https://github.com/user-attachments/assets/9b8e242f-5360-4c14-af7c-e6659fb957be" />


### Cadastrar cliente

<img width="933" height="2104" alt="image" src="https://github.com/user-attachments/assets/ea0e0ca6-e2ce-4f1a-9727-9759f4b27c30" />


### Cadastrar médico

<img width="933" height="1839" alt="image" src="https://github.com/user-attachments/assets/0d49ee9e-36c3-4c54-837f-d77cb3f174f3" />


### Cadastrar secretária

<img width="933" height="1714" alt="image" src="https://github.com/user-attachments/assets/6431d499-8d64-4909-bbff-7b4755c904fc" />


### Cadastrar especialidade

<img width="933" height="1336" alt="image" src="https://github.com/user-attachments/assets/5e22f6a3-641e-4ccf-b837-9cbc32f17a91" />


## Como executar após clonar

### Pré-requisitos

- PHP 8.5 ou compatível com a versão instalada do projeto.
- Composer.
- Node.js e NPM.
- MySQL 8.0 ou superior.

### Instalação

```bash
git clone https://github.com/VercosaV/telecare.git
cd telecare
composer install
npm install
cp .env.example .env
```

Edite o `.env` antes de continuar. Os campos marcados como obrigatórios em
[.env.example](.env.example) precisam ser preenchidos.

Configure o banco MySQL no `.env`:

```env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=telecare
DB_USERNAME=root
DB_PASSWORD=
```

Crie o banco de dados antes de executar as migrations:

```sql
CREATE DATABASE telecare CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
```

Depois, execute:

```bash
php artisan key:generate
php artisan migrate
php artisan storage:link
```

Para compilar os assets e iniciar a aplicação:

```bash
npm run build
php artisan serve --host=127.0.0.1 --port=8001
```

Acesse <http://127.0.0.1:8001>.

Durante o desenvolvimento, use `npm run dev` em um segundo terminal no lugar
de `npm run build`.

### Configuração de e-mail

A recuperação de senha usa SMTP. Para Gmail, crie uma senha de aplicativo e
configure no `.env`:

```env
MAIL_MAILER=smtp
MAIL_SCHEME=smtp
MAIL_HOST=smtp.gmail.com
MAIL_PORT=587
MAIL_USERNAME=seu-email@gmail.com
MAIL_PASSWORD=sua-senha-de-aplicativo
MAIL_FROM_ADDRESS="seu-email@gmail.com"
MAIL_FROM_NAME="${APP_NAME}"
```

Nunca versionar `.env` nem compartilhar senhas ou tokens.

## Fluxos principais

### Cadastrar um cliente

1. Faça login.
2. Acesse **Pacientes**.
3. Clique em **Cadastrar paciente**.
4. Preencha os dados pessoais e de endereço.
5. Clique em **Salvar**.

### Cadastrar um médico

1. Faça login.
2. Acesse **Profissionais**.
3. Clique em **Novo profissional**.
4. Selecione **Médico(a)** e preencha os dados.
5. Clique em **Escolher especialidade**.
6. Selecione uma especialidade existente ou cadastre uma nova.
7. Ao retornar, os dados já preenchidos continuam no formulário.
8. Clique em **Salvar profissional**.

### Cadastrar uma secretária

1. Faça login.
2. Acesse **Profissionais**.
3. Clique em **Novo profissional**.
4. Selecione **Secretário(a)**.
5. Preencha os dados do cadastro.
6. Clique em **Salvar profissional**.

### Cadastrar uma especialidade

1. Faça login.
2. Acesse **Profissionais** e clique em **Novo profissional**, ou acesse a tela de especialidades.
3. Clique em **Escolher especialidade**.
4. Clique em **Nova especialidade**.
5. Informe o nome da especialidade e salve.
6. O sistema retorna para a tela anterior com a especialidade disponível para seleção.

### Recuperar senha

1. Na tela de login, clique em **Esqueci minha senha**.
2. Informe o e-mail cadastrado.
3. Abra o link recebido por e-mail.
4. Informe e confirme a nova senha.

## Comandos úteis

```bash
php artisan test
php artisan migrate
php artisan config:clear
npm run build
```
