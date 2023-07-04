
# Teori Mendeteksi Marka Jalan
### 1. Membaca dan mengubah warna citra
Membaca dan mengubah warna citra merupakan langkah penting dalam pengolahan citra. 

Membaca Citra:
Membaca citra adalah langkah awal dalam pengolahan citra. Citra dapat berasal dari berbagai sumber, seperti file gambar, kamera, atau sumber data lainnya. Saat membaca citra, setiap piksel dalam citra direpresentasikan dalam bentuk matriks atau array piksel. Setiap piksel menyimpan informasi tentang intensitas atau warna di lokasi piksel tersebut.

Warna dalam Citra Digital:
Citra digital terdiri dari tiga komponen warna dasar: merah (Red), hijau (Green), dan biru (Blue), yang dikenal sebagai model warna RGB (Red-Green-Blue). Setiap piksel dalam citra dapat direpresentasikan oleh kombinasi nilai-nilai intensitas dari ketiga komponen warna tersebut. Misalnya, piksel dengan intensitas merah tinggi dan intensitas hijau serta biru rendah akan menghasilkan warna merah murni, sedangkan piksel dengan intensitas merah, hijau, dan biru yang sama akan menghasilkan warna abu-abu.

Konversi Warna:
Konversi warna adalah proses mengubah representasi warna citra dari satu model warna ke model warna lainnya. Dalam kodingan yang diberikan, terdapat konversi warna dari BGR (Blue-Green-Red) ke RGB (Red-Green-Blue) menggunakan fungsi cv2.cvtColor(image, cv2.COLOR_BGR2RGB). Hal ini dilakukan untuk memastikan citra ditampilkan dengan benar menggunakan library matplotlib, yang mengharapkan format warna RGB.

Mengubah Warna Citra:
Setelah citra diubah ke dalam format yang diinginkan, kita dapat melakukan manipulasi pada warna citra. Misalnya, kita dapat memanipulasi intensitas warna, mengubah saluran warna tertentu, atau menerapkan efek warna. Dalam kodingan tersebut, tidak ada manipulasi warna yang dilakukan, tetapi langkah selanjutnya adalah melakukan proses pengolahan citra lainnya, seperti pengaburan, segmentasi warna, atau deteksi objek.

### 2. Gaussian Blur
Gaussian Blur adalah suatu teknik dalam pengolahan citra yang digunakan untuk mengurangi noise atau detail kecil dalam citra. Teknik ini mengaburkan citra dengan menerapkan filter Gaussian pada setiap piksel citra. Filter Gaussian adalah filter linear yang memperhalus citra dengan memberikan bobot yang lebih besar pada piksel-piksel yang berdekatan dan bobot yang lebih kecil pada piksel-piksel yang lebih jauh.

Proses Gaussian Blur dilakukan dengan mengambil sejumlah tetangga piksel dari piksel yang sedang diproses, dan setiap piksel tetangga tersebut diberi bobot sesuai dengan fungsi Gauss yang mengikuti distribusi Gauss (bell-shaped). Bobot-bobot tersebut kemudian dinormalisasi sehingga jumlah bobotnya sama dengan 1. Proses ini dilakukan secara iteratif pada setiap piksel citra.

Berikut adalah langkah-langkah dalam penerapan Gaussian Blur pada citra:

Tentukan ukuran kernel: Kernel adalah matriks berukuran (n x n) yang digunakan untuk mengambil tetangga piksel dalam proses Gaussian Blur. Ukuran kernel menentukan seberapa besar area yang diambil sebagai tetangga setiap piksel. Biasanya, ukuran kernel berukuran ganjil, misalnya 3x3, 5x5, atau 7x7.

Hitung nilai bobot dalam kernel: Setiap piksel dalam kernel diberi bobot sesuai dengan fungsi Gauss. Bobot ini menentukan seberapa besar pengaruh tetangga piksel terhadap piksel yang sedang diproses. Nilai bobot dihitung menggunakan rumus:

w(i, j) = (1 / (2 * π * σ^2)) * exp(-((i - m)^2 + (j - n)^2) / (2 * σ^2))

di mana (i, j) adalah posisi piksel dalam kernel, (m, n) adalah pusat kernel, dan σ adalah standar deviasi yang mengontrol seberapa lebar distribusi Gauss. Semakin besar nilai σ, semakin lebar distribusi Gauss, dan semakin besar pengaruh tetangga piksel.

Normalisasi bobot: Setelah menghitung bobot dalam kernel, bobot-bobot tersebut dinormalisasi agar jumlah bobotnya sama dengan 1. Hal ini dilakukan dengan membagi setiap bobot dengan jumlah total bobot dalam kernel.

Terapkan filter Gaussian pada setiap piksel: Setelah mendapatkan kernel dengan bobot yang sudah dinormalisasi, filter Gaussian diterapkan pada setiap piksel citra. Untuk setiap piksel, tetangga pikselnya yang berada dalam ukuran kernel diambil, dan masing-masing piksel tetangga dikalikan dengan bobotnya. Hasil perkalian tersebut kemudian dijumlahkan untuk menghasilkan nilai baru untuk piksel tersebut. Proses ini diulang untuk setiap piksel dalam citra.

### 3. Konversi Warna Citra
Konversi warna citra adalah proses mengubah representasi warna sebuah citra dari satu ruang warna ke ruang warna lainnya. Setiap ruang warna memiliki cara yang berbeda untuk merepresentasikan warna dalam bentuk bilangan atau vektor. Konversi warna citra sangat penting dalam pengolahan citra untuk berbagai tujuan, seperti penyesuaian warna, analisis warna, segmentasi warna, dan pengenalan objek berdasarkan warna.

Salah satu konversi warna citra yang umum adalah konversi dari ruang warna BGR (Blue-Green-Red) ke ruang warna RGB (Red-Green-Blue) atau sebaliknya. Ruang warna BGR merupakan format standar dalam OpenCV, sedangkan RGB merupakan format yang lebih umum digunakan dalam pemrosesan dan tampilan citra.

Konversi warna citra antara BGR dan RGB dilakukan dengan menukar posisi komponen warna biru (B) dengan komponen warna merah (R). Hal ini dilakukan karena perbedaan konvensi penamaan komponen warna antara OpenCV dan standar RGB.

Proses konversi warna citra BGR ke RGB dapat dilakukan dengan langkah-langkah berikut:

Membaca citra: Citra BGR dibaca menggunakan library atau fungsi yang sesuai, seperti cv2.imread() dalam OpenCV.
Konversi warna: Citra BGR dikonversi menjadi citra RGB menggunakan fungsi cv2.cvtColor() dengan parameter cv2.COLOR_BGR2RGB.
Penggunaan citra hasil konversi: Citra RGB dapat digunakan untuk tujuan-tujuan seperti tampilan, analisis, atau pemrosesan selanjutnya.
Pada kodingan yang diberikan, terdapat langkah konversi warna citra dari BGR ke RGB menggunakan fungsi cv2.cvtColor() dengan parameter cv2.COLOR_BGR2RGB. Hal ini dilakukan untuk memastikan citra dapat ditampilkan dengan benar menggunakan library matplotlib.pyplot, yang menggunakan format RGB.

### 4. Range Warna 
Range warna adalah konsep dalam pengolahan citra yang digunakan untuk menentukan batasan atau rentang nilai warna yang akan diidentifikasi atau diambil dalam sebuah citra. Pada umumnya, range warna didefinisikan dalam sistem warna tertentu seperti RGB (Red, Green, Blue) atau HSV (Hue, Saturation, Value).

Dalam konteks pengolahan citra, range warna sangat berguna untuk melakukan segmentasi objek berdasarkan warna. Dengan menentukan range warna yang spesifik, kita dapat mengisolasi objek yang memiliki warna tertentu dalam sebuah citra.

Berikut adalah penjelasan lebih rinci tentang range warna dalam format HSV:

Hue (H): Hue mengacu pada jenis warna itu sendiri, seperti merah, hijau, biru, kuning, dan sebagainya. Rentang nilai Hue biasanya adalah 0-360 derajat, tetapi dalam OpenCV, rentang biasanya dipersempit menjadi 0-180 untuk memudahkan perhitungan. Misalnya, 0 derajat dapat mewakili merah, 60 derajat dapat mewakili kuning, 120 derajat mewakili hijau, dan seterusnya.

Saturation (S): Saturation mengacu pada kekayaan atau keintensifan warna. Nilai 0 berarti warna sepenuhnya netral (abu-abu) atau tidak jenuh, sedangkan nilai 1 berarti warna sepenuhnya jenuh atau terang. Rentang nilai Saturation biasanya adalah 0-1.

Value (V): Value mengacu pada kecerahan atau intensitas cahaya dari warna. Nilai 0 berarti kegelapan total atau hitam, sedangkan nilai maksimum (biasanya 1 atau 255 dalam skala 8-bit) berarti kecerahan penuh atau putih. Rentang nilai Value juga biasanya adalah 0-1.

Dalam kodingan yang diberikan, terdapat definisi range warna untuk mendeteksi marka jalan pada citra menggunakan format HSV. lower_yellow adalah batas bawah atau lower bound untuk rentang warna kuning yang akan dideteksi, sedangkan upper_yellow adalah batas atas atau upper bound-nya. Rentang warna ini digunakan untuk membuat mask dengan menggunakan fungsi cv2.inRange() yang akan menghasilkan citra biner di mana piksel-piksel yang berada dalam rentang warna tersebut akan menjadi putih (255) dan piksel lainnya menjadi hitam (0).

### 5. Masking
Masking adalah salah satu teknik dalam pengolahan citra yang digunakan untuk memisahkan atau menghilangkan bagian-bagian tertentu dalam citra berdasarkan kondisi tertentu. Teknik ini biasanya digunakan untuk fokus pada area yang menarik atau untuk menghilangkan gangguan atau elemen yang tidak diinginkan dari citra.

Konsep Dasar:

Masking melibatkan penggunaan sebuah mask atau gambar biner dengan ukuran yang sama dengan citra asli. Mask adalah citra yang terdiri dari piksel-piksel hitam dan putih, dengan piksel putih menunjukkan area yang ingin dipertahankan dan piksel hitam menunjukkan area yang ingin dihilangkan.

Jenis Masking:

Binary Masking: Masking menggunakan citra biner, di mana piksel putih menunjukkan area yang ingin dipertahankan dan piksel hitam menunjukkan area yang ingin dihilangkan.
Color Masking: Masking berdasarkan rentang warna tertentu dalam citra. Piksel yang berada dalam rentang warna ditandai sebagai putih, sedangkan piksel di luar rentang warna ditandai sebagai hitam.
Proses Masking:

Proses masking melibatkan kombinasi piksel-piksel pada citra asli dengan piksel-piksel pada mask. Setiap piksel pada citra asli akan diproses sesuai dengan nilai piksel yang sesuai pada mask.
Jika piksel pada mask adalah putih, maka piksel yang sesuai pada citra asli akan dipertahankan.
Jika piksel pada mask adalah hitam, maka piksel yang sesuai pada citra asli akan dihilangkan atau diberi nilai nol.
Manfaat Masking:

Memfokuskan perhatian pada area penting: Masking memungkinkan kita untuk menyorot area-area tertentu dalam citra yang memiliki kepentingan khusus, seperti objek atau fitur yang ingin ditonjolkan.
Menghilangkan gangguan atau elemen tidak diinginkan: Dengan menggunakan masking, kita dapat menghilangkan bagian-bagian citra yang tidak diperlukan atau menjadi gangguan dalam analisis atau pemrosesan selanjutnya.
Memisahkan objek dari latar belakang: Masking dapat digunakan untuk memisahkan objek yang diinginkan dari latar belakang atau elemen lain dalam citra.
Menggabungkan citra: Masking juga dapat digunakan untuk menggabungkan beberapa citra dengan cara memilih area tertentu dari setiap citra dan menggabungkannya menjadi satu citra.
Implementasi dalam Kodingan:

Dalam kodingan yang diberikan, masking dilakukan menggunakan fungsi cv2.inRange(). Fungsi ini menghasilkan citra biner (mask) di mana piksel yang berada dalam rentang warna tertentu ditandai sebagai putih dan piksel di luar rentang warna ditandai sebagai hitam.
Mask yang dihasilkan kemudian digunakan dalam proses deteksi marka jalan, di mana hanya piksel-piksel pada citra yang sesuai dengan piksel putih pada mask yang dipertahankan, sementara piksel-piksel yang sesuai dengan piksel hitam pada mask dihilangkan.

### 6. Deteksi Tepi (Edge Detection)
Deteksi tepi (edge detection) merupakan salah satu teknik penting dalam pengolahan citra yang bertujuan untuk menemukan garis tepi yang terdapat dalam citra. Deteksi tepi digunakan dalam berbagai aplikasi seperti segmentasi objek, ekstraksi fitur, pengenalan pola, dan pemrosesan citra lanjutan.

Deteksi tepi berfungsi untuk menemukan perbedaan intensitas yang signifikan antara piksel-piksel tetangga dalam citra. Perbedaan ini menunjukkan adanya perubahan signifikan dalam citra, yang sering kali berkorelasi dengan perubahan dalam konten visual seperti perbatasan antara objek atau perubahan tekstur.

Algoritma yang digunakan dalam deteksi tepi:

Operator Gradient:

Operator Sobel: Menggunakan filter Sobel untuk menghitung gradien citra dalam arah horizontal dan vertikal.
Operator Prewitt: Mirip dengan Sobel, namun menggunakan kernel Prewitt.
Operator Laplacian:

Operator Laplacian: Menggunakan filter Laplacian untuk menghitung gradien kedua citra.
Operator Canny:

Operator Canny: Menggunakan beberapa tahap pemrosesan untuk mendapatkan tepi yang lebih akurat. Tahap-tahapnya meliputi: pemulusan citra dengan Gaussian blur, perhitungan gradien dengan operator Sobel, pemilihan tepi dengan non-maximum suppression, dan hysteresis thresholding.
Operator LoG (Laplacian of Gaussian):

Operator LoG: Menggabungkan operasi pemulusan dengan Gaussian blur dan deteksi tepi dengan operator Laplacian.
Operator Roberts:

Operator Roberts: Menggunakan dua kernel kecil untuk menghitung gradien citra dalam arah diagonal.

### 7. Deteksi Garis
Deteksi Garis menggunakan metode Transformasi Hough (Hough Transform) adalah sebuah teknik dalam pengolahan citra yang digunakan untuk mendeteksi garis-garis lurus dalam citra yang kompleks atau mengandung banyak noise. Metode ini dapat mengidentifikasi garis-garis secara akurat meskipun terdapat perbedaan intensitas atau gangguan pada citra.

Representasi Garis dalam Koordinat Hough:

Pada metode Hough Transform, garis-garis dalam citra direpresentasikan dalam parameter (θ, ρ) dalam ruang Hough.
Parameter θ (theta) adalah sudut antara garis dan sumbu x.
Parameter ρ (rho) adalah jarak garis dari titik asal (0, 0) dalam garis tegak lurus terhadap garis tersebut.
Konversi Citra:

Sebelum menggunakan Hough Transform, citra biasanya diolah terlebih dahulu dengan langkah-langkah seperti deteksi tepi menggunakan operator seperti Canny.
Hal ini bertujuan untuk memperoleh kontur yang jelas dari garis-garis yang ada dalam citra.
Pembuatan Ruang Hough:

Ruang Hough adalah representasi dua dimensi yang menggunakan parameter (θ, ρ) untuk mendeteksi garis dalam citra.
Ruang Hough biasanya disimpan dalam bentuk matriks atau array yang diinisialisasi dengan nilai 0.
Proses Akumulasi:

Setiap piksel yang ada pada kontur atau tepi dalam citra memberikan kontribusi dalam akumulasi ruang Hough.
Untuk setiap piksel dalam kontur, semua kemungkinan garis yang melewati piksel tersebut dipertimbangkan.
Pada setiap iterasi, nilai yang sesuai dalam matriks ruang Hough diinkrementasi.
Pencarian Garis dalam Ruang Hough:

Setelah proses akumulasi selesai, pencarian dilakukan untuk menemukan puncak atau nilai maksimum dalam ruang Hough.
Nilai maksimum tersebut menunjukkan parameter (θ, ρ) yang sesuai dengan garis dalam citra.
Penentuan Garis:

Setelah nilai maksimum ditemukan dalam ruang Hough, garis yang sesuai dapat ditentukan berdasarkan parameter (θ, ρ) tersebut.
Garis dapat direkonstruksi menggunakan parameter yang ditemukan, seperti menggunakan titik awal dan akhir untuk menggambar garis pada citra asli.

### 8. Visualisasi Hasil
Visualisasi hasil adalah proses menampilkan informasi atau data dalam bentuk visual yang mudah dipahami. Dalam konteks pengolahan citra, visualisasi hasil bertujuan untuk menggambarkan citra yang telah diproses atau fitur-fitur yang ditemukan dalam citra secara jelas dan intuitif. Hal ini memudahkan pemahaman dan interpretasi data oleh pengguna.

Dalam kodingan yang diberikan, terdapat visualisasi hasil menggunakan matplotlib, sebuah library Python yang sering digunakan untuk visualisasi data dan citra.  Penjelasan mengenai visualisasi hasil:

Mengimport Library:

import matplotlib.pyplot as plt: Mengimport library matplotlib untuk membuat visualisasi dan plot.
Membuat Figure dan Axis:

Fig, ax = plt.subplots(1, 2, figsize=(12, 10)): Membuat sebuah figure dengan dua axis (subplot) dengan ukuran 1x2. Ukuran figure ditentukan oleh parameter figsize dengan lebar 12 dan tinggi 10.
Menampilkan Citra Asli:

ax[0].imshow(image_asli): Menampilkan citra asli pada axis pertama (ax[0]) menggunakan metode imshow().
Menampilkan Deteksi Marka Jalan:

ax[1].imshow(image_rgb): Menampilkan citra hasil deteksi marka jalan pada axis kedua (ax[1]) menggunakan metode imshow().
Memberikan Judul pada Plot:

ax[0].set_title('Gambar Asli'): Memberikan judul "Gambar Asli" pada axis pertama.
ax[1].set_title('Deteksi Marka Jalan'): Memberikan judul "Deteksi Marka Jalan" pada axis kedua.
Menampilkan Plot:

plt.show(): Menampilkan plot dengan semua citra dan judul yang telah ditentukan.



# Tahapan Penyelesaian Project

1. Import library:

a. cv2 adalah library OpenCV untuk pemrosesan gambar dan video.
b. numpy digunakan untuk operasi array dan matriks.
c. matplotlib.pyplot digunakan untuk menampilkan gambar.

2. Membaca gambar:
a. image = cv2.imread("Garis Parkiran Mobil.jpeg") membaca gambar dengan nama file "Garis Parkiran Mobil.jpeg" menggunakan fungsi cv2.imread().

3.Konversi warna:
image_asli = cv2.cvtColor(image, cv2.COLOR_BGR2RGB) mengonversi gambar dari format BGR (Blue-Green-Red) menjadi RGB (Red-Green-Blue) menggunakan fungsi cv2.cvtColor().

4. Pemrosesan gambar:

a. blurred_frame = cv2.GaussianBlur(image, (5, 5), 0) menggunakan filter Gaussian untuk mengaburkan gambar dan mengurangi noise.
b. hsv = cv2.cvtColor(blurred_frame, cv2.COLOR_BGR2HSV) mengonversi gambar yang sudah diblur menjadi format HSV (Hue-Saturation-Value), yang memudahkan dalam deteksi warna tertentu.

5. Menentukan range warna:

a. lower_yellow = np.array([20, 100, 100], dtype=np.uint8) mendefinisikan batas bawah range warna kuning dalam format HSV.
b. upper_yellow = np.array([30, 255, 255], dtype=np.uint8) mendefinisikan batas atas range warna kuning dalam format HSV.

6. Membuat mask:
mask = cv2.inRange(hsv, lower_yellow, upper_yellow) Membuat mask dengan menggunakan fungsi cv2.inRange() untuk mendapatkan area dengan warna kuning dalam gambar.

7.Deteksi tepi:
edges = cv2.Canny(mask, 74, 150) menggunakan metode Canny untuk mendeteksi tepi dalam gambar dengan mengambil input mask, nilai ambang bawah (74), dan nilai ambang atas (150).

8.Deteksi garis:
lines = cv2.HoughLinesP(edges, 1, np.pi / 100, 50, maxLineGap=50) menggunakan transformasi Hough Probabilistik (cv2.HoughLinesP()) untuk mendeteksi garis-garis dalam gambar berdasarkan tepi yang telah dideteksi sebelumnya. Parameter yang digunakan adalah: jarak resolusi spasial (1), resolusi sudut (np.pi / 100), ambang batas (50), dan ambang batas gap antar-garis (50).

9. Menggambar garis pada gambar asli:

Jika terdapat garis-garis yang terdeteksi (lines is not None), maka untuk setiap garis (line) yang terdeteksi, koordinat titik awal dan titik akhir garis ditentukan (x1, y1, x2, y2 = line[0]), dan kemudian garis tersebut digambar pada gambar asli (cv2.line(image, (x1, y1), (x2, y2), (0, 255, 0), 5)).

10. Konversi warna kembali:
image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB) mengonversi gambar dengan garis yang telah ditambahkan kembali ke format RGB menggunakan fungsi cv2.cvtColor().

11. Menampilkan gambar:

Fig, ax = plt.subplots(1, 2, figsize=(12, 10)) membuat sebuah figure dengan 2 axes (subplots) dengan ukuran 12x10.
ax[0].imshow(image_asli) menampilkan gambar asli pada axes pertama.
ax[0].set_title('Gambar Asli') memberikan judul pada axes pertama.
ax[1].imshow(image_rgb) menampilkan gambar dengan deteksi marka jalan pada axes kedua.
ax[1].set_title('Deteksi Marka Jalan') memberikan judul pada axes kedua.
plt.show() menampilkan figure dengan gambar-gambar yang telah ditambahkan.
## LINK JURNAL 
https://sttpln-my.sharepoint.com/:f:/g/personal/haya2131087_itpln_ac_id/Ep9If4nNbt1BthUhAaOESN8B-ra0_GMH4AZGLDqoU0y1QQ?e=DMskIi

link jurnal terkait project