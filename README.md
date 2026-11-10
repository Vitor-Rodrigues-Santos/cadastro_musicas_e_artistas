# 🎵 Sistema Musical - Gerenciamento de Artistas e Músicas

[![PHP](https://img.shields.io/badge/PHP-777BB4?style=for-the-badge&logo=php&logoColor=white)]()
[![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white)]()
[![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)]()
[![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)]()
[![Status](https://img.shields.io/badge/Status-Concluído-brightgreen?style=for-the-badge)]()

Este repositório contém o desenvolvimento de um **Sistema Musical** completo, que inclui controle de acesso, manipulação de banco de dados relacional e funcionalidades de CRUD (Create, Read, Update, Delete) para artistas e músicas. O sistema se destaca pela integração com links do YouTube, upload e redimensionamento dinâmico de imagens (capas de álbuns e fotos de artistas) e filtros avançados de busca.

---

## 🚀 Tecnologias Utilizadas

- **PHP 8+** (Linguagem backend, gerenciamento de sessões, tratamento de imagens via GD e Prepared Statements para segurança)
- **MySQL / MariaDB** (Banco de dados relacional estruturado com chaves estrangeiras)
- **HTML5 & CSS3** (Interface de usuário responsiva, uso de CSS Variables, Flexbox e Grid)

---

## 📋 Funcionalidades e Telas Desenvolvidas

### 🔐 1. Autenticação e Segurança (`login.php` e `logout.php`)
- **Descrição:** Sistema de controle de acesso restrito.
- **Lógica aplicada:**
  - Validação de credenciais usando banco de dados e hash seguro (`password_verify` para senhas com bcrypt).
  - Prevenção contra SQL Injection usando *Prepared Statements*.
  - Controle de sessão via `$_SESSION`.
  - Rotina de logout completa, destruindo variáveis ativas e removendo os cookies de sessão.

### 🏠 2. Menu Principal (`index.php`)
- **Descrição:** Dashboard de acesso protegido, garantido pela inclusão do arquivo `valida_sessao.php`.
- **Lógica aplicada:**
  - Saudação personalizada ao usuário logado utilizando tratamento contra XSS (`htmlspecialchars`).
  - Navegação visual através de *cards* interativos para as demais áreas do sistema.

### 🎤 3. Gerenciamento de Artistas (`cadastro_artista.php`)
- **Descrição:** Interface para inserção, edição, listagem e exclusão de artistas.
- **Lógica aplicada:**
  - Validação de exclusão: Impede deletar um artista se ele possuir músicas vinculadas no banco (integridade relacional).
  - **Upload de Imagens:** Função em PHP para validar formato, tamanho, redimensionar dinamicamente a foto (mantendo a proporção) e salvá-la no servidor no diretório `img/`.

### 🎵 4. Gerenciamento de Músicas (`cadastro_musica.php`)
- **Descrição:** CRUD de músicas com relacionamento (chave estrangeira) para a tabela de artistas.
- **Lógica aplicada:**
  - Caixa de seleção (`<select>`) alimentada dinamicamente pelo banco de dados com os artistas disponíveis.
  - Conversão inteligente de links do YouTube: Expressões Regulares (`preg_match`) capturam o ID de qualquer formato de link inserido pelo usuário.
  - Upload de imagens para as capas dos álbuns (com exclusão física do arquivo `unlink()` ao deletar o registro).

### 🎼 5. Biblioteca Musical (`listagem_musicas.php`)
- **Descrição:** Painel geral de visualização do acervo com sistema de busca inteligente.
- **Lógica aplicada:**
  - Junção de tabelas (`JOIN`) para exibir o nome do artista junto com os dados da música.
  - **Filtros dinâmicos (GET):** Permite pesquisar por texto livre (título/álbum/artista), por gênero ou por um artista específico, concatenando as cláusulas `WHERE` de forma dinâmica.
  - Botão de "Assistir" que gera a URL direta para o vídeo do YouTube em uma nova aba com os atributos de segurança `rel="noopener noreferrer"`.

---

## 🗄️ Estrutura do Banco de Dados (`bd_2.sql`)

O projeto utiliza o banco de dados `sistema_musical_v2` estruturado com 3 tabelas principais:
- **`usuarios`**: Armazena as credenciais de acesso com senhas criptografadas.
- **`artistas`**: Dados cadastrais e caminho da imagem do perfil.
- **`musicas`**: Dados da faixa, letra, link do YouTube, imagem da capa e `artista_id` (Foreign Key referenciando a tabela de artistas).

*As credenciais padrão de desenvolvimento são:*  
**Usuário:** `admin` | **Senha:** `123`

---

## 👤 Repositório desenvolvido por:

**Nome:** Vitor Rodrigues Santos  
**Turma:** 1ID-DS
