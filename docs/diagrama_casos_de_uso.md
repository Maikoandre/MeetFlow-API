# 📊 Diagrama de Casos de Uso da API

Este documento apresenta o diagrama de Casos de Uso que ilustra as interações dos diferentes atores do sistema (**Administrador**, **Organizador**, **Participante** e **Usuário Anônimo**) com os recursos fornecidos pela API e aplicação web do **MeetFlow**.

```mermaid
graph LR
    %% Actors (Stacked Vertically on the Left)
    Anon["  O  <br/> /|\ <br/> / \ <br/>Usuário Anônimo"]
    Part["  O  <br/> /|\ <br/> / \ <br/>Participante"]
    Org["  O  <br/> /|\ <br/> / \ <br/>Organizador"]
    Admin["  O  <br/> /|\ <br/> / \ <br/>Administrador"]

    Anon ~~~ Part
    Part ~~~ Org
    Org ~~~ Admin

    %% Use Cases Grouped by Role
    subgraph Geral [Ações Públicas]
        UC_VerEventos(Visualizar Eventos)
        UC_Cadastrar(Cadastrar-se no Sistema)
    end

    subgraph Participante_UC [Ações de Participante]
        UC_VerDetalhes(Visualizar Detalhes do Evento)
        UC_Inscrever(Inscrever-se em Evento)
        UC_CancelarInsc(Cancelar Inscrição)
        UC_VerInsc(Ver Minhas Inscrições)
        UC_GerirConta(Gerenciar Conta e Perfil)
    end

    subgraph Organizador_UC [Ações de Organizador]
        UC_CriarEvento(Criar Evento)
        UC_GerirEventos(Editar/Deletar Evento)
        UC_VerInscritos(Visualizar Inscritos)
        UC_MarcarPresenca(Marcar Presença)
        UC_GerirRelatorios(Gerar/Gerenciar Relatórios)
    end

    subgraph Admin_UC [Ações de Administrador]
        UC_AprovarEvento(Aprovar Eventos)
        UC_PublicarEvento(Publicar Eventos)
        UC_RelatorioAdmin(Visualizar Relatório Global)
        UC_GerirUsuarios(Gerenciar Usuários)
    end

    %% Vertical Stacking of Subgraphs (via invisible links)
    UC_VerEventos ~~~ UC_VerDetalhes
    UC_VerDetalhes ~~~ UC_CriarEvento
    UC_CriarEvento ~~~ UC_AprovarEvento

    %% Relations (Left to Right)
    Anon --> UC_VerEventos
    Anon --> UC_Cadastrar

    Part --> UC_VerDetalhes
    Part --> UC_Inscrever
    Part --> UC_CancelarInsc
    Part --> UC_VerInsc
    Part --> UC_GerirConta

    Org --> UC_CriarEvento
    Org --> UC_GerirEventos
    Org --> UC_VerInscritos
    Org --> UC_MarcarPresenca
    Org --> UC_GerirRelatorios
    Org --> UC_GerirConta

    Admin --> UC_AprovarEvento
    Admin --> UC_PublicarEvento
    Admin --> UC_RelatorioAdmin
    Admin --> UC_GerirUsuarios
    Admin --> UC_GerirConta
```
