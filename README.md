# Usage

```
version: "3"
services:
  frp:
    image: jackcvr/frp:latest
    network_mode: host
    volumes:
      - ./frp/frps.toml:/frp/frps.toml:ro
    command: [frps, -c, frps.toml]
    restart: always

  tcp-proxy:
    image: jackcvr/tcp-proxy:latest
    network_mode: host
    environment:
      BIND_PORT: 8000
      REMOTE_HOST: www.google.com
      REMOTE_PORT: 80
    restart: always

  endlessh:
    image: jackcvr/endlessh:latest
    network_mode: host
    volumes:
      - ./endlessh/endlessh.conf:/etc/endlessh.conf:ro
    command: [-f, /etc/endlessh.conf]
    restart: always
```
