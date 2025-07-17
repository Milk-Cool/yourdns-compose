# yourdns-compose
Docker Compose configs for yourdns. See [website](https://github.com/Milk-Cool/yourdns-website) and [server](https://github.com/Milk-Cool/yourdns-server) repos.

## `.env`
```bash
POSTGRES_PASSWORD=SecureKey1
ADMIN_KEY=SecureKey2
DEFAULT_SERVER=1.1.1.1 # any reliable dns server

AUTH_SECRET=SecureBase64String # openssl rand -base64 33
AUTH_GOOGLE_ID=GoogleOauthID
AUTH_GOOGLE_SECRET=GoogleOauthSecret

DNS_IP=YourOutsideIP # e. g. 123.45.67.89
DNS_DOH_HOST=YourOutsideDomain # e. g. yourdns.com
```

## DoH
Not included. I recommend balboah's coredns fork on the [doh-json](https://github.com/balboah/coredns/tree/doh-json) branch.

Config:
```
https://.:8044 {
	tls ssl.pem ssl.key
	forward . dns://127.0.0.1:53 {
		prefer_udp
	}
}
```

## running
```bash
docker-compose up
```