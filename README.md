# Site Sintoniza Contabilidade & BPO Financeiro

Landing page de página única, responsiva (celular, tablet e desktop), em um único `index.html` sem dependências de build. Logo, cifrão e leão estão embutidos em SVG; a foto e os ícones estão embutidos no próprio HTML. As fontes (Marcellus e Raleway) vêm do Google Fonts.

## Arquivos

| Arquivo | Função |
|---|---|
| `index.html` | O site completo |
| `og-image.jpg` | Imagem de prévia ao compartilhar o link (WhatsApp, Instagram, LinkedIn) |
| `robots.txt` | Libera a indexação pelos buscadores |
| `netlify.toml` | Cabeçalhos de segurança e cache (usado só no Netlify) |

## Como publicar

**Netlify (mais simples):** em app.netlify.com, arraste a pasta inteira para a área "Deploy manually". Depois, em Domain settings, conecte o domínio da cliente.

**Vercel ou outra hospedagem:** envie os quatro arquivos para a raiz do site. O `netlify.toml` pode ser ignorado.

## Depois de definir o domínio

1. No `index.html`, troque `content="og-image.jpg"` pela URL absoluta (`https://SEU-DOMINIO/og-image.jpg`). O WhatsApp só mostra a prévia com URL absoluta.
2. Adicione no `<head>`: `<link rel="canonical" href="https://SEU-DOMINIO/">` e `<meta property="og:url" content="https://SEU-DOMINIO/">`.
3. Ajuste a linha do Sitemap no `robots.txt`, se for criar um.
4. Teste a prévia do link em https://developers.facebook.com/tools/debug/ e enviando o link em uma conversa do WhatsApp.

## Como alterar dados de contato

- **WhatsApp:** buscar e substituir `5511916896153` (aparece nos links e no script do formulário) e `(11) 91689-6153` (texto visível).
- **E-mail:** buscar `sintonizabpo@gmail.com`.
- **Instagram:** buscar `instagram.com/sintonizabpo` (Sintoniza) e `instagram.com/contadoragabrielly_` (Gabrielly).

Cada botão abre o WhatsApp com uma mensagem diferente (contabilidade, BPO, consultoria, gestão, "Olá, Gabrielly", dúvida do FAQ), para identificar de qual parte do site veio o contato. O formulário monta a mensagem com nome, serviço e descrição; nenhum dado é armazenado no site.

## Verificações já feitas

- Acessibilidade: auditoria automática axe-core (WCAG 2.1 A/AA) sem violações em desktop e celular; contraste de texto acima de 4,5:1 em todas as combinações; navegação completa por teclado com foco visível; link "Pular para o conteúdo"; menu do celular fecha com Esc; faixa animada com botão de pausa; animações desligadas para quem ativa "reduzir movimento".
- Formulário: erros por campo, com foco no primeiro campo pendente.
- Sem JavaScript: o menu continua acessível e o formulário mostra um link direto para o WhatsApp.
- SEO: título, descrição, Open Graph e dados estruturados (schema.org `AccountingService`).

## Pendências de conteúdo (validar com a cliente)

- [ ] Números do hero: "+6 anos de experiência" e "+70 clientes atendidos".
- [ ] Resposta do FAQ sobre atendimento a outras cidades.
- [ ] Resposta do FAQ sobre acesso à conta bancária (substituir pelo procedimento real).
- [ ] Departamento pessoal e abertura de empresa: incluir nos serviços se ela oferecer.
- [ ] "Conversa de avaliação sem compromisso": se for gratuita, vale dizer.
- [ ] Foto original em alta resolução (a atual veio do WhatsApp, 640 px de largura).
- [ ] CRC e CNPJ no rodapé quando estiverem disponíveis.

## Checklist de publicação

- [ ] Pendências de conteúdo aprovadas pela cliente
- [ ] Domínio conectado e HTTPS ativo
- [ ] `og:image` com URL absoluta e prévia testada no WhatsApp
- [ ] Todos os botões de WhatsApp testados em um celular real
- [ ] Formulário testado (nome vazio, serviço vazio, envio completo)
- [ ] Site aberto em iPhone e Android, e em Chrome, Safari e Edge no computador
- [ ] Se ativar Google Analytics ou Meta Pixel: há um espaço reservado no `<head>`, e passa a ser necessário um aviso de cookies (LGPD)
