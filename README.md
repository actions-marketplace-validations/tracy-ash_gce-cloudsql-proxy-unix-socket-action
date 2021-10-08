# Google Cloud SQL Proxy Unix Socket

Github action which will start a [Google Cloud SQL Proxy](https://cloud.google.com/sql/docs/postgres/sql-proxy) as Docker container. 
Based on https://github.com/mattes/gce-cloudsql-proxy-action
## Prerequisites

Set up the following resources manually in the Cloud Console 
or use a tool like [Terraform](https://www.terraform.io).

* Running Cloud SQL instance with a public IP address
* Create Service Account with Role `Cloud SQL Client` and export a new JSON key.


## Github Action Inputs

| Variable                         | Description                                                                 |
|----------------------------------|-----------------------------------------------------------------------------|
| `creds`                          | ***Required*** Service Account JSON Key (not base64 encoded)                |
| `instance`                       | ***Required*** Cloud SQL connection name                                    |
| `dir`                            | directory to use for unix socket connection, default tmp/cloudsql           |
| `proxy_version`                  | Cloud SQL Proxy version, default 1.21.0                                     |


## Example Usage

```
uses: mattes/gce-cloudsql-proxy-unix-socket-action@v1
with:
  creds: ${{ secrets.GOOGLE_APPLICATION_CREDENTIALS }}
  instance: my-project:us-central1:instance-1
```

