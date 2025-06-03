---
layout: default
title: Estrutura de Páginas
---

# Estrutura e Semântica do HTML

## Introdução

A estrutura e semântica do HTML são fundamentais para criar páginas web acessíveis. Vamos explorar como as pessoas com deficiência navegam na web e porque estes aspetos são tão importantes.

### Como as pessoas com deficiência se orientam numa página

Imagine entrar numa biblioteca onde todos os livros estão empilhados aleatoriamente, sem estantes organizadas, sem sinalizações de secções, e sem um sistema de catalogação. Seria extremamente difícil encontrar o livro que procura, certo? Esta é uma experiência semelhante à que pessoas com deficiência enfrentam quando visitam páginas web mal estruturadas.

As pessoas com deficiência visual, por exemplo, não podem dar uma "vista de olhos rápida" à página para encontrar o que procuram. Em vez disso, dependem de tecnologias de apoio como leitores de ecrã, que leem o conteúdo sequencialmente. Para estas pessoas, uma boa estrutura é como ter um bibliotecário que pode rapidamente guiá-las para a informação que procuram.

Pessoas com deficiência motora podem usar apenas o teclado para navegar. Uma estrutura clara permite-lhes mover-se eficientemente entre diferentes secções da página sem terem que passar por cada elemento individualmente.

### Porque a estrutura e a semântica são essenciais para a acessibilidade?

A estrutura e a semântica do HTML são como a planta de uma página web. Elas fornecem:

1. **Navegação Eficiente**: Uma estrutura clara permite que os utilizadores encontrem rapidamente a informação que procuram, sem terem que processar todo o conteúdo.

2. **Compreensão do Contexto**: A semântica ajuda a entender a função e importância de cada elemento. Por exemplo, um título principal (`<h1>`) indica imediatamente o tema principal da página.

3. **Consistência**: Uma estrutura previsível ajuda os utilizadores a desenvolverem modelos mentais de como a informação está organizada, facilitando a navegação em diferentes páginas do mesmo site.

### Estratégias de navegação usadas por pessoas com deficiência

As pessoas com deficiência utilizam várias estratégias para navegar em páginas web:

**Navegação por Cabeçalhos**

```html
<!-- Bom exemplo -->
<h1>Produtos Sustentáveis</h1>
<h2>Produtos Populares</h2>
<h3>Garrafas Reutilizáveis</h3>
<h3>Sacos de Compras</h3>
<h2>Novidades</h2>

<!-- Mau exemplo -->
<div style="font-size: 24px">Produtos Sustentáveis</div>
<span class="titulo-grande">Produtos Populares</span>
```

O bom exemplo usa elementos de cabeçalho adequados, permitindo que utilizadores de leitores de ecrã naveguem rapidamente entre secções. O mau exemplo usa elementos sem significado semântico, tornando impossível distinguir títulos de conteúdo normal.

**Navegação por Landmarks**

```html
<!-- Bom exemplo -->
<header>
    <nav>Menu principal</nav>
</header>
<main>
    <article>Conteúdo principal</article>
</main>
<aside>Informação relacionada</aside>
<footer>Informação do site</footer>

<!-- Mau exemplo -->
<div class="header">
    <div class="nav">Menu principal</div>
</div>
<div class="main">
    <div class="article">Conteúdo principal</div>
</div>
```

O bom exemplo usa elementos semânticos que criam pontos de referência (landmarks) naturais na página. O mau exemplo usa apenas `<div>`, que não fornece informação sobre a função de cada secção.

**Listas de Links**

Os utilizadores de leitores de ecrã frequentemente recorrem a listas de todos os links numa página para navegação rápida. Por isso é crucial que os links tenham texto descritivo:

```html
<!-- Bom exemplo -->
<a href="contacto.html">Entre em contacto connosco</a>

<!-- Mau exemplo -->
<a href="pg1.html">Clique aqui</a>
```

O bom exemplo fornece contexto claro sobre o destino do link. O mau exemplo força o utilizador a adivinhar para onde o link o levará.

## Técnicas de Codificação

### Separar Estrutura e Estilo

Separar a estrutura (HTML) do estilo (CSS) é como construir uma casa: primeiro criamos a estrutura básica (paredes, teto, portas) e depois decoramos (cores, texturas, acabamentos). Esta separação traz várias vantagens:

1. **Manutenção mais fácil**

```html
<!-- Mau exemplo: Mistura de estrutura e estilo -->
<div style="font-size: 24px; color: blue; margin-top: 20px">
    Título Principal
</div>

<!-- Bom exemplo: Estrutura e estilo separados -->
<h1 class="titulo-principal">
    Título Principal
</h1>
```

No mau exemplo, se precisarmos de mudar o estilo em vários títulos, teremos que editar cada elemento individualmente. No bom exemplo, podemos modificar todos os títulos alterando apenas o CSS.

### Usar Elementos Nativos

Os elementos nativos do HTML são como blocos de LEGO oficiais: foram criados especificamente para uma função e encaixam perfeitamente no sistema. Vamos ver alguns exemplos:

```html
<!-- Mau exemplo: Criar um botão personalizado -->
<div class="botao" onclick="enviarFormulario()">
    Enviar
</div>

<!-- Bom exemplo: Usar o elemento nativo -->
<button type="submit">
    Enviar
</button>
```

O elemento nativo `<button>`:

- Recebe foco automaticamente
- É ativado com teclado (Enter e Espaço)
- Comunica sua função a tecnologias de apoio
- Tem estados visuais predefinidos (hover, focus, active)

Outro exemplo comum:

```html
<!-- Mau exemplo: Lista simulada -->
<div class="lista">
    <div class="item">Primeiro item</div>
    <div class="item">Segundo item</div>
</div>

<!-- Bom exemplo: Lista nativa -->
<ul>
    <li>Primeiro item</li>
    <li>Segundo item</li>
</ul>
```

A lista nativa:

- Comunica automaticamente o número total de itens
- Permite navegação rápida entre itens
- Mantém a relação semântica entre os elementos

### ARIA

ARIA (Accessible Rich Internet Applications) é como um conjunto de etiquetas extras que podemos adicionar ao HTML para melhorar a acessibilidade. É como colocar legendas em objetos numa casa para ajudar os visitantes a entenderem a sua função.

Existem três tipos principais de atributos ARIA:

1. **Roles (Funções)**

```html
<!-- Identificar a função de um elemento -->
<div role="search">
    <input type="text" aria-label="Pesquisar no site">
    <button>Pesquisar</button>
</div>
```

2. **Properties (Propriedades)**

```html
<!-- Adicionar informação extra sobre um elemento -->
<button aria-label="Close" onclick="closeDialog()">✖</button>
```

3. **States (Estados)**

```html
<!-- Comunicar o estado atual de um elemento -->
<button aria-expanded="false" aria-controls="menu">
    Menu Principal
</button>
```

**Importante**: ARIA deve ser usado apenas quando elementos nativos não são suficientes. Como regra:

1. Não usar ARIA é melhor que usar mal
2. Usar elementos nativos é melhor que adicionar ARIA
3. ARIA não modifica o comportamento dos elementos, apenas como são anunciados a tecnologias de apoio

```html
<!-- Mau exemplo: Uso desnecessário de ARIA -->
<button role="button" aria-label="Botão de enviar">
    Enviar
</button>

<!-- Bom exemplo: Elemento nativo é suficiente -->
<button type="submit">
    Enviar
</button>
```

No mau exemplo, o `role="button"` é redundante porque o elemento `<button>` já comunica sua função. O `aria-label` também é desnecessário porque o texto do botão já é claro.

## Recomendações para Conteúdo Acessível

### 1. Estrutura clara e consistente

Imagine uma página web como um livro bem organizado. Assim como um livro tem capítulos, secções e parágrafos, a sua página deve ter uma estrutura clara e previsível:

```html
<!-- Boa estrutura -->
<header>
    <h1>Loja de Plantas</h1>
    <nav>
        <h2>Menu Principal</h2>
        <ul>
            <li><a href="plantas.html">Plantas</a></li>
            <li><a href="acessorios.html">Acessórios</a></li>
        </ul>
    </nav>
</header>
<main>
    <h2>Plantas em Destaque</h2>
    <article>
        <h3>Orquídea Phalaenopsis</h3>
        <!-- conteúdo -->
    </article>
</main>
```

### 2. Use HTML semântico, começando por elementos nativos

Comece sempre por usar elementos HTML nativos antes de considerar ARIA. É como construir uma casa: use materiais padrão testados antes de recorrer a soluções personalizadas:

```html
<!-- Mau exemplo -->
<div class="botao-menu" onclick="toggleMenu()" role="button" tabindex="0">
    Menu
</div>

<!-- Bom exemplo -->
<button type="button" onclick="toggleMenu()">
    Menu
</button>
```

### 3. Mantenha a simplicidade

Não complique desnecessariamente a estrutura do seu código. Uma estrutura simples é mais fácil de manter e geralmente mais acessível:

```html
<!-- Estrutura desnecessariamente complexa -->
<div class="container">
    <div class="wrapper">
        <div class="content-box">
            <span class="text">Bem-vindo ao nosso site</span>
        </div>
    </div>
</div>

<!-- Estrutura simples e eficaz -->
<h1>Bem-vindo ao nosso site</h1>
```

### 4. Teste com diferentes dispositivos

Certifique-se que a sua estrutura funciona bem em diferentes contextos:

- Apenas teclado
- Leitores de ecrã
- Diferentes tamanhos de ecrã
- Diferentes navegadores
- Diferentes dispositivos apontadores

## Conclusão e Exercícios

### Resumo dos Pontos-Chave

- A estrutura e semântica são fundamentais para a acessibilidade
- Use elementos nativos sempre que possível
- Separe estrutura (HTML) do estilo (CSS)
- Use ARIA apenas quando necessário

### Exercícios Práticos

1. **Análise de Estrutura**

Visite um site à sua escolha e identifique:
   
   - A estrutura de cabeçalhos
   - Os landmarks principais
   - Áreas que poderiam ser melhoradas

2. **Refatoração de Código**
   
Melhore o seguinte código:
   
   ```html
   <div class="header">
       <div class="title">Meu Blog</div>
       <div class="menu">
           <div class="menu-item">Home</div>
           <div class="menu-item">Sobre</div>
       </div>
   </div>
   ```

3. **Criar uma Página Acessível**

Desenvolva uma página simples que inclua:

   - Uma estrutura clara de cabeçalhos
   - Navegação principal
   - Conteúdo principal
   - Rodapé
   - Use apenas elementos semânticos

4. **Teste a Acessibilidade**

Para a página que criou:

   - Navegue usando apenas o teclado
   - Use um leitor de ecrã (como NVDA ou VoiceOver)
   - Verifique a estrutura usando a ferramenta de inspeção do navegador

+++


# Cabeçalhos

## Introdução

Os cabeçalhos são como os sinais de trânsito de uma página web - eles guiam os utilizadores pelo conteúdo e ajudam-nos a entender a sua organização. Para pessoas com deficiência, os cabeçalhos são ainda mais cruciais, funcionando como pontos de referência essenciais.

### Como as Pessoas com Deficiência Usam Cabeçalhos

Imagine tentar encontrar um capítulo específico num livro sem poder ver o índice ou as páginas. É assim que muitas pessoas com deficiência visual navegam em páginas web. Os cabeçalhos funcionam como um índice sempre presente, permitindo:

1. **Navegação Rápida**: A maioria dos leitores de ecrã tem teclas de atalho para saltar entre cabeçalhos. Por exemplo:
   - "H" para navegar entre todos os cabeçalhos
   - "1" a "6" para navegar entre cabeçalhos de um nível específico

2. **Compreensão da Estrutura**: Os cabeçalhos ajudam a criar um esquema mental da página, como um mapa do conteúdo. Os utilizadores podem:
   - Gerar uma lista de todos os cabeçalhos para ter uma visão geral
   - Decidir rapidamente se uma secção é relevante
   - Saltar para a secção desejada sem ter que ouvir todo o conteúdo

#### Hierarquias Significativas e Consistentes

A hierarquia de cabeçalhos é como a estrutura organizacional de uma empresa:

```html
<!-- Boa hierarquia -->
<h1>Loja de Jardinagem</h1>
    <h2>Plantas de Interior</h2>
        <h3>Orquídeas</h3>
        <h3>Suculentas</h3>
    <h2>Plantas de Exterior</h2>
        <h3>Árvores</h3>
        <h3>Arbustos</h3>

<!-- Má hierarquia -->
<h1>Loja de Jardinagem</h1>
    <h3>Plantas de Interior</h3>
    <h2>Orquídeas</h2>
    <h4>Suculentas</h4>
    <h2>Plantas de Exterior</h2>
```

No bom exemplo:

- A estrutura é lógica e previsível
- Os níveis seguem uma ordem natural
- As relações entre os conteúdos são claras

No mau exemplo:

- Os níveis saltam sem lógica
- É difícil entender as relações entre os conteúdos
- A navegação torna-se confusa e imprevisível

### Requisitos de Acessibilidade

Para garantir que os cabeçalhos são verdadeiramente acessíveis, devem seguir estes requisitos:

1. **Hierarquia Correta**

- Começar com um único `<h1>` por página
- Não saltar níveis (ex: de h2 para h4)
- Usar níveis subsequentes apenas para subcategorias relacionadas

2. **Conteúdo Significativo**

O cabeçalho serve para ajudar o utilizador a perceber sobre o que é a secção de conteúdo que começa com o cabeçalho.

```html
<!-- Mau exemplo -->
<h2>_____________</h2>
<h2>Clique Aqui</h2>

<!-- Bom exemplo -->
<h2>Nossos Produtos Mais Vendidos</h2>
<h2>Horário de Funcionamento</h2>
```

3. **Uso Semântico**

Como os cabeçalhos tendem a ter uma apresentação visual destacada, por vezes são usados (erradamente) apenas para destacar visualmente texto, não para assinalar o início de uma secção de conteúdo.

```html
<!-- Mau exemplo: usar cabeçalho apenas para estilo -->
<h3 class="texto-grande">Este texto precisa ser maior</h3>

<!-- Bom exemplo: usar CSS para estilo -->
<p class="texto-grande">Este texto precisa ser maior</p>
```

4. **Consistência**

- Usar a mesma estrutura de cabeçalhos em páginas similares
- Manter padrões previsíveis na organização do conteúdo
- Usar termos consistentes para secções similares

5. **Visibilidade**

- Garantir que todos os cabeçalhos são visíveis e legíveis
- Manter contraste adequado entre texto e fundo

Seguindo estes requisitos, os cabeçalhos tornam-se ferramentas poderosas de navegação e compreensão, beneficiando todos os utilizadores, mas especialmente aqueles que dependem de tecnologias de apoio.

## Técnicas de Codificação

### H1 a H6: Os Níveis de Cabeçalhos HTML

Os cabeçalhos HTML são como um índice de um livro, organizando o conteúdo em níveis hierárquicos. O HTML oferece seis níveis de cabeçalhos, de `<h1>` a `<h6>`.

#### Regras Básicas para Uso de Cabeçalhos

1. **Título Principal da Página**

```html
<!-- Bom exemplo -->
<h1>Loja de Artesanato</h1>

<!-- Mau exemplo -->
<h1>Loja de Artesanato</h1>
<h1>Produtos em Destaque</h1>
```

No bom exemplo, há apenas um `<h1>` que identifica claramente o propósito da página. No mau exemplo, múltiplos `<h1>` criam confusão sobre qual é o título principal.

2. **Secções e Subsecções**

```html
<!-- Bom exemplo -->
<h1>Receitas Vegetarianas</h1>
    <h2>Entradas</h2>
        <h3>Saladas</h3>
        <h3>Sopas</h3>
    <h2>Pratos Principais</h2>
        <h3>Massas</h3>
        <h3>Legumes</h3>

<!-- Mau exemplo -->
<h1>Receitas Vegetarianas</h1>
    <h2>Entradas</h2>
        <h4>Saladas</h4>
        <h3>Sopas</h3>
    <h2>Pratos Principais</h2>
```

O bom exemplo mantém uma estrutura lógica e consistente. O mau exemplo tem níveis desorganizados que confundem a hierarquia.

### Cabeçalhos ARIA

ARIA oferece formas adicionais de criar e modificar cabeçalhos quando os elementos HTML padrão não são suficientes.

#### Uso do role="heading"

```html
<!-- Bom exemplo - quando precisa de criar um cabeçalho dinâmico -->
<div role="heading" aria-level="2">
    Resultados da Pesquisa (12 itens encontrados)
</div>

<!-- Mau exemplo - quando um elemento h2 seria suficiente -->
<div role="heading" aria-level="2">
    Sobre Nós
</div>
```

O bom exemplo usa ARIA para um cabeçalho que precisa de ser atualizado dinamicamente. O mau exemplo usa ARIA desnecessariamente quando um `<h2>` nativo seria mais apropriado.

#### Modificar Níveis de Cabeçalhos

```html
<!-- Bom exemplo - ajustar o nível em um contexto específico -->
<section aria-label="Widget de Notícias">
    <div role="heading" aria-level="3">
        Últimas Atualizações
    </div>
</section>

<!-- Mau exemplo - uso incorreto de aria-level -->
<h2 aria-level="1">
    Título da Secção
</h2>
```

O bom exemplo usa ARIA para criar um cabeçalho contextual dentro de um widget. O mau exemplo tenta incorretamente mudar o nível de um elemento de cabeçalho HTML nativo.

## Recomendações para Conteúdo Acessível

Para criar cabeçalhos verdadeiramente acessíveis, aqui estão as principais recomendações e os erros mais comuns a evitar.

1. **Prefira Elementos Nativos**
```html
<!-- Melhor escolha -->
<h2>Produtos em Destaque</h2>

<!-- Evite quando possível -->
<div role="heading" aria-level="2">Produtos em Destaque</div>
```

2. **Use ARIA apenas quando necessário**

- Para cabeçalhos gerados dinamicamente
- Em componentes personalizados complexos
- Quando a estrutura HTML não pode ser modificada

3. **Mantenha a Consistência**
```html
<!-- Bom exemplo - consistência na estrutura -->
<main>
    <h1>Título Principal</h1>
    <section>
        <h2>Secção 1</h2>
        <!-- conteúdo -->
    </section>
    <section>
        <h2>Secção 2</h2>
        <!-- conteúdo -->
    </section>
</main>

<!-- Mau exemplo - mistura inconsistente -->
<main>
    <h1>Título Principal</h1>
    <section>
        <h2>Secção 1</h2>
        <!-- conteúdo -->
    </section>
    <section>
        <div role="heading" aria-level="2">Secção 2</div>
        <!-- conteúdo -->
    </section>
</main>
```

O bom exemplo mantém uma estrutura consistente usando elementos nativos. O mau exemplo mistura cabeçalhos nativos e ARIA sem necessidade, tornando a manutenção mais difícil.

### Erros Comuns

1. **Saltar Níveis de Cabeçalhos**

```html
<!-- Erro comum -->
<h1>Loja Online</h1>
<h4>Produtos em Destaque</h4>

<!-- Forma correta -->
<h1>Loja Online</h1>
<h2>Produtos em Destaque</h2>
```

No exemplo errado, saltamos do nível 1 para o nível 4, o que é como saltar do capítulo 1 para a subsecção 1.1.1.1 num livro. A forma correta mantém uma progressão lógica dos níveis.

2. **Uso de Cabeçalhos para Estilo**
```html
<!-- Erro comum -->
<h3>Este texto precisa de ser maior</h3>

<!-- Forma correta -->
<p class="texto-grande">Este texto precisa de ser maior</p>
```

Usar cabeçalhos apenas para conseguir um determinado estilo visual é como usar uma chave de fendas como martelo - a ferramenta errada para o trabalho.

3. **Múltiplos H1 na Mesma Página**

```html
<!-- Erro comum -->
<h1>Blog de Culinária</h1>
<h1>Receitas Populares</h1>
<h1>Sobre Nós</h1>

<!-- Forma correta -->
<h1>Blog de Culinária</h1>
<h2>Receitas Populares</h2>
<h2>Sobre Nós</h2>
```

Ter múltiplos H1 é como ter vários títulos principais num livro - cria confusão sobre qual é o tema principal.

4. **Cabeçalhos Vazios ou Não Descritivos**

```html
<!-- Erro comum -->
<h2>______</h2>
<h2>Clique Aqui</h2>

<!-- Forma correta -->
<h2>Categorias de Produtos</h2>
<h2>Horário de Atendimento</h2>
```

Cabeçalhos vazios ou não descritivos são como sinais de trânsito em branco - não cumprem sua função de orientação.

## Conclusão e Exercícios

### Resumo dos Pontos-Chave

- Use sempre um único H1 por página
- Mantenha uma hierarquia lógica e sequencial
- Use cabeçalhos para estruturar o conteúdo, não para estilo
- Escreva cabeçalhos descritivos e significativos

### Exercícios Práticos

1. **Análise de Estrutura**

Visite três sites diferentes e analise a estrutura dos cabeçalhos:

- Use as ferramentas de desenvolvedor do navegador
- Liste os cabeçalhos encontrados
- Identifique problemas na hierarquia
- Proponha melhorias

2. **Correção de Hierarquia**

Corrija a seguinte estrutura de cabeçalhos:

```html
<h1>Loja de Música</h1>
<h3>Instrumentos de Corda</h3>
    <h2>Violões</h2>
    <h5>Guitarras</h5>
<h4>Instrumentos de Sopro</h4>
    <h6>Flautas</h6>
```

3. **Criação de Estrutura**

Crie uma estrutura de cabeçalhos para um site de notícias com:

- Título principal
- Secções de notícias (Internacional, Desporto, Cultura)
- Subsecções dentro de cada categoria

4. **Teste com Leitor de Ecrã**

- Use um leitor de ecrã (como NVDA ou VoiceOver)
- Navegue usando apenas os cabeçalhos
- Documente sua experiência
- Identifique pontos de melhoria

+++


# Landmarks

## Introdução

Os landmarks (pontos de referência) são como a planta de um edifício - ajudam as pessoas a entender onde estão e como navegar pelo espaço. No contexto web, landmarks são elementos HTML que definem as diferentes áreas funcionais de uma página.

### Como as Pessoas com Deficiência Usam Landmarks

Imagine entrar num supermercado desconhecido. A experiência é muito mais fácil se houver sinais claros indicando onde estão as diferentes secções: padaria, frutas e legumes, caixa, etc. Os landmarks funcionam de maneira similar numa página web.

#### Estratégias de Navegação com Landmarks

As pessoas com deficiência usam landmarks de várias formas:

1. **Navegação Rápida**

- Usam teclas de atalho ou gestos para saltar entre diferentes landmarks
- Geram listas de todos os landmarks da página
- Usam landmarks para entender a estrutura geral da página

2. **Orientação**

- Landmarks ajudam a responder a perguntas como:
    - "Onde está o menu principal?"
    - "Onde começa o conteúdo principal?"
    - "Há informação complementar?"

3. **Eficiência**

- Evitam ter que passar por todo o conteúdo
- Saltam diretamente para a área desejada
- Ignoram secções repetitivas (como menus de navegação)

### Requisitos de Acessibilidade

Para garantir que os landmarks são eficazes, eles devem seguir certos requisitos:

1. **Cobertura Completa**

```html
<!-- Bom exemplo -->
<header>
    <nav>Menu de navegação</nav>
</header>
<main>Conteúdo principal</main>
<aside>Conteúdo relacionado</aside>
<footer>Rodapé</footer>

<!-- Mau exemplo -->
<div class="header">Cabeçalho</div>
<div>Conteúdo misturado sem estrutura clara</div>
<div class="footer">Rodapé</div>
```

O bom exemplo tem todas as áreas principais da página claramente identificadas. O mau exemplo deixa áreas sem identificação adequada.

2. **Unicidade**

```html
<!-- Bom exemplo -->
<main>Conteúdo principal único</main>

<!-- Mau exemplo -->
<main>Primeira área principal</main>
<main>Segunda área principal</main>
```

Alguns landmarks, como `<main>`, devem ser únicos na página. Ter múltiplos elementos do mesmo landmark pode confundir os utilizadores.

3. **Nomes Descritivos**

```html
<!-- Bom exemplo -->
<nav aria-label="Menu principal">
    <!-- links de navegação -->
</nav>
<nav aria-label="Menu do rodapé">
    <!-- links de navegação -->
</nav>

<!-- Mau exemplo -->
<nav><!-- links --></nav>
<nav><!-- outros links --></nav>
```

Quando há múltiplos elementos do mesmo tipo (como `<nav>`), eles precisam de rótulos distintos para serem identificáveis.

4. **Hierarquia Lógica**
```html
<!-- Bom exemplo -->
<body>
    <header>
        <nav>Navegação principal</nav>
    </header>
    <main>
        <article>
            <h1>Título principal</h1>
            <!-- conteúdo -->
        </article>
    </main>
    <aside>
        <nav>Links relacionados</nav>
    </aside>
</body>

<!-- Mau exemplo -->
<body>
    <main>Conteúdo principal</main>
    <header>Cabeçalho que deveria estar no topo</header>
</body>
```

A ordem dos landmarks deve refletir a estrutura lógica da página. O mau exemplo tem uma ordem que não faz sentido visualmente nem semanticamente.

Seguindo estes requisitos, os landmarks tornam-se ferramentas poderosas de navegação, beneficiando não apenas pessoas com deficiência, mas todos os utilizadores da página.

## Técnicas de Codificação

Vamos explorar cada elemento landmark e como usá-lo corretamente para criar páginas acessíveis.

### `<header>`

O `<header>` é como a capa de uma revista - contém informações introdutórias sobre o conteúdo que se segue.

```html
<!-- Bom exemplo -->
<header>
    <h1>Blog de Viagens</h1>
    <nav>
        <ul>
            <li><a href="#">Destinos</a></li>
            <li><a href="#">Dicas</a></li>
        </ul>
    </nav>
</header>

<!-- Mau exemplo -->
<div class="header">
    <div class="title">Blog de Viagens</div>
    <!-- sem estrutura de navegação clara -->
</div>
```

O bom exemplo identifica claramente a área de cabeçalho e inclui navegação estruturada. O mau exemplo perde semântica e estrutura.

### `<main>`

O elemento `<main>` é como o corpo principal de um livro - contém o conteúdo central da página.

```html
<!-- Bom exemplo -->
<main>
    <h1>Destinos Populares</h1>
    <article>
        <h2>Paris</h2>
        <!-- conteúdo sobre Paris -->
    </article>
</main>

<!-- Mau exemplo -->
<main>
    <!-- conteúdo de rodapé -->
</main>
<main>
    <!-- conteúdo principal -->
</main>
```

O bom exemplo usa `<main>` corretamente para o conteúdo principal. O mau exemplo viola a regra de ter apenas um `<main>` por página.

### `<nav>`

O `<nav>` é como o índice de um livro - ajuda os utilizadores a encontrar diferentes secções do site.

```html
<!-- Bom exemplo -->
<nav aria-label="Menu principal">
    <ul>
        <li><a href="#home">Início</a></li>
        <li><a href="#produtos">Produtos</a></li>
    </ul>
</nav>

<!-- Mau exemplo -->
<nav>
    <a href="#home">Início</a>
    <a href="#produtos">Produtos</a>
    <p>Texto que não é navegação</p>
</nav>
```

O bom exemplo tem uma estrutura clara e usa um rótulo descritivo. O mau exemplo mistura conteúdo não relacionado com navegação.

### `<footer>`

O `<footer>` é como a contracapa de um livro - contém informações complementares e finais.

```html
<!-- Bom exemplo -->
<footer>
    <nav aria-label="Links do rodapé">
        <ul>
            <li><a href="#privacidade">Política de Privacidade</a></li>
            <li><a href="#acessibilidade">Declaração de Acessibilidade</a></li>
        </ul>
    </nav>
    <p>&copy; 2025 Minha Empresa</p>
</footer>

<!-- Mau exemplo -->
<div class="footer">
    Alguns links e informações
</div>
```

O bom exemplo fornece estrutura e contexto claros. O mau exemplo perde a semântica e não estrutura o conteúdo.

### `<aside>`

O `<aside>` é como uma caixa de texto lateral num livro - contém informação relacionada mas não essencial.

```html
<!-- Bom exemplo -->
<aside aria-label="Informações relacionadas">
    <h2>Artigos Relacionados</h2>
    <ul>
        <li><a href="#">Dica de Viagem</a></li>
    </ul>
</aside>

<!-- Mau exemplo -->
<main>
    <aside>
        <!-- conteúdo principal da página -->
    </aside>
</main>
```

O bom exemplo usa `<aside>` para conteúdo complementar. O mau exemplo usa-o dentro do conteúdo principal, o que não é o propósito semântico do `<aside>`, que existe para apresentar conteúdo complementar ao principal.

### `<section>`

O `<section>` é como um capítulo de um livro - agrupa conteúdo relacionado.

```html
<!-- Bom exemplo -->
<section aria-labelledby="destaques">
    <h2 id="destaques">Produtos em Destaque</h2>
    <!-- conteúdo da secção -->
</section>

<!-- Mau exemplo -->
<section>
    <!-- conteúdo sem título -->
</section>
```

O bom exemplo tem um cabeçalho claro e rótulo descritivo. O mau exemplo não tem estrutura identificável.

### `<article>`

O `<article>` é como um artigo numa revista - contém conteúdo independente e completo.

```html
<!-- Bom exemplo -->
<article>
    <h2>Como Fazer Pão Caseiro</h2>
    <p>Ingredientes necessários...</p>
    <p>Passo a passo...</p>
</article>

<!-- Mau exemplo -->
<article>
    <div>Fragmento de conteúdo</div>
    <!-- sem estrutura ou contexto -->
</article>
```

O bom exemplo contém conteúdo completo e independente. O mau exemplo usa `<article>` para conteúdo fragmentado.

### Landmarks ARIA

ARIA permite criar ou modificar landmarks quando os elementos HTML não são suficientes.

```html
<!-- Bom exemplo - quando não pode usar elementos nativos -->
<div role="search">
    <form>
        <label for="search">Pesquisar:</label>
        <input type="search" id="search">
    </form>
</div>

<!-- Mau exemplo - quando existe elemento nativo -->
<div role="main">
    <!-- use <main> instead -->
</div>
```

O primeiro exemplo usa ARIA para criar um landmark específico que não existe em HTML nativo, enquanto que o segundo exemplo usa ARIA desnecessariamente.

#### Tabela de Roles ARIA e Elementos HTML Equivalentes

| Role ARIA | Descrição | Elemento HTML Nativo | Exemplo com role | Exemplo com elemento nativo |
|-----------|-----------|---------------------|------------------|---------------------------|
| `banner` | Cabeçalho global da página | `<header>` (quando filho direto de `<body>`) | `<div role="banner">` | `<header>` |
| `main` | Conteúdo principal | `<main>` | `<div role="main">` | `<main>` |
| `contentinfo` | Rodapé global da página | `<footer>` (quando filho direto de `<body>`) | `<div role="contentinfo">` | `<footer>` |
| `complementary` | Conteúdo complementar | `<aside>` | `<div role="complementary">` | `<aside>` |
| `navigation` | Área de navegação | `<nav>` | `<div role="navigation">` | `<nav>` |
| `search` | Área de pesquisa | *Nenhum* | `<div role="search">` | - |
| `article` | Conteúdo independente | `<article>` | `<div role="article">` | `<article>` |
| `region` | Secção importante | `<section>` com aria-label/aria-labelledby | `<div role="region" aria-label="...">` | `<section aria-label="...">` |

**Importante**: A melhor prática é usar sempre elementos HTML nativos quando disponíveis. Use roles ARIA apenas quando:

1. Não existe um elemento HTML nativo equivalente
2. Precisa modificar a semântica de um elemento existente
3. Quer criar componentes personalizados complexos

Um elemento HTML nativo já inclui toda a semântica necessária e comportamentos padrão (como foco e interação com teclado) que precisariam de ser implementados de raiz se usar ARIA.

## Recomendações para Conteúdo Acessível

Para criar landmarks verdadeiramente acessíveis, siga as recomendações anteriores e evite os erros comuns.

### Erros Comuns

1. **Duplicação de Landmarks Únicos**
```html
<!-- Erro -->
<main>Área principal 1</main>
<main>Área principal 2</main>

<!-- Correto -->
<main>
    <section>Área principal 1</section>
    <section>Área principal 2</section>
</main>
```

Este erro é como ter dois centros num campo de futebol - causa confusão sobre qual é o ponto principal de referência.

2. **Landmarks sem Identificação**

```html
<!-- Erro -->
<nav>
    <ul>
        <li><a href="#">Link 1</a></li>
    </ul>
</nav>
<nav>
    <ul>
        <li><a href="#">Link 2</a></li>
    </ul>
</nav>

<!-- Correto -->
<nav aria-label="Menu principal">
    <ul>
        <li><a href="#">Link 1</a></li>
    </ul>
</nav>
<nav aria-label="Menu secundário">
    <ul>
        <li><a href="#">Link 2</a></li>
    </ul>
</nav>
```

É como ter várias portas sem placas de identificação num prédio.

3. **Uso Incorreto de Section**
```html
<!-- Erro -->
<section>
    <p>Algum conteúdo sem cabeçalho</p>
</section>

<!-- Correto -->
<section aria-label="Informações de contacto">
    <h2>Contacte-nos</h2>
    <p>Nosso endereço...</p>
</section>
```

Uma section sem identificação é como um capítulo sem título num livro.

4. **Encadeamento Incorreto**
```html
<!-- Erro -->
<main>
    <header>Título da página</header>
    <nav>Menu principal</nav>
</main>

<!-- Correto -->
<header>
    <nav>Menu principal</nav>
</header>
<main>
    <h1>Título da página</h1>
</main>
```

O encadeamento incorreto é como colocar a entrada principal de um prédio dentro de um dos apartamentos.

## Conclusão e Exercícios

### Resumo dos Pontos-Chave

- Os landmarks são essenciais para navegação acessível
- Use elementos HTML nativos sempre que possível
- Forneça identificação clara para landmarks duplicados
- Mantenha uma estrutura lógica e consistente

### Exercícios Práticos

1. **Análise de Landmarks**

Visite três websites diferentes e:

- Identifique todos os landmarks presentes
- Verifique se estão corretamente implementados
- Liste problemas encontrados
- Sugira melhorias

2. **Correção de Estrutura**

Melhore o seguinte código:

   ```html
   <div class="header">
       <div class="nav">Menu</div>
   </div>
   <div class="main">
       Conteúdo principal
       <div class="aside">
           Barra lateral
       </div>
   </div>
   <div class="footer">
       Rodapé
   </div>
   ```

3. **Prática com ARIA Labels**

Crie uma página com:

- Múltiplas áreas de navegação
- Múltiplas secções
- Use aria-label apropriadamente
- Teste com um leitor de ecrã

4. **Avaliação de Acessibilidade**

Para uma página existente:

- Use ferramentas de inspeção do navegador
- Verifique a estrutura dos landmarks
- Teste a navegação por teclado
- Documente problemas encontrados

+++


# Elementos Semânticos

## Introdução

Os elementos semânticos do HTML são como as peças de um jogo de LEGO - cada uma tem um propósito específico e, quando usadas corretamente, criam uma estrutura significativa e acessível.

### Como as Pessoas com Deficiência Usam Elementos Semânticos

Imagine tentar montar um puzzle com peças sem imagem. Seria muito difícil entender onde cada peça se encaixa, certo? É assim que uma página sem elementos semânticos pode parecer para pessoas que usam tecnologias de apoio.

As pessoas com deficiência dependem dos elementos semânticos de várias formas:

1. **Navegação Estruturada**

- Saltam entre diferentes tipos de elementos (links, botões, campos de formulário)
- Geram listas de elementos específicos (todas as tabelas, todos os formulários)
- Entendem a relação entre elementos (cabeçalhos de tabela e suas células)

2. **Compreensão do Contexto**

- Identificam a função de cada elemento (botão vs. link)
- Entendem agrupamentos de informação (listas, tabelas)
- Reconhecem a importância relativa do conteúdo

3. **Interação Eficiente**

- Usam atalhos específicos para diferentes tipos de elementos
- Interagem apropriadamente com controlos (botões, campos de formulário)
- Navegam dentro de estruturas complexas (tabelas, listas aninhadas)

### Requisitos de Acessibilidade

Para garantir que os seus sítios são acessíveis, use elementos semânticos corretamente:

1. **Uso Apropriado**

```html
<!-- Bom exemplo -->
<button type="submit">Enviar formulário</button>

<!-- Mau exemplo -->
<div onclick="submitForm()" class="button">
    Enviar formulário
</div>
```

O bom exemplo usa o elemento correto para a função pretendida. O mau exemplo tenta recriar um botão a partir de um elemento genérico.

2. **Relações Claras**

```html
<!-- Bom exemplo -->
<label for="nome">Nome:</label>
<input type="text" id="nome">

<!-- Mau exemplo -->
Nome:
<input type="text">
```

O bom exemplo estabelece uma relação clara entre o rótulo e o campo de edição. O mau exemplo deixa o rótulo desligado do campo.

3. **Estrutura Lógica**

```html
<!-- Bom exemplo -->
<table>
    <caption>Horário das Aulas</caption>
    <thead>
        <tr><th>Hora</th><th>Segunda</th></tr>
    </thead>
    <tbody>
        <tr><td>9:00</td><td>Matemática</td></tr>
    </tbody>
</table>

<!-- Mau exemplo -->
<div class="table">
    Horário das Aulas
    <div class="row">
        <div class="cell">Hora</div><div class="cell">Segunda</div>
    </div>
</div>
```

O bom exemplo organiza a informação de forma estruturada e com semântica que permite ao utilizador compreender os dados enquanto os navega. O mau exemplo não transmite estrutura nem informação a tecnologias de apoio.

### Variedade de Elementos Semânticos

O HTML oferece uma rica variedade de elementos semânticos para diferentes propósitos:

1. **Elementos de Texto**

- `<p>` para parágrafos
- `<blockquote>` para citações
- `<em>` e `<strong>` para ênfase
- `<abbr>` para abreviações e acrónimos

2. **Elementos de Agrupamento**

- `<ul>`, `<ol>`, `<li>` para listas
- `<dl>`, `<dt>`, `<dd>` para listas de definições
- `<figure>` e `<figcaption>` para ilustrações

3. **Elementos de Formulário**

- `<input>` com diferentes tipos
- `<select>` e `<option>` para menus
- `<textarea>` para texto longo
- `<fieldset>` e `<legend>` para grupos

4. **Elementos de Tabela**

- `<table>`, `<tr>`, `<td>` para tabelas, suas linhas e dados
- `<thead>`, `<tbody>`, `<tfoot>` para estruturar tabelas
- `<caption>` para título
- `<th>` para cabeçalhos

5. **Elementos Interativos**

- `<button>` para botões
- `<a>` para links
- `<details>` e `<summary>` para conteúdo expansível
- `<dialog>` para diálogos modais

Cada um destes elementos traz consigo comportamentos e significados específicos que ajudam as tecnologias de apoio a interpretar e apresentar o conteúdo adequadamente.

## Técnicas de Codificação

### Listas

As listas são como organizadores de armário - ajudam a agrupar itens relacionados de forma clara e ordenada.

```html
<!-- Bom exemplo: Lista não ordenada -->
<ul>
    <li>Maçã</li>
    <li>Banana</li>
    <li>Laranja</li>
</ul>

<!-- Bom exemplo: Lista ordenada -->
<ol>
    <li>Pré-aqueça o forno</li>
    <li>Misture os ingredientes</li>
    <li>Asse por 30 minutos</li>
</ol>

<!-- Bom exemplo: Lista de definições -->
<dl>
    <dt>HTML</dt>
    <dd>Linguagem de marcação para criar páginas web</dd>
    <dt>CSS</dt>
    <dd>Linguagem para estilizar páginas web</dd>
</dl>

<!-- Mau exemplo -->
<div class="lista">
    * Primeiro item<br>
    * Segundo item<br>
</div>
```

Os bons exemplos usam elementos semânticos apropriados que:

- Comunicam a quantidade de itens
- Permitem navegação entre itens
- Indicam o tipo de lista (ordenada, não ordenada, definições)

### Tabelas

As tabelas organizam dados em linhas e colunas para facilitar a compreensão.

```html
<!-- Bom exemplo -->
<table>
    <caption>Horário das Aulas</caption>
    <thead>
        <tr>
            <th scope="col">Hora</th>
            <th scope="col">Segunda</th>
            <th scope="col">Terça</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <th scope="row">9:00</th>
            <td>Matemática</td>
            <td>História</td>
        </tr>
    </tbody>
</table>

<!-- Mau exemplo -->
<div class="tabela">
    <div class="linha">
        <div class="celula">Hora</div>
        <div class="celula">Segunda</div>
    </div>
</div>
```

O bom exemplo:

- Usa caption para identificar a tabela
- Diferencia os cabeçalhos dos dados, usando os elementos `<th>` e `<td>`
- Indica o escopo dos cabeçalhos através do atributo `scope`
- Agrupa linhas logicamente usando os elementos `<tr>`, `<thead>` e `<tbody>`

### Parágrafos e Texto

O texto é a base da comunicação web e precisa de ser estruturado adequadamente.

```html
<!-- Bom exemplo -->
<article>
    <h1>Receita de Bolo</h1>
    <p>Esta receita tradicional foi passada por gerações.</p>
    <p>O segredo está na qualidade dos ingredientes.</p>
    <blockquote>
        <p>O melhor bolo que já provei!</p>
        <cite>- Maria Silva</cite>
    </blockquote>
</article>

<!-- Mau exemplo -->
Esta receita tradicional foi passada por gerações.<br><br>
O segredo está na qualidade dos ingredientes.
```

O bom exemplo:

- Usa elementos semânticos para diferentes tipos de texto
- Estrutura o conteúdo logicamente
- Fornece contexto apropriado

### Formulários

Os formulários são como conversas - perguntas seguidas de respostas. Precisam de ser claros, organizados e fáceis de seguir.

#### Campos de Edição

```html
<!-- Bom exemplo -->
<form>
    <div>
        <label for="nome">Nome completo:</label>
        <input type="text" id="nome" name="nome" required>
    </div>
    <div>
        <label for="email">Email:</label>
        <input type="email" id="email" name="email"
               pattern=".+@.+\..+" 
               aria-describedby="email-hint">
        <p id="email-hint">Exemplo: nome@dominio.com</p>
    </div>
</form>

<!-- Mau exemplo -->
<form>
    Nome:<input type="text">
    Email:<input type="text">
</form>
```

O bom exemplo usa elementos semânticos apropriados como `<label>` com atributos `for`, tipos de input corretos, validação e textos de ajuda, tornando o formulário acessível para tecnologias de apoio e mais fácil de usar para todos. O mau exemplo usa apenas texto simples sem associação aos campos, tipos incorretos de input e não tem validação ou ajuda, tornando-o inacessível e difícil de usar.

#### Grupos de Controlos

```html
<!-- Bom exemplo -->
<fieldset>
    <legend>Preferências de Contacto</legend>
    <div>
        <input type="checkbox" id="email-prefs" name="contato">
        <label for="email-prefs">Email</label>
    </div>
    <div>
        <input type="checkbox" id="tel-prefs" name="contato">
        <label for="tel-prefs">Telefone</label>
    </div>
</fieldset>

<!-- Mau exemplo -->
<div class="grupo">
    Preferências de Contacto
    <input type="checkbox"> Email
    <input type="checkbox"> Telefone
</div>
```

O bom exemplo agrupa logicamente os controlos relacionados usando `<fieldset>` e `<legend>`, e associa cada checkbox ao seu rótulo usando `<label>` com `for`, permitindo que tecnologias de apoio compreendam e anunciem corretamente a estrutura. O mau exemplo usa elementos genéricos sem semântica nem associações entre controlos e rótulos, tornando impossível para tecnologias de apoio entenderem que os checkboxes fazem parte de um grupo de opções relacionadas.

### Botões

Os botões são como interruptores - precisam ser claramente identificáveis e utilizáveis. Tal como um interruptor, um botão serve para o utilizador realizar ações, não para navegar (para isso deve usar-se uma ligação). 

```html
<!-- Bom exemplo -->
<button type="submit">Enviar formulário</button>
<button type="button" aria-expanded="false">
    Mostrar mais opções
</button>

<!-- Mau exemplo -->
<div class="botao" onclick="enviar()">ENVIAR</div>
<span class="botao-expandir" onclick="expandir()">+</span>
```

O bom exemplo usa o elemento nativo `<button>` com tipos específicos e texto descritivo, garantindo funcionalidade de teclado automática e comunicação clara com tecnologias de apoio. O mau exemplo tenta criar botões usando elementos genéricos (`<div>` e `<span>`), perdendo toda a semântica e acessibilidade nativa dos botões, incluindo foco e interação por teclado.

### Ligações

As ligações (links) são como portas - devem indicar claramente para onde levam. Tal como uma porta, uma ligação serve para o utilizador navegar (na página ou no sítio), não para realizar ações (para isso deve usar-se um botão).

```html
<!-- Bom exemplo -->
<a href="politica-privacidade.html">
    Consulte nossa política de privacidade
</a>
<a href="documento.pdf" type="application/pdf">
    Download do relatório anual (PDF, 2MB)
</a>

<!-- Mau exemplo -->
<a href="#" onclick="abrirPolitica()">Clique aqui</a>
<a href="doc.pdf">Download</a>
```

O bom exemplo:

- Fornece descrição clara do destino
- Indica o tipo e tamanho de arquivos
- Usa texto significativo que faz sentido fora de contexto

## Recomendações para Conteúdo Acessível

### Erros Comuns

1. **Uso de Elementos Não Semânticos**

```html
<!-- Erro comum -->
<div onclick="fazerAlgo()" class="botao">Clique Aqui</div>

<!-- Forma correta -->
<button onClick="fazerAlgo()">Enviar formulário</button>
```

É como tentar cortar pão com uma colher - usar a ferramenta errada para o trabalho torna tudo mais difícil.

2. **Falta de Associações em Campos de Formulários**

```html
<!-- Erro comum -->
Nome: <input type="text">

<!-- Forma correta -->
<label for="nome">Nome:</label>
<input type="text" id="nome">
```

É como dar instruções sem pontos de referência - deixa as pessoas perdidas.

3. **Texto Não Descritivo**

```html
<!-- Erro comum -->
<a href="doc.pdf">Clique aqui</a>

<!-- Forma correta -->
<a href="doc.pdf">Download do relatório anual 2024 (PDF, 2MB)</a>
```

É como colocar "Porta" em todas as portas de um prédio - não ajuda ninguém a encontrar o que procura.

4. **Estruturas Complexas sem Organização**

```html
<!-- Erro comum -->
<div class="tabela">
    <div>Nome</div>
    <div>Idade</div>
    <div>João</div>
    <div>25</div>
</div>

<!-- Forma correta -->
<table>
    <thead>
        <tr><th>Nome</th><th>Idade</th></tr>
    </thead>
    <tbody>
        <tr><td>João</td><td>25</td></tr>
    </tbody>
</table>
```

É como tentar organizar um arquivo usando folhas soltas em vez de pastas - sem uma estrutura adequada, torna-se impossível entender a relação entre as informações e navegar eficientemente através delas.

## Conclusão e Exercícios

### Resumo dos Pontos-Chave

- Use sempre elementos HTML nativos quando disponíveis
- Forneça contexto e associações claras
- Use texto descritivo e significativo
- Mantenha uma estrutura lógica e consistente

### Exercícios Práticos

1. **Análise de Código**

- Examine o seguinte código e identifique problemas de acessibilidade:

```html
<div class="header">
    <div class="menu">Menu</div>
</div>
<div class="content">
    <div class="title">Bem-vindo</div>
    <div class="links">
        <span class="link" onclick="goTo('home')">Home</span>
        <span class="link" onclick="goTo('about')">Sobre</span>
    </div>
</div>
```

2. **Refatoração de código**

- Reescreva o código do exercício 1 usando elementos semânticos apropriados
- Adicione rótulos e descrições necessários
- Certifique-se que todos os elementos interativos são acessíveis por teclado

3. **Criação de Formulário**

Crie um formulário de contacto com:

- Campos para nome, email e mensagem
- Agrupamento lógico de campos
- Rótulos e descrições claros

4. **Teste de Acessibilidade**

- Use um leitor de ecrã
- Navegue pelos exercícios anteriores usando apenas o teclado
- Documente problemas encontrados
- Proponha soluções

+++


# Preocupações Adicionais de Acessibilidade Relacionadas com Estrutura e Semântica

## Saltar Blocos de Conteúdo Repetidos

### Problemas de Acessibilidade

Imagine ter que passar por um longo corredor de publicidade de cada vez que entrar numa loja - seria frustrante, certo? É assim que utilizadores de tecnologias de apoio se sentem quando têm que passar pelo mesmo menu de navegação, cabeçalho e outros elementos repetidos em cada página antes de chegar ao conteúdo principal.

Este problema afeta principalmente:

- Utilizadores de leitores de ecrã que ouvem todo o conteúdo sequencialmente
- Utilizadores de teclado que têm que fazer Tab através de todos os links
- Pessoas com limitações motoras ao nível dos membros superiores que fazem uso de software de seleção por varrimento

### Técnicas de Codificação

A solução mais comum é adicionar um "skip link" - uma ligação que permite saltar diretamente para o conteúdo principal.

```html
<!-- Bom exemplo -->
<body>
    <a href="#conteudo-principal" class="skip-link">
        Saltar para o conteúdo principal
    </a>
    
    <header>
        <!-- menu de navegação longo -->
    </header>

    <main id="conteudo-principal">
        <!-- conteúdo principal -->
    </main>
</body>

<style>
.skip-link {
    position: absolute;
    top: -40px;
    left: 0;
    padding: 8px;
    background: #000;
    color: #fff;
}

.skip-link:focus {
    top: 0;
}
</style>

<!-- Mau exemplo -->
<body>
    <header>
        <!-- menu de navegação longo sem opção de saltar -->
    </header>
    <main>
        <!-- conteúdo principal sem id -->
    </main>
</body>
```

O bom exemplo:

- Fornece uma ligação visível quando recebe foco
- Usa posicionamento CSS para ocultar a ligação até ser necessária
- Tem um destino claro identificado por ID

Outras técnicas úteis:

1. **Múltiplos Skip Links**

```html
<nav aria-label="Links de salto">
    <ul>
        <li><a href="#conteudo">Ir para conteúdo</a></li>
        <li><a href="#pesquisa">Ir para pesquisa</a></li>
        <li><a href="#rodape">Ir para rodapé</a></li>
    </ul>
</nav>
```

2. **Skip Links com Descrição**

```html
<a href="#conteudo" class="skip-link">
    Saltar menu de navegação (13 links)
</a>
```

3. **Links de Retorno**

```html
<header id="top">
    <!-- cabeçalho da página -->
</header>
<main id="conteudo">
    <h1>Título da Página</h1>
    <a href="#top" class="back-to-top">
        Voltar ao topo da página
    </a>
</main>
```

Dicas importantes:

1. O skip link deve ser o primeiro elemento focável da página
2. O destino do skip link deve ser focável 
3. O texto do skip link deve ser claro e descritivo
4. A ligação deve ser visível quando recebe foco
5. O destino deve ter um ID único na página

Esta funcionalidade simples pode fazer uma grande diferença na experiência de utilizadores que dependem de tecnologias de apoio, nomeadamente software de selecção por varrimento, ou navegação por teclado.

## Páginas Longas

### Problemas de Acessibilidade

As páginas longas são como edifícios altos - podem tornar-se cansativas e desorientadoras para navegar se não tiverem um elevador, especialmente para pessoas com deficiência. Os principais problemas incluem:

- Perda de contexto quando se navega por teclado
- Dificuldade em encontrar informação específica
- Desorientação sobre a posição atual na página

### Técnicas de Codificação

#### Tabelas de Conteúdo

As tabelas de conteúdo funcionam como um índice de um livro - permitem que os utilizadores saltem diretamente para secções específicas.

```html
<!-- Bom exemplo -->
<nav aria-labelledby="nav_topo">
    <h2 id="nav_topo">Nesta página</h2>
    <ul>
        <li><a href="#introducao">Introdução</a></li>
        <li><a href="#metodos">Métodos de Pagamento</a>
            <ul>
                <li><a href="#cartao">Cartão de Crédito</a></li>
                <li><a href="#mbway">MB WAY</a></li>
            </ul>
        </li>
    </ul>
</nav>

<main>
    <h1>Política de Pagamentos</h1>
    <section id="introducao">
        <h2>Introdução</h2>
        <!-- conteúdo -->
    </section>
    <section id="metodos">
        <h2>Métodos de Pagamento</h2>
        <section id="cartao">
            <h3>Cartão de Crédito</h3>
            <!-- conteúdo -->
        </section>
        <section id="mbway">
            <h3>MB WAY</h3>
            <!-- conteúdo -->
        </section>
    </section>
</main>

<!-- Mau exemplo -->
<div class="indice">
    Conteúdo:
    - Introdução
    - Métodos de Pagamento
</div>
```

O bom exemplo:

- Usa marcação semântica (`<nav>`)
- Reflete a hierarquia de conteúdo
- Tem IDs e ligações correspondentes
- Inclui rótulo descritivo

#### Ligações "Voltar ao Topo"

Estas ligações são como botões de elevador - permitem retornar rapidamente ao início da página.

```html
<!-- Bom exemplo -->
<header id="top">
    <!-- cabeçalho da página -->
</header>
<main>
    <section class="conteudo-longo">
        <!-- conteúdo -->
        <a href="#top" class="voltar-topo" aria-label="Voltar ao topo da página">
            ↑ Topo
        </a>
    </section>
</main>

<style>
.voltar-topo {
    position: fixed;
    bottom: 20px;
    right: 20px;
    background: #000;
    color: #fff;
    padding: 10px;
    border-radius: 4px;
    display: none;
}

/* Mostrar botão apenas quando necessário */
@media (min-height: 1000px) {
    .voltar-topo {
        display: block;
    }
}
</style>

<!-- Mau exemplo -->
<div onclick="scrollToTop()">
    ^
</div>
```

O bom exemplo:

- Usa uma ligação real em vez de JavaScript puro
- Fornece texto descritivo
- Tem posicionamento consistente
- Inclui estilos que garantem contraste adequado
- Aparece apenas em páginas longas

Dicas importantes:

1. Combine ambas as técnicas para melhor navegação
2. Mantenha a consistência no posicionamento
3. Use texto descritivo
4. Certifique-se que os elementos são focáveis
5. Forneça feedback visual e auditivo
6. Considere diferentes tamanhos de ecrã
7. Teste com tecnologias de apoio

## Apresentar Conteúdo numa Sequência Significativa

### Problemas de Acessibilidade

A ordem em que o conteúdo é apresentado é como uma história - faz sentido quando lida do princípio para o fim. Quando a sequência não é lógica, surgem vários problemas:

- Utilizadores de leitores de ecrã ouvem o conteúdo numa ordem diferente da visual
- Utilizadores de teclado encontram uma ordem de tabulação confusa
- Pessoas com deficiência cognitiva perdem-se na estrutura da página
- Utilizadores de dispositivos móveis podem ver layouts completamente diferentes

### Técnicas de Codificação

#### Considerar Diferentes Tamanhos de Ecrã

A adaptação do conteúdo a diferentes ecrãs é como um jogo de Tetris - as peças precisam de se reorganizar mantendo uma sequência lógica.

```html
<!-- Bom exemplo -->
<main>
    <article class="produto">
        <h2>Câmara Digital</h2>
        <div class="produto-info">
            <img src="camera.jpg" alt="Câmara digital preta, modelo XYZ">
            <div class="detalhes">
                <p class="preco">299€</p>
                <p class="descricao">Câmara digital com 20MP...</p>
                <button type="button">Adicionar ao carrinho</button>
            </div>
        </div>
    </article>
</main>

<style>
.produto-info {
    display: flex;
    flex-direction: column;
}

@media (min-width: 768px) {
    .produto-info {
        flex-direction: row;
        gap: 20px;
    }
}
</style>

<!-- Mau exemplo -->
<div class="produto">
    <div style="float: left">
        <img src="camera.jpg">
    </div>
    <div style="position: absolute; top: 0; right: 0">
        299€
    </div>
    <div>
        Câmara digital com 20MP...
    </div>
</div>
```

O bom exemplo:

- Usa uma estrutura HTML lógica independente do layout
- Mantém informação relacionada agrupada
- Adapta o layout usando CSS flexível
- Preserva a ordem de leitura em todos os tamanhos

Dicas importantes:

1. **Ordem do Código HTML**
```html
<!-- Boa ordem -->
<header>
    <h1>Título</h1>
    <nav>Menu principal</nav>
</header>
<main>
    <article>Conteúdo principal</article>
    <aside>Conteúdo relacionado</aside>
</main>

<!-- Má ordem -->
<aside>Conteúdo relacionado</aside>
<nav>Menu principal</nav>
<article>Conteúdo principal</article>
```

2. **Layout Responsivo**

```css
/* Bom exemplo */
.container {
    display: grid;
    grid-template-areas: 
        "header"
        "main"
        "sidebar";
}

@media (min-width: 768px) {
    .container {
        grid-template-areas: 
            "header header"
            "main sidebar";
    }
}

/* Mau exemplo */
.sidebar {
    display: none;
}
@media (min-width: 768px) {
    .sidebar {
        display: block;
    }
}
```

3. **Considerar a Navegação por Teclado**

```html
<!-- Bom exemplo -->
<div class="layout-grid">
    <nav tabindex="0">Menu</nav>
    <main tabindex="0">Conteúdo</main>
    <aside tabindex="0">Extra</aside>
</div>

<!-- Mau exemplo -->
<div class="layout-grid">
    <div tabindex="3">Extra</div>
    <div tabindex="1">Menu</div>
    <div tabindex="2">Conteúdo</div>
</div>
```

Lembre-se:

- A ordem do HTML deve fazer sentido mesmo sem CSS
- O layout visual não deve comprometer a ordem lógica
- Evite esconder conteúdo importante em ecrãs pequenos
- Teste a navegação por teclado em todos os breakpoints
- Verifique a ordem de leitura com leitores de ecrã

## Navegação dentro dos Sítios

### Problemas de Acessibilidade

Navegar num sítio mal estruturado é como tentar encontrar um livro numa biblioteca onde os livros estão dispostos aleatoriamente, sem sistema de catalogação. As pessoas com deficiência enfrentam vários desafios:

- Desorientação sobre localização atual no site
- Dificuldade em entender a estrutura global
- Confusão em processos multi-passos
- Perda de contexto entre páginas

### Técnicas de Codificação

#### Mapas do Sítio

O mapa do sítio é como um índice detalhado de um livro - oferece uma visão geral de todo o conteúdo disponível.

```html
<!-- Bom exemplo -->
<nav aria-label="Mapa do site">
    <h1>Mapa do Site</h1>
    <ul>
        <li>
            <a href="/produtos">Produtos</a>
            <ul>
                <li><a href="/cameras">Câmaras</a></li>
                <li><a href="/lentes">Lentes</a></li>
            </ul>
        </li>
        <li>
            <a href="/servicos">Serviços</a>
            <ul>
                <li><a href="/reparacao">Reparação</a></li>
                <li><a href="/aluguer">Aluguer</a></li>
            </ul>
        </li>
    </ul>
</nav>

<!-- Mau exemplo -->
<div class="sitemap">
    Produtos
    - Câmaras
    - Lentes
    Serviços
    - Reparação
    - Aluguer
</div>
```

#### Títulos de Páginas Descritivos

```html
<!-- Bom exemplo -->
<title>Câmaras Digitais - Produtos - Loja de Fotografia</title>

<!-- Mau exemplo -->
<title>Página 2</title>
```

O bom exemplo:

- Inclui informação específica da página
- Mostra a hierarquia (subpágina > secção > site)
- Ajuda na orientação quando se usa múltiplos separadores

#### Processos com Vários Passos

Para processos complexos, como checkout ou registo, use indicadores de progresso claros que permitam ao utilizador saber quantos passos existem no processo e em que passo se encontra:

```html
<!-- Bom exemplo -->
<nav aria-label="Progresso de checkout">
    <ol class="progresso">
        <li aria-current="step">
            1. Carrinho
            <span class="status">(passo atual)</span>
        </li>
        <li>
            2. Entrega
            <span class="status">(próximo passo)</span>
        </li>
        <li>
            3. Pagamento
            <span class="status">(pendente)</span>
        </li>
    </ol>
</nav>

<!-- Mau exemplo -->
<div class="steps">
    <div class="active">1</div>
    <div>2</div>
    <div>3</div>
</div>
```

Dicas importantes para processos multi-passos:

1. **Feedback Claro**

```html
<div role="alert" aria-live="polite">
    Morada guardada com sucesso. 
    Próximo: selecione o método de pagamento.
</div>
```

Manter o utilizador informado sobre o que aconteceu e o que deve fazer a seguir reduz a ansiedade e confusão, especialmente para pessoas que usam leitores de ecrã. No exemplo, os atributos role="alert" e aria-live="polite" garantem que as tecnologias de apoio anunciam as atualizações de estado sem interromper abruptamente o utilizador.

2. **Navegação Entre Passos**

```html
<nav class="navegacao-passos">
    <button type="button" class="anterior">
        ← Voltar para Entrega
    </button>
    <button type="submit" class="seguinte">
        Continuar para Pagamento →
    </button>
</nav>
```

Os utilizadores precisam de poder navegar livremente entre os passos do processo, seja para verificar informação anterior ou corrigir erros. O exemplo fornece botões claramente identificados para avançar e retroceder, com setas direcionais e texto descritivo que indica explicitamente o destino de cada ação.

## Recomendações para Conteúdo Acessível

### Erros Comuns

1. **Esconder Conteúdo Importante em Ecrãs Pequenos**

```html
<!-- Erro -->
<nav class="menu-mobile" style="display: none">
    <!-- menu simplificado -->
</nav>

<!-- Melhor abordagem -->
<nav class="menu" aria-label="Menu principal">
    <!-- menu adaptativo -->
</nav>
```

É como remover portas de emergência num prédio pequeno - o conteúdo importante deve estar sempre acessível, apenas apresentado de forma diferente.

2. **Dependência de Características Específicas**

```html
<!-- Erro -->
<div onmouseover="mostrarInfo()">
    Passe o rato para ver mais informação
</div>

<!-- Melhor abordagem -->
<button onclick="toggleInfo()" aria-expanded="false">
    Mostrar mais informação
</button>
```

É como criar um edifício acessível apenas por escadas - deve funcionar para todos os utilizadores, independentemente das suas capacidades.

3. **Falta de Feedback em Processos**

```html
<!-- Erro -->
<button onclick="submeterForm()">Enviar</button>

<!-- Melhor abordagem -->
<button onclick="submeterForm()">Enviar</button>
<div role="status" aria-live="polite" class="feedback"></div>
```

É como não indicar a um cliente que a sua encomenda está pronta para ser levantada - se uma ação tem um resultado, este deve ser apresentado de forma acessível a todos os utilizadores.

## Conclusão e Exercícios

### Exercícios Práticos

1. **Auditoria de Acessibilidade**

- Escolha um website popular
- Identifique problemas de acessibilidade em:
    - Navegação
    - Formulários
    - Conteúdo dinâmico
    - Estrutura da página
- Proponha soluções

2. **Refatoração**

Melhore o seguinte código:

```html
<div class="nav">
    <div class="items">Menu</div>
</div>
<div class="main">
    <div class="title">Página Principal</div>
    <div class="content">
        <img src="grafico.jpg">
        <div class="btn" onclick="next()">></div>
    </div>
</div>
```

3. **Teste com Tecnologias de Apoio**

- Use um leitor de ecrã
- Tente completar tarefas comuns:
    - Preencher um formulário
    - Navegar entre páginas
    - Encontrar informação específica
- Documente os problemas encontrados

+++


# Conclusão e Boas Práticas

## Recapitulação

Ao longo deste módulo, explorámos como criar sítios web acessíveis das perspetivas estrutural e semântica. Os pontos principais que abordámos foram:

1. **Estrutura e Semântica**

- Uso correto de elementos HTML
- Importância da estrutura lógica
- Papel do ARIA

2. **Cabeçalhos**

- Hierarquia significativa
- Navegação eficiente
- Organização do conteúdo

3. **Landmarks**

- Pontos de referência claros
- Navegação estruturada
- Orientação na página

4. **Elementos Semânticos**

- Formulários acessíveis
- Tabelas estruturadas
- Links e botões significativos

5. **Preocupações Adicionais**

- Skip links
- Páginas longas
- Navegação entre páginas

## Recursos Adicionais

### Documentação

- [WCAG 2.2](https://www.w3.org/WAI/standards-guidelines/wcag/)
- [WAI-ARIA](https://www.w3.org/WAI/standards-guidelines/aria/)
- [MDN Accessibility](https://developer.mozilla.org/en-US/docs/Web/Accessibility)

### Ferramentas

- [accessMonitor](https://accessmonitor.acessibilidade.gov.pt)
- [WAVE](https://wave.webaim.org/)
- [aXe](https://www.deque.com/axe/)
- [NVDA](https://www.nvaccess.org/)
- [VoiceOver](https://www.apple.com/accessibility/mac/vision/)

### Comunidades e Blogs

- [Inclusive Components](https://inclusive-components.design/)

## Exercícios de Consolidação

1. **Auditoria Completa**

Escolha um website e avalie:

- Estrutura HTML
- Navegação por teclado
- Uso de ARIA
- Comportamento responsivo

2. **Projeto Prático**

Crie uma página que inclua:

- Formulário complexo
- Navegação principal e secundária
- Tabelas de dados
- Diferentes breakpoints

3. **Documentação**

Desenvolva:

- Guia de estilo de acessibilidade
- Checklist de verificação
- Exemplos de código
- Casos de teste

### Lista de Verificação Final

- ✓ Compreende os princípios fundamentais
- ✓ Sabe implementar soluções acessíveis
- ✓ Conhece as ferramentas disponíveis
- ✓ Pode testar efetivamente
- ✓ Entende as necessidades dos utilizadores
- ✓ Pode formar outros na equipa
- ✓ Mantém-se atualizado sobre boas práticas

A acessibilidade web não é um destino, mas uma jornada contínua de aprendizagem e melhoria. Continue a aprender, a testar e a adaptar as suas práticas à medida que novas tecnologias e diretrizes surgem.

