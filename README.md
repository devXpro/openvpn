# Usage
1. Create certificate (use some pass phrase)
   ```
   docker-compose run --rm openvpn ovpn_genconfig -u udp://{vpn_server_address}
   docker-compose run --rm openvpn ovpn_initpki
   ```
2. Run openvpn: 
   `docker-compose up -d openvpn`
3. Generate certificate for specific user (use pass phrase from p.1):
  `docker-compose run --rm openvpn easyrsa build-client-full {client_name} nopas`
   
4. Export certificate generated in p.3
   `docker-compose run --rm openvpn ovpn_getclient {client_name} > certificate.ovpn`
