# TaskSync

Um gerenciador de tarefas focado em produtividade. O projeto está sendo construído utilizando **Bootstrap 5**, sem uso de JavaScript do Bootstrap ou qualquer tipo de script JS.

## Estrutura e Páginas Atuais

1. **Página Inicial (`index.html`)**: Landing Page focada nas atividades imediatas do usuário. Contém a Hero Section, Cards de Projetos com layout de Grid responsivo e uma Tabela de Atividades moderna.
2. **Gestão de Tarefas (`pages/tarefas.html`)**: Página dedicada para criação de novas tarefas e alocação de membros, estruturada com formulários, validações visuais e layouts responsivos.
3. **Painel Analítico (`pages/dashboard.html`)**: Tela administrativa introduzida na Etapa 9, incorporando uma Sidebar. Apresenta alertas contextualizados, métricas corporativas através de barras de progresso cruzadas e tabelas de status de equipe.

## Classes Bootstrap Utilizadas 

O objetivo principal foi respeitar ao máximo o framework, utilizando suas classes utilitárias e semânticas em vez de criar CSS customizado:

- **Layout e Utilitários Flexbox:** `.container`, `.container-fluid`, `.row`, `.col-12`, `.col-md-6`, `.col-md-8`, `.col-md-4`, `.col-lg-2`, `.col-lg-3`, `.col-lg-5`, `.col-lg-6`, `.col-lg-7`, `.col-lg-9`, `.col-xl-10`, `.g-3`, `.g-4`, `.order-1`, `.order-2`, `.order-lg-1`, `.order-lg-2`, `.flex-column`, `.flex-sm-row`, `.d-flex`, `.align-items-center`, `.justify-content-center`, `.justify-content-between`, `.justify-content-lg-start`, `.justify-content-lg-end`, `.ms-auto`, `.me-2`, `.me-3`, `.gap-2`, `.gap-3`, `.mt-2`, `.mt-3`, `.mt-4`, `.mt-lg-0`, `.mt-auto`, `.mb-0`, `.mb-1`, `.mb-2`, `.mb-3`, `.mb-4`, `.mb-5`, `.my-lg-5`, `.pt-4`, `.pb-5`, `.py-2`, `.py-3`, `.py-4`, `.py-5`, `.px-0`, `.px-3`, `.px-4`, `.h-100`, `.min-vh-100`. 
- **Componentes Base da Navbar:** `.navbar`, `.navbar-expand-lg`, `.navbar-brand`, `.navbar-nav`, `.nav-item`, `.nav-link`, `.collapse`, `.navbar-collapse`, `.bg-transparent`, `.border-bottom`, `.border-end`, `.active`.
- **Componentes de Conteúdo (Cards, Badges, Modais e Tabelas):** `.card`, `.card-body`, `.card-title`, `.card-text`, `.border-0`, `.badge`, `.rounded-pill`, `.text-bg-primary`, `.text-bg-success`, `.text-bg-warning`, `.text-bg-info`, `.text-bg-secondary`, `.text-bg-danger`, `.list-group`, `.list-group-item`, `.list-group-flush`, `.progress`, `.progress-bar`, `.alert`, `.alert-warning`, `.alert-info`, `.alert-dismissible`, `.table`, `.table-responsive`, `.table-striped`, `.table-hover`, `.table-dark`, `.table-light`, `.align-middle`.
- **Formulários:** `.form-label`, `.form-control`, `.form-select`, `.input-group`, `.input-group-text`, `.form-check`, `.form-check-inline`, `.form-check-input`, `.form-check-label`, `.is-valid`, `.is-invalid`, `.valid-feedback`, `.invalid-feedback`.
- **Botões e Ícones:** `.btn`, `.btn-primary`, `.btn-secondary`, `.btn-danger`, `.btn-dark`, `.btn-outline-primary`, `.btn-outline-dark`, `.btn-lg`, ícones `.bi` (Bootstrap Icons).
- **Tipografia, Cores e Estilo:** `.display-4`, `.display-6`, `.lead`, `.fw-bold`, `.fw-semibold`, `.fw-medium`, `.fs-4`, `.fs-5`, `.fs-2`, `.text-primary`, `.text-secondary`, `.text-warning`, `.text-info`, `.text-danger`, `.text-muted`, `.text-body`, `.text-body-secondary`, `.text-center`, `.text-lg-start`, `.bg-light`, `.bg-body`, `.bg-primary`, `.bg-success`, `.bg-warning`, `.bg-info`, `.rounded-3`, `.rounded-4`, `.shadow-sm`, `.img-fluid`, `.w-100`, `.opacity-75`.
- **Responsividade de Visibilidade:** `.d-none`, `.d-lg-none`, `.d-lg-flex`, `.d-block` para exibir ou ocultar elementos conforme as dimensões da tela.

## CSS Customizado: Onde e Por Quê?

- **Sistema de Design Integrado (Etapa 8):** Optou-se por rejeitar o uso isolado de classes forçadas. Toda a construção da identidade visual foi resolvida alterando as raízes do framework (SASS pre-compile/CSS vars). As variáveis `.bs-primary`, `.bs-secondary` e a tipografia foram sobrescritas globalmente direto na raiz `:root`. Componentes como `text-bg-primary` reagem intrinsecamente a esta matriz sem depender de arquivos pesados de estilo.
- **Destaques da Sidebar:** Nativamente, Bootstrap tende a não aplicar cores personalizadas estáticas em propriedades como os _pills_ de navegação quando isolados. Adicionou-se uma sub-regra `.nav-pills .nav-link.active` ao CSS garantindo a injeção incondicional da paleta primária.
- **Menu Mobile Sem JS (Checkbox Hack):** A navegação interativa (hamburguer menu) opera com queries contextuais (seletor adjacente genérico `~`), permitindo expansões fluidas na classe `.mobile-menu-content`.
- **Modais 100% Nativos via HTML:** O comportamento dos componentes de confirmação foi isolado em máscaras HTML invisíveis atreladas a `<label>`. É possível fechar o modal ao se clicar no plano de fundo, recriando o script nativo através do rastreamento da matriz `z-index`.
- **Compatibilidade em SVGs:** Utilizou-se `filter: drop-shadow()` em `img.drop-shadow-lg` para rastrear perfis poligonais da arte principal, superando a classe estática `.shadow`.

## Principais Dificuldades Resolvidas

1. **Menu Hamburguer Responsivo:** A navbar nativa do Bootstrap é completamente dependente de JavaScript para alternar a classe `.collapse`. A restrição motivou a adoção completa da técnica the checkboxes com estados `:checked`.
2. **Modais Sem JS:** Disparar caixas modais e permitir navegação em profundidade sem travar as interações em dispositivos móveis requereu arquitetura criativa usando inputs, posicionamento estático e seletores combinados `.modal-state:checked + .custom-modal`.
3. **Dashboard e Layout Sidebar:** Conciliar uma Dashboard lateral e uma Top Navbar, tudo sem `position: absolute`, esbarrou na quebra constante de fluxo. Isto foi sanado amarrando o menu a um container flexível do sistema de Grid `.col-lg-3 d-none d-lg-flex`, controlando o ciclo de exibição móvel-desktop de maneira segura.
