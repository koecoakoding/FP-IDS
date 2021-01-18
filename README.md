# FP-IDS

# Fachrizal Rahmat Hidayat
# 05311840000005

## Teler (Real Time Detection intrution)

### Requirement

Web yang memiliki web server Nginx

Menginstalll nginx dan php

![gambar](https://user-images.githubusercontent.com/55182321/104443625-42a79b00-55c9-11eb-840c-e46e6a664e47.png)


### Instalasi

Install teler menggunakan `curl -sSfL 'https://ktbs.dev/get-teler.sh' | sh -s -- -b /usr/local/bin`

lalu cek menggunakan teler -h 

![gambar](https://user-images.githubusercontent.com/55182321/104423224-67434900-55b0-11eb-9267-46a0a388d935.png)


Membuat file konfigurasi nya dengan membuat `teler.yaml` 

```
log_format: |
  $remote_addr $remote_user - [$time_local] "$request_method $request_uri $request_protocol" 
  $status $body_bytes_sent "$http_referer" "$http_user_agent"
```
Menggunakan log format Nginx

```
rules:
  cache: true
  threat:
    excludes:
      # - "Common Web Attack"
      # - "CVE"
      # - "Bad IP Address"
      # - "Bad Referrer"
      # - "Bad Crawler"
      # - "Directory Bruteforce"

    # It can be user-agent, request path, HTTP referrer, IP address and/or request query values parsed in regExp
    whitelists:
      # - "(curl|Go-http-client|okhttp)/*"
      # - "^/wp-login\\.php"
      # - "https://www\\.facebook\\.com"
      # - "192\\.168\\.0\\.1"
```

Mengatur rules yang diinginkan

Setelah itu menggunakan command `tail -f /var/log/nginx/access.log | teler -c /path/to/config/teler.yaml` Untuk menjalankan programnya

![gambar](https://user-images.githubusercontent.com/55182321/104919459-dc57b980-59c8-11eb-822d-34094a690a2e.png)

Akan keluar seperti gambar di atas jika sudah di jalankan

