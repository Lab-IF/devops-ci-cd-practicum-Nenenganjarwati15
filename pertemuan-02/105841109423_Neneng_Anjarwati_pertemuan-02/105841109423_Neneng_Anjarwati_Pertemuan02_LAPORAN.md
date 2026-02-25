# 🐳 Laporan Praktikum Pertemuan 02
## Docker Fundamentals

---

## 👤 Identitas Mahasiswa

| Item | Keterangan |
|------|------------|
| **Nama** | Neneng Anjarwati |
| **NIM** | 105841109423 |
| **Kelas** | 5C |
| **Tanggal** | 2026-02-25 |

---

## 📚 Pemahaman Docker

### Apa itu Docker?

Docker adalah platform yang digunakan untuk menjalankan aplikasi di dalam sebuah container. Secara sederhana, Docker memungkinkan kita membungkus aplikasi beserta semua kebutuhan pendukungnya (library, dependensi, konfigurasi, dan sistem pendukung lainnya) ke dalam satu paket yang disebut container, sehingga aplikasi bisa berjalan dengan cara yang sama di mana pun baik di laptop pribadi, server, maupun cloud.

### Komponen Utama Docker

1. Images
Image adalah template atau cetakan dasar yang digunakan untuk membuat dan menjalankan aplikasi di Docker. Di dalam image sudah terdapat sistem operasi dasar, bahasa pemrograman, library, dependensi, serta konfigurasi yang dibutuhkan aplikasi agar bisa berjalan dengan baik. Image bersifat read-only (tidak dapat diubah) dan dapat digunakan berulang kali untuk membuat banyak container. Image biasanya dibuat melalui Dockerfile, kemudian dapat disimpan atau dibagikan kepada pengguna lain.

2. Containers
Container adalah hasil eksekusi dari sebuah image. Jika image diibaratkan sebagai blueprint, maka container adalah aplikasi yang sudah berjalan berdasarkan blueprint tersebut. Container bersifat ringan, terisolasi, dan dapat dijalankan, dihentikan, maupun dihapus sesuai kebutuhan. Container memastikan aplikasi berjalan dalam lingkungan yang konsisten, sehingga meminimalkan masalah perbedaan konfigurasi antara satu sistem dengan sistem lainnya.

3. Registry
Registry adalah tempat penyimpanan image Docker. Registry berfungsi untuk menyimpan, mengelola, serta mendistribusikan image agar dapat digunakan kembali atau dibagikan kepada orang lain. Pengguna dapat mengunggah (push) image ke registry dan mengunduh (pull) image dari registry. Registry bisa bersifat publik maupun privat, dan salah satu contoh registry publik yang paling populer adalah Docker Hub.

### Perbedaan Docker vs Virtual Machine

| Aspek               | Docker Container     | Virtual Machine      |
| ------------------- | -------------------- | -------------------- |
| Sistem Operasi      | Berbagi kernel host  | Memiliki OS sendiri  |
| Ukuran              | Lebih ringan         | Lebih besar          |
| Kecepatan           | Startup sangat cepat | Startup lebih lambat |
| Penggunaan Resource | Lebih hemat          | Lebih besar          |
| Isolasi             | Cukup kuat           | Sangat kuat          |


---

## 🔧 Praktik Docker Commands

### Output docker ps -a

```
Belum diisi
```

### Output docker images

```
Belum diisi
```

### Docker Run Command

```bash
Belum diisi
```

---

## 📄 Dockerfile

### Isi Dockerfile

```dockerfile
# Gunakan nginx alpine sebagai base image
FROM nginx:alpine

# Copy file HTML ke direktori nginx
COPY app/index.html /usr/share/nginx/html/index.html

# Expose port 80
EXPOSE 80

# Command default nginx
CMD ["nginx", "-g", "daemon off;"]
```

### Penjelasan Dockerfile

1. FROM nginx:alpine
Baris ini menentukan base image yang digunakan. Artinya, image yang dibuat akan menggunakan image nginx dengan versi alpine sebagai dasar. nginx:alpine adalah versi ringan dari Nginx karena menggunakan Alpine Linux yang berukuran kecil. Image ini tersedia di registry seperti Docker Hub.

COPY app/index.html /usr/share/nginx/html/index.html
Perintah ini menyalin file index.html dari folder lokal app/ ke dalam direktori default Nginx di dalam container, yaitu /usr/share/nginx/html/. Folder tersebut adalah lokasi tempat Nginx membaca file website yang akan ditampilkan ke browser.

2. EXPOSE 80
Perintah ini memberi tahu bahwa container akan menggunakan port 80 (port default HTTP). Ini tidak otomatis membuka port ke luar, tetapi sebagai dokumentasi dan informasi bahwa aplikasi di dalam container berjalan di port 80.

3. CMD ["nginx", "-g", "daemon off;"]
Perintah ini menentukan command default yang dijalankan saat container mulai berjalan.

nginx → menjalankan server Nginx

-g "daemon off;" → membuat Nginx tetap berjalan di foreground (tidak berjalan di background)

---

## 🐙 Docker Compose

### Isi docker-compose.yml

```yaml
version: '3.8'

services:
  web:
    image: nginx:alpine
    ports:
      - "8080:80"
    volumes:
      - ./app:/usr/share/nginx/html:ro
    depends_on:
      - api
    networks:
      - praktikum-net

  api:
    image: httpd:alpine
    ports:
      - "8081:80"
    networks:
      - praktikum-net

  db:
    image: postgres:15-alpine
    environment:
      POSTGRES_USER: praktikum
      POSTGRES_PASSWORD: devops123
      POSTGRES_DB: praktikum_db
    volumes:
      - db_data:/var/lib/postgresql/data
    networks:
      - praktikum-net

networks:
  praktikum-net:
    driver: bridge

volumes:
  db_data:
```

### Penjelasan Docker Compose

version: '3.8'

Baris ini menentukan versi format Docker Compose yang digunakan. Versi 3.8 adalah salah satu versi yang umum dipakai dan kompatibel dengan Docker versi terbaru.

Bagian services

Bagian ini mendefinisikan container-container yang akan dijalankan.

Service: web

Service web menggunakan image nginx:alpine, yaitu web server ringan berbasis Alpine Linux yang tersedia di Docker Hub.

ports
"8080:80" berarti port 80 di dalam container dipetakan ke port 8080 di komputer host. Jadi aplikasi bisa diakses melalui http://localhost:8080.

volumes
./app:/usr/share/nginx/html:ro berarti folder app di komputer lokal dihubungkan ke folder default Nginx di dalam container.
:ro (read-only) artinya file hanya bisa dibaca, tidak bisa diubah oleh container.

depends_on
Menandakan bahwa service web bergantung pada service api. Artinya, Docker akan menjalankan api terlebih dahulu sebelum web.

networks
Service ini terhubung ke jaringan praktikum-net, sehingga bisa berkomunikasi dengan service lain dalam jaringan yang sama.

Service: api

Service api menggunakan image httpd:alpine, yaitu Apache HTTP Server versi ringan.

ports
"8081:80" berarti port 80 di container dipetakan ke port 8081 di host. Bisa diakses melalui http://localhost:8081.

networks
Terhubung ke jaringan praktikum-net, sehingga bisa berkomunikasi dengan web dan db.

Service: db

Service db menggunakan image postgres:15-alpine, yaitu PostgreSQL versi 15 berbasis Alpine Linux.

environment
Berisi variabel lingkungan untuk konfigurasi database:

POSTGRES_USER → username database

POSTGRES_PASSWORD → password database

POSTGRES_DB → nama database yang otomatis dibuat

volumes
db_data:/var/lib/postgresql/data berarti data database disimpan di volume bernama db_data. Ini penting agar data tidak hilang meskipun container dihentikan atau dihapus.

networks
Terhubung ke jaringan praktikum-net.

Bagian networks
networks:
  praktikum-net:
    driver: bridge

Bagian ini membuat jaringan khusus bernama praktikum-net dengan driver bridge.
Network bridge memungkinkan container saling berkomunikasi dalam satu jaringan internal.

Bagian volumes
volumes:
  db_data:

Bagian ini mendefinisikan volume bernama db_data. Volume digunakan untuk menyimpan data secara persisten agar tidak hilang saat container dihapus.

### Output Docker Compose Up

```
Belum diisi
```

---

## 📸 Screenshots

| No | Screenshot | Keterangan |
|----|------------|------------|
| 1 | ![Container Running](screenshots/01-container-running.png) | Container yang sedang berjalan |
| 2 | ![Docker Images](screenshots/02-docker-images.png) | Daftar Docker images |
| 3 | ![Dockerfile](screenshots/03-dockerfile-content.png) | Isi file Dockerfile |
| 4 | ![Docker Build](screenshots/04-docker-build.png) | Proses docker build |
| 5 | ![App Browser](screenshots/05-app-browser.png) | Aplikasi berjalan di browser |
| 6 | ![Compose Up](screenshots/06-compose-up.png) | Docker Compose up |

---

## 💭 Refleksi & Kesimpulan

### Yang Dipelajari

Dari praktikum Docker ini, saya mempelajari bagaimana cara membuat, menjalankan, dan mengelola aplikasi menggunakan container agar dapat berjalan secara konsisten di berbagai lingkungan tanpa terkendala perbedaan konfigurasi. Saya memahami perbedaan antara image dan container, cara membuat Dockerfile, serta bagaimana menggunakan Docker Compose untuk mengatur beberapa service seperti web, API, dan database dalam satu jaringan yang saling terhubung. Selain itu, saya juga belajar tentang penggunaan port, volume untuk penyimpanan data persisten, dan network untuk komunikasi antar container, sehingga proses development dan deployment menjadi lebih terstruktur, efisien, dan mudah dikelola.

### Manfaat Docker

Docker membantu dalam pengembangan software dengan menyediakan lingkungan yang konsisten dan terisolasi melalui container, sehingga aplikasi dapat berjalan dengan cara yang sama di komputer pengembang, server, maupun cloud. Dengan Docker, semua dependensi seperti bahasa pemrograman, library, dan konfigurasi sistem dikemas dalam satu image, sehingga mengurangi masalah “berjalan di komputer saya tapi tidak di server”. Docker juga mempercepat proses setup environment karena pengembang tidak perlu menginstal banyak software secara manual. Selain itu, dengan bantuan Docker Compose, beberapa layanan seperti frontend, backend, dan database dapat dijalankan secara bersamaan dan terhubung dalam satu konfigurasi, sehingga mempermudah proses pengujian, kolaborasi tim, serta deployment aplikasi menjadi lebih cepat, efisien, dan terstruktur.

### Tantangan dan Solusi

_Tidak ada tantangan khusus_

---

## ✅ Checklist

- [x] Berhasil membuat Dockerfile yang valid
- [x] Berhasil build Docker image
- [x] Container berjalan dan aplikasi bisa diakses
- [x] Docker Compose berhasil dijalankan
- [x] Semua screenshot lengkap dan jelas
- [x] Penjelasan ditulis dengan bahasa sendiri

---

*Laporan ini dibuat pada Rabu, 25 Februari 2026*
