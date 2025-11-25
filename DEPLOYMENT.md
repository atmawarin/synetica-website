# GitHub Pages Deployment Guide

This guide explains how to deploy the Synetica website to GitHub Pages and configure a custom domain.

## Step 1: Enable GitHub Pages

1. Go to your repository on GitHub: `https://github.com/atmawarin/synetica-website`
2. Click on **Settings** tab
3. Scroll down to **Pages** in the left sidebar
4. Under **Source**, select:
   - **Source**: `GitHub Actions` (this will use the workflow we created)
5. Save the settings

## Step 2: Configure Custom Domain

### Option A: Using GitHub Pages Settings (Recommended)

1. In the **Pages** settings, scroll to **Custom domain**
2. Enter your domain (e.g., `synetica.com` or `www.synetica.com`)
3. Check **Enforce HTTPS** (recommended)
4. GitHub will automatically create/update the `CNAME` file

### Option B: Manual CNAME File

1. Edit the `CNAME` file in the repository root
2. Replace the placeholder with your domain (one domain per line)
3. Commit and push the changes

## Step 3: Configure DNS Records

You need to configure DNS records with your domain provider. Choose one of these options:

### Option 1: Apex Domain (e.g., synetica.com)

Add these A records pointing to GitHub Pages IPs:
```
Type: A
Name: @ (or leave blank)
Value: 185.199.108.153
TTL: 3600 (or default)

Type: A
Name: @ (or leave blank)
Value: 185.199.109.153
TTL: 3600

Type: A
Name: @ (or leave blank)
Value: 185.199.110.153
TTL: 3600

Type: A
Name: @ (or leave blank)
Value: 185.199.111.153
TTL: 3600
```

### Option 2: Subdomain (e.g., www.synetica.com)

Add a CNAME record:
```
Type: CNAME
Name: www
Value: atmawarin.github.io
TTL: 3600 (or default)
```

**Note**: GitHub Pages IPs may change. Check the latest IPs at: https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site#configuring-an-apex-domain

## Step 4: Verify DNS Propagation

After configuring DNS, wait for propagation (can take a few minutes to 48 hours). Verify with:

```bash
# For apex domain
dig synetica.com +noall +answer

# For subdomain
dig www.synetica.com +noall +answer
```

Or use online tools:
- https://dnschecker.org
- https://www.whatsmydns.net

## Step 5: Enable HTTPS

1. After DNS is configured and verified, go back to GitHub Pages settings
2. The **Enforce HTTPS** checkbox should become available
3. Check it to enable SSL/TLS for your custom domain
4. GitHub will automatically provision an SSL certificate via Let's Encrypt

## Step 6: Deploy

The GitHub Actions workflow will automatically deploy when you push to `main` branch. To manually trigger:

1. Go to **Actions** tab in your repository
2. Select **Deploy to GitHub Pages** workflow
3. Click **Run workflow**

## Troubleshooting

### Site not loading
- Check DNS propagation (Step 4)
- Verify CNAME file exists and has correct domain
- Check GitHub Actions workflow for errors

### HTTPS not working
- Wait 24 hours after DNS configuration
- Ensure DNS is fully propagated
- Try unchecking and rechecking "Enforce HTTPS"

### 404 errors
- Verify `index.html` is in the repository root
- Check GitHub Pages source is set to `GitHub Actions`
- Review workflow logs in Actions tab

## Testing Locally

Before deploying, test locally:

```bash
# Using Python
python3 -m http.server 8000

# Using Node.js (if you have http-server installed)
npx http-server

# Then visit http://localhost:8000
```

## Additional Resources

- [GitHub Pages Documentation](https://docs.github.com/en/pages)
- [Custom Domain Setup](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site)
- [GitHub Actions for Pages](https://github.com/actions/deploy-pages)

