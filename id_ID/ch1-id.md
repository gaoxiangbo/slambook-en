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

Readers who are interested in SLAM but do not have the above mentioned knowledge may find it difficult to proceed with this book. If you do not understand the basics of C++, you can read some introductory books such as _C ++ Primer Plus_. If you do not have the relevant math knowledge, we also suggest that you read some relevant math textbooks first. Nevertheless, we think that most readers who have completed undergraduate study should already have the necessary mathematical arsenal. Regarding the code, we recommend that you spend time typing them by yourself, and tweaking the parameters to see how they affect outputs. This will be very helpful.

This book can be used as a textbook for SLAM-related courses, but also suitable as extra-curricular self-study materials.

### Style

This book covers both mathematical theory and programming implementation. Therefore, for the convenience of reading, we will be using different layouts to distinguish different contents.

1.  Mathematical formulas will be listed separately, and important formulas will be assigned with an equation number on the right end of the line, for example:

	![](http://latex.codecogs.com/gif.latex?\\bm{y}=\\bm{A}\\bm{x})

	Italics are used for scalars (e.g. ![](http://latex.codecogs.com/gif.latex?a)), bold italics are used for vectors and matrices (e.g. ![](http://latex.codecogs.com/gif.latex?\\bm{a}), ![](http://latex.codecogs.com/gif.latex?\\bm{A})). Hollow bold represents special sets, e.g. real number ![](http://latex.codecogs.com/gif.latex?\\mathbb{R}) and integer set ![](http://latex.codecogs.com/gif.latex?\\mathbb{Z}). Gothic is used for Lie Algebra, e.g. ![](http://latex.codecogs.com/gif.latex?\\mathfrak{se}(3)).

2.  Source code will be framed into boxes, using a smaller font size, with line numbers on the left. If a code block is long, the box may continue to the next page:

	```cpp
	#include <iostream>
	using namespace std;
	
	int main ( int argc, char** argv )
	{
		cout<<"Hello"<<endl;
		return 0;
	}
	```

3.  When the code block is too long or contains repeated parts with previously listed code, it is not appropriate to be listed entirely. We will **only give important snippets** and mark it with "Snippet". Therefore, we strongly recommend that readers download all the source code on GitHub and complete the exercises to better understand the book.

4.  Due to typographical reasons, the code shown in the book may be slightly different from the code hosted on GitHub. In that case please use the code on GitHub.

5.  For each of the libraries we use, it will be explained in details when first appearing, but not repeated in the follow-up. Therefore, it is recommended that readers read this book in order.

6.  An abstract will be presented at the beginning of each lecture. A summary and some exercises will be given at the end. The cited references are listed at the end of the book.

7.  The chapters with an asterisk mark in front are optional readings, and readers can read them according to their interest. Skipping them will not hinder the understanding of subsequent chapters.

8.  Important contents will be marked in **bold**, as we are accustomed to.

9.  Most of the experiments we designed are demonstrative. Understanding them does not mean that you are already familiar with the entire library. So we recommend that you spend time on yourselves in further exploring the important libraries frequently used in the book.

10. The book's exercises and optional readings may require you to search for additional materials, so you need to learn to use search engines.

### Acknowledgments

### Exercises (self-test questions)

1. There is a linear equation ![](http://latex.codecogs.com/gif.latex?\\bm{A}\\bm{x}=\\bm{b}), if ![](http://latex.codecogs.com/gif.latex?\\bm{A}) and ![](http://latex.codecogs.com/gif.latex?\\bm{b}) are known, how to solve for ![](http://latex.codecogs.com/gif.latex?\\bm{x})? What are the requirements for ![](http://latex.codecogs.com/gif.latex?\\bm{A}) and ![](http://latex.codecogs.com/gif.latex?\\bm{b})? (Hint: the dimensionality and rank of ![](http://latex.codecogs.com/gif.latex?\\bm{A}))

2. What is a Gaussian distribution? What does it look like in one-dimensional case? How about in high-dimensional case?

3. Do you know what a **class** is in C++? Do you know STL? Have you ever used them?

4. How do you write a C++ program? (It's completely fine if your answer is "using Visual C++ 6.0". As long as you have C++ or C programming experience, you are in good hand)

5. Do you know the C++11 standard? Which new features have you heard of or used? Are you familiar with any other standard?

6. Do you know Linux? Have you used at least one flavor (not including Android), such as Ubuntu?

7. What is the directory structure of Linux? What basic commands do you know? (e.g. ls, cat, etc.)

8. How to install a software in Ubuntu (without using the Software Center)? What directories are software usually installed under? If you only know the fuzzy name of a software (for example, you want to install a library with a word "eigen" in its name), how would you do it?

9. *Spend an hour learning Vim, you will be using it sooner or later. You can enter "vimtutor" in an terminal and read through its contents. We do not require you to operate it very skillfully, as long as you can use it to edit the code in the process of learning this book. **Do not waste time on its plugins, do not try to turn Vim into an IDE for now, we will only use it for text editing.**

### References

- [Davison2007]. A. Davison, I. Reid, N. Molton, and O. Stasse, “Monoslam: Real-time single camera SLAM,” IEEETransactions on Pattern Analysis and Machine Intelligence, vol. 29, no. 6, pp. 1052–1067, 2007.
- [Hartley2003]. R. Hartley and A. Zisserman, Multiple View Geometry in Computer Vision. Cambridge universitypress, 2003.
- [Smith1986]. R. C. Smith and P. Cheeseman, “On the representation and estimation of spatial uncertainty,” In-ternational Journal of Robotics Research, vol. 5, no. 4, pp. 56–68, 1986.
- [Thrun2005]. S. Thrun, W. Burgard, and D. Fox, Probabilistic robotics. MIT Press, 2005.
- T. Barfoot, “State estimation for robotics: A matrix lie group approach,”, Cambridge Press, 2016.
