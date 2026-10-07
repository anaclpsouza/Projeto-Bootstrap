# TaskSync

Um gerenciador de tarefas focado em produtividade. O projeto está sendo construído utilizando **Bootstrap 5**, sem uso de JavaScript do Bootstrap ou qualquer tipo de script JS.

## Estrutura e Páginas Atuais

1. **Página Inicial (`index.html`)**: Contém a Hero Section, Cards de Projetos com layout de Grid responsivo, e uma Tabela de Atividades moderna.
2. **Gestão de Tarefas (`pages/tarefas.html`)**: Página dedicada para criação de novas tarefas e alocação de membros, estruturada com formulários complexos e responsivos.

## Classes Bootstrap Utilizadas 

Meu objetivo principal foi respeitar ao máximo o framework, utilizando suas classes utilitárias e semânticas em vez de criar CSS customizado:

- **Layout e Utilitários Flexbox:** `.container`, `.row`, `.col-12`, `.col-md-6`, `.col-md-8`, `.col-md-4`, `.col-lg-3`, `.col-lg-6`, `.g-3`, `.g-4`, `.order-1`, `.order-2`, `.order-lg-1`, `.order-lg-2`, `.flex-column`, `.flex-sm-row`, `.d-flex`, `.align-items-center`, `.justify-content-center`, `.justify-content-lg-start`, `.justify-content-lg-end`, `.ms-auto`, `.me-2`, `.gap-2`, `.gap-3`, `.mt-3`, `.mt-4`, `.mt-lg-0`, `.mt-auto`, `.mb-2`, `.mb-3`, `.mb-4`, `.mb-5`, `.my-lg-5`, `.py-3`, `.py-5`, `.px-4`, `.h-100`. 
- **Componentes Base da Navbar:** `.navbar`, `.navbar-expand-lg`, `.navbar-brand`, `.navbar-nav`, `.nav-item`, `.nav-link`, `.collapse`, `.navbar-collapse`, `.bg-transparent`, `.border-bottom`.
- **Componentes de Conteúdo (Cards, Badges e Tabelas):** `.card`, `.card-body`, `.card-title`, `.card-text`, `.border-0`, `.badge`, `.text-bg-primary`, `.text-bg-success`, `.text-bg-warning`, `.text-bg-info`, `.table`, `.table-responsive`, `.table-striped`, `.table-hover`, `.table-dark`, `.align-middle`.
- **Formulários:** `.form-label`, `.form-control`, `.form-select`, `.input-group`, `.input-group-text`, `.form-check`, `.form-check-inline`, `.form-check-input`, `.form-check-label`, `.is-valid`, `.is-invalid`, `.valid-feedback`, `.invalid-feedback`.
- **Botões e Ícones:** `.btn`, `.btn-primary`, `.btn-secondary`, `.btn-danger`, `.btn-dark`, `.btn-outline-primary`, `.btn-outline-dark`, `.btn-lg`, ícones `.bi` (Bootstrap Icons).
- **Tipografia, Cores e Estilo:** `.display-4`, `.display-6`, `.lead`, `.fw-bold`, `.fw-medium`, `.fs-4`, `.fs-2`, `.text-primary`, `.text-body`, `.text-body-secondary`, `.text-center`, `.text-lg-start`, `.bg-light`, `.bg-body`, `.rounded-3`, `.shadow-sm`, `.img-fluid`, `.w-100`.
- **Responsividade de Visibilidade:** `.d-lg-none`, `.d-lg-flex`, `.d-block` para controlar a exibição em diferentes breakpoints.

## CSS Customizado: Onde e Por Quê?

- **Paleta Própria e Tipografia:** Em vez de criar classes soltas como `.btn-custom`, optei por injetar a paleta na raiz do Bootstrap, sobrescrevendo as variáveis `--bs-primary`, `--bs-secondary` e `--bs-font-sans-serif` diretamente no `:root`. Dessa forma, todos os botões e textos são coloridos organicamente pelas classes nativas do framework (como `.text-primary`).
- **Menu Mobile sem JS:** Implementei o CSS *Checkbox Hack*. Foi necessária uma media query (`max-width: 991.98px`) para exibir dinamicamente a div `.mobile-menu-content` usando o seletor condicional `~`.
- **Modais Nativos (Sem JS):** Reutilizei a lógica do *Checkbox Hack*, conectando inputs escondidos aos componentes visuais por meio do seletor adjacente `+`. O fundo escuro (`.custom-modal-backdrop`) foi construído com a tag `<label>`, permitindo que um clique fora do modal desmarque o input e oculte o painel branco na mesma hora, gerenciando os índices de profundidade (`z-index`) para sobrepor a interface principal.
- **Sombra para SVG (drop-shadow):** O Bootstrap nativo usa `box-shadow` em suas classes `.shadow`, o que gera uma caixa quadrada ao redor de imagens sem fundo. Para contornar e sombrear a logo SVG, criei a classe `.drop-shadow-lg` que utiliza a propriedade `filter: drop-shadow()`.

## Principais Dificuldades 

1. **Menu Hamburguer Responsivo:** A navbar nativa do Bootstrap é completamente dependente de seu arquivo JavaScript para alternar a exibição da classe `.collapse`. Descartar o JS exigiu adaptar o código com `<label>`s responsivos conectados a um `input[type="checkbox"]`, que utiliza o estado `:checked` no CSS para engatilhar uma animação `slideDown` de forma autônoma.
2. **Sistema de Modais Estáticos:** Emular o comportamento complexo de um Modal (abrir, focar, fechar no "X" e fechar ao clicar fora) sem Javascript demandou estruturação criativa do DOM. Tive que posicionar o HTML no fim do documento com `position: fixed` e utilizar `<label>` como máscara de fundo para fechar a janela ao detectar cliques fora da área de conteúdo.
