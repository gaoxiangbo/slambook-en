## Kata Pengantar

### Buku apa ini?

Ini adalah buku yang memperkenalkan visual SLAM, dan ini mungkin buku China pertama yang hanya berfokus pada topik spesifik ini.

Jadi, apa itu SLAM?

SLAM adalah singkatan dari **S**imultaneous **L**ocalization **a**nd **M**apping. Biasanya mengacu pada robot atau bodi kaku yang bergerak, dilengkapi dengan sensor khusus, memperkirakan **motion** sendiri dan membangun **model** (beberapa jenis deskripsi) dari lingkungan sekitar, tanpa informasi apriori [Davison2007]. Jika sensor yang dimaksud di sini terutama kamera, itu disebut "Visual SLAM".

Visual SLAM adalah subjek dari buku ini. Kami sengaja memasukkan definisi panjang menjadi satu kalimat tunggal, sehingga pembaca bisa memiliki konsep yang lebih jelas. Pertama-tama, SLAM bertujuan untuk memecahkan masalah "positioning" dan "map building" pada saat bersamaan. Dengan kata lain, ini adalah masalah bagaimana memperkirakan lokasi sensor itu sendiri, sambil memperkirakan model lingkungan. Jadi bagaimana mencapainya? Hal ini membutuhkan pemahaman yang baik tentang informasi sensor. Sensor dapat mengamati dunia luar dalam bentuk tertentu, namun pendekatan spesifik untuk memanfaatkan pengamatan semacam itu biasanya berbeda. Dan, mengapa masalah ini layak dikeluarkan untuk diselidiki oleh seluruh buku? Cukup karena sulit, apalagi kalau kita ingin sukses sukses SLAM secara **real time** dan **tanpa sepengetahuan**. Ketika kita berbicara tentang visual SLAM, kita perlu memperkirakan lintasan dan peta berdasarkan serangkaian gambar kontinu (yang membentuk sebuah video).

Hal ini tampaknya cukup intuitif. Ketika kita manusia memasuki lingkungan yang asing, bukankah kita melakukan hal yang persis sama? Jadi, pertanyaannya adalah apakah kita bisa menulis program dan membuat komputer melakukannya.

Pada saat lahirnya penglihatan komputer, orang membayangkan suatu saat komputer bisa bertindak seperti manusia, mengamati dan mengamati dunia, dan memahami lingkungan sekitar. Kemampuan menjelajahi daerah yang tidak diketahui adalah mimpi indah dan romantis, menarik banyak peneliti untuk mengatasi masalah ini siang dan malam [Hartyley2003]. Kami pikir ini tidak akan sesulit itu, tapi kemajuannya ternyata tidak semulus yang diharapkan. Bunga, pohon, serangga, burung dan hewan, dicatat sangat berbeda di komputer: mereka hanyalah matriks yang terdiri dari angka. Untuk membuat komputer memahami isi gambar, sama sulitnya membuat kita memahami blok angka tersebut. Kami bahkan tidak tahu bagaimana kami memahami gambar, dan kami juga tidak tahu bagaimana cara membuat komputer melakukannya. Namun, setelah berpuluh-puluh tahun berjuang, akhirnya kami mulai melihat tanda-tanda kesuksesan - melalui teknologi Artificial Intelligence (AI) dan Mesin Belajar (ML), yang secara bertahap memungkinkan komputer mengidentifikasi objek, wajah, suara, teks, walaupun dengan cara (probabilistik pemodelan) yang masih sangat berbeda dari kita. Di sisi lain, setelah hampir tiga dasawarsa perkembangan di SLAM, kamera kami mulai menangkap gerakan mereka dan mengetahui posisi mereka, walaupun masih ada celah besar antara kemampuan komputer dan manusia. Periset telah berhasil membangun berbagai sistem SLAM real-time. Beberapa dari mereka dapat secara efisien melacak lokasi mereka sendiri, dan yang lainnya bahkan dapat melakukan rekonstruksi tiga dimensi secara real-time

Ini sangat sulit, tapi kami telah membuat kemajuan yang luar biasa. Yang lebih seru lagi adalah, dalam beberapa tahun terakhir, kita telah melihat munculnya sejumlah besar aplikasi terkait SLAM. Lokasi sensor bisa sangat berguna di banyak area: mesin penyapu indoor dan robot mobile, mobil penggerak otomatis, Unmanned Aerial Vehicles (UAV) di udara, Virtual Reality (VR) dan Augmented Reality (AR). SLAM sangat penting Tanpa itu, mesin sweeping tidak bisa bermanuver di ruangan secara mandiri, tapi mengembara secara membabi buta; robot domestik tidak bisa mengikuti instruksi untuk mencapai ruangan tertentu secara akurat; Virtual Reality akan selalu terbatas dalam ruang yang dipersiapkan. Jika tidak ada inovasi ini yang bisa dilihat dalam kehidupan nyata, betapa disayangkannya itu.

Periset dan pengembang hari ini semakin menyadari pentingnya teknologi SLAM. SLAM memiliki hampir 30 tahun sejarah penelitian, dan telah menjadi topik hangat di komunitas robotika dan visi komputer. Sejak abad ke-21, teknologi SLAM visual telah mengalami perubahan dan terobosan yang signifikan baik dalam teori maupun praktik, dan secara bertahap berpindah dari laboratorium ke dunia nyata. Pada saat yang sama, kami dengan menyesal menemukan bahwa, setidaknya dalam bahasa China, makalah dan buku SLAM masih sangat langka, membuat banyak pemula di bidang ini tidak dapat memulai dengan lancar. Meski kerangka teoritis SLAM pada dasarnya telah menjadi matang, untuk menerapkan sistem SLAM yang lengkap masih sangat menantang dan membutuhkan keahlian teknis tingkat tinggi. Peneliti baru di daerah tersebut harus menghabiskan waktu lama untuk mempelajari sejumlah besar pengetahuan yang tersebar, dan seringkali harus melewati sejumlah jalan memutar untuk mendekati inti sebenarnya.

Buku ini secara sistematis menjelaskan teknologi visual SLAM. Kami berharap hal itu (setidaknya sebagian) mengisi celah saat ini. Kami akan merinci latar belakang teoritis SLAM, arsitektur sistem, dan berbagai modul utama. Pada saat bersamaan, kami menekankan praktik: semua algoritma penting yang diperkenalkan dalam buku ini akan dilengkapi dengan kode runnable yang dapat diuji sendiri, sehingga pembaca dapat mencapai pemahaman yang lebih dalam. Visual SLAM, lagipula, adalah teknologi untuk aplikasi. Meskipun teori matematika bisa indah, jika Anda tidak bisa mengubahnya menjadi garis kode, akan seperti kastil di udara, yang membawa sedikit dampak praktis. Kami percaya bahwa praktik memverifikasi pengetahuan sejati, dan latihan menguji gairah sejati. Hanya setelah membuat tangan Anda kotor dengan algoritme, Anda benar-benar bisa mengerti SLAM, dan mengklaim bahwa Anda telah jatuh cinta pada penelitian SLAM

Sejak didirikan pada tahun 1986 [Smith1986], SLAM telah menjadi topik penelitian yang panas dalam bidang robotika. Sangat sulit untuk memberikan pengantar lengkap untuk semua algoritma dan variannya dalam sejarah SLAM, dan kami menganggapnya sebagai hal yang tidak perlu juga. Buku ini pertama-tama akan memperkenalkan pengetahuan latar belakang, seperti geometri proyektif, visi komputer, teori estimasi negara, Lie Group dan Lie aljabar, dan lain-lain. Selain itu, kami akan menunjukkan batang pohon SLAM, dan menghilangkan yang rumit. dan daun berbentuk aneh. Kami pikir ini efektif. Jika pembaca bisa menguasai esensi dari bagasi, mereka sudah mendapatkan kemampuan untuk menjelajahi detil dari wilayah penelitian. Jadi tujuan kami adalah untuk membantu para pemula SLAM dengan cepat tumbuh menjadi peneliti dan pengembang yang berkualitas. Di sisi lain, bahkan jika Anda sudah menjadi peneliti SLAM berpengalaman, buku ini mungkin masih mengungkapkan area yang tidak Anda kenal, dan mungkin memberi Anda wawasan baru.

Ada beberapa buku SLAM yang terkait, seperti "Probabilistic Robotics" [Thrun2005], "Multiple View Geometry in Computer Vision" [Hartley2003], "Estimasi Negara untuk Robotika: Pendekatan Matrix-Lie-Group" [Barfoot2017 ], dll. Mereka menyediakan konten yang kaya, diskusi komprehensif dan derivasi yang ketat, dan oleh karena itu adalah buku teks terpopuler di antara peneliti SLAM. Namun, ada dua hal penting: Pertama, tujuan dari buku-buku ini sering kali memperkenalkan teori matematika fundamental, dengan SLAM menjadi satu dari aplikasinya. Oleh karena itu, mereka tidak bisa dianggap secara khusus fokus visual SLAM. Kedua, mereka menempatkan penekanan besar pada teori matematika, namun relatif lemah dalam pemrograman. Hal ini membuat pembaca tetap meraba-raba saat mencoba menerapkan pengetahuan yang mereka pelajari dari buku. Keyakinan kami adalah: hanya setelah coding, debugging dan algoritma tweaking dan parameter dengan tangannya sendiri, seseorang dapat mengklaim pemahaman yang sebenarnya akan suatu masalah.

Dalam buku ini, kami akan memperkenalkan sejarah, teori, algoritma dan status penelitian di SLAM, dan menjelaskan sistem SLAM yang lengkap dengan membaginya menjadi beberapa modul: odometri visual, optimasi back-end, pembuatan peta, dan deteksi penutupan loop. Kami akan menyertai pembaca selangkah demi selangkah untuk menerapkan algoritme inti setiap modul, jelajahi mengapa mereka efektif, dalam situasi apa mereka merasa tidak nyaman, dan membimbing mereka menjalankan kode pada mesin mereka sendiri. Anda akan terpapar teori matematika kritis dan pengetahuan pemrograman, dan akan menggunakan berbagai perpustakaan termasuk Eigen, OpenCV, PCL, g2o, dan Ceres, dan menguasai penggunaannya dalam sistem operasi Linux.

Nah, cukup bicara, semoga perjalananmu menyenangkan!

### Bagaimana cara menggunakan buku ini?

Buku ini berjudul "14 Ceramah tentang Visual SLAM". Seperti namanya, kita akan mengatur isinya menjadi "kuliah" seperti kita belajar di kelas. Setiap ceramah berfokus pada satu topik tertentu, disusun secara logis. Setiap bab akan mencakup bagian teoretis dan bagian praktis, dengan teoritis biasanya datang lebih dulu. Kami akan memperkenalkan matematika yang penting untuk memahami algoritme, dan sebagian besar waktu dalam cara naratif, bukan dalam pendekatan "definisi, teorema, inferensi" yang diadopsi oleh sebagian besar buku teks matematika. Kami pikir ini akan lebih mudah dipahami, tapi tentu saja dengan harga yang kurang ketat kadang kala. Pada bagian praktis, kami akan memberikan kode dan mendiskusikan makna berbagai bagian, dan menunjukkan beberapa hasil eksperimen. Jadi, ketika Anda melihat bab dengan kata "latihan" dalam judul, Anda harus menyalakan komputer Anda dan mulai memprogram bersama kami, dengan gembira.

Buku ini dapat dibagi menjadi dua bagian: Bagian pertama terutama berfokus pada pengetahuan matematika dasar, yang berisi:

1. Kuliah 1: kata pengantar (yang sedang Anda baca sekarang), mengenalkan isi dan struktur buku ini.
2. Kuliah 2: gambaran umum tentang sistem SLAM. Ini menggambarkan setiap modul sistem SLAM dan menjelaskan apa yang mereka lakukan dan bagaimana mereka melakukannya. Bagian latihan mengenalkan pemrograman C ++ dasar di lingkungan Linux dan penggunaan IDE.
3. Kuliah 3: gerak tubuh kaku di ruang 3D. Anda akan belajar pengetahuan tentang matriks rotasi, quaternions, sudut Euler, dan mempraktikkannya dengan perpustakaan Eigen.
4. Kuliah 4: Lie group dan Lie aljabar. Tidak masalah jika Anda belum pernah mendengarnya. Anda akan mempelajari dasar-dasar kelompok Lie, dan memanipulasinya dengan Sophus.
5. Kuliah 5: model kamera lubang jarum dan ekspresi gambar di komputer. Anda akan menggunakan OpenCV untuk mengambil parameter intrinsik dan ekstrinsik kamera, dan kemudian menghasilkan titik awan dengan menggunakan informasi mendalam melalui PCL (Library Point Cloud).
6. Kuliah 6: pengoptimalan nonlinier, termasuk estimasi negara, metode kuadrat dan gradien terkecil, mis. Gauss-Newton dan Levenburg-Marquardt. Anda akan menyelesaikan masalah pas kurva dengan menggunakan perpustakaan Ceres dan g2o.

Dari kuliah 7, kita akan membahas algoritma SLAM, dimulai dengan Visual Odometry (VO) dan diikuti oleh masalah pembuatan peta:

7. Kuliah 7: odometri visual berbasis fitur, yang saat ini menjadi mainstream di VO. Isi mencakup ekstraksi fitur dan pencocokan, perhitungan geometri epipolar, algoritma Perspective-n-Point (PnP), algoritma Iterative Closest Point (ICP), dan Bundle Adjustment (BA), dll. Anda akan menjalankan algoritma ini baik dengan memanggil fungsi OpenCV atau dengan membangun masalah optimasi Anda sendiri di Ceres dan g2o.
8. Kuliah 8: metode langsung (atau intensitas berbasis) untuk VO. Anda akan mempelajari prinsip aliran optik dan metode langsung, dan kemudian menggunakan g2o untuk mencapai metode berbasis langsung RGB-D sederhana VO (optimasi di sebagian besar algoritma VO langsung akan lebih rumit).
9. Kuliah 9: bab latihan untuk VO. Anda akan membangun kerangka odometer visual sendiri dengan mengintegrasikan pengetahuan yang telah dipelajari sebelumnya, dan memecahkan masalah seperti kerangka dan pengelolaan titik peta, pemilihan bingkai kunci dan kontrol pengoptimalan.
10. Kuliah 10: optimasi back-end. Kita akan membahas Penyesuaian Bundle secara rinci, dan menunjukkan hubungan antara strukturnya yang jarang dan model grafik yang sesuai. Anda akan menggunakan Ceres dan g2o secara terpisah untuk memecahkan masalah BA yang sama.
11. Kuliah 11: grafik pose dalam optimasi back-end. Pose graph adalah representasi yang lebih kompak untuk BA yang meminggirkan semua titik peta menjadi batasan antara keyframes. Anda akan menggunakan g2o dan gtsam untuk mengoptimalkan grafik pose.
12. Ceramah 12: deteksi penutupan loop, terutama metode berbasis Bag-of-Word (BoW). Anda akan menggunakan dbow3 untuk melatih kamus dari gambar dan mendeteksi loop dalam video.
13. Kuliah 13: pembuatan peta. Kami akan membahas bagaimana memperkirakan kedalaman titik fitur pada SLAM monokular (dan menunjukkan mengapa mereka tidak dapat diandalkan). Dibandingkan dengan perkiraan kedalaman monokuler, membangun peta padat dengan kamera RGB-D jauh lebih mudah. Anda akan menulis program pencarian garis epipolar dan pencocokan patch untuk memperkirakan kedalaman dari gambar monokuler, dan kemudian membangun peta titik awan dan peta pohon segi delapan dari data RGB-D.
14. Kuliah 14: proyek open source SLAM saat ini dan arah pengembangan masa depan. Kami percaya bahwa setelah membaca bab-bab sebelumnya, Anda akan dapat memahami pendekatan orang lain dengan mudah, dan mampu mewujudkan gagasan baru Anda sendiri.

Akhirnya, jika Anda tidak mengerti apa yang sedang kita bicarakan sama sekali, selamat! Buku ini tepat untuk Anda! Ayo dan melawan!

### Sumber Kode

Semua kode sumber dalam buku ini di-host di github:

[https://github.com/gaoxiang12/slambook](https://github.com/gaoxiang12/slambook)

Sangat disarankan pembaca mendownloadnya untuk dilihat kapan saja. Kode dibagi dengan bab, misalnya isi kuliah ke 7 akan ditempatkan di folder "ch7". Selain itu, beberapa perpustakaan kecil yang digunakan dalam buku ini dapat ditemukan di folder "pihak ke-3" sebagai paket terkompresi. Untuk perpustakaan berukuran besar dan menengah seperti OpenCV, kami akan mengenalkan metode instalasi mereka saat pertama kali muncul. Jika ada pertanyaan mengenai kode ini, klik tombol "Masalah" di GitHub untuk dikirim. Jika memang ada masalah dengan kode tersebut, kami akan melakukan perubahan pada waktu yang tepat. Sekalipun pemahaman Anda bias, kami masih akan menjawab sebanyak mungkin. Jika Anda tidak terbiasa menggunakan Git, Anda juga bisa mengklik tombol di sebelah kanan yang berisi kata "download" untuk mendownload file zip ke drive lokal Anda.

### Orientasi pembaca

Buku ini diperuntukkan bagi mahasiswa dan peneliti yang tertarik dengan SLAM. Membaca buku ini membutuhkan prasyarat tertentu, kita asumsikan bahwa Anda memiliki pengetahuan berikut:

* **Kalkulus, Aljabar Linear, Teori Probabilitas** Ini adalah pengetahuan matematis mendasar yang harus dipelajari oleh kebanyakan pembaca selama studi sarjana. Anda setidaknya harus mengerti apa itu matriks dan vektor, dan apa artinya dengan melakukan diferensiasi dan integrasi. Untuk pengetahuan matematika lanjutan yang dibutuhkan, kami akan memperkenalkannya dalam buku ini saat kami melanjutkan.

* **Basic C ++ Programming.** Karena kita akan menggunakan C ++ sebagai bahasa pemrograman utama kita, disarankan agar pembaca setidaknya terbiasa dengan konsep dasar dan sintaksinya. Misalnya, Anda harus tahu kelas apa, bagaimana cara menggunakan perpustakaan standar C ++, bagaimana menggunakan kelas template, dll. Kami akan mencoba sebaik mungkin untuk menghindari penggunaan trik, namun dalam situasi tertentu, kami benar-benar tidak dapat mencegahnya. Selain itu, kita akan mengadopsi beberapa standar C ++ 11, tapi jangan khawatir, mereka akan dijelaskan saat muncul.

* **Linux Basics.** Lingkungan pengembangan kita adalah Linux dan bukan Windows, dan kita hanya akan menyediakan source code untuk Linux. ** Kami percaya bahwa menguasai Linux adalah keterampilan penting bagi peneliti SLAM, dan mohon dimulainya. Setelah membaca isi buku ini, kami yakin Anda akan setuju dengan kami. ** Di Linux, konfigurasi perpustakaan terkait sangat mudah, dan Anda akan secara bertahap menghargai manfaat penguasaannya. Jika Anda tidak pernah menggunakan sistem Linux, akan sangat bermanfaat jika Anda dapat menemukan beberapa materi pembelajaran Linux dan meluangkan waktu untuk membacanya (untuk menguasai dasar-dasar Linux, beberapa bab pertama dari sebuah buku pengantar harus cukup memadai). Kami tidak meminta pembaca untuk memiliki kemampuan operasi Linux yang luar biasa, namun kami berharap pembaca setidaknya tahu cara menyalakan terminal, dan memasukkan direktori kode. Ada beberapa pertanyaan swauji di Linux di akhir bab ini. Jika Anda memiliki jawaban untuk mereka, Anda seharusnya tidak memiliki banyak masalah dalam memahami kode dalam buku ini.

Pembaca yang tertarik dengan SLAM tetapi tidak memiliki hal di atas seperti pengetahuan yang disebutkan mungkin merasa sulit untuk melanjutkan buku ini. Jika Anda tidak memahami dasar-dasar C++, Anda dapat membaca beberapa buku pengantar seperti _C ++ Primer Plus_. Jika Anda tidak memiliki pengetahuan matematika yang relevan, kami juga menyarankan Anda membaca beberapa buku pelajaran matematika relevan pertama. Namun demikian, kita berpikir bahwa sebagian besar pembaca yang telah menyelesaikan sarjana harus sudah memiliki gudang matematika diperlukan. Mengenai kode, kami sarankan bahwa Anda menghabiskan waktu untuk mengetik kode itu sendiri, dan men-tweak parameter untuk melihat bagaimana mereka mempengaruhi output. Ini akan sangat membantu.

Buku ini dapat digunakan sebagai buku teks untuk kursus SLAM, tetapi ini juga cocok sebagai bahan belajar-sendiri sebagai ekstra kurikuler.

### Gaya

Buku ini mencakup teori matematika dan pemrograman implementasi. Oleh karena itu, untuk kemudahan membaca, kita akan menggunakan layout yang berbeda untuk membedakan isi yang berbeda.

1. Rumus matematika akan dicantumkan secara terpisah, dan rumus yang penting ini akan ditetapkan dengan nomor persamaan di ujung kanan baris, misalnya:

	![](http://latex.codecogs.com/gif.latex?\\bm{y}=\\bm{A}\\bm{x})

	Huruf miring digunakan untuk skalar (misalnya ![](http://latex.codecogs.com/gif.latex?a)), huruf tebal dna miring digunakan untuk vektor dan matriks (misalnya ![](http://latex.codecogs.com/gif.latex?\\bm{a}), ![](http://latex.codecogs.com/gif.latex?\\bm{A})). Huruf tebal hollow mewakili set khusus, misalnya nomor asli ![](http://latex.codecogs.com/gif.latex?\\mathbb{R}) dan integer mengatur ![](http://latex.codecogs.com/gif.latex?\\mathbb{Z}). Gothic digunakan untuk Lie Algebra, misalnya ![](http://latex.codecogs.com/gif.latex?\\mathfrak{se}(3)).

2. Kode sumber akan dibingkai ke dalam kotak, menggunakan ukuran font yang lebih kecil, dengan nomor baris di sebelah kiri. Jika sebuah blok kode panjang, kotak dapat dilanjutkan ke halaman berikutnya:

	```cpp
	#include <iostream>
	using namespace std;
	
	int main ( int argc, char** argv )
	{
		cout<<"Hello"<<endl;
		return 0;
	}
	```

3. Ketika blok kode terlalu panjang atau mengandung bagian-bagian yang berulang-ulang dengan kode yang terdaftar sebelumnya, hal ini tidak tepat untuk didaftarkan lagi sepenuhnya. Kami hanya **akan memberikan snippets penting** dan menandainya sebgai "Snippets". Oleh karena itu, kami sangat menyarankan kepada pembaca untuk mengunduh semua sumber kode GitHub dan menyelesaikan latihan agar Anda lebih memahami buku ini.

4. Alasan tipografi, kode yang ditunjukkan dalam buku mungkin sedikit berbeda dari kode host di GitHub. Dalam hal ini silakan gunakan kode pada GitHub.

5. Untuk masing-masing perpustakaan yang kami gunakan, itu akan dijelaskan secara rinci ketika pertama kali muncul, tetapi tidak diulang dalam tindak lanjut. Oleh karena itu, disarankan bahwa pembaca membaca buku ini secara berurutan.

6. Abstrak akan disajikan pada permulaan masing-masing kuliah. Ringkasan dan beberapa latihan akan diberikan pada akhir. Referensi tercantum di akhir buku.

7. Bab dengan tanda asterisk di depan adalah bacaan opsional, dan pembaca dapat membaca sesuai dengan minat mereka. Melewatkannya tidak akan menghalangi pemahaman pada bab-bab berikutnya.

8. Konten penting akan ditandai dengan **tebal**, karena kita sudah terbiasa.

9. Sebagian besar percobaan kami rancang secara demonstratif. Memahami mereka bukan berarti bahwa Anda sudah familiar dengan seluruh perpustakaan. Jadi kami sarankan Anda untuk menjelajahi lebih lanjut pada perpustakaan penting yang sering digunakan dalam buku.

10. Buku latihan dan bacaan opsional mungkin mengharuskan Anda untuk mencari bahan tambahan, sehingga Anda perlu belajar untuk menggunakan mesin pencari.

### Ucapan Terima kasih

### Latihan (pertanyaan self-test)

1. Ada persamaan linear ![](http://latex.codecogs.com/gif.latex?\\bm{A}\\bm{x}=\\bm{b}), jika ![](http://latex.codecogs.com/gif.latex?\\bm{A}) dan ![](http://latex.codecogs.com/gif.latex?\\bm{b}) diketahui, bagaimana memecahkan ![](http://latex.codecogs.com/gif.latex?\\bm{x})? Apa persyaratan untuk ![](http://latex.codecogs.com/gif.latex?\\bm{A}) dan ![](http://latex.codecogs.com/gif.latex?\\bm{b})? (Petunjuk: dimensi dan pangkat dari ![](http://latex.codecogs.com/gif.latex?\\bm{A}))

2. Apa itu distribusi Gaussian? Apa yang terlihat seperti dalam kasus dimensi? Bagaimana tentang kasus dimensi tinggi?

3. Apakah Anda tahu **class** dalam C++? Apakah Anda tahu STL? Apakah Anda pernah menggunakan mereka?

4. Bagaimana Anda menulis sebuah program C++? (Ini sangat baik jika jawaban Anda adalah "menggunakan Visual C++ 6.0". Karena selama Anda memiliki C++ atau C programming experience, Anda berada di posisi yang benar)

5. Apakah Anda tahu C++11 standar? Yang baru memiliki fitur mendengar atau digunakan? Apakah Anda akrab dengan standar lain?

6. Apakah Anda tahu Linux? Apakah Anda menggunakan setidaknya satu jenis (tidak termasuk Android), seperti Ubuntu?

7. Apa yang dimaksud dengan struktur direktori Linux? Perintah-perintah dasar apa yang Anda tahu? (misalnya ls, cat, dll.)

8. Bagaimana cara menginstal perangkat lunak di Ubuntu (tanpa menggunakan Software Center)? Dimana direktori perangkat lunak yang biasanya dipasang? Jika Anda hanya tahu nama lain dari perangkat lunak (misalnya, Anda ingin menginstal sebuah perpustakaan dengan kata "eigen" dalam namanya), bagaimana Anda akan melakukannya?

9. *Akan menghabiskan satu jam belajar Vim, Anda akan menggunakannya cepat atau lambat. Anda dapat memasukkan "vimtutor" dalam terminal dan membaca isinya. Kami tidak mengharuskan Anda untuk beroperasi dengan sangat terampil, selama Anda dapat menggunakannya untuk mengedit kode dalam proses pembelajaran buku ini. **Jangan buang waktu mempelajari plugin, jangan coba untuk menjadi Vim IDE untuk sekarang, kita hanya akan menggunakannya untuk teks editing.**

### Referensi

- [Davison2007]. A. Davison, I. Reid, N. Molton, and O. Stasse, “Monoslam: Real-time single camera SLAM,” IEEETransactions on Pattern Analysis and Machine Intelligence, vol. 29, no. 6, pp. 1052–1067, 2007.
- [Hartley2003]. R. Hartley and A. Zisserman, Multiple View Geometry in Computer Vision. Cambridge universitypress, 2003.
- [Smith1986]. R. C. Smith and P. Cheeseman, “On the representation and estimation of spatial uncertainty,” In-ternational Journal of Robotics Research, vol. 5, no. 4, pp. 56–68, 1986.
- [Thrun2005]. S. Thrun, W. Burgard, and D. Fox, Probabilistic robotics. MIT Press, 2005.
- T. Barfoot, “State estimation for robotics: A matrix lie group approach,”, Cambridge Press, 2016.
