## Tugas 2: Sistem Kontrol Kecepatan Kendaraan Otomatis dengan Fuzzy Logic

Branch ini berisi implementasi sistem kontrol fuzzy logic untuk mengatur kecepatan kendaraan secara otomatis berdasarkan kondisi berkendara.

### Deskripsi

Sistem ini menggunakan fuzzy logic untuk menentukan akselerasi kendaraan yang optimal berdasarkan:
- **Input 1**: Kecepatan saat ini (0-150 km/jam)
- **Input 2**: Jarak ke kendaraan di depan (0-200 meter)
- **Input 3**: Batas kecepatan jalan (40-100 km/jam)
- **Output**: Akselerasi yang diinginkan (-5 hingga 5 m/s²)

Output akselerasi:
- Nilai positif: tambah kecepatan
- Nilai negatif: kurangi kecepatan (rem)
- Nilai nol: pertahankan kecepatan

### File

- `vehicle_speed_control.ipynb` - Jupyter notebook yang berisi implementasi lengkap sistem fuzzy logic
- `vehicle_speed_control_dataset.csv` - Dataset untuk testing sistem (130 data points)

### Instalasi

1. Pastikan Python 3.11+ terinstal
2. Install dependencies:
```bash
pip install -r requirements.txt
```

3. Install ipykernel untuk menjalankan notebook (opsional):
```bash
pip install ipykernel
```

### Menjalankan

1. Buka `vehicle_speed_control.ipynb` di Jupyter Notebook atau VS Code
2. Restart kernel (Kernel → Restart)
3. Jalankan semua cell secara berurutan (Run All)

### Fitur

- **Dataset Generation**: 130 data points dengan berbagai skenario berkendara
- **Exploratory Data Analysis (EDA)**:
  - Distribusi data untuk semua variabel
  - Matriks korelasi antar variabel
- **Fuzzy Logic Implementation**:
  - 3 input variables dengan 3 membership functions masing-masing
  - 1 output variable dengan 5 membership functions
  - 19 fuzzy rules untuk coverage lengkap
- **Visualisasi**:
  - Membership functions untuk semua variabel
  - Scatter plot actual vs predicted
  - Distribusi error dan box plot
  - Perbandingan bar chart untuk 50 samples
- **Evaluasi**:
  - Mean Absolute Error (MAE)
  - Mean Squared Error (MSE)
  - Root Mean Squared Error (RMSE)
  - Mean Absolute Percentage Error (MAPE)
  - Analisis error berdasarkan kategori kecepatan dan jarak
- **Testing**:
  - Testing dengan 5 sample cases
  - Evaluasi dengan seluruh dataset
  - Simulasi interaktif untuk testing manual

### Fuzzy Rules Logic

Sistem menggunakan prioritas keputusan:
1. **Keselamatan Utama**: Jarak dekat → Rem keras (apapun kondisinya)
2. **Kecepatan vs Batas**: Kecepatan tinggi + batas rendah → Rem
3. **Akselerasi Aman**: Kecepatan rendah + jarak jauh → Akselerasi
4. **Maintain**: Kecepatan sesuai batas + jarak sedang → Pertahankan

### Aplikasi

- Cruise control adaptif
- Sistem bantuan pengemudi (ADAS - Advanced Driver Assistance Systems)
- Kendaraan otonom
- Sistem peringatan tabrakan
