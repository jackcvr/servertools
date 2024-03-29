# Usage

```
version: "3"
services:
  frp:
    image: jackcvr/frp:latest
    network_mode: host
    volumes:
      - ./frp/frps.toml:/frp/frps.toml:ro
    restart: always
    command: [frps, -c, frps.toml]

  tcp-proxy:
    image: jackcvr/tcp-proxy:latest
    network_mode: host
    restart: always
    environment:
      BIND_PORT: 8000
      REMOTE_HOST: www.google.com
      REMOTE_PORT: 80

  endlessh:
    image: jackcvr/endlessh:latest
    network_mode: host
    volumes:
      - ./endlessh/endlessh.conf:/etc/endlessh.conf:ro
    restart: always
    command: [-f, /etc/endlessh.conf]

  socat:
    image: jackcvr/socat:latest
    network_mode: host
    volumes:
      - /dev:/dev
    restart: always
    command: [pty-tcp-serve, /dev/vpty0, "9000", -d, -d]
    # command: [tcp-proxy, "9000", "google.com:80", -d, -d]
```
