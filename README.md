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
- `public Elemento` — Construtor.

```java
public class Elemento {
    String id;
    String descricao;
    String dataHora;
    String nomeCliente;
    Elemento proximo;
}


public Elemento(String id, String descricao, String dataHora, String nomeCliente) {
        this.id = id;
        this.descricao = descricao;
        this.dataHora = dataHora;
        this.nomeCliente = nomeCliente;
        this.proximo = null;
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

    public Pilha() {
        topo = null;
    }

    public void empilhar(String id, String descricao, String dataHora) {
        Elemento novo = new Elemento(id, descricao, dataHora, null); // Adicionado null para nomeCliente
        novo.proximo = topo;
        topo = novo;
    }

    public void desempilhar() {
        if (estaVazia()) {
            System.out.println("Histórico vazio!");
        } else {
            System.out.println("Removido: " + topo.id + " - " + topo.descricao);
            topo = topo.proximo;
        }
    }

    public boolean estaVazia() {
        return topo == null;
    }

    public void exibirHistorico() {
        if (estaVazia()) {
            System.out.println("Histórico vazio.");
            return;
        }
        Elemento atual = topo;
        while (atual != null) {
            System.out.println(atual.id + " - " + atual.descricao + " (" + atual.dataHora + ")");
            atual = atual.proximo;
        }
    }
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

    public Fila() {
        frente = null;
        tras = null;
    }

    public void enfileirar(String id, String nome, String motivo) {
        Elemento novo = new Elemento(id, motivo, null, nome); // Ajustado a ordem dos parâmetros
        if (estaVazia()) {
            frente = novo;
            tras = novo;
        } else {
            tras.proximo = novo;
            tras = novo;
        }
    }

    public void atender() {
        if (estaVazia()) {
            System.out.println("Fila de atendimento vazia!");
        } else {
            System.out.println("Atendendo: " + frente.nomeCliente + " - " + frente.descricao);
            frente = frente.proximo;
            if (frente == null) {
                tras = null;
            }
        }
    }

    public boolean estaVazia() {
        return frente == null;
    }

    public void exibirFila() {
        if (estaVazia()) {
            System.out.println("Fila vazia.");
            return;
        }
        Elemento atual = frente;
        while (atual != null) {
            System.out.println(atual.id + " - " + atual.nomeCliente + ": " + atual.descricao);
            atual = atual.proximo;
        }
    }
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
https://youtu.be/d3oiB8y4k2w
