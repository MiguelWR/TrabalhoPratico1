# TrabalhoPratico1
# Sistema de Gerenciamento de Atendimento ao Cliente

## Integrantes do Grupo
### Carlos Eduardo Jeronimo
### Guilherme Santos de Oliveira
### Marcelo Eduardo Lins
### Miguel Wihby Rezende

## Descrição do Projeto

Este projeto implementa um sistema simples de gerenciamento de atendimento ao cliente utilizando **estruturas de dados próprias**: uma pilha para o histórico de atendimentos e uma fila para a ordem de atendimento dos clientes.

## Estrutura do Sistema

### 1. Classe `Elemento`
Classe base que tem um nó na lista encadeada:
- `id` — Identificador único.
- `descricao` — Descrição do atendimento.
- `dataHora` — Data e hora da solicitação (histórico).
- `nomeCliente` — Nome do cliente (usado na fila).
- `proximo` — Referência para o próximo elemento.


```java
public class Elemento {
    String id;
    String descricao;
    String dataHora;
    String nomeCliente;
    Elemento proximo;
}
```


### 2. Pilha — Histórico de Solicitações

A pilha armazena o histórico de solicitações já realizadas.  

Métodos principais:
- `empilhar(id, descricao, dataHora)` — Adiciona uma nova solicitação ao histórico.
- `desempilhar()` — Remove a solicitação mais recente.
- `estaVazia()` — Verifica se o histórico está vazio.
- `exibirHistorico()` — Mostra todas as solicitações do histórico.


```java
public class Pilha {
    private Elemento topo;
    ...
}
```


### 3. Fila — Ordem de Atendimento

A fila gerencia a ordem de atendimento dos clientes.

Métodos principais:
- `enfileirar(id, nome, motivo)` — Adiciona um cliente à fila de atendimento.
- `atender()` — Atende o cliente que está na frente da fila.
- `estaVazia()` — Verifica se a fila está vazia.
- `exibirFila()` — Mostra todos os clientes aguardando.


```java
public class Fila {
    private Elemento frente;
    private Elemento tras;
    ...
}
```


## Fluxo do Programa (`Main.java`)

O sistema oferece um menu interativo para o usuário:

- Adicionar Solicitação ao Histórico;
- Remover Solicitação do Histórico;
- Mostrar Histórico;
- Adicionar Cliente à Fila;
- Atender Cliente;
- Mostrar Fila de Atendimento;
- Sair do Sistema.

O usuário interage via scanner no console, preenchendo as informações conforme solicitado.

## Demonstração em Vídeo

Link do vídeo com a explicação do funcionamento do sistema:  
[Inserir Link do YouTube Aqui]
