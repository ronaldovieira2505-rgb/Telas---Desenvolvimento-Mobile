# Telas---Desenvolvimento-Mobile

Atividade: Protótipo Mobile e Organização dos Estilos com BEM (Desenvolvimento Mobile).

## Integrantes

- Ronaldo da Costa Vieira Filho — 10754098
- Gabriel Santoro Silveira — 10437314
- Gabriel Marinho Rosa — 10443598

## Sobre o app

Nosso app é um marketplace para contratar trabalhadores por turno. Pequenas empresas (contratantes) publicam vagas pontuais, como ajudante de obra, repositor de loja, apoio de evento e carga e descarga, e trabalhadores autônomos se candidatam. Cada vaga tem data, horário, local e valor definidos.

O tema veio do projeto do grupo em outra disciplina (Projetos de Engenharia da Computação I).

O app tem três tipos de usuário:

- **Trabalhador:** procura vagas, se candidata e acompanha suas candidaturas.
- **Contratante:** publica vagas, que passam por aprovação antes de aparecer no app.
- **Administrador:** aprova vagas, modera avaliações e cuida das categorias, dos destaques e dos usuários.

## Telas

Usamos as 14 telas do exemplo do professor como base e adaptamos ao nosso tema: os posts viraram vagas, a newsletter virou alertas de vagas e os comentários viraram avaliações dos turnos.

| Nº | Tela | O que tem | Arquivo |
|---|---|---|---|
| 01 | Início | Busca, categorias, vagas em destaque, contratantes verificados, convite para os alertas | (wireframes/tela_01.png) |
| 02 | Vagas por categoria | Filtros, cards de vagas, botão "Carregar mais" | (wireframes/tela_02.png) |
| 03 | Destaques | Cards das vagas em destaque | (wireframes/tela_03.png) |
| 04 | Alertas de vagas | E-mail, categoria, cidade, aceite, botão "Assinar alertas" | (wireframes/tela_04.png) |
| 05 | Admin: Categorias | Indicadores, busca, lista de categorias com Editar e Excluir | (wireframes/tela_05.png) |
| 06 | Contratante: Nova vaga | Formulário da vaga, "Enviar para revisão" e "Salvar rascunho" | (wireframes/tela_06.png) |
| 07 | Admin: Destaques | Lista de vagas com Destacar e Remover | (wireframes/tela_07.png) |
| 08 | Admin: Usuários | Lista de contas com status e Bloquear/Desbloquear | (wireframes/tela_08.png) |
| 09 | Admin: Aprovação | Vagas enviadas para revisão com Aprovar e Reprovar | (wireframes/tela_09.png) |
| 10 | Admin: Avaliações | Avaliações dos turnos com Aprovar e Reprovar | (wireframes/tela_10.png) |
| 11 | Resultados da busca | Ordenação e cards compactos das vagas encontradas | (wireframes/tela_11.png) |
| 12 | Entrar | E-mail, senha, "Entrar", "Entrar com Google", link para criar conta | (wireframes/tela_12.png) |
| 13 | Criar conta | Nome, e-mail, tipo de conta, senha, confirmação, aceite dos termos | (wireframes/tela_13.png) |
| 14 | Perfil | Dados pessoais, minhas candidaturas com status, minhas avaliações | (wireframes/tela_14.png) |

## Fluxos

- **Público:** Início (01) → Categoria (02), Destaques (03), Busca (11) ou Alertas (04)
- **Conta:** Entrar (12) → Criar conta (13) → Perfil (14)
- **Admin:** Categorias (05), Destaques (07), Usuários (08), Aprovação (09) e Avaliações (10), ligadas pelas abas do painel

O fluxo principal é o de uma vaga: o contratante cria a vaga (06), o administrador aprova (09), a vaga aparece nas telas 01, 02, 03 e 11, o trabalhador se candidata e acompanha o status no perfil (14).

Outras ligações entre as telas:

- As vagas marcadas na tela 07 aparecem nas telas 01 e 03.
- As avaliações aprovadas na tela 10 aparecem no perfil (14).

## Adaptações para o mobile

- O menu de cima virou uma barra embaixo da tela (Início, Buscar, Alertas, Perfil).
- As categorias e os filtros viraram botões com rolagem para o lado.
- Os cards que ficavam em 3 colunas agora ficam em 1 coluna.
- O menu lateral do painel virou abas no topo.
- As tabelas do admin viraram listas, com cada linha em um bloco.
- Nos formulários, os campos e os botões ocupam a largura toda.

## Componentes

| Componente | Onde aparece | Variações |
|---|---|---|
| Cabeçalho | Todas as telas | público (claro), painel (escuro) |
| Menu | Todas as telas | barra inferior, abas do painel, item ativo |
| Botão | Todas as telas | primário, secundário, perigo, desativado |
| Card | 01, 02, 03, 11 | padrão, compacto, destaque |
| Filtro | 01, 02, 06, 11 | padrão, ativo |
| Formulário | 04, 06, 12, 13, 14 | login, cadastro, alertas, vaga, perfil |
| Status | 07, 08, 09, 10, 14 | pendente, aprovado, recusado |
| Lista | 05, 07, 08, 09, 10, 14 | simples, com status |
| Indicador | 05, 07, 08, 09, 10 | padrão, alerta |

### Variações do Card

![Variações do Card](wireframes/variacoes_card.png)

### Variações do Botão

![Variações do Botão](wireframes/variacoes_botao.png)

## CSS com BEM

Seguimos três regras:

- **Bloco:** o componente (`.card`).
- **Elemento:** uma parte do bloco (`.card__title`).
- **Modificador:** uma variação, sempre usada junto com a classe do bloco (`class="card card--featured"`).

| Componente | Bloco | Elementos | Modificadores |
|---|---|---|---|
| Cabeçalho | `.header` | `__logo`, `__back`, `__title`, `__search`, `__action` | `--panel` |
| Menu | `.navigation` | `__item` | `--bottom`, `--tabs`, `__item--active` |
| Botão | `.button` | — | `--primary`, `--secondary`, `--danger`, `--disabled` |
| Card | `.card` | `__image`, `__title`, `__info`, `__price`, `__actions` | `--compact`, `--featured` |
| Filtro | `.chip` | — | `--active` |
| Formulário | `.form` | `__title`, `__field`, `__label`, `__input`, `__checkbox`, `__actions` | `--login`, `--signup`, `--alerts`, `--job`, `--profile` |
| Status | `.badge` | — | `--pending`, `--approved`, `--rejected` |
| Lista | `.list` | `__item`, `__title`, `__info`, `__actions` | `--status` |
| Indicador | `.stat` | `__value`, `__label` | `--alert` |

Os status usam sempre o mesmo modificador para o mesmo sentido:

- `--pending`: em análise, em verificação
- `--approved`: ativo, aprovada, publicada, confirmada, em destaque
- `--rejected`: bloqueado, reprovada, recusada

## Organização dos arquivos

```
projeto-mobile/
├── README.md
├── wireframes/
│   ├── tela_01.png ... tela_14.png
│   ├── variacoes_card.png
│   └── variacoes_botao.png
└── css/
    ├── variables.css
    ├── header.css
    ├── navigation.css
    ├── button.css
    ├── card.css
    ├── chip.css
    ├── form.css
    ├── badge.css
    ├── list.css
    └── stat.css
```

- `wireframes/`: as 14 telas e as imagens das variações.
- `css/`: um arquivo para cada componente. O `variables.css` guarda as cores e os espaçamentos usados nos outros arquivos.

Cada componente da tabela vai virar um componente React na próxima etapa, e os modificadores vão virar as opções desses componentes.