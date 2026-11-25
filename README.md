## Overview
This project provides a captive portal HTML page designed specifically for Mikrotik WiFi hotspots. It integrates with [MIKHMON V3](https://github.com/laksa19/mikhmonv3) for hotspot monitoring and management.

It is a static HTML/CSS/JS project (no build step required) and is intended to be hosted on your own web server/domain, then connected to your MikroTik hotspot flow.

## Included Pages
- `index.html` - main captive portal login page
- `qr.html` - QR voucher scanner page
- `status.html` - account status page
- `logout.html` - logout redirect page
- `api.html` - API redirect helper
- `xml/*` and `errors.txt` - MikroTik hotspot support files

## Replication Guide (for other developers)

### 1) Clone and host files
Deploy all repository files to your web host document root.

### 2) Replace project-specific domain values
This repo currently uses `kaybigan.hotspot` in several files. Replace it with your own hotspot/login domain:

- `index.html`  
  - `http://kaybigan.hotspot/login?...` (login submit URL)
- `qr.html`  
  - `string.match(/http:\/\/kaybigan\.hotspot\/login\?/);`
- `status.html`  
  - `location.replace('http://kaybigan.hotspot/status');`
  - `location.replace('http://kaybigan.hotspot/logout?erase-cookie=on');`
- `logout.html`  
  - `location.replace('http://kaybigan.hotspot/logout');`
- `api.html`  
  - `location.replace("http://kaybigan.hotspot/api.json");`

If your setup supports HTTPS end-to-end, use `https://` links consistently.

### 3) Configure MikroTik local hotspot pages
In MikroTik local `login.html`, redirect to your hosted portal domain:

```html
<script>
  window.location.replace("https://your-domain.example");
</script>
```

Current repo `login.html` uses:
```html
window.location.replace('/');
```
Update this to match your deployment strategy.

### 4) Configure walled garden
Allow required domains in MikroTik walled garden:
- Your portal host/domain (required)
- Any external services you keep enabled (example: Google AdSense scripts in `index.html`, `qr.html`, `status.html`)

If walled garden restrictions block external resources, remove/disable those external scripts.

### 5) Authentication behavior
- Login flow is URL-based to hotspot endpoints.
- The project currently uses HTTP PAP-style login flow.
- CHAP handling is not implemented in this portal.

## Notes
- Intended for MikroTik hotspot environments.
- Static project: no npm/pip/go build tools are required.
- Verify all hardcoded domain references before production use.

## License
See [LICENSE](LICENSE).

### Third-Party Licenses
This project includes and is a derivative work of the following open source projects:

- **jQuery**  
  Licensed under the MIT License. See [jQuery License](https://github.com/jquery/jquery/blob/main/LICENSE.txt).

- **Bootstrap 5**  
  Licensed under the MIT License. See [Bootstrap License](https://github.com/twbs/bootstrap/blob/main/LICENSE).

- **Mikhmon V3**  
  Licensed under the GNU GPL v2.0 License. See [Mikhmon V3 License](https://github.com/laksa19/mikhmonv3/blob/master/LICENSE).
  
- **Fontello**  
   Licensed under the MIT License. See [Fontello License](https://github.com/fontello/fontello/blob/master/LICENSE).
