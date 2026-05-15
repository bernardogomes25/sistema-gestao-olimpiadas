# 🏅 Sistema de Gestão das Olimpíadas (SGO)

> **Disciplina:** Projeto de Software — Engenharia de Software · PUC Minas  
> **Professor:** João Paulo Carneiro Aramuni  
> **Período:** 4º · Turno: Manhã  
> **Integrantes:** Bernardo Gomes · Pedro Arthur

---

## 📋 Descrição do Sistema

Com a chegada das Olimpíadas, um novo sistema de gestão é necessário para coordenar os diferentes aspectos do evento. O **SGO** permite o gerenciamento de competições, inscrições de atletas, alocação de locais para as provas e controle de resultados.

---

## 📐 Regras de Negócio

| # | Regra |
|---|-------|
| RN1 | **Cadastro de competições:** o sistema deve permitir o cadastro de competições com nome da modalidade, data, horário, local e lista de atletas inscritos. |
| RN2 | **Inscrição de atletas:** cada atleta pode participar de várias competições, mas só pode representar um país em cada modalidade. |
| RN3 | **Alocação de locais:** um local só pode abrigar uma competição por vez — conflitos de horário devem ser evitados. |
| RN4 | **Controle de resultados:** após a realização da competição, o sistema registra o 1º, 2º e 3º colocados. |
| RN5 | **Relatórios de medalhas:** o sistema gera relatórios mostrando o desempenho de cada país com base nas medalhas de ouro, prata e bronze conquistadas. |

---

## 👤 Histórias de Usuário

### US01 — Cadastrar Competição
**Como** Administrador,  
**quero** cadastrar uma nova competição informando modalidade, data, horário e local,  
**para que** o evento fique registrado no sistema e possa receber inscrições de atletas.

**Critérios de aceitação:**
- O sistema deve exigir: nome da modalidade, data, horário e local.
- A competição deve ser salva com status `PENDENTE`.
- Não deve ser possível cadastrar duas competições no mesmo local e horário.

---

### US02 — Inscrever Atleta em Competição
**Como** Atleta,  
**quero** me inscrever em uma competição específica representando meu país,  
**para que** minha participação fique registrada e eu possa competir oficialmente.

**Critérios de aceitação:**
- O atleta deve selecionar a competição disponível na lista.
- O sistema deve impedir que o mesmo atleta represente países diferentes na mesma modalidade.
- O atleta pode estar inscrito em múltiplas competições de modalidades distintas.

---

### US03 — Alocar Local para Competição
**Como** Administrador,  
**quero** alocar um local disponível para uma competição,  
**para que** o espaço físico esteja reservado sem conflito de horário.

**Critérios de aceitação:**
- O sistema deve verificar a disponibilidade do local na data e horário informados.
- Um local não pode ser alocado para duas competições simultâneas.
- O sistema deve exibir mensagem de erro em caso de conflito.

---

### US04 — Registrar Resultado de Competição
**Como** Comissão Técnica,  
**quero** registrar os resultados de uma competição encerrada,  
**para que** os classificados em 1º, 2º e 3º lugares sejam formalizados no sistema.

**Critérios de aceitação:**
- Somente competições com status `ENCERRADA` podem ter resultado registrado.
- Os três colocados devem ser atletas previamente inscritos na competição.
- O registro de resultado deve atualizar automaticamente o contador de medalhas do país.

---

### US05 — Consultar Competições
**Como** Administrador, Atleta ou Comissão Técnica,  
**quero** consultar a lista de competições cadastradas com seus detalhes,  
**para que** eu possa acompanhar o calendário e o status de cada prova.

**Critérios de aceitação:**
- A listagem deve exibir: modalidade, data, horário, local e status.
- Deve ser possível filtrar por modalidade, data ou status.
- Qualquer usuário autenticado pode consultar as competições.

---

### US06 — Gerar Relatório de Medalhas
**Como** Comissão Técnica,  
**quero** gerar um relatório de medalhas por país,  
**para que** o desempenho de cada delegação olímpica seja visível e comparável.

**Critérios de aceitação:**
- O relatório deve listar todos os países com ao menos uma medalha.
- A ordenação padrão deve ser: ouro (desc) → prata (desc) → bronze (desc).
- O relatório deve ser acessível após ao menos um resultado ser registrado.

---

## 📂 Estrutura do Repositório

```
sistema-gestao-olimpiadas/
│
├── README.md
│
├── imagens/
│   ├── diagrama-de-caso-de-uso.png
│   ├── diagrama-de-classes.png
│   ├── diagrama-de-pacotes.png
│   ├── diagrama-de-componentes.png
│   └── diagrama-de-implantacao.png
│
└── codigos/
    ├── diagrama-de-caso-de-uso.puml
    ├── diagrama-de-classes.puml
    ├── diagrama-de-pacotes.puml
    ├── diagrama-de-componentes.puml
    └── diagrama-de-implantacao.puml
```

---

## 🗂️ Diagramas UML

### 1. Diagrama de Caso de Uso

Modela os atores (**Administrador**, **Atleta**, **Comissão Técnica**) e seus casos de uso principais dentro da fronteira do sistema SGO. Inclui relações `<<include>>` e `<<extend>>` entre os casos de uso.

<img width="700px" src="https://raw.githubusercontent.com/bernardogomes25/sistema-gestao-olimpiadas/main/imagens/diagrama-de-caso-de-uso.png"/>

---

### 2. Diagrama de Classes

Representa a estrutura estática do sistema com as classes **Competicao**, **Atleta**, **Local**, **Resultado**, **Pais** e **RelatorioMedalhas**, seus atributos, métodos, visibilidades e relacionamentos (associações, agregações e dependências) com multiplicidades corretas.

<img width="700px" src="https://raw.githubusercontent.com/bernardogomes25/sistema-gestao-olimpiadas/main/imagens/diagrama-de-classes.png"/>

---

### 3. Diagrama de Pacotes

Organiza o sistema em quatro camadas de responsabilidade — **Interface**, **Controle**, **Modelo** e **Persistência** — com dependências `<<use>>` explícitas entre os pacotes, seguindo o padrão arquitetural em camadas.

<img width="700px" src="https://raw.githubusercontent.com/bernardogomes25/sistema-gestao-olimpiadas/main/imagens/diagrama-de-pacotes.png"/>

---

### 4. Diagrama de Componentes

Modela os componentes executáveis do sistema (**Interface de Usuário**, **Módulos de Backend** e **Banco de Dados**), com interfaces fornecidas (lollipop `○—`) e requeridas (`—(`) explícitas, mostrando como os módulos se comunicam entre si.

<img width="700px" src="https://raw.githubusercontent.com/bernardogomes25/sistema-gestao-olimpiadas/main/imagens/diagrama-de-componentes.png"/>

---

### 5. Diagrama de Implantação

Ilustra a arquitetura física distribuída do sistema em quatro nós: **Dispositivo do Usuário**, **Servidor Web**, **Servidor de Aplicação** e **Servidor de Banco de Dados**, com protocolos e portas de comunicação especificados em cada canal.

<img width="700px" src="https://raw.githubusercontent.com/bernardogomes25/sistema-gestao-olimpiadas/main/imagens/diagrama-de-implantacao.png"/>

---

## 🛠️ Tecnologias Utilizadas

| Ferramenta | Finalidade |
|---|---|
| [PlantUML](https://plantuml.com/) | Geração dos diagramas UML a partir de código `.puml` |
| [PlantText](https://www.planttext.com/) | Visualização online dos diagramas |
| GitHub | Versionamento e entrega do repositório |

---

## ▶️ Como visualizar os diagramas

1. Acesse [planttext.com](https://www.planttext.com/).
2. Abra o arquivo `.puml` desejado da pasta `codigos/`.
3. Cole o conteúdo no editor online.
4. O diagrama será renderizado automaticamente.

---

## 📎 Referências

- [PlantUML — Documentação oficial](https://plantuml.com/guide)
- [PlantUML API — Prof. João Paulo Aramuni](https://github.com/joaopauloaramuni/projeto-de-software/tree/main/PROJETOS/Python/Projeto%20PlantUML%20API)
- Sommerville, I. **Engenharia de Software**. 10ª ed. Pearson, 2018.
- Larman, C. **Utilizando UML e Padrões**. 3ª ed. Bookman, 2007.
