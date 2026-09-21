Repositório da Prática Extensionista IV — UNOESC

# Conexão & Tradição
### Aplicativo mobile para o resgate do carneamento comunitário no Sul do Brasil

**Autores:** Ana Paula Hilgert Boff, Fábio Czechwoski Costa, Guilherme, Jonas Cervelin Minati

**Curso:** Sistemas de Informação — UNOESC
**Componente curricular:** Prática Extensionista IV
**Ano:** 2026

---

<p align="justify">
<strong>Introdução</strong>: No interior do Paraná, de Santa Catarina e do Rio Grande do Sul, o carneamento comunitário de gado e porco sempre foi uma prática de união entre vizinhos: as famílias se reuniam para ajudar no abate e dividiam a carne entre si. Com o êxodo rural e a urbanização, essa tradição vem se perdendo e o contato entre quem produz e quem consome passou a depender de intermediários ou da indicação boca a boca. Isso encarece a carne para o consumidor, reduz a renda do pequeno produtor rural e afasta a população urbana da cultura do campo. <strong>Objetivo</strong>: Desenvolver e publicar o aplicativo mobile <em>Conexão & Tradição</em>, que conecta diretamente produtores rurais à comunidade. O produtor anuncia seus eventos de carneamento (data, local, animal, cortes e preço por kg) e a população encontra eventos na sua região, reserva cortes, conversa com o produtor e participa da experiência. <strong>Metodologia</strong>: Trata-se de uma pesquisa aplicada, de natureza extensionista, com abordagem qualitativa. O levantamento de requisitos foi feito a partir do contexto de produtores rurais do oeste catarinense. O desenvolvimento seguiu um processo iterativo e incremental, com o app Android nativo (Kotlin, arquitetura MVVM e abordagem <em>offline-first</em>) integrado ao Firebase (Authentication, Cloud Firestore e Cloud Messaging), e com o código-fonte versionado no GitHub. Nesta etapa são documentadas a arquitetura da aplicação, a arquitetura de implantação, o fluxo DevOps e a infraestrutura de publicação da solução. <strong>Resultados esperados</strong>: Um canal digital direto entre produtor e comunidade, com carne de procedência conhecida e preço mais justo para quem compra, renda complementar sem intermediários para o pequeno produtor e fortalecimento da tradição cultural e da convivência entre o meio urbano e o rural. <strong>Conclusão</strong>: A solução mostra como a tecnologia pode apoiar uma prática cultural e econômica tradicional. O app foi pensado para o público rural, com interface simples, funcionamento com sinal fraco e suporte a aparelhos Android mais simples.
</p>

<strong>Palavras-chave</strong>: Extensão universitária. Aplicativo mobile. Agricultura familiar. Carneamento comunitário. Firebase.

---

## Problema social atendido

| Público | Problema | Como o app ajuda |
|---|---|---|
| Pequeno produtor rural | Depende de intermediários ou do boca a boca para vender, com margem baixa | Anuncia eventos de carneamento e vende direto ao consumidor |
| População em geral | Carne cara e de procedência desconhecida | Encontra eventos próximos, reserva cortes e conhece o produtor |
| Comunidade / cultura local | A tradição do carneamento comunitário está se perdendo | Resgata a prática e aproxima o meio urbano do rural |

## Funcionalidades (requisitos funcionais)

| Código | Funcionalidade |
|---|---|
| RF01 | Cadastro e login (e-mail/senha e Google) |
| RF02 | Perfil do usuário com reputação (estrelas) e histórico |
| RF03 | Listagem dos próximos eventos de carneamento |
| RF04 | Busca e filtro por cidade e por corte/produto |
| RF05 | Cadastro de evento pelo produtor (animal, cortes, preço/kg) |
| RF06 | Detalhes do evento com tabela de preços |
| RF07 | Agendamento/cancelamento de participação com reserva de cortes |
| RF08 | Chat em tempo real entre comprador e produtor |
| RF09 | Localização do evento (liberada só após confirmar presença) |
| RF10 | Finalização do evento, fotos e avaliação nos dois sentidos |
| RF11 | Notificações de mensagens e lembretes |

## Tecnologias

| Camada | Tecnologia |
|---|---|
| Aplicativo | Android nativo, Kotlin, Android Studio, Gradle |
| Arquitetura do app | MVVM (View → ViewModel → Repository), Navigation Component, LiveData/Flow |
| Persistência local (offline-first) | Room (SQLite) |
| Backend (BaaS) | Firebase Authentication, Cloud Firestore, Firebase Cloud Messaging |
| Serviços externos | Google Sign-In, Google Maps (geolocalização) |
| Versionamento | Git + GitHub |

## Estrutura do repositório

```
PEIV-ConexaoTradicao/
├── README.md          → este documento
├── doc/               → documentação e diagramas da Prática Extensionista IV
│   ├── README.md      → índice da documentação
│   └── diagramas/     → diagramas (pacotes, implantação, DevOps)
└── app/               → aplicação (link para o código-fonte)
    └── README.md
```

## Documentação da arquitetura

| Item | Arquivo |
|---|---|
| Diagrama UML de pacotes (arquitetura da aplicação) | [doc/diagramas/diagrama-pacotes.png](doc/diagramas/diagrama-pacotes.png) |
| Diagrama de arquitetura de implantação | [doc/diagramas/diagrama-implantacao.png](doc/diagramas/diagrama-implantacao.png) |
| Diagrama de arquitetura DevOps | [doc/diagramas/diagrama-devops.png](doc/diagramas/diagrama-devops.png) |
| Infraestrutura de deploy/publicação e justificativa | [doc/README.md — seção 4](doc/README.md#4-infraestrutura-de-deploypublicação) |

## Código-fonte da aplicação

O código-fonte do aplicativo Android está em:
**https://github.com/fabioccf2/ConexaoTradicao-App**

## Como executar o projeto

1. Clonar o repositório do app: `git clone https://github.com/fabioccf2/ConexaoTradicao-App.git`
2. Abrir a pasta no **Android Studio** e aguardar a sincronização do Gradle.
3. Colocar o arquivo `google-services.json` do projeto Firebase na pasta `app/`.
4. Executar em um emulador ou aparelho com **Android 8.0 (API 26) ou superior**.

## Integrantes

| Nome |
|---|
| Ana Paula Hilgert Boff |
| Fábio Czechwoski Costa |
| Guilherme Gonçalves |
| Jonas Cervelin Minati |
