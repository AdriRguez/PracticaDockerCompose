version: '3.9'
services:
  bind9:
    container_name: asir_bind9_1
    image: internetsystemsconsortium/bind9:9.16
    ports:
    - 5300:53/udp
    - 5300:53/tcp
    volumes:
    - /home/asir2a/Escritorio/DNS/config:/etc/bind
    - /home/asir2a/Escritorio/DNS/zonas:/var/lib/bind
  asir_cliente:
    container_name: asir_cliente_1
    image: alpine
    networks:
      - bind9_subnet
    stdin_open: true
    tty: true
    dns:
      - 10.1.0.254
networks:
  bind9_subnet:
    external: true