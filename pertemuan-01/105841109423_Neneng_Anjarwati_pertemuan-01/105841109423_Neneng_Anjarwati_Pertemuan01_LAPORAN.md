# 📋 Laporan Praktikum Pertemuan 01
## DevOps Culture & Principles

---

## 👤 Identitas Mahasiswa

| Item | Keterangan |
|------|------------|
| **Nama** | Neneng Anjarwati |
| **NIM** | 105841109423 |
| **Kelas** | 5C |
| **Tanggal** | 2026-02-25 |

---

## 📚 Pemahaman DevOps

### Apa itu DevOps?

DevOps adalah sebuah pendekatan dalam pengembangan perangkat lunak yang menggabungkan dua peran utama dalam proses pembuatan aplikasi, yaitu development (pengembang) dan operations (operasional atau pengelola sistem). Sebelumnya, kedua tim ini sering bekerja secara terpisah, sehingga menimbulkan masalah komunikasi, keterlambatan rilis, dan kesalahan saat aplikasi dipindahkan dari lingkungan pengembangan ke server produksi. DevOps hadir untuk menjembatani kesenjangan tersebut dengan mendorong kolaborasi, komunikasi yang lebih baik, serta penggunaan otomatisasi dalam setiap tahapan pengembangan software.

Dalam praktiknya, DevOps menekankan proses yang berkelanjutan seperti Continuous Integration (CI) dan Continuous Deployment (CD), di mana setiap perubahan kode akan otomatis diuji dan dipersiapkan untuk dirilis. Dengan cara ini, pengembang dapat mengetahui lebih cepat jika terjadi kesalahan, sehingga perbaikan bisa dilakukan sebelum aplikasi digunakan oleh pengguna. Selain itu, DevOps juga memanfaatkan teknologi seperti container dan cloud computing untuk memastikan aplikasi dapat berjalan secara konsisten di berbagai lingkungan.

Tujuan utama DevOps adalah mempercepat siklus pengembangan, meningkatkan kualitas software, serta menjaga stabilitas sistem. Dengan adanya DevOps, perusahaan dapat merilis fitur baru lebih cepat, merespons kebutuhan pengguna dengan lebih baik, dan meminimalkan risiko gangguan layanan. Secara keseluruhan, DevOps bukan hanya tentang penggunaan tools, tetapi juga tentang perubahan budaya kerja yang lebih kolaboratif, transparan, dan berorientasi pada efisiensi serta kualitas.

### Mengapa DevOps Penting?

DevOps penting dalam industri software saat ini karena membantu perusahaan merespons perubahan dan kebutuhan pasar dengan lebih cepat, efisien, dan stabil. Di era digital yang menuntut pembaruan fitur secara terus-menerus, DevOps memungkinkan proses pengembangan, pengujian, dan deployment dilakukan secara otomatis dan berkelanjutan sehingga waktu rilis menjadi lebih singkat tanpa mengorbankan kualitas. Selain itu, kolaborasi yang erat antara tim development dan operations mengurangi kesalahan komunikasi, mempercepat penyelesaian masalah, serta meningkatkan keandalan sistem. Dengan menerapkan DevOps, perusahaan dapat meningkatkan produktivitas tim, meminimalkan risiko downtime, dan memberikan pengalaman pengguna yang lebih baik secara konsisten.

### Contoh Perusahaan yang Menerapkan DevOps

1. Netflix
Netflix dikenal sebagai salah satu pelopor penerapan DevOps dalam skala besar. Mereka menggunakan arsitektur microservices dan otomatisasi penuh dalam proses deployment sehingga mampu melakukan ribuan perubahan sistem setiap hari tanpa mengganggu layanan streaming. Dengan DevOps, Netflix dapat menjaga ketersediaan layanan secara global dengan downtime yang sangat minim.

2. Amazon
Amazon menerapkan DevOps untuk mempercepat proses rilis fitur dan pembaruan sistem. Perusahaan ini menggunakan praktik Continuous Integration dan Continuous Deployment (CI/CD) sehingga tim dapat melakukan deployment secara cepat dan rutin. Pendekatan ini membantu Amazon berinovasi dengan cepat sekaligus menjaga stabilitas platform e-commerce mereka.

---

## 🎯 Pemahaman Prinsip CALMS

Prinsip CALMS adalah lima pilar utama dalam DevOps yang menjadi panduan agar implementasi berjalan efektif. CALMS merupakan singkatan dari Culture, Automation, Lean, Measurement, dan Sharing.

1. Culture (Budaya)
Culture menekankan pentingnya kolaborasi antara tim development dan operations. Dalam DevOps, kedua tim tidak lagi bekerja secara terpisah, tetapi saling bertanggung jawab terhadap keberhasilan aplikasi dari tahap pengembangan hingga produksi. Contoh penerapannya adalah membuat tim lintas fungsi (cross-functional team) yang bersama-sama merancang, mengembangkan, menguji, dan memantau aplikasi, serta rutin melakukan meeting evaluasi seperti sprint review atau retrospective.

2. Automation (Otomatisasi)
Automation berarti mengotomatisasi proses yang berulang seperti build, testing, dan deployment agar lebih cepat dan minim kesalahan manusia. Contohnya adalah penggunaan pipeline CI/CD yang secara otomatis menjalankan testing setiap kali ada perubahan kode, lalu langsung melakukan deployment ke server jika tidak ditemukan error.

3. Lean (Efisiensi)
Lean berfokus pada pengurangan pemborosan dan peningkatan efisiensi proses kerja. Prinsip ini mendorong tim untuk merilis fitur dalam skala kecil namun sering (small batch release) agar risiko kesalahan lebih rendah. Contohnya adalah merilis update fitur kecil secara berkala dibanding menunggu banyak fitur sekaligus.

4. Measurement (Pengukuran)
Measurement menekankan pentingnya mengukur performa sistem dan proses pengembangan. Data digunakan untuk pengambilan keputusan yang lebih akurat. Contohnya adalah memantau waktu deployment, tingkat kegagalan sistem, response time aplikasi, dan jumlah bug untuk mengevaluasi kualitas software.

5. Sharing (Berbagi)
Sharing berarti berbagi pengetahuan, tanggung jawab, dan feedback antar tim. Transparansi sangat penting dalam DevOps. Contohnya adalah dokumentasi terbuka, penggunaan dashboard monitoring yang bisa diakses semua tim, serta sesi sharing knowledge untuk membahas masalah dan solusi.

Kelima prinsip CALMS ini saling berkaitan dan membantu organisasi menerapkan DevOps secara menyeluruh, bukan hanya dari sisi teknologi, tetapi juga dari sisi budaya dan proses kerja.

---

## 🔧 Setup Development Environment

### Versi Software

| Software | Versi |
|----------|-------|
| Git | git version 2.50.1.windows.1 |
| Docker | Docker version 29.0.1, build eedd969 |

### Konfigurasi Git

```
user.name = "Neneng Anjarwati"
user.email = "105841109423@student.unismuh.ac.id
```

### VS Code Extensions

1. Docker
2. Docker DX
3. Gitlens
4. YAML

### GitHub Account

- Username: -

---

## 📸 Screenshots

| No | Screenshot | Keterangan |
|----|------------|------------|
| 1 | ![Git Version](screenshots/01-git-version.png) | Output git --version |
| 2 | ![Git Config](screenshots/02-git-config.png) | Output git config --list |
| 3 | ![Docker Version](screenshots/03-docker-version.png) | Output docker --version |
| 4 | ![Docker Hello World](screenshots/04-docker-hello-world.png) | Output docker run hello-world |
| 5 | ![VS Code](screenshots/05-vscode-extensions.png) | VS Code dengan extensions |

---

## 💭 Refleksi Pribadi

### Harapan dari Praktikum Ini

Harapan saya dari praktikum DevOps ini adalah dapat memahami konsep DevOps tidak hanya secara teori, tetapi juga mampu menerapkannya secara langsung dalam praktik nyata. Saya berharap dapat menguasai penggunaan tools pendukung seperti version control, container, CI/CD, dan monitoring sehingga mampu mengelola proses pengembangan dan deployment aplikasi dengan lebih terstruktur dan otomatis. Selain itu, saya ingin belajar bagaimana membangun kolaborasi yang baik antara tim development dan operations agar proses kerja menjadi lebih efisien dan minim kesalahan. Melalui praktikum ini, saya juga berharap dapat meningkatkan kesiapan saya dalam menghadapi kebutuhan industri yang menuntut kecepatan, kualitas, dan stabilitas dalam pengembangan software.

### Skill yang Ingin Dikuasai

Di akhir semester, saya ingin menguasai kemampuan dalam mengimplementasikan praktik DevOps secara menyeluruh, mulai dari penggunaan version control seperti Git, pembuatan dan pengelolaan container menggunakan Docker, hingga membangun pipeline CI/CD untuk otomatisasi proses build, testing, dan deployment aplikasi. Saya juga ingin memahami cara mengelola infrastruktur dan jaringan antar service, melakukan monitoring performa aplikasi, serta menangani proses deployment ke server atau cloud dengan lebih percaya diri. Selain keterampilan teknis, saya berharap dapat meningkatkan kemampuan kolaborasi tim, problem solving, dan manajemen workflow agar siap menghadapi tantangan di dunia industri software.

### Tantangan yang Dihadapi

_Tidak ada tantangan khusus_

---

## ✅ Checklist

- [x] Git terinstall dan terkonfigurasi dengan benar
- [x] Docker dapat menjalankan container hello-world
- [x] VS Code terinstall dengan semua extensions yang diminta
- [x] Laporan ditulis dengan bahasa yang baik dan benar
- [x] Semua screenshot jelas dan terbaca

---

*Laporan ini dibuat pada Rabu, 25 Februari 2026*
