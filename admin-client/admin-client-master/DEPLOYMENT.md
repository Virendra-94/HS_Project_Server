# Deployment Configuration for React Router

This project includes multiple configuration files to handle client-side routing on different hosting platforms.

## Configuration Files

### For Netlify
- `_redirects` - Redirects all routes to index.html
- `netlify.toml` - Alternative Netlify configuration

### For Vercel
- `vercel.json` - Rewrites all routes to index.html

### For Apache Servers
- `.htaccess` - Apache rewrite rules

### For Static Hosting (Render, Surge.sh, etc.)
- `static.json` - Rewrites all routes to index.html

## How It Works

When a user refreshes a page like `/products` or `/offers`, the browser makes a direct request to the server for that path. Since these are client-side routes handled by React Router, the server doesn't have physical files for these paths.

These configuration files tell the server: "For any request that doesn't match a physical file, serve the `index.html` file instead." This allows React Router to handle the routing on the client side.

## Deployment Steps

1. Build the project: `npm run build`
2. Deploy the `build` folder to your hosting service
3. Ensure the appropriate configuration file is recognized by your hosting platform

## Troubleshooting

If you're still getting 404 errors on refresh:

1. Check which hosting platform you're using
2. Verify the correct configuration file is in your build folder
3. Some platforms may require specific file names or locations
4. Check your hosting platform's documentation for SPA routing configuration

## Alternative Solution

If server configuration doesn't work, you can switch to HashRouter in `src/App.js`:

```javascript
import { HashRouter as Router } from 'react-router-dom';
```

This will make URLs look like `yoursite.com/#/products` but will work without server configuration.
