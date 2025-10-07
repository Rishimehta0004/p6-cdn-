# Performance testing your CDN practical

This document includes quick steps to measure site performance after you've pushed your practical to GitHub and deployed/served it locally or on a host that supports HTTPS and HTTP/2.

1) Lighthouse (Chrome)
- Open Chrome and visit your site (example: https://localhost or your deployed URL).
- Open DevTools → Lighthouse → Generate report.
- Choose categories (Performance, Accessibility, Best Practices) and run.

2) Lighthouse CLI
```bash
# install
npm install -g lighthouse
# run against a public https URL
lighthouse https://your-site.example.com --output html --output-path ./lighthouse-report.html
```

3) wrk (load-testing)
- wrk is a light-weight HTTP benchmarking tool. Example command:
```bash
wrk -t4 -c100 -d30s https://your-site.example.com/
```
- This runs for 30s with 4 threads and 100 concurrent connections.

4) WebPageTest
- Visit https://webpagetest.org and run a test from a chosen location and browser. Compare first-byte time and visual metrics.

Notes
- For accurate HTTP/2 measurements ensure your server supports TLS (HTTPS) and HTTP/2.
- If testing locally, you can use the provided `certs/server.crt` and `certs/server.key` with your server to enable HTTPS.
