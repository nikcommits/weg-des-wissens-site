# Cloudflare-Pages-Migration

Stand: 13. September 2026

## Pages-Konfiguration

- GitHub-Repository: `nikcommits/weg-des-wissens-site`
- Produktions-Branch: `main`
- Framework: Astro (statischer Export)
- Build-Befehl: `pnpm build`
- Build-Ausgabe: `dist`
- Root-Verzeichnis: `/`
- Pages-Projektname (vorgeschlagen): `weg-des-wissens-site`
- Erwartete Vorschau-URL: `https://weg-des-wissens-site.pages.dev`

Die frühere GitHub-Pages-Unterpfad-Konfiguration wurde in der vorhandenen, noch
nicht übernommenen Änderung an `astro.config.mjs` bereits entfernt. Das ist für
eine eigene Pages-Domain korrekt.

## DNS- und Mail-Backup vor Umstellung

Quelle: öffentliche DNS-Abfrage sowie webgo-Domainverwaltung am 13. September
2026. In der webgo-DNS-Zonenübersicht waren keine manuellen Subrecords sichtbar;
die unten aufgeführten Werte werden offenbar aus dem webgo-Hosting bereitgestellt.

| Name | Typ | Wert | TTL |
| --- | --- | --- | --- |
| `@` | A | `185.30.35.13` | 43200 |
| `www` | A | `185.30.35.13` | nicht ermittelt |
| `mail` | A | `185.30.35.13` | nicht ermittelt |
| `webmail` | A | `185.30.35.13` | nicht ermittelt |
| `autoconfig` | A | `185.30.35.13` | nicht ermittelt |
| `autodiscover` | A | `185.30.35.13` | nicht ermittelt |
| `@` | MX | `10 s312.goserver.host.` | 43200 |
| `@` | MX | `20 s312.goserver.host.` | 43200 |
| `@` | TXT | `google-site-verification=qbU5eoRdpkwIuzeDv7rNcXAaBpYrU3sWspm3dZNkCZ4` | 3600 |
| `@` | TXT | `SMTP.GOOGLE.COM` | 3600 |
| `@` | TXT (SPF) | `v=spf1 a mx ip4:37.17.224.0/21 ip4:185.30.32.0/22 ip4:88.82.224.0/19 ip4:45.153.56.0/22 ~all` | 3600 |
| `_dmarc` | TXT | `v=DMARC1; p=quarantine;` | nicht ermittelt |

Aktuelle autoritative Nameserver: `ns1.webgo.de`, `ns2.webgo.de`,
`ns3.webgo.de`, `ns4.webgo.de`.

## Geplanter Ablauf nach Freigabe

1. Cloudflare Pages mit dem vorhandenen GitHub-Repository verbinden und die
   oben genannten Build-Werte einrichten.
2. Den ersten Deployment-Build abwarten und `pages.dev` funktional prüfen.
3. `wegdeswissens.de` in Cloudflare als Zone hinzufügen und die gesicherten
   Mail-Einträge unverändert übernehmen. Mail-bezogene Records bleiben DNS-only.
4. Die von Cloudflare zugewiesenen Nameserver bei webgo eintragen. Die Domain
   bleibt dabei bei webgo registriert; weder Transfer noch Kündigung sind nötig.
5. Nach aktivierter Zone die Pages-Custom-Domain `wegdeswissens.de` (und
   `www.wegdeswissens.de` mit gewünschter Weiterleitung) verbinden und Web-
   DNS auf Pages umstellen.

Bis zur ausdrücklichen Freigabe erfolgen weder Cloudflare-/GitHub-Änderungen
noch DNS- oder Nameserver-Änderungen bei webgo.
