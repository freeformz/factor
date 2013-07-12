
## Goals

  * listens on `:$PROXY_PORT` for requests to proxy to `http://localhost:$PORT` (http).
  * listens on `:$SNS_PORT` for SNS Notifications (https).
  * uses an instance `$ROLE` to register with an SNS `$TOPIC` as `http://<ip>:$SNS_PORT`
  * confirms the subscription so that it can recieve notifications
  * Terminates itself and the instance ASAP on any errors
  * Low memory usage
  * Fair or better performance

### Notifications
  * New App Release: Download slug, start new version, start proxying new requests to new app version, stop proxying request to old app version, shutdown old app version.
  * Shutdown: Stop accepting new connections, finish existing connections, and terminate instance.
  * Update: Download new factor version and migrate existing app to it.
