# Study Workspace landing page

Static landing page for `https://study-workspace.theodosiou.me`.
The application links point to `https://study.theodosiou.me`.

## Files

- `index.html`: page markup, styles and interactive demo.
- `img/`: product screenshots.
- `media/`: teaser video and poster.
- `deploy/study-landing.nginx.conf`: initial HTTP Nginx configuration.

## Deployment

No Node.js build or PM2 process is required. Nginx serves the static files
from `/var/www/study-landing/current` on the Ubuntu VM.

Create the upload bundle from the repository root:

```sh
tar -czf deploy/study-landing.tar.gz index.html img media
```

The generated archive is ignored by Git. Deploy only `index.html`, `img/`
and `media/` into the web root.

Before enabling the supplied Nginx configuration, check the existing virtual
hosts and DNS. Test with `nginx -t` before reloading Nginx. HTTPS must be
configured using the VM's certificate setup; the supplied configuration
currently listens on HTTP only. VM deployment and HTTPS setup are pending.
