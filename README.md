# TaskSync

Um gerenciador de tarefas focado em produtividade. O projeto está sendo construído utilizando **Bootstrap 5**, sem uso de JavaScript do Bootstrap ou qualquer tipo de script JS.

## Estrutura e Páginas Atuais

1. **Página Inicial (`index.html`)**

## Classes Bootstrap Utilizadas 

O objetivo principal foi respeitar ao máximo o framework, utilizando suas classes utilitárias e semânticas em vez de criar CSS customizado:

- **Layout e Utilitários Flexbox:** `.container`, `.d-flex`, `.align-items-center`, `.justify-content-lg-end`, `.ms-auto`, `.me-2`, `.gap-2`, `.gap-3`, `.mt-3`. 
- **Componentes Base da Navbar:** `.navbar`, `.navbar-expand-lg`, `.navbar-brand`, `.navbar-nav`, `.nav-item`, `.nav-link`, `.collapse`, `.navbar-collapse`, `.bg-transparent`, `.border-bottom`, `.py-3`.
- **Botões e Auxiliares:** `.btn`, `.btn-outline-dark`.
- **Tipografia e Estilo:** `.fw-bold`, `.fw-medium`, `.fs-4`, `.fs-2`, `.text-primary`, `.text-body`, `.rounded-3`, `.shadow-sm`.
- **Responsividade de Visibilidade:** `.d-lg-none`, `.d-lg-flex` para controlar a barra de navegação no formato desktop x mobile.

## CSS Customizado: Onde e Por Quê?

- **Paleta Própria e Tipografia:** Em vez de criar classes soltas como `.btn-custom`, optei por injetar a paleta na raiz do Bootstrap, sobrescrevendo as variáveis `--bs-primary`, `--bs-secondary` e `--bs-font-sans-serif` diretamente no `:root`. Dessa forma, todos os botões e textos são coloridos organicamente pelas classes nativas do framework (como `.text-primary`).
- **Menu Mobile sem JS:** Implementei o CSS *Checkbox Hack*. Foi necessária uma media query (`max-width: 991.98px`) para exibir dinamicamente a div `.mobile-menu-content` usando o seletor condicional `~`.

## Principais Dificuldades 

1. **Menu Hamburguer Responsivo:** A navbar nativa do Bootstrap é completamente dependente de seu arquivo JavaScript para alternar a exibição da classe `.collapse`. Descartar o JS exigiu adaptar o código com `<label>`s responsivos conectados a um `input[type="checkbox"]`, que utiliza o estado `:checked` no CSS para engatilhar uma animação `slideDown` de forma autônoma.
