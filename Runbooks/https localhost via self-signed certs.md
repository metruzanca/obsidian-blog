```bash
brew install mkcert;
#brew install nss  # if you use firefox

# this creates a local cert authority
mkcert -install;

mkdir ~/.local-certs
mkcert \
-cert-file ~/.local-certs/self-signed-localhost-cert.pem \
-key-file ~/.local-certs/self-signed-localhost-key.pem \
localhost 127.0.0.1 ::1 # localtest.me "*.localtest.me"
```

