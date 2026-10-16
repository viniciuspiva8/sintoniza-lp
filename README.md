# Sintoniza Contabilidade · Landing page

Landing page institucional para a **Sintoniza Contabilidade & BPO Financeiro**, escritório de contabilidade estratégica integrada à gestão financeira de pequenas empresas e profissionais liberais.

O projeto foi construído como uma página única em HTML, CSS e JavaScript puros, sem framework e sem etapa de build, com foco em conversão via WhatsApp, acessibilidade WCAG 2.1 AA e identidade visual premium fiel à marca.

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat-square&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-vanilla-F7DF1E?style=flat-square&logo=javascript&logoColor=black)
![Netlify](https://img.shields.io/badge/deploy-Netlify-00C7B7?style=flat-square&logo=netlify&logoColor=white)
![WCAG 2.1 AA](https://img.shields.io/badge/WCAG_2.1-AA-2E7D32?style=flat-square)
![Dependências](https://img.shields.io/badge/depend%C3%AAncias-0-555?style=flat-square)

**Demo:** [sintonizacontabilidade.netlify.app](https://sintonizacontabilidade.netlify.app/#topo)

![Página inicial no desktop](docs/screenshot-desktop.jpg)

<p align="center">
  <img src="docs/screenshot-mobile.jpg" alt="Página inicial no celular" width="300">
</p>

<details>
<summary>Ver a página completa</summary>

![Página completa](docs/screenshot-full.jpg)

</details>

---

## Sumário

- [Contexto](#contexto)
- [Destaques técnicos](#destaques-técnicos)
- [Stack e decisões de arquitetura](#stack-e-decisões-de-arquitetura)
- [Design system](#design-system)
- [Estrutura da página](#estrutura-da-página)
- [Pipeline de assets](#pipeline-de-assets)
- [Acessibilidade](#acessibilidade)
- [Performance e SEO](#performance-e-seo)
- [Como rodar localmente](#como-rodar-localmente)
- [Deploy](#deploy)
- [Configuração e customização](#configuração-e-customização)
- [Qualidade e testes](#qualidade-e-testes)
- [Roadmap](#roadmap)
- [Créditos e licença](#créditos-e-licença)

---

## Contexto

A cliente tinha um site antigo feito no Canva, com excesso de texto e posicionamento voltado apenas para BPO Financeiro. O novo projeto precisava:

- reposicionar a marca com **a contabilidade como serviço principal** e o BPO Financeiro como diferencial;
- transmitir **autoridade técnica com proximidade**, usando a identidade preto e dourado com o leão da marca;
- converter visitas vindas principalmente do Instagram em **conversas qualificadas no WhatsApp**;
- funcionar bem em qualquer tela e ser simples de hospedar e manter.

O trabalho incluiu imersão em referências do setor, briefing estruturado com a cliente, reescrita completa do conteúdo, design, desenvolvimento e auditoria de qualidade.

## Destaques técnicos

- **Arquivo único, zero dependências:** todo o site cabe em um `index.html` (~190 KB, ~110 KB com gzip), com CSS e JS embutidos. Não há `node_modules`, bundler nem build.
- **Marca vetorizada a partir de PNG:** logotipo, cifrão e leão foram convertidos de imagens rasterizadas para paths SVG com OpenCV, o que permite reaproveitar cada elemento separadamente, aplicar gradiente dourado via `<linearGradient>` e manter nitidez em qualquer densidade de tela.
- **Conversão orientada a contexto:** cada CTA abre o WhatsApp com uma mensagem pré-preenchida diferente (serviço específico, seção "sobre", FAQ), permitindo identificar a origem do lead sem nenhuma ferramenta de analytics.
- **Formulário sem backend:** os campos montam a mensagem e redirecionam para `wa.me`. Nenhum dado pessoal é armazenado ou trafegado por servidor próprio.
- **Animação com propósito:** uma sequência orquestrada no carregamento, um brilho em SMIL que percorre o leão a cada 30 segundos (suspenso quando a aba está em segundo plano), a faixa de serviços em loop contínuo e uma linha de progresso no "Como funciona" acionada por `IntersectionObserver`.
- **Progressive enhancement:** sem JavaScript, o menu continua navegável e o formulário oferece um link direto para o WhatsApp.
- **Acessível de verdade:** zero violações no axe-core (WCAG 2.1 A/AA), navegação completa por teclado, botão para pausar o conteúdo em movimento e respeito a `prefers-reduced-motion`.

## Stack e decisões de arquitetura

| Camada | Escolha | Motivo |
|---|---|---|
| Marcação | HTML5 semântico | Landmarks, `details/summary` nativo para o FAQ, formulário com `label` e `aria-describedby` |
| Estilo | CSS puro com custom properties | Tokens de design em `:root`, layout com Grid e Flexbox, tipografia fluida com `clamp()` |
| Comportamento | JavaScript vanilla (~4 KB) | Poucas interações; um framework adicionaria peso sem benefício |
| Gráficos | SVG inline com `<symbol>` e `<use>` | Logo, cifrão e ícones definidos uma vez e reutilizados no header, faixa, serviços e rodapé |
| Imagens | Data URIs (JPEG/PNG) | Página autocontida, sem requisições extras para a foto e o ícone de tela inicial |
| Fontes | Google Fonts (Marcellus + Raleway) | Raleway reproduz a tagline do logotipo; Marcellus traz o tom institucional aos títulos |
| Hospedagem | Netlify | Deploy estático por arrastar e soltar, HTTPS automático e cabeçalhos via `netlify.toml` |

**Por que não React, Next.js ou Tailwind?** É uma landing page de conteúdo estático com meia dúzia de interações. HTML e CSS puros entregam o menor tempo de carregamento possível, eliminam manutenção de dependências e permitem que qualquer pessoa edite o conteúdo sem ambiente de desenvolvimento. Se o site evoluir para várias páginas ou blog, a migração natural seria para um gerador estático (Astro ou 11ty) reaproveitando os mesmos tokens e componentes.

## Design system

### Cores

| Token | Hex | Uso |
|---|---|---|
| `--onix` | `#0E0D0B` | Fundo principal |
| `--grafite` | `#171512` | Superfícies (cards, faixa, formulário) |
| `--marfim` | `#F2ECE2` | Texto principal (branco quente, evita frieza do branco puro) |
| `--areia` | `#B9B0A2` | Texto secundário |
| `--ouro` | `#C9A45C` | Detalhes, marcadores e ícones |
| `--ouro-claro` | `#E8CF8A` | Links e destaques |
| `--linho` | `#EEE7DA` | Fundo da seção clara ("Como funciona") |
| `--tinta` | `#1B1813` | Texto sobre fundo claro |

O dourado é aplicado como gradiente metálico (`--grad-ouro`) nos botões principais e no logotipo, reproduzindo o acabamento da identidade original.

### Tipografia

- **Marcellus** (serifada inscricional) para títulos, em caixa normal, com escala fluida de `2rem` a `4.4rem`.
- **Raleway** para texto corrido e interface, com `font-variant-numeric: lining-nums` para números alinhados.
- Medida de linha limitada a ~60–70 caracteres nos blocos de texto.

### Princípios

- Uma única ousadia visual: o leão em escala monumental no hero. O restante é contido.
- Dourado usado com parcimônia, nunca como fundo de grandes áreas.
- Hierarquia por conteúdo: o serviço principal ocupa a largura total; os demais aparecem em grade de três colunas.

## Estrutura da página

| Seção | Objetivo |
|---|---|
| Hero | Proposta de valor, CTA principal e indicadores de prova social |
| Faixa animada | Reforço dos serviços em loop contínuo, com botão de pausa |
| Dores | Identificação do visitante com frases na voz do cliente |
| Serviços | Contabilidade completa em destaque, seguida de BPO Financeiro, consultoria e gestão financeira |
| Para quem é | Quatro perfis de público atendido |
| Como funciona | Processo em cinco etapas, em seção clara para quebrar o ritmo escuro |
| Sobre | Apresentação da fundadora, formação e propósito da marca |
| FAQ | Oito objeções frequentes em acordeão nativo |
| Contato | Canais com ícones e formulário que gera a mensagem do WhatsApp |

## Pipeline de assets

A cliente forneceu o kit de marca apenas em PNG (3375 × 3375 px). Para uso na web, os elementos foram vetorizados em Python:

1. **Logotipo:** binarização da versão branca sobre fundo preto e extração de contornos com `cv2.findContours` (`RETR_CCOMP`), preservando os furos das letras com `fill-rule="evenodd"`.
2. **Separação de elementos:** projeções horizontais e verticais dos pixels identificam os vãos entre o cifrão, o nome e a tagline, gerando três paths independentes que recebem cores diferentes.
3. **Leão:** isolado da arte com logo por limiar de cor (cinza neutro de baixa luminância), seguido de fechamento e abertura morfológicos para remover ruído, e simplificado com `approxPolyDP`.
4. **Fotos e imagem de compartilhamento:** recorte, correção leve de tom e exportação com Pillow.

O resultado são ~23 KB de paths SVG que substituem várias imagens de alta resolução.

## Acessibilidade

Auditado com **axe-core** nas regras WCAG 2.1 A/AA e boas práticas, em desktop (1366 px) e celular (390 px): **0 violações**.

- Contraste mínimo de 4,5:1 em todas as combinações de texto (entre 4,9:1 e 16,5:1) e 3:1 em bordas de campos.
- Link "Pular para o conteúdo", visível ao receber foco.
- Foco visível em todos os elementos interativos e ordem de tabulação coerente com a leitura.
- Menu mobile com `aria-expanded`, fechamento por Esc e por clique fora, devolvendo o foco ao botão.
- Faixa animada com botão de pausa (critério 2.2.2) e todas as animações desativadas com `prefers-reduced-motion`.
- Formulário com rótulos explícitos, erros por campo associados via `aria-describedby` e foco no primeiro campo pendente.
- Áreas de toque de no mínimo 44 px nos controles principais.

## Performance e SEO

- Uma requisição para o documento, mais a folha e os arquivos de fonte do Google Fonts (com `preconnect` e `display=swap`).
- Sem imagens externas, sem scripts de terceiros e sem bloqueio de renderização além das fontes.
- Metadados de título, descrição e Open Graph, com imagem de compartilhamento 1200 × 630.
- Dados estruturados em JSON-LD (`schema.org/AccountingService`) com contatos e perfis sociais.
- `robots.txt` liberando indexação e cabeçalhos de segurança (`X-Content-Type-Options`, `X-Frame-Options`, `Referrer-Policy`, `Permissions-Policy`) configurados no Netlify.

## Como rodar localmente

Não há instalação. Basta abrir o `index.html` no navegador ou servir a pasta:

```bash
# com Python
python3 -m http.server 8080

# ou com Node
npx serve .
```

Acesse `http://localhost:8080`.

## Deploy

**Netlify (recomendado):** em *Add new site › Deploy manually*, arraste a pasta do projeto. O `netlify.toml` aplica os cabeçalhos automaticamente. Para deploy contínuo, conecte este repositório em *Import from Git*; não há comando de build e o diretório de publicação é a raiz.

**Outras hospedagens estáticas** (Vercel, GitHub Pages, Cloudflare Pages, hospedagem tradicional): publique os arquivos na raiz. O `netlify.toml` é ignorado fora do Netlify.

### Após definir o domínio

1. Troque `content="og-image.jpg"` pela URL absoluta (`https://dominio/og-image.jpg`), pois o WhatsApp só exibe a prévia com URL absoluta.
2. Adicione `<link rel="canonical">` e `<meta property="og:url">` com o domínio final.
3. Valide a prévia no [Sharing Debugger da Meta](https://developers.facebook.com/tools/debug/).

## Configuração e customização

| O que mudar | Onde |
|---|---|
| Número do WhatsApp | Buscar `5511916896153` (links e script do formulário) e o texto visível do telefone |
| E-mail | Buscar o endereço de e-mail no `index.html` |
| Instagram | Buscar `instagram.com/` (há um perfil institucional e um da fundadora) |
| Mensagens pré-preenchidas | Parâmetro `text` de cada link `wa.me` |
| Itens da faixa animada | Lista `.faixa-group` (duplicada para o loop contínuo) |
| Cores e tipografia | Custom properties em `:root` |
| Analytics | Comentário reservado no `<head>`; ao ativar, incluir aviso de cookies conforme a LGPD |

## Qualidade e testes

Validações executadas antes da entrega, com **Playwright** e **axe-core**:

- Renderização em 390 px, 768 px, 1366 px e 1440 px, sem rolagem horizontal.
- Auditoria de acessibilidade automatizada (0 violações).
- Ordem de tabulação, abertura e fechamento do menu por teclado e funcionamento do botão de pausa.
- Validação do formulário: campos vazios, foco no erro e limpeza do erro ao corrigir.
- Funcionamento com JavaScript desativado.
- Intervalo da animação do leão verificado com relógio simulado (disparos em 1,3 s, 31 s e 61 s).
- Ausência de erros no console em todas as larguras.

## Roadmap

- [ ] Domínio próprio com `canonical` e Open Graph absolutos
- [ ] Analytics com banner de consentimento (LGPD) e página de política de privacidade
- [ ] Testes E2E e de acessibilidade em CI (GitHub Actions + Playwright + axe-core)
- [ ] Separar o código-fonte e os scripts de vetorização em um pipeline de build reprodutível
- [ ] Seção de depoimentos quando houver avaliações publicadas

## Estrutura do repositório

```
.
├── index.html       # Site completo (HTML, CSS, JS, SVG e imagens embutidos)
├── og-image.jpg     # Imagem de compartilhamento (1200 × 630)
├── robots.txt       # Diretivas para buscadores
├── netlify.toml     # Cabeçalhos de segurança e cache
└── docs/            # Capturas de tela usadas neste README
```

## Créditos e licença

Desenvolvido por **Vinicius Piva** · [LinkedIn](https://www.linkedin.com/in/SEU-PERFIL) · [GitHub](https://github.com/SEU-USUARIO)

O código-fonte está disponível para fins de portfólio. A marca Sintoniza, o logotipo, a ilustração do leão, as fotografias e os textos institucionais pertencem à Sintoniza Contabilidade & BPO Financeiro e não podem ser reutilizados sem autorização.
