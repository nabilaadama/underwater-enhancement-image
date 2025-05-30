# Image Enhancement Tool

Aplikasi Python untuk meningkatkan kualitas gambar dengan teknik noise reduction dan color correction menggunakan OpenCV dan teknik morphological operations.

## 📋 Deskripsi

Tool ini dirancang untuk melakukan enhancement pada gambar dengan fokus pada:
- **Noise Reduction**: Mengurangi noise menggunakan kombinasi median filtering, morphological opening, dan Gaussian blur
- **Color Correction**: Memperbaiki keseimbangan warna dan kontras gambar
- **Analisis Metrik**: Menghitung berbagai metrik kualitas gambar seperti MSE, PSNR, dan peningkatan kontras

## 🚀 Fitur Utama

### 1. Noise Reduction
- Median filtering untuk menghilangkan salt-and-pepper noise
- Morphological opening dengan kernel lingkaran custom
- Gaussian blur untuk smoothing selektif

### 2. Color Correction
- Penyesuaian channel RGB individual
- Normalisasi berdasarkan rata-rata grayscale
- Peningkatan kontras dan keseimbangan warna

### 3. Analisis Metrik
- **MSE (Mean Square Error)**: Mengukur perbedaan pixel
- **PSNR (Peak Signal-to-Noise Ratio)**: Kualitas sinyal
- **Contrast Improvement**: Peningkatan kontras
- **Balance Improvement**: Perbaikan keseimbangan warna

### 4. Visualisasi
- Perbandingan gambar before/after
- Histogram distribusi warna
- Tampilan metrik teknis

## 📦 Dependencies

```
numpy
opencv-python (cv2)
matplotlib
```

## 🛠️ Instalasi

1. **Clone atau download kode**
   ```bash
   # Jika dari repository
   git clone <repository-url>
   cd image-enhancement-tool
   ```

2. **Install dependencies**
   ```bash
   pip install numpy opencv-python matplotlib
   ```

   Atau menggunakan requirements file:
   ```bash
   pip install -r requirements.txt
   ```

3. **Siapkan gambar input**
   - Letakkan file gambar di direktori yang sama dengan script
   - Pastikan format gambar didukung (JPG, PNG, BMP, dll.)

## 🎯 Cara Penggunaan

### Method 1: Direct Execution
```bash
python image_enhancement.py
```

### Method 2: Custom Image Path
Edit bagian `main()` function untuk mengubah path gambar:
```python
def main():
    path = 'nama_gambar_anda.jpg'  # Ganti dengan path gambar Anda
    # ... rest of the code
```

### Method 3: Import sebagai Module
```python
from image_enhancement import load_image, noise_reduction, color_correction, calculate_metrics

# Load gambar
original = load_image('your_image.jpg')

# Proses enhancement
denoised = noise_reduction(original)
enhanced = color_correction(denoised)

# Hitung metrik
metrics = calculate_metrics(original, enhanced)
```

## 📁 Struktur File

```
project/
│
├── image_enhancement.py    
├── pari2.jpg              
└── README.md         
```

## 🔧 Parameter yang Dapat Disesuaikan

### Noise Reduction
- **Kernel size**: Ubah parameter `size` di `create_morphological_kernel()`
- **Median blur kernel**: Ubah parameter kedua di `cv2.medianBlur()`
- **Gaussian blur**: Sesuaikan parameter `(3, 3), 0.5` di `cv2.GaussianBlur()`

### Color Correction
```python
img[:, :, 0] *= 1.35  # Red channel
img[:, :, 1] *= 0.70  # Green channel  
img[:, :, 2] *= 0.85  # Blue channel
```

## 📊 Output

Setelah eksekusi, Anda akan mendapatkan:

1. **Visualisasi Matplotlib** dengan 4 panel:
   - Gambar asli
   - Gambar hasil enhancement
   - Histogram warna gambar asli
   - Histogram warna gambar hasil

2. **Metrik Teknis** di console:
   ```
   Metrik Teknis:
      • MSE (Mean Square Error): XX.XX
      • PSNR (Peak Signal-to-Noise Ratio): XX.XX dB
      • Peningkatan Kontras: X.XXx
      • Peningkatan Color Balance: X.XXx
   
   Perubahan Visual:
      • Brightness Original: XXX.X
      • Brightness Enhanced: XXX.X
      • Kontras Original: XX.X
      • Kontras Enhanced: XX.X
   ```

## 🎛️ Troubleshooting

### Error: FileNotFoundError
```bash
# Pastikan file gambar ada di direktori yang benar
ls -la *.jpg *.png  # Linux/Mac
dir *.jpg *.png     # Windows
```

### Error: ModuleNotFoundError
```bash
# Install dependencies yang hilang
pip install opencv-python numpy matplotlib
```

### Gambar tidak muncul
```python
# Tambahkan di akhir script jika menggunakan environment tertentu
plt.show(block=True)
```

**Catatan**: Pastikan gambar input memiliki resolusi yang wajar untuk performa optimal. Untuk gambar berukuran sangat besar, pertimbangkan untuk melakukan resize terlebih dahulu.