# Custom Domain Setup for GitHub Pages

## Your Domain: lifematika.link

### Step 1: Configure DNS Records

Go to your domain registrar (where you bought the domain) and add these DNS records:

#### Option A: Apex Domain (lifematika.link)

Add these **A records**:

```
Type: A
Name: @
Value: 185.199.108.153

Type: A
Name: @
Value: 185.199.109.153

Type: A
Name: @
Value: 185.199.110.153

Type: A
Name: @
Value: 185.199.111.153
```

#### Option B: www Subdomain (www.lifematika.link)

Add this **CNAME record**:

```
Type: CNAME
Name: www
Value: lifematika-creator.github.io
```

#### Recommended: Both apex and www

For best results, add BOTH:
- The 4 A records above (for lifematika.link)
- The CNAME record (for www.lifematika.link)
- Add a CNAME from `@` to `www.lifematika.link` OR keep the A records

### Step 2: Verify DNS (After Adding Records)

Wait 5-60 minutes for DNS propagation, then check:

```bash
# Check A records
dig lifematika.link +short

# Check CNAME
dig www.lifematika.link +short
```

You should see the GitHub IPs in the output.

### Step 3: Configure GitHub Pages

1. Go to your repository: https://github.com/lifematika-creator/lifematika.link
2. Go to **Settings** → **Pages**
3. Under **Custom domain**, enter: `lifematika.link`
4. Click **Save**
5. Wait a few minutes
6. Check **"Enforce HTTPS"** (recommended)

### Step 4: Commit and Push CNAME File

The CNAME file has been created in your repository. Now commit and push it:

```bash
git add CNAME
git commit -m "Add custom domain"
git push origin main
```

---

## Common DNS Providers

### Cloudflare
1. DNS → Add record
2. Type: A, Name: @, Content: (GitHub IPs)
3. Proxy status: DNS only (gray cloud)

### Namecheap
1. Advanced DNS
2. Add New Record
3. Type: A Record, Host: @, Value: (GitHub IPs)

### GoDaddy
1. DNS Management
2. Add → A
3. Name: @, Value: (GitHub IPs)

### Google Domains
1. DNS → Custom records
2. Type: A, Data: (GitHub IPs)

---

## Troubleshooting

### DNS not propagating
- Wait up to 24 hours (usually 5-30 minutes)
- Use https://www.whatsmydns.net/ to check propagation

### "Domain's DNS record could not be retrieved"
- Wait for DNS propagation
- Verify DNS records are correct
- Try removing and re-adding the custom domain

### Certificate errors (HTTPS)
- Wait 24 hours for certificate provisioning
- Uncheck and re-check "Enforce HTTPS"

### www vs apex
- Both should work if configured correctly
- GitHub will redirect one to the other

---

## Quick Commands

```bash
# Check DNS
dig lifematika.link +short
dig www.lifematika.link +short

# Alternative DNS check
nslookup lifematika.link
nslookup www.lifematika.link

# Check if site is live
curl -I https://lifematika.link
```

---

## Expected Timeline

1. DNS records added: **0 minutes**
2. DNS propagation: **5-60 minutes**
3. GitHub recognizes domain: **1-5 minutes after DNS**
4. HTTPS certificate: **0-24 hours**
5. Site fully live: **Within 1 hour typically**

---

**Need help?** Contact: [@valchalyi](https://t.me/valchalyi)

