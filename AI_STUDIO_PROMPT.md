# BizFlow AI Catalog - Complete Generation Prompt for Google AI Studio

Copy everything below this line and paste into Google AI Studio to generate the complete app.

---

Create a complete React + Vite web application called "BizFlow AI Catalog" with the following specifications:

## Project Setup
- Framework: React 18.3.1 with Vite 5.4.0
- Language: JavaScript/JSX
- Build tool: Vite with @vitejs/plugin-react
- Type: ESM (module)
- Package manager: npm

## Core Features

### 1. Voice Search
- Implement Web Speech API for voice-to-text search functionality
- Add microphone button in search bar
- Display recognized text in real-time
- Support for common product searches

### 2. QR Code Scanning
- Use qr-scanner library for camera-based QR code scanning
- Add QR scanner button in navbar
- Scan products by QR code
- Navigate to product details when QR code is scanned

### 3. Product Catalog
- Display products in responsive grid layout
- Show product image, name, description, price
- Search functionality (text and voice)
- Filter by category
- Click to view product details
- Mobile-optimized card design

### 4. Admin Section
- Password-protected admin login (default password: "admin123")
- Add new products with form
- Edit existing products
- Delete products
- Manage product categories
- Set protection level for sensitive products

### 5. Protected Products
- Mark products as admin-only/protected
- Require password to view protected products
- Display badge on protected products
- Hide from public view until authenticated

## Data Management
- Use browser's localStorage for data persistence
- No backend required - all data stays on device
- Default starting products included in App.jsx
- Export product catalog as JSON
- Import catalog from JSON file
- Auto-save on every change

## PWA & Installation

### Files to Create:
1. **public/manifest.webmanifest** - PWA manifest with app details
2. **public/sw.js** - Service worker for offline support
3. **public/icon-192.png** - App icon 192x192px
4. **public/icon-512.png** - App icon 512x512px
5. **public/apple-touch-icon.png** - iOS app icon 180x180px

### Features:
- Enable "Add to Home Screen" on iOS and Android
- Full-screen mode when installed as app
- Theme color: #4A5CFF
- Works offline with cached assets
- Splash screen support

## UI/UX Design

### Theme
- Primary color: #4A5CFF (indigo)
- Secondary color: darker shade of indigo
- Accent color: derived from primary
- Text color: #333333
- Background: #FFFFFF

### Layout
- Mobile-first responsive design
- Support for phones, tablets, desktops
- Full-screen PWA capability
- No browser chrome when installed
- Smooth animations and transitions
- Touch-optimized buttons (44x44px minimum)

### Components
- Header with logo and nav
- Search bar with voice button
- QR scanner button
- Product grid/list
- Product detail modal
- Admin login page
- Admin dashboard
- Settings page

## Customization Points

### In src/App.jsx - Easy to modify:
```javascript
const BRAND = "BizFlow AI"; // Change to client's brand name

const DEFAULT_PRODUCTS = [
  // Replace with client's actual products
  { id: 1, name: "Product 1", description: "...", price: 99.99, category: "Electronics", protected: false },
  // ... more products
];

const C = {
  indigo: "#4A5CFF",        // Primary brand color
  indigoDeep: "#2E3AA0",    // Darker shade
  // Other colors derived from these
};
```

## Project Structure

```
bizflow-ai-catalog/
├── public/
│   ├── manifest.webmanifest    (PWA manifest)
│   ├── sw.js                    (Service worker)
│   ├── icon-192.png             (App icon)
│   ├── icon-512.png             (App icon)
│   └── apple-touch-icon.png     (iOS icon)
├── src/
│   ├── main.jsx                 (Entry point)
│   ├── App.jsx                  (Main app component)
│   ├── components/
│   │   ├── Header.jsx
│   │   ├── SearchBar.jsx
│   │   ├── ProductGrid.jsx
│   │   ├── ProductDetail.jsx
│   │   ├── AdminLogin.jsx
│   │   ├── AdminDashboard.jsx
│   │   └── QRScanner.jsx
│   └── styles/
│       └── App.css              (Global styles)
├── index.html
├── package.json
├── vite.config.js
└── README.md
```

## HTML Template

Use this exact HTML structure in index.html:

```html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover" />
    <title>BizFlow AI Catalog</title>
    <meta name="description" content="Product catalog with voice search and QR scanning" />
    <meta name="theme-color" content="#4A5CFF" />
    <link rel="manifest" href="/manifest.webmanifest" />
    <link rel="icon" href="/icon-192.png" />
    <link rel="apple-touch-icon" href="/apple-touch-icon.png" />
    <meta name="apple-mobile-web-app-capable" content="yes" />
    <meta name="apple-mobile-web-app-status-bar-style" content="black-translucent" />
    <style>
      html, body, #root { height: 100%; margin: 0; }
      body { -webkit-tap-highlight-color: transparent; overscroll-behavior-y: none; }
    </style>
  </head>
  <body>
    <div id="root"></div>
    <script type="module" src="/src/main.jsx"></script>
  </body>
</html>
```

## Package.json Configuration

```json
{
  "name": "bizflow-ai-catalog",
  "private": true,
  "version": "1.0.0",
  "type": "module",
  "scripts": {
    "dev": "vite",
    "build": "vite build",
    "preview": "vite preview"
  },
  "dependencies": {
    "react": "^18.3.1",
    "react-dom": "^18.3.1",
    "qr-scanner": "^1.4.2"
  },
  "devDependencies": {
    "@vitejs/plugin-react": "^4.3.1",
    "vite": "^5.4.0"
  }
}
```

## Vite Configuration

```javascript
import { defineConfig } from "vite";
import react from "@vitejs/plugin-react";

export default defineConfig({
  plugins: [react()],
});
```

## Key Features Implementation

### Voice Search
- Use Web Speech API (SpeechRecognition)
- Show listening state with visual feedback
- Display recognized text
- Auto-search on speech end
- Fallback for unsupported browsers

### QR Scanning
- Use qr-scanner library
- Request camera permission
- Display live camera feed
- Highlight detected QR codes
- Parse product IDs from QR codes

### Admin Authentication
- Simple password validation (localStorage-based)
- Show/hide admin features based on login state
- Session management (logout functionality)
- Secure password entry field

### Product Management
- CRUD operations (Create, Read, Update, Delete)
- Form validation
- Image upload (base64 or URL)
- Category management
- Stock/quantity tracking optional

## Additional Requirements

### Error Handling
- Handle camera permission denied
- Handle speech recognition errors
- Handle storage quota exceeded
- User-friendly error messages

### Performance
- Optimize images
- Lazy load product images
- Minimize re-renders
- Efficient localStorage usage

### Accessibility
- Semantic HTML
- ARIA labels
- Keyboard navigation
- Color contrast compliance
- Screen reader support

### Testing Considerations
- Test on iOS Safari
- Test on Android Chrome
- Test offline functionality
- Test "Add to Home Screen" installation

## Deployment

This is a static site - no backend required:
1. Push to GitHub repo: hpgamer90/bizflow-ai-catalog
2. Deploy to Vercel.com (auto-detects Vite)
3. Get URL like client-name.vercel.app
4. Each client gets separate instance
5. Can attach custom domain in Vercel settings

## Notes for AI Studio

- Make the app production-ready
- Include comprehensive error handling
- Add loading states where appropriate
- Use modern CSS (flexbox, grid)
- Keep code modular and maintainable
- Add inline comments for customization points
- Include a clear README with setup and customization instructions
- Make sure service worker properly caches app shell and assets
- Ensure responsive design works on all screen sizes from 320px to 2560px

---

**Ready to generate? Paste this entire prompt into Google AI Studio now!**
