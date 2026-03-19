# widgeterian.com

Personal homepage served via GitHub Pages from a custom domain.

## GitHub Pages Setup

1. Create a repository named `widgeterian.com` under your GitHub account (`grishick`).
2. Push this code to the `main` branch.
3. Go to **Settings → Pages** in the repository.
4. Under **Source**, select **Deploy from a branch** → `main` / `/ (root)`.
5. Under **Custom domain**, enter `widgeterian.com` and save.
6. Check **Enforce HTTPS** once DNS has propagated.

## Route 53 DNS Setup

In your Route 53 hosted zone for `widgeterian.com`, create the following records:

### Apex domain (`widgeterian.com`)

Create **four A records** pointing to GitHub Pages IPs:

| Type | Name            | Value             |
|------|-----------------|-------------------|
| A    | widgeterian.com | 185.199.108.153   |
| A    | widgeterian.com | 185.199.109.153   |
| A    | widgeterian.com | 185.199.110.153   |
| A    | widgeterian.com | 185.199.111.153   |

### www subdomain

| Type  | Name                | Value             |
|-------|---------------------|-------------------|
| CNAME | www.widgeterian.com | grishick.github.io |

### Verification (if prompted by GitHub)

GitHub may ask you to add a TXT record for domain verification under your **account settings → Pages → Verified domains**. Follow the instructions there.

## Deployment

```bash
git init
git add .
git commit -m "Initial homepage"
git remote add origin git@github.com:grishick/widgeterian.com.git
git branch -M main
git push -u origin main
```

The site will be live at https://widgeterian.com after DNS propagation (up to 48 hours, usually minutes).
