# Tutorial para Instalação e Configuração do OpenVPN

Este tutorial guiará você através dos passos para baixar e configurar o OpenVPN.

## Passo 1: Baixar o OpenVPN

1. Acesse o site oficial do OpenVPN em [OpenVPN Download](https://openvpn.net/community-downloads/).
2. Escolha a versão apropriada para o seu sistema operacional (Windows, macOS ou Linux) e faça o download do instalador.

## Passo 2: Instalar o OpenVPN

1. Localize o arquivo baixado e execute-o para iniciar a instalação.
2. Siga as instruções na tela para completar a instalação.

## Passo 3: Criar um Novo Perfil

1. Abra o OpenVPN.
2. Vá em **File** > **New Profile** para criar um novo perfil.

## Passo 4: Upload do Arquivo de Configuração

1. No novo perfil criado, clique em **Upload File**.
2. Selecione o arquivo de configuração VPN fornecido (geralmente termina com `.ovpn`) e faça o upload.

## Passo 5: Configurar o Protocolo VPN

1. No perfil, vá em **Settings**.
2. Dentro de **VPN Protocol**, marque a opção **UDP**.

## Passo 6: Configurações Avançadas

1. Ainda em **Settings**, acesse **Advanced Settings**.
2. Encontre a opção **Allow IPv6** e marque como **NO**.

## Passo 7: Conectar à VPN

1. Volte para a tela principal do OpenVPN.
2. Selecione seu perfil e clique em **Connect** para estabelecer uma conexão VPN.

Parabéns! Você configurou o OpenVPN para usar UDP e desativou o suporte ao IPv6.
