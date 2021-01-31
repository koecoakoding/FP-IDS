# FP-IDS Teler (Real Time Detection intrution)

# Fachrizal Rahmat Hidayat
# 05311840000005

## 1. Requirement

Web yang memiliki web server Nginx

Menginstalll nginx dan php

![gambar](https://user-images.githubusercontent.com/55182321/104443625-42a79b00-55c9-11eb-840c-e46e6a664e47.png)


## 2. Instalasi

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

## 3. Notifikasi

Menginstall node.js dengan menggunakan command 

curl -sL https://deb.nodesource.com/setup_14.x | sudo -E bash -
sudo apt-get install -y nodejs

Lalu jalankan `npm init -y` untuk memebuat package.json

lalu menjalankan command `npm install discord.js` Untuk menginstall discord.js nya

Setelah itu membuat bot discord melalui https://discord.com/developers/applications

1.New application

2.Create

3.Dan akan muncul seperti

![gambar](https://user-images.githubusercontent.com/55182321/106352124-56663780-6313-11eb-8031-d44f6dfc6238.png)

4. Setelah itu ke tab BOT dan add bot

![gambar](https://user-images.githubusercontent.com/55182321/106352226-beb51900-6313-11eb-9f25-c4283f692250.png)

5. Masukan BOT ke server discord

![gambar](https://user-images.githubusercontent.com/55182321/106373276-772d9c00-63aa-11eb-8dca-31b0870efade.png)

6. Buat index.js dengan isi

![gambar](https://user-images.githubusercontent.com/55182321/106373136-24071980-63a9-11eb-9152-2eaaa0c5f745.png)

7. Lalu buat file config.json dengan isi token dari bot dan juga prefix

![gambar](https://user-images.githubusercontent.com/55182321/106373203-b90a1280-63a9-11eb-9007-0485747f53d5.png)

8. Jalankan node `index.js` berbarengan dengan menjalankan teler

![gambar](https://user-images.githubusercontent.com/55182321/106373326-02a72d00-63ab-11eb-8950-82d9e09dccad.png)

9. Kembali ke discord dan ketikan prefix `!gas`

![gambar](https://user-images.githubusercontent.com/55182321/106373385-73e6e000-63ab-11eb-8d1a-93af68eb9d7e.png)
