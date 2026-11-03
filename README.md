# LP09 — Inteligência Artificial para Empresas | ON Solutions Brasil

Landing page estática (HTML5 + CSS3 + JavaScript puro) para o serviço de Inteligência Artificial para Empresas da ON Solutions Brasil, com foco em conversão via WhatsApp.

## Estrutura
```
index.html          Marcação da página
css/styles.css       Estilos e responsividade
js/main.js           Interações (WhatsApp, seleção de desafios, carrossel, header, rastreamento)
assets/img/          Imagens (favicon, logo e logos de clientes)
```

## Como executar
Abra `index.html` no navegador ou sirva localmente:
```
python -m http.server 8000
```
e acesse `http://localhost:8000`.

## Principais recursos
- Integração com WhatsApp (`wa.me/5511972243329`) com mensagem pré-preenchida e codificada.
- Seleção múltipla de desafios com mensagem dinâmica e prévia sincronizada no Hero.
- Carrossel infinito de clientes (respeita `prefers-reduced-motion`).
- Header que esconde/reaparece conforme a rolagem.
- Estrutura de rastreamento (GTM/GA4/Google Ads) preparada — ativa somente com IDs configurados.
- SEO preservado: `noindex,follow`, canonical, theme-color, Poppins.

## Pendências
Os arquivos em `assets/img/` são placeholders e devem ser substituídos pelos materiais originais.
Veja `DOCUMENTACAO-LP09-INTELIGENCIA-ARTIFICIAL-PARA-EMPRESAS.md` para detalhes.
