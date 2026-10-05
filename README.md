# tinkeredtactile-redirect

Tiny GitHub Pages site that redirects `tinkeredtactile.com` (and any path
under it) to `https://randomstringofwords.com/tinkered-tactile/`, the
Tinkered Tactile maker site that lives inside the RSOW Jekyll repo. Same
approach as `rsow-redirect`: Namecheap's URL Forwarding is HTTP-only, and
GitHub Pages provides Let's Encrypt for the custom domain, so HTTPS works.

## How it works

- `index.html` does a JS `location.replace` to `/tinkered-tactile/`
  (keeping any query string and hash) plus a meta-refresh fallback for
  no-JS clients.
- `404.html` is a copy of `index.html`, so any other path (old Wix links
  like `/shop`) lands on the same page instead of a GitHub 404. Paths are
  not preserved on purpose: none of the old Wix paths exist on the new site.
- `CNAME` binds the site to `tinkeredtactile.com` for GitHub Pages.

## DNS (set at Namecheap)

Nameservers: Namecheap BasicDNS. Apex `tinkeredtactile.com` A records →
GitHub Pages IPs:

```
185.199.108.153
185.199.109.153
185.199.110.153
185.199.111.153
```

`www.tinkeredtactile.com` CNAME → `palamedes.github.io`
