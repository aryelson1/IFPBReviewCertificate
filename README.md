# Plugin Genérico de Certificado para Revisores de Artigos

O **Plugin Genérico de Certificado para Revisores de Artigos** é uma ferramenta inovadora projetada para simplificar e aprimorar o reconhecimento dos revisores que contribuem significativamente para o processo de revisão de artigos científicos. Este plugin integra-se perfeitamente ao **Open Journal Systems (OJS)**, proporcionando aos autores a capacidade de baixar um certificado em formato PDF, validando e destacando seu papel como revisor de um artigo específico.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## Recursos Principais:

1. **Geração Automática de Certificados:**
   - O plugin automatiza a geração de certificados personalizados para os revisores, eliminando a necessidade de processos manuais demorados.

2. **Integração Perfeita com o OJS:**
   - Integração fácil e direta com o ambiente do Open Journal Systems, proporcionando uma experiência tranquila tanto para os autores quanto para os administradores da revista.

3. **Download Conveniente em Formato PDF:**
   - Os revisores podem baixar seus certificados em formato PDF de maneira simples e direta, garantindo facilidade de acesso e compartilhamento.

4. **Personalização do Certificado:**
   - Os administradores têm a capacidade de personalizar o design e as informações presentes nos certificados, adaptando-os às necessidades específicas da revista.

5. **Registro Histórico de Revisões:**
   - O plugin mantém um registro histórico das revisões realizadas por cada revisor, contribuindo para a transparência e reconhecimento contínuo.

## Como Utilizar:

1. **Instalação:**
   - Faça o download do plugin e siga as instruções de instalação no ambiente do OJS.

2. **Configuração:**
   - Personalize os certificados de acordo com as diretrizes da revista.

3. **Uso por Autores/Revisores:**
   - Após a conclusão bem-sucedida da revisão, os autores podem acessar o certificado correspondente através do OJS e realizar o download do PDF.

4. **Aprimoramento da Experiência do Revisor:**
   - A implementação deste plugin visa não apenas reconhecer os revisores, mas também melhorar a experiência geral, promovendo a participação ativa e contínua.

Este **Plugin Genérico de Certificado para Revisores de Artigos** é uma adição valiosa para qualquer revista que busca aprimorar o reconhecimento dos revisores, incentivando sua participação e contribuição essenciais para o avanço da pesquisa científica.

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

# Atualização do Open Journal Systems (OJS)

Antes de começar, é altamente recomendável fazer backup do seu sistema, incluindo a pasta `files` e um dump do banco de dados.

## 1. Backup do Sistema

- **Pasta 'files':**
  - Faça uma cópia de backup da pasta `files` do seu diretório OJS. Esta pasta contém os uploads de arquivos, como imagens e documentos.

- **Backup do Banco de Dados:**
  - Execute um dump do banco de dados atual usando ferramentas como `mysqldump` ou qualquer outra ferramenta que você prefira.

## 2. Download da Nova Versão do OJS

- Acesse o site oficial do OJS para baixar a versão mais recente: [https://pkp.sfu.ca/ojs/ojs_download/](https://pkp.sfu.ca/ojs/ojs_download/)

## 3. Descompacte o Novo OJS

- Descompacte o arquivo baixado em um diretório temporário.

## 4. Substitua a Pasta 'files'

- Copie a pasta `files` do seu backup para o diretório do novo OJS. Isso garantirá que todos os uploads e arquivos personalizados sejam preservados.

## 5. Migração do Banco de Dados

- Execute o novo OJS no navegador, o que geralmente inicia o processo de migração do banco de dados.

## 6. Configuração do Banco de Dados

- Durante o processo de instalação/migração, você será solicitado a fornecer informações do banco de dados. Use as mesmas informações que você usou na versão anterior do OJS.

## 7. Verificação e Configuração Adicional

- Verifique se tudo está funcionando corretamente no OJS após a atualização.
- Consulte a documentação da versão específica do OJS para quaisquer configurações adicionais ou ajustes necessários.

## 8. Conclusão

Parabéns, você concluiu a atualização do OJS! Certifique-se de revisar qualquer documentação de versão fornecida pela equipe do OJS para garantir que todas as novas funcionalidades sejam aproveitadas.

Aqui estão alguns links úteis para a documentação do OJS:

- [Documentação Geral do OJS](https://docs.pkp.sfu.ca/)

- [Guia de Atualização do OJS](https://docs.pkp.sfu.ca/learning-ojs/3.3/pt/about-ojs#install-and-upgrade)

- [Fórum da Comunidade OJS](https://forum.pkp.sfu.ca/)

## Contribuições

Se você encontrar problemas durante a atualização ou quiser contribuir com melhorias para este guia, sinta-se à vontade para abrir uma "issue" ou enviar um "pull request".

## Autores

- Aryelson Gonçalves(https://github.com/aryelson1)
- Symon Bezerra da Nóbrega(https://github.com/SymonBezerra)
- Edson Gervásio dos Santos Júnior(https://github.com/)

## Licença

Este plugin é distribuído sob a [Licença MIT](LICENSE), proporcionando flexibilidade e liberdade para sua utilização e adaptação conforme necessário.
