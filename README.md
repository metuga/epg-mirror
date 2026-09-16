# Espelho EPG descomprimido

Publica uma lista EPG XMLTV em XML puro, para aplicacoes que nao suportam `.gz`.

- **Origem:** <https://JohnPulse.github.io/iptv-epg/epg-strong8k.xml.gz> (2,2 MB gzip)
- **Resultado:** `https://<utilizador>.github.io/<repo>/epg.xml` (~34 MB de XML)

Um workflow do GitHub Actions descarrega o `.gz`, descomprime-o e publica o XML
no GitHub Pages duas vezes por dia. O ficheiro **nao** e commitado: vai como
artefacto do Pages, senao o repositorio crescia dezenas de MB por dia.

## Mudar a origem ou o horario

Ambos em `.github/workflows/mirror-epg.yml`: o URL no `curl`, o `cron` em UTC.

## Atualizar a qualquer momento

Separador **Actions** -> *Espelhar EPG descomprimido* -> **Run workflow**.

O job falha de proposito se o XML vier com menos de 1 MB ou sem a etiqueta
final `</tv>`, para nao publicar um ficheiro truncado por cima de um bom.
