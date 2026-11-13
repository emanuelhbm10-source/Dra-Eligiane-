# LP — Dra. Eligiane Costa | Fisioterapeuta Pélvica

Site estático (HTML/CSS/JS puro), pronto para GitHub → Vercel. Sem build: suba a pasta inteira.

## Antes de publicar
1. **Domínio** — troque `SEUDOMINIO.com.br` em `index.html` (canonical, Open Graph, JSON-LD), `robots.txt` e `sitemap.xml`.
2. **WhatsApp** — confirme o número com a cliente. `(66) 9277-4986` tem 8 dígitos; se o celular for `(66) 99277-4986`, troque `WHATSAPP` no `SITE_CONFIG` e os textos visíveis (busque por `9277-4986`).
3. **Itens “a confirmar”** (tracejados) — formação, especialização, certificações, nº do CREFITO, endereço e horário. Busque por `pendente` no HTML; ao preencher, remova a classe `pendente`. O código de ética do COFFITO pede nome, profissão e nº do CREFITO na publicidade — vale confirmar a regra atual com a cliente.
4. **Etapas da primeira consulta** (seção "Como é a primeira consulta") e chips dos tratamentos — redigidos de forma genérica; confirme com a Dra. como ela conduz a consulta.
5. **Textos de tratamentos e FAQ** — redigidos de forma genérica e sem promessa de resultado. Peça para a Dra. revisar antes de publicar.

## Rastreamento
No topo do `index.html`, objeto `window.SITE_CONFIG`:
- `GTM_ID` — ID do Google Tag Manager (o script só carrega quando o ID real é preenchido). Descomente também o `<noscript>` logo após o `<body>`.
- `GA4_ID` — opcional, só se o GA4 NÃO for configurado pelo GTM.
- `FORM_ENDPOINT` — opcional. URL que recebe o formulário via POST JSON (Formspree, Make, n8n…). Vazio = o formulário abre o WhatsApp com os dados preenchidos.

Eventos enviados ao `dataLayer` (use como gatilhos no GTM para GA4, Google Ads e Meta Pixel):

| Evento | Parâmetros | Uso sugerido |
|---|---|---|
| `whatsapp_click` | `cta_location`, `cta_label` | Conversão principal (Google Ads / Meta `Contact`) |
| `generate_lead` | `method`, `lead_subject` | Conversão do formulário (Meta `Lead`) |
| `instagram_click` | `cta_location` | Engajamento |
| `faq_open` | `faq_question` | Engajamento |
| `treatment_tab` | `treatment` | Interesse por tratamento |

`cta_location` identifica o botão: `menu`, `hero`, `identificacao`, `card-…`, `sobre`, `faq`, `cta-final`, `rodape`, `flutuante`.

## Estrutura
- `index.html` — página completa (CSS e JS embutidos)
- `img/` — fotos em WebP (com JPG de reserva) em vários tamanhos + `og-image.jpg`
- `fonts/` — Italiana e Montserrat hospedadas localmente (licença SIL OFL)
- `robots.txt`, `sitemap.xml`, `vercel.json` (cache longo para imagens e fontes)
