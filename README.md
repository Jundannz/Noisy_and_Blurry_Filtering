# Tugas 2 PCD: Penanganan Noise dan Penajaman Citra Blur

Eksperimen penanganan noise (averaging filter dan median filter) serta penajaman citra blur (laplacian filter 4-tetangga dan 8-tetangga) untuk mata kuliah Pengolahan Citra Digital.

## Struktur folder

```
.
├── images/
│   ├── noisy_image.jpg
│   ├── noisy_image2.jpg
│   ├── noisy_image3.jpg
│   ├── blurred_image.jpg
│   ├── blurred_image2.jpg
│   └── blurred_image3.jpg
├── PCD_Assignment02.ipynb
├── Laporan_PCD_Image_Enhancement_Using_Filtering_Jundan.pdf
└── README.md
```

`images/` berisi enam data sekunder yang dipakai sebagai input, terbagi dua kelompok: tiga citra noisy dan tiga citra blur. Notebook berisi seluruh kode eksperimen, dan laporan PDF berisi hasil serta analisisnya.

## Isi eksperimen

Semua citra dimuat langsung dalam grayscale lewat `cv2.imread` dengan flag `cv2.IMREAD_GRAYSCALE`, tanpa tahap resize atau crop tambahan. Citra noisy berukuran 321x481 piksel, citra blur berukuran 1365x2048 piksel.

Dua eksperimen utama dijalankan:

1. **Penanganan noise**, ketiga citra noisy diproses dengan averaging filter (mean 3x3) dan median filter (3x3), keduanya dibangun manual lewat sliding window dan zero padding.
2. **Penajaman citra blur**, ketiga citra blur diproses dengan konvolusi spasial memakai kernel laplacian komposit, dalam dua varian ketetanggaan: 4-tetangga dan 8-tetangga (faktor c = 3.0, mode high-boost).

Catatan cakupan pengujian: verifikasi zoom-in dan peta selisih untuk melihat efek penajaman laplacian hanya dilakukan pada `blurred_image2.jpg`. Untuk `blurred_image.jpg` dan `blurred_image3.jpg`, perbandingan yang tersedia hanya sebatas tampilan skala penuh. Tidak ada pengukuran numerik (variance atau sharpness metric) yang dihitung untuk membandingkan hasil laplacian 4-tetangga vs 8-tetangga secara kuantitatif. Detail dan alasan pembagian ini ada di laporan.

Rincian lengkap desain eksperimen, hasil, dan analisis (termasuk waktu eksekusi tiap filter) ada di `Laporan_PCD_Noise_Blur.pdf`.

## Menjalankan notebook

Notebook ditulis untuk Google Colab dan memakai Google Drive sebagai sumber citra (lihat sel `drive.mount` dan `DRIVE_IMG_DIR`). Untuk menjalankan di luar Colab, ganti bagian mount drive dan `DRIVE_IMG_DIR` dengan path lokal ke folder `images/`.

Dependencies:

```
opencv-python
numpy
matplotlib
```

## Penulis

Jundan Saiful Haq
NIM 25/560768/PA/23633
