<h1>Práctica 5 - Anxo Vázquez</h1>
<h2>Configura un contenedor coa imaxe oficial de bind9 usando docker-compose</h2>
<p>Primeiro descargo a imaxe con "docker pull internetsystemsconsortium/bind9:9.20" e modifico o compose.yaml para que lanze un contenedor coa imaxe bind9.20 e despois o lanzo con docker compose up (primeiro executo o comando "sudo systemctl stop systemd-resolved" porque estaba usando o porto 53" e s"udo update-alternatives --config iptables").</p>
<p>Archivo compose.yaml:</p>
<p>services:
  bind9:
    image: internetsystemsconsortium/bind9:9.20
    container_name: bind9
    ports:
      - "53:53/udp"
      - "53:53/tcp"
    volumes:
      - ./bind:/etc/bind
    restart: unless-stopped

</p>
<p>docker pull internetsystemsconsortium/bind9:9.20</p>
<p>docker compose up</p>
<br>
<h2>Usa os volumes como se explica</h2>
<p>Modifico o archivo compose.yaml</p>
<p>Contido a engadir:</p>
<p>
      - /var/cache/bind \
      - /var/lib/bind \
      - /var/log \

</p>
<p>Archivo compose.yaml</p>
<p>                            
services:
  bind9:
    image: internetsystemsconsortium/bind9:9.20
    container_name: bind9
    ports:
      - "53:53/udp"
      - "53:53/tcp"
    volumes:
      - ./bind:/etc/bind
      - /var/cache/bind \
      - /var/lib/bind \
      - /var/log \
    restart: unless-stopped

</p>
