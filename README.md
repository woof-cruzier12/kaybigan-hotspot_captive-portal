## Overview

This project provides a captive portal HTML page designed specifically for Mikrotik WiFi hotspots. It integrates with **Mikhmon V3** for hotspot monitoring and management.

## Features

- **Captive Portal**: Custom landing page (`index.html`) for WiFi login.
- **Mikhmon V3 Integration**: Monitor and manage hotspot users.
- **HTTPS Support**: Files are suitable for HTTPS connections (ensure your domain is whitelisted in the Mikrotik walled garden).
- **Google AdSense**: Provisional support for displaying ads.
- **First Stable Version**: Initial release for production use.

## Usage

1. **Deploy the HTML files** to your hosted domain's web server.
    - For Mikrotik local `login.html`, set up a redirection using:
      ```html
      <script>
         window.location.replace("https://www.yourdomain.com");
      </script>
      ```
2. **Enable walled garden** for your domain to allow access over HTTPS.
3. **Authentication**: Uses HTTP PAP (CHAP challenge is not supported).

## Notes

- This portal is intended for Mikrotik WiFi hotspots only.
- The project was initially planned as a Login+blog, but development was discontinued.
- Ensure your Mikrotik hotspot is configured to redirect users to `index.html` for login.

## License

See [LICENSE](LICENSE) for details.