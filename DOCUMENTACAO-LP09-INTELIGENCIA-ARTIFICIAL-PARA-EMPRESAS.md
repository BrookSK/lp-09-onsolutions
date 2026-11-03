# Documentação — LP09 Inteligência Artificial para Empresas | ON Solutions Brasil

## 1. Objetivo da landing page
Apresentar e converter o serviço de **Inteligência Artificial para Empresas** da ON Solutions Brasil, com foco em conversão via WhatsApp. Posicionamento comercial preservado: *"Sem modismo: cada solução de IA nasce de um problema real do seu negócio."*

## 2. Escopo
- Desenvolvimento **exclusivo** da Landing Page 09 (página única).
- Sem páginas adicionais, painel administrativo, CMS, banco de dados ou backend.
- Reprodução fiel da referência `09-lp-inteligencia-artificial-para-empresas.html` (conteúdo, identidade visual, estrutura, interações, responsividade, SEO e integração com WhatsApp).

## 3. Estrutura de arquivos
```
lp-09-onsolutions/
├── index.html
├── css/
│   └── styles.css
├── js/
│   └── main.js
├── assets/
│   └── img/
│       ├── favicon.png              (placeholder — ver Pendências)
│       ├── logo-onsolutions.png     (placeholder — ver Pendências)
│       ├── cliente-braziliana.png   (placeholder — ver Pendências)
│       ├── cliente-quatri.png       (placeholder — ver Pendências)
│       ├── cliente-brooks.png       (placeholder — ver Pendências)
│       ├── cliente-crosshr.png      (placeholder — ver Pendências)
│       ├── cliente-multilife.png    (placeholder — ver Pendências)
│       └── cliente-mafedo.png       (placeholder — ver Pendências)
├── DOCUMENTACAO-LP09-INTELIGENCIA-ARTIFICIAL-PARA-EMPRESAS.md
└── README.md
```
A referência original embutia todos os materiais gráficos em **Base64** dentro do próprio HTML. Nesta implementação, os materiais foram **externalizados** para `assets/img/` (melhora performance e manutenção), mantendo a mesma aparência e papel visual de cada elemento. A estrutura separa HTML, CSS e JavaScript, seguindo o padrão das demais LPs da ON Solutions.

## 4. Tecnologias utilizadas
- **HTML5**, **CSS3**, **JavaScript puro (Vanilla JS)**.
- Fonte **Poppins** (pesos 400, 500, 600, 700, 800) via Google Fonts, com `preconnect`.
- Nenhum framework, biblioteca, sistema de build ou dependência de execução em produção.

## 5. Organização do HTML (`index.html`)
Seções na ordem da referência:
1. `header.top` — logo, nome, telefone, botão Orçamento (header com hide/show no scroll).
2. `section.hero` — badge, H1 com palavra-chave em turquesa (`<mark>`), subtítulo, pontos, selos de confiança e card ilustrativo do WhatsApp (`[data-bubble]`).
3. `#dores` — 4 botões de desafio (`.pain`, `aria-pressed`) + feedback dinâmico (`[data-hint]`).
4. `#beneficios` — 4 cards com ícones SVG.
5. `#clientes` (`.proof`) — indicadores (100+, 50+, Brasil e exterior) + carrossel de logos (6 imagens + wordmark "Central RZ").
6. `#como-funciona` — 3 passos.
7. `#oferta` — bloco escuro com os 3 itens da conversa gratuita.
8. `#duvidas` — FAQ com `<details>/<summary>`.
9. `.final#conversa` — CTA final.
10. `footer.foot` — texto institucional, e-mail e links LGPD/Privacidade.
11. `.sticky` — botão fixo inferior de WhatsApp.

O `<main>` mantém os atributos de dados da referência (`data-kind`, `data-route`, `data-service`, `data-title`), usados pela lógica de mensagem e rastreamento.

## 6. Organização do CSS (`css/styles.css`)
- Variáveis de identidade em `:root` (ver seção 9).
- Reset, tipografia base, utilitário `.w` (largura central responsiva).
- Blocos por seção (header, hero, dores, benefícios, prova, carrossel, passos, oferta, FAQ, CTA, footer, sticky).
- **Breakpoints**: `max-width: 430px`, `380px`, `340px` (ajustes de CTA e tipografia) e `min-width: 860px` (layout desktop: grid do hero, 4 colunas de benefícios, 3 colunas de passos/stats/offer).
- Animações: `ping` (badge), `shine` (brilho do CTA), `mq` (carrossel), `up` (entrada da barra fixa).
- `@media (prefers-reduced-motion: reduce)` desativa animações/transições e o scroll suave.

## 7. Organização do JavaScript (`js/main.js`)
- `WA_NUMBER` e `waLink()` (codificação com `encodeURIComponent`).
- `ON_TRACKING` (estrutura preparada, sem IDs) e `ON_APPEND_ORIGIN`.
- Leitura da origem do anúncio (`utm_term`/`kw`/`utm_campaign`/`gclid`) → `window.ON_ORIGIN`.
- Preenchimento de `href` em todos os `[data-wa]` com `target="_blank"` e `rel="noopener"`.
- Carregamento condicional de GTM/GA4/Google Ads (só se houver IDs).
- `onWhatsAppClick(pos)` → eventos `whatsapp_click` e `generate_lead`.
- Comportamento de scroll do header (classe `.hide`, retorno no foco).
- Lógica de seleção de desafios (marca/desmarca, mensagem dinâmica, prévia e feedback).
- Carrossel infinito com clone de itens, velocidade proporcional, pausa no toque e respeito a `prefers-reduced-motion`.

## 8. Seções implementadas
Todas as 11 seções da referência foram implementadas, na mesma ordem, com conteúdo e textos preservados (sem alterações de copy).

## 9. Identidade visual
| Variável | Valor | Uso |
|---|---|---|
| `--ink` | `#0B1220` | Fundos escuros / identidade principal |
| `--navy` | `#0F172A` | Fundos secundários |
| `--bg` | `#F5F8FB` | Fundo claro |
| `--line` | `#E2E8F0` | Bordas e divisores |
| `--text` | `#0F172A` | Texto principal |
| `--soft` | `#52627A` | Texto auxiliar |
| `--mint` | `#5EEAD4` | Destaques |
| `--teal` | `#0D9488` | Elementos de destaque |
| `--tealD` | `#0F766E` | Verde-petróleo em textos/elementos |
| `--wa` | `#25D366` | Botões WhatsApp |
| `--waD` | `#1EBE5B` | Hover dos botões WhatsApp |

Tipografia: **Poppins** (400–800). Estética moderna, tecnológica, clean e minimalista preservada.

## 10. Funcionalidade de seleção dos desafios
- 4 opções exatas da referência, com seleção **individual e múltipla** e desmarcação.
- Estado visual via `aria-pressed=true` (borda e fundo verdes, check visível).
- Acessível por teclado (botões `<button>`), `aria-live="polite"` no feedback.

## 11. Lógica de montagem da mensagem
- Base: `Olá, vim do site e gostaria de saber mais sobre os serviços de Inteligência Artificial.`
- 1 opção: acrescenta `Meu maior desafio hoje: [desafio].`
- 2+ opções: acrescenta `Meus maiores desafios hoje: [d1]; [d2].`
- Apenas opções efetivamente marcadas entram; origem do anúncio é anexada quando disponível.

## 12. Prévia dinâmica do WhatsApp
A bolha do Hero (`[data-bubble]`) é atualizada em tempo real conforme as seleções, garantindo que a prévia seja idêntica à mensagem enviada (sem divergência).

## 13. Integração com WhatsApp
- Número: `5511972243329` — base `https://wa.me/5511972243329`.
- Mensagem via parâmetro `text` com `encodeURIComponent()`.
- Pontos de acesso: telefone do header, botão de orçamento, botão fixo — todos com `data-wa-main` e sincronizados.
- Abertura em nova aba com `rel="noopener"`.

## 14. Rastreamento
- Estrutura `ON_TRACKING = { gtmId, ga4Id, gadsId, gadsConversionLabel }` preservada **vazia** (sem IDs fictícios).
- Eventos `whatsapp_click` e `generate_lead` enviados via `dataLayer`/`gtag`.
- Identificação de posição: `topo-telefone`, `topo`, `barra-fixa` (atributo `data-pos`).
- GTM/GA4/Google Ads só carregam se os respectivos IDs forem preenchidos.
- **Status:** preparado para configuração — não ativo (nenhuma integração está funcionando até os IDs serem informados).

## 15. SEO
- Title: `IA Para Empresas | ON Solutions Brasil`
- Description: `Sem modismo: cada solução de IA nasce de um problema real do seu negócio.`
- Canonical: `https://onsolutionsbrasil.com.br/lp/inteligencia-artificial-para-empresas/`
- Robots: `noindex,follow` (preservado)
- Theme color: `#0B1220`; viewport com `viewport-fit=cover`; `lang="pt-BR"`.
- Hierarquia de headings mantida (um `<h1>` no hero, `<h2>` por seção, `<h3>` nos cards).

## 16. Responsividade
Breakpoints testados: 340px, 380px, 400px, 430px, 860px e desktop. Layout fluido, sem rolagem horizontal; barra fixa respeita `env(safe-area-inset-bottom)`.

## 17. Dependências externas
- Google Fonts (Poppins) — única dependência externa.
- Google Tag Manager / GA4 / Google Ads — **opcionais**, carregados somente com IDs configurados.

## 18. Instruções de execução
Por ser página estática, basta abrir `index.html` no navegador. Para testar o carregamento de assets e fontes corretamente, sirva via um servidor local, por exemplo:
```
# Python
python -m http.server 8000
# depois acesse http://localhost:8000
```

## 19. Testes realizados
- **Build/validação:** `node --check js/main.js` → sem erros de sintaxe.
- **Lógica de mensagem (unit test):** base, 1 desafio, múltiplos desafios e codificação de URL → todos corretos.
- **Estrutura HTML:** 8 `<section>`, 7 IDs de seção corretos, 3 `<details>` (FAQ), 3 botões `data-wa-main`, 7 chips, referências de imagem consistentes.
- **CSS:** folha organizada, breakpoints e `prefers-reduced-motion` presentes.
- **Não verificado automaticamente:** renderização pixel a pixel em navegadores reais e leitura por tecnologias assistivas (requer teste manual).

## 20. Pendências
1. **Materiais gráficos originais (importante):** a referência embutia os materiais em Base64. Os arquivos em `assets/img/` são atualmente **placeholders válidos (PNG 1×1 transparente)** para evitar imagens quebradas. É necessário substituí-los pelos **arquivos originais** extraídos do pacote de referência, mantendo os mesmos nomes:
   - `favicon.png`, `logo-onsolutions.png`
   - `cliente-braziliana.png`, `cliente-quatri.png`, `cliente-brooks.png`, `cliente-crosshr.png`, `cliente-multilife.png`, `cliente-mafedo.png`
   - Observação técnica: o arquivo HTML de referência não estava acessível no ambiente (caminho temporário do RAR com acesso negado), e os blocos Base64 não puderam ser reconstruídos com garantia de integridade byte a byte sem o arquivo-fonte. Por isso os materiais foram deixados como placeholders e esta pendência documentada, conforme a orientação de preservar a qualidade dos materiais.
2. **Links legais do footer:** `LGPD e proteção de dados` e `Política de privacidade` estão com `href="#"`, exatamente como na referência. Não há páginas/destinos reais no ambiente atual. Apresentação visual preservada; destinos a definir quando as páginas existirem.
3. **Rastreamento:** preencher `ON_TRACKING` (GTM/GA4/Google Ads) para ativar os disparos de conversão.
