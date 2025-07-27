## Overview
This project provides a captive portal HTML page designed specifically for Mikrotik WiFi hotspots. It integrates with **Mikhmon V3** for hotspot monitoring and management.

## Features

- **Captive Portal**: Custom landing page (`index.html`) for WiFi login.
- **Mikhmon V3 Integration**: Monitor and manage hotspot users.
- **QR Code Support**: Includes QR code login functionality using Mikhmon QR reader code. The system automatically scans for valid matches for your domain and rejects unsupported QR codes. To customize this behavior, modify the `string.match()` script located in `qr.html`.
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