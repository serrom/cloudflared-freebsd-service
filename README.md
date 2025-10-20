# cloudflared-freebsd-service

A minimal rc.d script to run Cloudflare Tunnel (cloudflared) as a service on FreeBSD.

## Installation

1. Copy the `cloudflared` script to `/usr/local/etc/rc.d/`.
2. Make it executable: `chmod +x /usr/local/etc/rc.d/cloudflared`.
3. Create the configuration file at `/usr/local/etc/cloudflared/config.yml` based on `config.yml.example`.
4. Enable the service: `service cloudflared enable`.
5. Start the service: `service cloudflared start`.

## Configuration

Edit `/usr/local/etc/cloudflared/config.yml` with your tunnel details.

Example:
```
tunnel: <your-tunnel-name>
credentials-file: /root/.cloudflared/<your-tunnel-id>.json
origincert: /root/.cloudflared/cert.pem

ingress:
  - hostname: <your-domain>
    service: http://127.0.0.1:80
  - service: http_status:404
```

## Requirements

- FreeBSD
- cloudflared installed (`pkg install cloudflared`)

## Log Rotation

Log rotation for `/var/log/cloudflared.log` is set up automatically on first start: the script adds the necessary entry to `/etc/newsyslog.conf` if not present.

The configuration rotates the log when it exceeds 1 MB, keeps 7 copies, compresses them, and signals the process using the PID file.

If needed, you can check or modify `/etc/newsyslog.conf` manually.