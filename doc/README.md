# Documentação — Prática Extensionista IV

Documentação de arquitetura do aplicativo **Conexão & Tradição**.

## 1. Diagrama UML de pacotes (arquitetura da aplicação)

![Diagrama UML de pacotes](diagramas/diagrama-pacotes.png)

<p align="justify">
O diagrama representa a organização do código-fonte do aplicativo Android em pacotes (namespaces Kotlin), com as dependências entre eles. O aplicativo segue o padrão arquitetural <strong>MVVM (Model–View–ViewModel)</strong> com a camada <strong>Repository</strong>, recomendado pelo Google para apps Android. Ele também adota a abordagem <strong>offline-first</strong>: os dados ficam salvos no aparelho (Room) e são sincronizados com a nuvem (Firebase) quando há conexão, o que atende ao público rural com sinal de internet instável.
</p>

### Pacotes da aplicação

| Pacote | Camada | Responsabilidade |
|---|---|---|
| `ui.login`, `ui.register` | Apresentação | Telas de login e cadastro (e-mail/senha e Google) — RF01 |
| `ui.home` | Apresentação | Listagem e busca dos próximos eventos de carneamento — RF03, RF04 |
| `ui.createevent` | Apresentação | Cadastro de evento pelo produtor (animal, cortes, preço/kg, localização) — RF05, RF09 |
| `ui.eventdetail` | Apresentação | Detalhes do evento, agendamento, finalização e avaliação — RF06, RF07, RF10 |
| `ui.chat` | Apresentação | Chat em tempo real entre comprador e produtor — RF08 |
| `ui.profile` | Apresentação | Perfil, reputação e histórico de participações — RF02, RF10 |
| `data.repository` | Dados | Regras de acesso a dados; decide entre o banco local e o Firebase e faz a sincronização |
| `data.local` | Dados | Banco de dados local (Room/SQLite): `AppDatabase` e DAOs |
| `data.model` | Dados | Entidades do domínio: usuário, evento, corte, participação, avaliação, mensagem |
| `data.remote` | Dados | Serviço de recebimento de notificações push (Firebase Cloud Messaging) — RF11 |
| `util` | Utilitário | Classes de apoio usadas pelas duas camadas (estado de carregamento, imagens, notificações) |
| Classes da raiz | Entrada | `ConexaoTradicaoApp` (inicializa o app), `AuthActivity` (fluxo de login) e `MainActivity` (fluxo principal) |

### Bibliotecas externas

| Pacote | Uso no projeto |
|---|---|
| `androidx.lifecycle` | ViewModel e LiveData (padrão MVVM) |
| `androidx.navigation` | Navegação entre as telas |
| `androidx.room` | Banco de dados local (offline-first) |
| `com.google.firebase.auth` | Autenticação de usuários |
| `com.google.firebase.firestore` | Banco de dados na nuvem, em tempo real |
| `com.google.firebase.messaging` | Notificações push |
| `com.google.android.gms.auth` | Login com conta Google |
| `com.google.android.gms.location` | Localização do evento (GPS) |

### Regras de dependência

<p align="justify">
As dependências seguem um único sentido, de cima para baixo: <strong>ui → data → bibliotecas externas</strong>. As telas (<code>ui</code>) acessam os dados por meio do <code>data.repository</code>. As exceções pontuais são a consulta ao usuário logado (<code>firebase.auth</code>) e a leitura do nome do produtor no cadastro de evento (<code>createevent → data.local</code>), ambas representadas no diagrama. A camada de dados, por sua vez, não depende de nenhuma classe da interface. Essa separação diminui o acoplamento, facilita os testes e permite trocar a fonte de dados (por exemplo, outro backend) sem alterar as telas. As dependências foram levantadas a partir dos <code>import</code> do código-fonte real, disponível em <a href="https://github.com/fabioccf2/ConexaoTradicao-App">github.com/fabioccf2/ConexaoTradicao-App</a>.
</p>

**Notação UML utilizada:** pacote (retângulo com aba), pacotes aninhados, classe, dependência (seta tracejada com ponta aberta) com os estereótipos `«use»` (uso de pacote interno) e `«import»` (importação de biblioteca externa), além dos estereótipos `«application»`, `«layer»` e `«library»`.

## 2. Diagrama de arquitetura de implantação

*Em elaboração: será publicado em `diagramas/`.*

## 3. Diagrama de arquitetura DevOps

*Em elaboração: será publicado em `diagramas/`.*

## 4. Infraestrutura de deploy/publicação

*Em elaboração: escolha, descrição e justificativa da infraestrutura de publicação da solução.*
