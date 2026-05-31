# Walkie Talkie Messenger

Aplicativo desktop de mensagens em tempo real, inspirado na lógica de um walkie talkie digital.

O usuário escolhe uma frequência, informa um nome, define uma senha secreta e conversa instantaneamente com outras pessoas conectadas à mesma frequência.

O projeto combina um cliente desktop em Python, um servidor WebSocket em Go e criptografia de ponta a ponta aplicada no lado do cliente.

## Visão geral

O Walkie Talkie Messenger funciona com o conceito de frequências.

Cada frequência atua como uma sala temporária. Pessoas que informam a mesma frequência e a mesma senha secreta conseguem trocar mensagens em tempo real.

As mensagens não são armazenadas em banco de dados. O servidor apenas recebe e retransmite os dados para os usuários conectados à mesma frequência.

## Funcionalidades

- Aplicativo desktop com interface moderna e limpa
- Entrada por nome de usuário
- Entrada por frequência personalizada
- Senha secreta por frequência
- Conversas em tempo real
- Criptografia de ponta a ponta
- Servidor WebSocket desenvolvido em Go
- Cliente desktop desenvolvido em Python
- Comunicação online via servidor hospedado no Render
- Sem armazenamento de histórico de mensagens no aplicativo
- Possibilidade de gerar executável para Windows

## Tecnologias utilizadas

### Cliente desktop

- Python
- CustomTkinter
- websocket-client
- cryptography
- PyInstaller

### Servidor

- Go
- Gorilla WebSocket
- Render

## Como funciona

O sistema é dividido em duas partes principais.

### Cliente Python

O cliente é o aplicativo que o usuário abre no computador.

Nele, o usuário informa:

- Nome
- Frequência
- Senha secreta
- Mensagem

Antes de sair do computador, a mensagem é criptografada localmente. Isso significa que o servidor não recebe o conteúdo real da conversa.

### Servidor Go

O servidor recebe conexões WebSocket e organiza os usuários por frequência.

Ele não interpreta o conteúdo das mensagens. A função dele é apenas retransmitir os dados para os demais usuários da mesma frequência.

## Criptografia

O projeto utiliza criptografia de ponta a ponta baseada em uma senha secreta compartilhada entre os participantes da frequência.

Na prática:

- Quem tem a mesma frequência e a mesma senha consegue ler as mensagens.
- Quem tem a frequência, mas não tem a senha correta, não consegue descriptografar o conteúdo.
- O servidor não precisa conhecer a senha.
- O servidor não armazena mensagens.

## Aviso sobre segurança

Este projeto foi desenvolvido para fins de estudo, portfólio e experimentação técnica.

Embora implemente criptografia de ponta a ponta no cliente, nenhum sistema deve ser considerado 100% seguro de forma absoluta.

O objetivo é demonstrar conceitos de comunicação em tempo real, WebSocket, interface desktop, servidor em Go, criptografia aplicada e geração de aplicativo executável.

## Como executar o servidor localmente

É necessário ter o Go instalado.

Execute:

```bash
go run main.go
