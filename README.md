# Título do Repositório

Descrição curta do propósito do repositório.

## Instalação do XAMPP

O XAMPP é um pacote que inclui Apache, MySQL, PHP e Perl. Ele fornece um ambiente de desenvolvimento local para facilitar a criação e teste de aplicações web.

### Passo 1: Download do XAMPP

Faça o download do XAMPP no site oficial: [https://www.apachefriends.org/index.html](https://www.apachefriends.org/index.html)

### Passo 2: Instalação

Siga as instruções específicas para o seu sistema operacional:

- **Windows:**
  - Execute o instalador baixado.
  - Siga as instruções na tela para concluir a instalação.

- **Linux:**
  - Abra um terminal.
  - Navegue até o diretório onde o arquivo foi baixado.
  - Dê permissões de execução ao arquivo: `chmod +x nome-do-arquivo.run`
  - Execute o instalador: `./nome-do-arquivo.run`

- **macOS:**
  - Abra o arquivo .dmg baixado.
  - Arraste o ícone do XAMPP para a pasta "Applications".

### Passo 3: Iniciar o XAMPP

- **Windows:**
  - Inicie o XAMPP a partir do menu Iniciar.
  - Clique em "Start" para os módulos Apache e MySQL.

- **Linux:**
  - Inicie o XAMPP a partir do terminal: `sudo /opt/lampp/lampp start`

- **macOS:**
  - Abra o XAMPP na pasta "Applications".
  - Clique em "Start" para os módulos Apache e MySQL.

## Verificando a Versão do PHP

### Passo 1: Acesse o PHP no Navegador

  1. Abra o navegador e digite o seguinte URL:

      ```bash
      http://localhost/dashboard/

### Passo 2: Verifique a Versão do PHP

No painel do XAMPP, clique em "phpMyAdmin" ou "Status" e procure pela seção que exibe a versão do PHP.

Pronto! Agora você instalou o XAMPP e verificou a versão do PHP em seu ambiente de desenvolvimento local.

## Instalação do Open Journal Systems (OJS)

### Passo 1: Download do OJS

Faça o download da última versão do OJS no site oficial: [https://pkp.sfu.ca/ojs/ojs_download/](https://pkp.sfu.ca/ojs/ojs_download/)

### Passo 2: Extração dos Arquivos

Descompacte o arquivo baixado em um diretório de sua escolha.

### Passo 3: Configuração do Banco de Dados

- Acesse o PHPMyAdmin: [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/)
- Crie um novo banco de dados para o OJS.
- Anote as credenciais do banco de dados (nome do banco, usuário e senha).

### Passo 4: Configuração do OJS

- Navegue até o diretório onde o OJS foi descompactado.
- Renomeie o arquivo `config.TEMPLATE.inc.php` para `config.inc.php`.
- Abra o arquivo `config.inc.php` em um editor de texto.
- Preencha as informações do banco de dados nas configurações apropriadas.

### Passo 5: Instalação

- Acesse o OJS no navegador, por exemplo: `http://localhost/caminho-para-ojs/`.
- Siga as instruções na tela para concluir a instalação.

Pronto! Agora você instalou o XAMPP, configurou o banco de dados e instalou o Open Journal Systems em seu ambiente de desenvolvimento local.

# Adicionando um Plugin Genérico ao Open Journal Systems (OJS)

1. **Obtenha o Plugin Genérico:**
   - Certifique-se de ter o plugin genérico desejado. Isso pode ser obtido a partir do repositório oficial do OJS ou de outras fontes confiáveis.

2. **Localize a Pasta de Plugins do OJS:**
   - Navegue até o diretório onde o OJS está instalado.

3. **Acesse a Pasta de Plugins:**
   - Dentro do diretório do OJS, vá para a pasta `plugins`.

4. **Crie uma Subpasta para o Novo Plugin:**
   - Dentro da pasta `plugins`, crie uma nova pasta com o nome do seu plugin genérico. Por exemplo, se o plugin for chamado "MeuPlugin", crie uma pasta chamada `MeuPlugin`.

5. **Copie os Arquivos do Plugin:**
   - Copie todos os arquivos do plugin genérico para a pasta que você acabou de criar (`MeuPlugin`). Certifique-se de copiar a estrutura completa do plugin.

6. **Ative o Plugin no OJS:**
   - Acesse a interface de administração do OJS no navegador.
   - Vá para "Configurações do Site" e, em seguida, "Plugins".
   - Procure pelo seu plugin na lista e ative-o.

7. **Configure o Plugin (se necessário):**
   - Após ativar o plugin, você pode precisar configurar algumas opções. Isso geralmente é feito na mesma página onde você ativou o plugin.

8. **Verifique a Funcionalidade:**
   - Após a ativação e configuração do plugin, verifique se a funcionalidade desejada está disponível no OJS.

Lembre-se de seguir a documentação específica do plugin, se disponível, para garantir que você atenda a todos os requisitos e configurações necessárias. Certifique-se também de fazer backup do seu sistema antes de fazer alterações significativas.


## Contribuições

Se você quiser contribuir para este projeto, sinta-se à vontade para abrir uma "issue" ou enviar um "pull request". Estamos abertos a melhorias e novas ideias.

## Licença

Este projeto está licenciado sob a [Licença MIT](LICENSE).
