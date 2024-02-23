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

Faça o download da versão 2.x ~ 3.x do OJS no site oficial: [https://pkp.sfu.ca/ojs/ojs_download/](https://pkp.sfu.ca/ojs/ojs_download/)

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

# Atualização do OJS 2.x => 3.x

## Dump do banco de dados

O dump do BD da versão atual (2.4.5) precisa ser feito com o seguinte comando
`mysqldump -u[usuário] -p[senha] --default-character-set=utf8 --skip-set-charset [banco de dados] > [arquivo de dump].sql`

## OJS 2.4.8-4

A versão atual do banco está em `2.4.5`. Vamos atualizá-lo para `2.4.8-4` (versão que já permite atualização para 3.x).

Antes de tudo, copie a pasta `public` para o mesmo diretório onde ficará a pasta do OJS 2.4.8-4. Serão construídos dois contâineres, como o comando `docker-compose up --build -d`, para esta atualização: um para o PHP5.6 e outro para o MySQL 5.7.44.

Antes da build, adicione as pastas `files\` e `ojs\` no arquivo `.dockerignore`. Isso reduzirá significativamente o tempo desta etapa.

Após a construção dos contâneires, execute os seguintes passos:

1. Copie o dump do banco de dados para a pasta `mysql-data`.
2. Copie o script de correção do banco de dados - `correcao_charset.sh` - para a pasta `mysql-data`.
    + O script sofreu uma pequena alteração, adicionando a flag `--defaults-file` para autenticação quando este for executado.
3. Execute o comando `docker cp my.cnf ojs2_mysql_1:/etc/mysql/conf.d/my-custom.cnf`. Isso irá adicionar as credenciais `user=admin` e `password=admin` no arquivo `my-custom.cnf`.
    + Se isso for feito na etapa de build, há uma chance de gerar um problema de autenticação na criação do banco de dados, no script de entrypoint.
4. Faça o dump do banco de dados - `mysql -uadmin -padmin ojs < [arquivo de dump].sql` - e em seguida, rode o script de correção.

Após estas etapas, o banco de dados estará pronto para a atualização.

## Atualização

Nesta etapa, já podemos remover as pastas `files` e `ojs` do `.dockerignore`. Reinicie também os contâineres com `docker-compose restart` para que os diretórios sejam montados pelo Docker.

Coloque as seguintes configurações no arquivo `config.inc.php`:
```
installed = Off

[database]
host =mysql
user = admin
password = admin
database = ojs

locale = pt_BR

client_charset = utf-8

database_charset = utf8

connection_charset = utf8

files_dir = /home/files/
```

O diretório da pasta `files` será montado, pelo contâiner, na pasta  `home`. Certifique-se que as permissões das pastas `/home/files` e `/var/www/html` (pasta do OJS) estão configuradas para `www-data:www-data` (usuário do Apache) com o comando `ls -l`. Se necessário, modifique as permissões com `chown -R www-data:www-data [pasta]` e `chmod -R 755 [pasta]`.

Após isso, execute este comando para checar a conexão do banco.

```bash
php -d memory_limit=2048M -d max_execution_time=300 -d post_max_size=8M -d upload_max_filesize=2000M -d max_input_time=600 tools/upgrade.php check
```

Por fim, execute a atualização.

```bash
nohup php -d memory_limit=2048M -d max_execution_time=300 -d post_max_size=8M -d upload_max_filesize=2000M -d max_input_time=600 tools/upgrade.php upgrade > upgrade_248.log & tail -f upgrade_248.log
```

Tempo estimado (dump + correção do charset + cópia da pasta `files` + atualização): <30min

## OJS 3.2.1-5

O primeiro passo será coletar a pasta `public`. Feito o dump do banco de dados, usando o mesmo comando dado acima, já podemos desmontar os contâineres com o comando `docker-compose down -v`.

Reinsira o diretório `files` e pasta `ojs` no `.dockerignore`, antes de montar os novos contâineres. Confira também no container para o MySQL se as variáveis de `character_set` estão em `utf8mb3`. Se não, use o comando `SET NAMES utf8mb3`.

Como esta etapa é significativamente mais longa, recomendamos aumentar o tempo de `timeout` da VM no arquivo `/etc/ssh/sshd_config`:
```
ClientAliveInterval 7200
ClientAliveCountMax 3
```

Recomendamos também executar o dump através do comando `SOURCE /var/lib/mysql/[nome do arquivo].sql` ao invés de `mysql ... ojs < [nome do arquivo].sql`, ao logar no banco de dados usando `mysql -u[usuário] -p[senha] [banco de dados]`

- Trocar no `config.inc.php`:
```ini

locale = pt-BR 

collation = utf8mb3_unicode_ci

connection_charset = utf8mb3

[database]
driver = mysqli
host = mysql
username = admin
password = admin
name = ojs

files = /home/files/
```

Removidas as pastas principais no arquivo `.dockerignore`, confira as permissões da pasta do OJS e da pasta `files` dentro do banco.

Após isso, execute este comando para checar a conexão do banco.

```bash
php -d memory_limit=2048M -d max_execution_time=300 -d post_max_size=8M -d upload_max_filesize=2000M -d max_input_time=600 tools/upgrade.php check
```

Por fim, execute a atualização.

```bash
nohup php -d memory_limit=2048M -d max_execution_time=300 -d post_max_size=8M -d upload_max_filesize=2000M -d max_input_time=600 tools/upgrade.php upgrade > upgrade_321.log & tail -f upgrade_321.log
```

Tempo estimado: 1h

Obs.: Pode ocorrer um travamento em `setFileName`, mas o processo segue, e é concluído normalmente.

## OJS 3.3.0-15

O processo desta etapa será idêntico à anterior.

Tempo estimado: < 20min

## Documentação

Aqui estão alguns links úteis para a documentação do OJS:

- [Documentação Geral do OJS](https://docs.pkp.sfu.ca/)

- [Guia de Atualização do OJS](https://docs.pkp.sfu.ca/learning-ojs/3.3/pt/about-ojs#install-and-upgrade)

- [Fórum da Comunidade OJS](https://forum.pkp.sfu.ca/)

## Tutoriais

Explore os seguintes tutoriais para obter informações detalhadas sobre a utilização do sistema:

   - [Tutorial Adicionar Assinatura ](https://drive.google.com/file/d/1UBK-XUUzCNE1DXd3Mo257GraEkMAVObn/view?usp=sharing)

   - [Tutorial Resetando Informações do E-Mail ](https://drive.google.com/file/d/1j8scB3GBmKQIzVCc5uZMACEVwu7dwevw/view?usp=sharing)

   - [Tutorial Redifinição dos Papéis](https://drive.google.com/file/d/1u0kWmCQbtAOiJ6VfvDjbevLLFAKgi3R6/view?usp=sharing)

## Contribuições

Se você encontrar problemas durante a atualização ou quiser contribuir com melhorias para este guia, sinta-se à vontade para abrir uma "issue" ou enviar um "pull request".

## Autores

- Aryelson Gonçalves(https://github.com/aryelson1)
- Symon Bezerra da Nóbrega(https://github.com/SymonBezerra)
- Edson Gervásio dos Santos Júnior(https://github.com/)

## Licença

# Gerador de Certificado para Open Journal Systems
# Versão 1.0

Este trabalho é software livre; você pode redistribuí-lo e/ou modificá-lo nos termos da Licença Pública Geral GNU publicada pela Free Software Foundation, na versão 3 da Licença, ou (a seu critério) qualquer versão posterior.

Este trabalho é distribuído na esperança de que será útil, mas SEM QUALQUER GARANTIA; sem a garantia implícita de COMERCIALIZAÇÃO ou ADEQUAÇÃO A UMA FINALIDADE ESPECÍFICA. Consulte a Licença Pública Geral GNU para obter mais detalhes.

Você deve ter recebido uma cópia da Licença Pública Geral GNU junto com este trabalho; se não, escreva para a Free Software Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA 02110-1301, USA.

