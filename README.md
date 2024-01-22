# Plugin Genérico de Certificado para Revisores de Artigos

O **Plugin Genérico de Certificado para Revisores de Artigos** é uma ferramenta inovadora projetada para simplificar e aprimorar o reconhecimento dos revisores que contribuem significativamente para o processo de revisão de artigos científicos. Este plugin integra-se perfeitamente ao **Open Journal Systems (OJS)**, proporcionando aos autores a capacidade de baixar um certificado em formato PDF, validando e destacando seu papel como revisor de um artigo específico.

[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)

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

Pronto! Agora você configurou o banco de dados e instalou o Open Journal Systems em seu ambiente de desenvolvimento local.

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

# Processo de Dockerização OJS - Periódicos IFPB

## Configuração dos contâiners

### Dockerfiles 

O processo de criação dos containêres Docker se inicia a partir da criação de uma imagem Docker, contida nos arquivos `Dockerfile`. Neste caso, utilizamos dois arquivos deste tipo, um para o contâiner Apache que irá rodar o OJS e outro para o banco de dados MySQL.

**Dockerfile para MySQL**
```Dockerfile
FROM mysql:latest

# configurações para character set
COPY my-custom.cnf /etc/mysql/conf.d/my-custom.cnf

RUN chown -R mysql:mysql /var/lib/mysql

EXPOSE 3306

# executar configurações
CMD ["mysqld"]
```

**Dockerfile para OJS**
```Dockerfile
FROM php:7.4-apache

RUN apt-get update && apt-get install -y \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libmcrypt-dev \
    libpng-dev \
    libxml2-dev \
    zlib1g-dev \
    libicu-dev \
    libzip-dev \
    libonig-dev \
    unzip \
    tar \
    wget \
    nano \
    jq \
    net-tools \
    gettext
    
RUN docker-php-ext-install -j$(nproc) iconv pdo pdo_mysql mbstring zip intl gettext

# configurações Apache
COPY apache-conf.conf /etc/apache2/sites-available/000-default.conf

# reiniciar o Apache assim que o contâiner for iniciado
CMD ["apache2ctl", "-D", "FOREGROUND"]

WORKDIR /var/www/ojsnovo

# configurar permissão do Apache para o Apache
RUN chown -R www-data:www-data /var/www/ojsnovo
```

### Docker Compose

Após isso, iremos utilizar o comando `docker-compose` para criar e executar nossa imagem Docker. Primeiro, vamos entender a composição do diretório.

```bash
root@seerojs:/var/www ls -1a
.
..
apache-conf.conf
bd.sql
docker-compose.yml
Dockerfile.mysql
Dockerfile.ojs
.env
fullchain1.pem
html
my-custom.cnf
mysql-data
ojsnovo
privkey1.pem
```

Os arquivos `apache-conf.conf` e `my-custom.cnf` serão copiados para dentro dos contâiners através dos seus respectivos Dockerfiles. Já o `.env` define as variáveis de ambiente para o contâiner do banco de dados (isso será linkado através do docker-compose). O diretório `ojs` contém os arquivos do OJS e a pasta `mysql-data` irá persistir os dados do banco. 

O arquivo `docker-compose.yml` está configurado da seguinte maneira:
```yml
version: '3'
services:
  ojs:
    build:
      context: .
      dockerfile: Dockerfile.ojs
    env_file:
      - .env
    ports:
      - "8080:8080"
      - "443:443" # HTTPS
    volumes:
      - ./ojsnovo/:/var/www/ojsnovo # a pasta do OJS será dockerizada
    depends_on:
      - mysql
    networks:
      - periodicos

  mysql:
    build:
      context: .
      dockerfile: Dockerfile.mysql
    env_file:
      - .env
    networks:
      - periodicos
    volumes:
      - ./mysql-data:/var/lib/mysql
    ports:
      - "3306:3306"

volumes:
  mysql-data:

networks:
  periodicos:
    driver: bridge
```

### Configurações adicionais

É necessário estar atento ao arquivo `.env`, que define as variáveis de ambiente para os contâineres. No caso, será preciso configurar a conexão do banco de dados no arquivo `config.inc.php` do OJS para as do contâiner, que segue:

```ini
MYSQL_ROOT_PASSWORD=root
MYSQL_DATABASE=ojs248ult
MYSQL_USER=admin
MYSQL_PASSWORD=admin
```

No `config.inc.php`:
```inc
;;;;;;;;;;;;;;;;;;;;;
; Database Settings ;
;;;;;;;;;;;;;;;;;;;;;

[database]

driver = mysql
host = mysql
username = admin
password = admin
name = ojs248ult
```


### Executando os contâineres

Utilizaremos o comando `docker-compose up --build -d` para construir e executar nossos containêres, e `docker-compose up -d` para rodá-los outra vez. Para desativar os contâineres, `docker-compose stop`; e para removê-los, `docker-compose down`.

### MySQL Dump

Ao executar o containêr do banco de dados pela primeira vez, precisamos rodar o script de dump dos nossos dados. 

1. Copiar o arquivo do dump (`bd.sql`) para dentro da pasta `mysql-data`
2. Acessar o terminal do containêr: `docker exec -it ifpb_mysql_1 /bin/bash`
3. Acessar a pasta do MySQL: `cd var/lib/mysql`
4. Rodar o script de dump: `mysql -uadmin -padmin ojs248ult < bd.sql`

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
