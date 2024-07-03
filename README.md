# prometheus-authentication
Adding self-signed certificates authentication and encryption to Prometheus. These files enable authentication in the Node exporter so that only our Prometheus server is allowed access. Now, if anyone still manages to capture the packets from our target, they can read it in plain text and that's why we also implement encryption with TLS.

First create the directory "etc/node_exporter" so that we can store our configurations there, then lets create our certificates using OpenSSL:
openssl req   -x509   -newkey rsa:4096   -nodes   -keyout node_exporter.key   -out node_exporter.crt

Then you can download the config.yaml in this repo to etc/node_exporter and change its ownership to the node_exporter user and group (ne):
chown -R ne:ne /etc/node_exporter/

We can check whether TLS is enabled or not using this command:
node_exporter --web.config.file="config.yaml"
![TLS is enabled](https://github.com/Ahmed2420/prometheus-authentication/assets/74218745/90ecc2a8-dfcf-467a-99dd-97386b8c4980)
