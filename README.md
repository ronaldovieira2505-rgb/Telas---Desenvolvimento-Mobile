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

Cada tela está em duas formas na pasta `Wireframes/`: a imagem em baixa fidelidade (`.png`) e a tela navegável (`.html`), em que os botões levam às outras telas do fluxo.

| Nº | Tela | O que tem | Imagem | Navegável |
|---|---|---|---|---|
| 01 | Início | Busca, categorias, vagas em destaque, contratantes verificados, convite para os alertas | [png](Wireframes/tela_01.png) | [html](Wireframes/tela_01.html) |
| 02 | Vagas por categoria | Filtros, cards de vagas, botão "Carregar mais" | [png](Wireframes/tela_02.png) | [html](Wireframes/tela_02.html) |
| 03 | Destaques | Cards das vagas em destaque | [png](Wireframes/tela_03.png) | [html](Wireframes/tela_03.html) |
| 04 | Alertas de vagas | E-mail, categoria, cidade, aceite, botão "Assinar alertas" | [png](Wireframes/tela_04.png) | [html](Wireframes/tela_04.html) |
| 05 | Admin: Categorias | Indicadores, busca, lista de categorias com Editar e Excluir | [png](Wireframes/tela_05.png) | [html](Wireframes/tela_05.html) |
| 06 | Contratante: Nova vaga | Formulário da vaga, "Enviar para revisão" e "Salvar rascunho" | [png](Wireframes/tela_06.png) | [html](Wireframes/tela_06.html) |
| 07 | Admin: Destaques | Lista de vagas com Destacar e Remover | [png](Wireframes/tela_07.png) | [html](Wireframes/tela_07.html) |
| 08 | Admin: Usuários | Lista de contas com status e Bloquear/Desbloquear | [png](Wireframes/tela_08.png) | [html](Wireframes/tela_08.html) |
| 09 | Admin: Aprovação | Vagas enviadas para revisão com Aprovar e Reprovar | [png](Wireframes/tela_09.png) | [html](Wireframes/tela_09.html) |
| 10 | Admin: Avaliações | Avaliações dos turnos com Aprovar e Reprovar | [png](Wireframes/tela_10.png) | [html](Wireframes/tela_10.html) |
| 11 | Resultados da busca | Ordenação e cards das vagas encontradas | [png](Wireframes/tela_11.png) | [html](Wireframes/tela_11.html) |
| 12 | Entrar | E-mail, senha, "Entrar", "Entrar com Google", link para criar conta | [png](Wireframes/tela_12.png) | [html](Wireframes/tela_12.html) |
| 13 | Criar conta | Nome, e-mail, tipo de conta, senha, confirmação, aceite dos termos | [png](Wireframes/tela_13.png) | [html](Wireframes/tela_13.html) |
| 14 | Perfil | Dados pessoais, minhas candidaturas com status, minhas avaliações | [png](Wireframes/tela_14.png) | [html](Wireframes/tela_14.html) |

## Fluxos

- **Público:** Início (01) → Categoria (02), Destaques (03), Busca (11) ou Alertas (04)
- **Conta:** Entrar (12) → Criar conta (13) → Perfil (14)
- **Painel administrativo:** Categorias (05), Destaques (07), Usuários (08), Aprovação (09) e Avaliações (10), ligadas entre si pelas abas do painel
- **Contratante:** Início (01) → Nova vaga (06) → Aprovação (09)

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
- Nas telas de foco (04, 12 e 13) só aparece o conteúdo do formulário, sem as seções extras.

## Componentes

| Componente | Bloco | Onde aparece | Variações |
|---|---|---|---|
| Cabeçalho | `.header` | Todas as telas | público, administrativo |
| Navegação | `.nav` | Todas menos a 06 | barra inferior do app, abas do painel, item ativo |
| Filtro | `.chip` | 01, 02, 06, 11 | padrão, ativo, tag |
| Botão | `.button` | Todas as telas | primário, secundário, perigo, desativado, pequeno, largura total |
| Card | `.card` | 01, 02, 03, 11, 14 | padrão, destaque, horizontal, compacto |
| Formulário | `.form` | 04, 05, 06, 07, 08, 12, 13, 14 | login, cadastro, alertas, painel, em linha |
| Lista | `.list` | 05, 07, 08, 09, 10, 14 | padrão, compacta, revisão, comentários |
| Indicador | `.stat` | 05, 07, 08, 09, 10 | padrão, atenção |
| Status | `.badge` | 07, 08, 09, 10, 14 | pendente, aprovado, recusado |
| Mensagem | `.alert` | 01, 07 | chamada |
| Tela | `.screen` | Todas as telas | padrão, administrativa, foco |
| Seção | `.section` | 01, 02, 03, 05, 07, 08, 09, 10, 11, 12, 13, 14 | padrão, grade |

## CSS com BEM

Seguimos três regras:

- **Bloco:** o componente (`.card`).
- **Elemento:** uma parte do bloco (`.card__title`).
- **Modificador:** uma variação, sempre usada junto com a classe do bloco (`class="card card--featured"`).

| Bloco | Elementos | Modificadores | Arquivo |
|---|---|---|---|
| `.screen` | `__title`, `__subtitle`, `__content`, `__footer-note` | `--admin`, `--focus` | `base.css` |
| `.section` | `__header`, `__title`, `__link`, `__body` | `--grid` | `base.css` |
| `.header` | `__logo`, `__back`, `__title`, `__search`, `__action` | `--admin` | `navigation.css` |
| `.nav` | `__item` | `--tabs`, `--admin`, `__item--active` | `navigation.css` |
| `.chip` | — | `--active`, `--tag` | `navigation.css` |
| `.button` | — | `--primary`, `--secondary`, `--danger`, `--disabled`, `--small`, `--block` | `button.css` |
| `.card` | `__image`, `__body`, `__title`, `__subtitle`, `__meta`, `__price`, `__actions` | `--featured`, `--horizontal`, `--compact` | `card.css` |
| `.form` | `__group`, `__label`, `__input`, `__select`, `__textarea`, `__check`, `__hint`, `__row`, `__upload`, `__actions`, `__footer` | `--login`, `--signup`, `--alerts`, `--admin`, `--inline` | `form.css` |
| `.list` | `__item`, `__title`, `__info`, `__meta`, `__actions` | `--compact`, `--review`, `--comments` | `list.css` |
| `.stat` | `__value`, `__label` | `--attention` | `stat.css` |
| `.badge` | — | `--pending`, `--approved`, `--rejected` | `badge.css` |
| `.alert` | `__title`, `__text`, `__action` | `--cta` | `alert.css` |

Além desses, dois blocos auxiliares só organizam o espaçamento de um grupo de itens: `.chip-list`, que alinha os filtros em uma linha com rolagem, e `.button-group`, que agrupa botões (com `--stacked` para empilhá-los).

Os status usam sempre o mesmo modificador para o mesmo sentido:

- `--pending`: em análise, em verificação
- `--approved`: ativo, aprovada, publicada, confirmada, em destaque
- `--rejected`: bloqueado, reprovada, recusada

## Organização dos arquivos

```
Telas---Desenvolvimento-Mobile/
├── README.md
├── CSS/
│   ├── main.css        importa todos os outros
│   ├── variables.css   cores, espaçamentos e tamanhos de texto
│   ├── base.css        reset e os blocos de estrutura (screen e section)
│   ├── navigation.css  header, nav e chip
│   ├── button.css
│   ├── card.css
│   ├── form.css
│   ├── list.css
│   ├── stat.css
│   ├── badge.css
│   └── alert.css
└── Wireframes/
    ├── tela_01.html … tela_14.html
    └── tela_01.png … tela_14.png
```

Cada arquivo do `CSS/` responde por um bloco BEM, em vez de concentrar tudo em um arquivo só. As telas carregam apenas o `main.css`, que importa os demais na ordem certa: primeiro as variáveis e o base, depois os componentes.

Cada componente da tabela vai virar um componente React na próxima etapa, e os modificadores vão virar as opções desses componentes.