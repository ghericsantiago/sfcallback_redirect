# Salesforce Connected App Callback Redirect

A simple GitHub Pages site that serves as a callback page for Salesforce connected apps. This page handles OAuth redirects by accepting a `state` parameter and redirecting users to the specified URL.

## How It Works

1. Salesforce connected app redirects users to this callback page with a query parameter
2. The page extracts the `state` parameter from the query string
3. The URL is validated for security
4. Users are automatically redirected to the provided URL

## Usage

### Basic Redirect
```
https://[your-username].github.io/sfcallback_redirect/?state=https://example.com/callback
```

### With Additional Parameters
Any query parameters besides `state` will be automatically passed to the target website:
```
https://[your-username].github.io/sfcallback_redirect/?state=https://example.com/callback&code=abc123&token=xyz789
```
This will redirect to: `https://example.com/callback?code=abc123&token=xyz789`

### With URL Encoding
If your redirect URL or parameters contain special characters, make sure to URL-encode them:
```
https://[your-username].github.io/sfcallback_redirect/?state=https%3A%2F%2Fexample.com%2Fcallback&token=abc%2B123%3D
```

## Salesforce Connected App Configuration

When setting up a Salesforce connected app, configure the callback URLs as:
```
https://[your-username].github.io/sfcallback_redirect/?state=[your-final-redirect-url]
```

## Features

- ✅ URL validation (prevents invalid redirect attempts)
- ✅ User-friendly error messages
- ✅ Loading indicator during redirect
- ✅ Responsive design
- ✅ No external dependencies
- ✅ Works on all modern browsers

## Deployment

This repository is ready to be deployed to GitHub Pages:

1. Push the repository to GitHub
2. Go to **Settings** > **Pages**
3. Select **Deploy from a branch**
4. Choose the branch and root folder (or `/docs` if using a subdirectory)
5. Your site will be available at `https://[your-username].github.io/sfcallback_redirect/`

## Security Notes

- The page validates URLs before redirecting
- Query parameters are logged only in the browser console for debugging
- In production, consider:
  - Whitelisting allowed redirect domains
  - Implementing CORS headers if needed
  - Using HTTPS only (GitHub Pages provides this automatically)

## Error Handling

If an invalid or missing `state` is provided, the user will see an error message explaining:
- If no redirect URL was provided
- If the redirect URL format is invalid

## Browser Support

Works on all modern browsers (Chrome, Firefox, Safari, Edge) and supports mobile devices.

## Contributing

Feel free to submit issues or pull requests to improve this callback page.

## License

MIT
