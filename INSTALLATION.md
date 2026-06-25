# PII Document Redactor - Installation & Deployment Guide

## 📦 Installation

### Option 1: Local Use (Recommended for Privacy)

#### Requirements
- Any modern web browser (Chrome, Firefox, Safari, Edge)
- No server or backend required
- No installation needed

#### Steps
1. Download `index.html` from repository
2. Open file in web browser (File → Open or drag-drop)
3. Start using immediately

#### Windows
```bash
# Method 1: Direct open
1. Right-click index.html
2. Open with → Chrome (or your browser)

# Method 2: Drag and drop
1. Drag index.html into browser window
```

#### macOS
```bash
# Method 1: Finder
1. Double-click index.html
2. Opens in default browser

# Method 2: Terminal
open index.html

# Method 3: Drag and drop
1. Drag index.html into browser
```

#### Linux
```bash
# Method 1: File manager
1. Double-click index.html

# Method 2: Terminal
xdg-open index.html  # GNOME/KDE
firefox index.html   # Firefox

# Method 3: Direct browser
1. Drag into browser
```

### Option 2: Local Server (Recommended for Organization)

#### Using Python
```bash
# Python 3.x
python -m http.server 8000

# Python 2.x
python -m SimpleHTTPServer 8000

# Then visit: http://localhost:8000
```

#### Using Node.js
```bash
# Install http-server globally
npm install -g http-server

# Run from directory with index.html
http-server

# Then visit: http://localhost:8080
```

#### Using PHP
```bash
# PHP 5.4+
php -S localhost:8000

# Then visit: http://localhost:8000
```

#### Using Ruby
```bash
# Ruby 1.9+
ruby -run -ehttpd . -p8000

# Then visit: http://localhost:8000
```

### Option 3: Web Hosting (Organization Deployment)

#### Requirements
- Web hosting with HTTPS support
- Any web server (Apache, Nginx, IIS, etc.)
- Recommended: Security headers

#### Steps
1. Upload `index.html` to web server
2. Access via `https://your-domain.com/index.html`
3. Configure security headers (see below)

#### Security Headers (Apache .htaccess)
```apache
# Enable HTTPS only
Header set Strict-Transport-Security "max-age=31536000; includeSubDomains"

# Content Security Policy
Header set Content-Security-Policy "default-src 'self'; script-src 'self' https://cdn.jsdelivr.net; style-src 'self' 'unsafe-inline'"

# X-Frame-Options
Header set X-Frame-Options "DENY"

# X-Content-Type-Options
Header set X-Content-Type-Options "nosniff"

# Referrer Policy
Header set Referrer-Policy "no-referrer"
```

#### Security Headers (Nginx)
```nginx
# In server block
add_header Strict-Transport-Security "max-age=31536000; includeSubDomains" always;
add_header Content-Security-Policy "default-src 'self'; script-src 'self' https://cdn.jsdelivr.net" always;
add_header X-Frame-Options "DENY" always;
add_header X-Content-Type-Options "nosniff" always;
add_header Referrer-Policy "no-referrer" always;
```

## 🔐 Security Configuration

### HTTPS Requirement
```
✅ MUST use HTTPS for organization deployments
❌ HTTP not recommended for sensitive data
```

### SSL/TLS Certificate
Options:
- Let's Encrypt (free)
- Commercial certificate
- Self-signed (testing only)

### Example: Let's Encrypt with Certbot
```bash
# Install Certbot
sudo apt-get install certbot python3-certbot-apache

# Get certificate
sudo certbot --apache -d your-domain.com

# Auto-renewal
sudo systemctl enable certbot.timer
```

## 🗄️ Deployment Scenarios

### Scenario 1: Individual Use
```
Use: Local file opening
Security: ✅ High (no network transmission)
Setup: None required
Cost: $0
```

### Scenario 2: Small Team (5-10 people)
```
Use: Shared network folder or local server
Security: ✅ High (internal network)
Setup: Network share or simple HTTP server
Cost: $0-20/month
```

### Scenario 3: Organization (100+ people)
```
Use: Web-hosted with authentication
Security: ✅ Very High (HTTPS + auth + logging)
Setup: Web server with security headers
Cost: $20-100/month
```

### Scenario 4: Enterprise
```
Use: Integrated with document management
Security: ✅ Enterprise (audit, access control)
Setup: Custom integration + logging
Cost: Custom pricing
```

## 🔧 Configuration Options

### Self-Hosted Checklist
- [ ] HTTPS enabled
- [ ] Security headers configured
- [ ] Access logging enabled
- [ ] Automatic backups configured
- [ ] Monitoring in place
- [ ] Documentation created
- [ ] User training completed

### Browser Configuration

#### Recommended Settings
```
JavaScript: ✅ Enabled (required for OCR)
WebAssembly: ✅ Enabled (required for OCR)
Cookies: ❌ Disabled (not needed)
Plugins: ❌ Disabled (not used)
LocalStorage: ❌ Disabled (no persistent storage)
```

## 📊 Deployment Architecture

### Individual
```
┌─────────────┐
│   Browser   │
│ index.html  │
└─────────────┘
     Local File
```

### Small Team
```
┌──────────────┐
│ Local Server │
│ index.html   │
└──────────────┘
     Shared Network
   ┌─────────────────────────┐
   ├─→ User 1 Browser
   ├─→ User 2 Browser
   └─→ User 3 Browser
```

### Organization
```
┌──────────────────────────────────┐
│    Web Server (HTTPS)            │
│    index.html + Security Headers │
└──────────────────────────────────┘
         Internet
   ┌─────────────────────────────┐
   ├─→ Office Users
   ├─→ Remote Users
   └─→ Mobile Users
```

## 📋 System Requirements

### Minimum
- Processor: 1 GHz dual-core
- RAM: 2 GB
- Browser: Chrome 90+, Firefox 88+
- Disk: 50 MB (includes OCR models)
- Network: For CDN access (Tesseract)

### Recommended
- Processor: 2+ GHz quad-core
- RAM: 4+ GB
- Browser: Latest version
- Disk: 200 MB free
- Network: High-speed internet for first run

## 🌐 Network Considerations

### First Run
- Downloads Tesseract.js (via CDN)
- Model files (~50 MB)
- One-time download, then cached

### Subsequent Runs
- Uses cached models
- Minimal network usage
- Can work offline after caching

### Offline Mode
```
Not fully supported yet, but:
1. Download all CDN files first
2. Host locally
3. Update CDN URLs in HTML
```

## 🚀 Performance Optimization

### For Web Server
```
1. Enable gzip compression
2. Set cache headers
3. Use CDN for dependencies
4. Minimize CSS/JS (optional)
```

### Apache Configuration
```apache
<IfModule mod_deflate.c>
    AddOutputFilterByType DEFLATE text/html
    AddOutputFilterByType DEFLATE application/javascript
    AddOutputFilterByType DEFLATE text/css
</IfModule>

<IfModule mod_expires.c>
    ExpiresActive On
    ExpiresByType text/html "access plus 1 day"
    ExpiresByType application/javascript "access plus 30 days"
</IfModule>
```

### Nginx Configuration
```nginx
gzip on;
gzip_types text/html application/javascript text/css;

expires 1d;
add_header Cache-Control "public, max-age=86400";
```

## 📊 Monitoring & Logging

### What to Monitor
- Access logs
- Error logs
- Usage patterns
- Performance metrics

### Apache Logs
```bash
# Access log
tail -f /var/log/apache2/access.log

# Error log
tail -f /var/log/apache2/error.log
```

### Nginx Logs
```bash
# Access log
tail -f /var/log/nginx/access.log

# Error log
tail -f /var/log/nginx/error.log
```

## 🔄 Update Process

### Updating Files
1. Download latest `index.html`
2. Backup current version
3. Replace with new version
4. Test in staging
5. Deploy to production

### Version Control (Git)
```bash
# Clone repository
git clone https://github.com/vivek1350/pii_redaction.git

# Pull latest updates
cd pii_redaction
git pull origin main

# Deploy
cp index.html /var/www/html/
```

## 🔒 Access Control

### Basic Authentication (Apache)
```apache
<Directory /var/www/html/pii_redactor>
    AuthType Basic
    AuthName "PII Redactor"
    AuthUserFile /etc/apache2/.htpasswd
    Require valid-user
</Directory>
```

### Create Password File
```bash
htpasswd -c /etc/apache2/.htpasswd username
# Enter password when prompted
```

## 📱 Mobile Deployment

### iOS
1. Add to Home Screen (Safari)
2. Works like native app
3. Offline access after first load

### Android
1. Chrome → Menu → Add to Home Screen
2. Works like native app
3. Offline access after first load

## 🐛 Troubleshooting Deployment

### CDN Access Issues
```
Problem: Tesseract.js not loading
Solution:
1. Check internet connection
2. Check firewall rules
3. Host libraries locally if CDN blocked
```

### HTTPS Issues
```
Problem: Mixed content warning
Solution:
1. All resources must be HTTPS
2. Update CDN URLs to https://
3. Check Content-Security-Policy
```

### Performance Issues
```
Problem: Application slow on deployment
Solution:
1. Enable compression
2. Check server resources
3. Monitor network latency
4. Consider caching headers
```

## 📋 Deployment Checklist

- [ ] Source files downloaded/cloned
- [ ] HTTPS certificate installed
- [ ] Security headers configured
- [ ] Access logging enabled
- [ ] Performance optimized (compression, caching)
- [ ] Tested on supported browsers
- [ ] Tested on mobile devices
- [ ] Documentation updated
- [ ] User training provided
- [ ] Backup strategy established
- [ ] Monitoring configured
- [ ] Update process documented

## 📚 Additional Resources

- [Mozilla Web Security](https://developer.mozilla.org/en-US/docs/Web/Security)
- [OWASP Guidelines](https://owasp.org/)
- [Let's Encrypt](https://letsencrypt.org/)
- [Apache Documentation](https://httpd.apache.org/)
- [Nginx Documentation](https://nginx.org/)

---

**Version**: 1.0  
**Last Updated**: June 25, 2026
