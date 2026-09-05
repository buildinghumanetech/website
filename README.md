# buildinghumanetech.com

Static one-page site. No build step, no framework, no dependencies.
`index.html` is the whole site: CSS is inline, the logo is inline SVG,
the only external request is Google Fonts (Lora).

## Files

| File | Purpose |
|---|---|
| `index.html` | The site |
| `CNAME` | Custom domain for GitHub Pages. Must contain exactly `buildinghumanetech.com` |
| `favicon.svg` / `favicon.png` / `apple-touch-icon.png` | Icons |
| `og.png` | 1200x630 social preview card |
| `robots.txt`, `sitemap.xml` | Crawling |

## Editing

Open `index.html` and edit the text. There is nothing to compile.
Commit to `main` and GitHub Pages redeploys in about a minute.

## Deploy (GitHub Pages)

1. Create a public repo at `github.com/buildinghumanetech/website`
2. Upload every file in this folder to the repo root
3. Settings -> Pages -> Source: `Deploy from a branch`, branch `main`, folder `/ (root)`
4. Wait for the green check, then open `https://buildinghumanetech.github.io/website`
5. Settings -> Pages -> Custom domain -> `buildinghumanetech.com` -> Save
6. Set DNS (see below), then tick **Enforce HTTPS** once the certificate is issued

## DNS

Apex `buildinghumanetech.com` -> four A records:

    185.199.108.153
    185.199.109.153
    185.199.110.153
    185.199.111.153

And optionally AAAA:

    2606:50c0:8000::153
    2606:50c0:8001::153
    2606:50c0:8002::153
    2606:50c0:8003::153

`www` -> CNAME -> `buildinghumanetech.github.io`

If the domain is on Cloudflare, set these as DNS-only (grey cloud) until
GitHub issues the certificate, then you may enable the proxy.

Verify current DNS before changing anything:

    dig +short buildinghumanetech.com
    dig +short www.buildinghumanetech.com
