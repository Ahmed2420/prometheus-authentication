# prometheus-authentication
Adding self-signed certificates authentication and encryption to Prometheus. These files enable authentication in the Node exporter so that only our Prometheus server is allowed access. Now, if anyone still manages to capture the packets from our target, they can read it in plain text and that's why we also implement encryption with TLS.
