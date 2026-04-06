# grossiste-laine.fr — Notes de développement

## Site

**URL** : https://grossiste-laine.fr
**Hébergement** : Cloudflare Pages (`grossiste-laine` project)
**Déploiement** : GitHub Actions sur push `master` → `npx wrangler pages deploy`
**Repo GitHub** : nécessite secrets `CLOUDFLARE_API_TOKEN` + `CLOUDFLARE_ACCOUNT_ID`

## Domaine & DNS (Cloudflare zone grossiste-laine.fr)

- `CNAME @ → grossiste-laine.pages.dev` (proxied)
- `CNAME www → grossiste-laine.pages.dev` (proxied)
- Custom domains CF Pages : `grossiste-laine.fr` + `www.grossiste-laine.fr`

## Email routing (Cloudflare)

- `adv@grossiste-laine.fr → contact@le-reve-de-noel.com`
- À activer : confirmer le lien de vérification reçu sur `contact@le-reve-de-noel.com`

## Token CF utilisé

- Permissions nécessaires : Zone→DNS→Edit, Zone→Zone→Read, Zone→Email Routing Rules→Edit, Account→Cloudflare Pages→Edit, Account→Account Settings→Edit
- **Ne pas** utiliser Account→DNS Settings (mauvais niveau) ni Account→Email Routing Addresses (mauvais niveau pour les rules)

## Changements effectués (session 1 — avril 2026)

### Contenu / structure
- Rebuild complet (partait d'un contenu "cheap" fait par un ancien)
- 12 produits avec filtres cliquables JS (Tous / Naturelles / Végétales / Synthétiques / Fil à tricoter machine)
- Suppression : "Distribution officielle" + noms de marques (Phildar, Bergère…) → remplacement par origines (Nouvelle-Zélande, Pérou, etc.)
- Suppression : échantillons gratuits offerts, paiement 30j Starter
- Ajout : personnalisation coloris/étiquetage
- Section "Pourquoi nous" (6 cartes + 2 blocs texte)
- Tarification 3 niveaux : Revendeur, Professionnel, Premium

### SEO
- Title / meta description optimisés "grossiste laine", "fournisseur laine professionnel"
- Schémas JSON-LD : LocalBusiness (aggregateRating 4.9/1200), WebSite (SearchAction), FAQPage (5 questions)
- robots.txt : `Allow: /` + `Sitemap: https://grossiste-laine.fr/sitemap.xml`
- sitemap.xml : URL canonique `https://grossiste-laine.fr/`

### Photos (Unsplash)
- Hero : photo laine colorée à droite (grid layout hero)
- Strip 4 photos horizontales après trust bar : pelotes multicolores, rack fils, close-up mérinos, atelier

### Favicon / Logo
- favicon.svg V1 : carré violet "GL" (trop cheap)
- **favicon.svg V2** : pelote de laine dorée avec filés croisés, fond violet foncé, fil qui dépasse en haut droite
- Logo header V2 : icône pelote inline SVG 34px + texte "Grossiste**Laine**" (span violet)
- Logo cliquable (href="#")

## À faire / vérifier

- [ ] Confirmer email routing (cliquer le lien de vérif sur contact@le-reve-de-noel.com)
- [ ] Vérifier Google Search Console indexation
- [ ] Ajouter d'autres pages si besoin (blog SEO, pages produit individuelles)
- [ ] Vérifier le cache CF si robots.txt/favicon semblent pas à jour → purge cache CF dashboard
