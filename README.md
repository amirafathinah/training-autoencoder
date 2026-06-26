# Training di Kaggle dan Rekonstruksi Citra Fashion-MNIST melalui Decoder 

## Identitas Mahasiswa
* **Nama Lengkap:** Amira Fathinah
* **NIM:** 452024618075
* **Program Studi:** Teknik Informatika C1
* **Semester:** 5
* **Mata Kuliah:** Pembelajaran Mesin 2

## Deskripsi
Project ini merupakan implementasi **Autoencoder** menggunakan framework **PyTorch** untuk melakukan kompresi dan rekonstruksi citra pada dataset **Fashion-MNIST**. Model dilatih menggunakan tiga variasi ukuran **latent dimension**, yaitu **2**, **8**, dan **32**. Setelah proses training selesai, model disimpan dalam format `.pth` dan digunakan kembali untuk melakukan proses rekonstruksi citra melalui terminal menggunakan file `reconstruct.py`.

---

# 1. Requirements
## Python
- Python 3.12
## Library
Project ini menggunakan beberapa library berikut.
- torch
- torchvision
- matplotlib
- numpy
- argparse
- os

Install library menggunakan perintah berikut.
```bash
pip install torch torchvision matplotlib numpy
```

# 2. Cara Menjalankan Training di Kaggle

1. Buka Kaggle Notebook.
2. Upload notebook `autoencoder-fashion-mnist.ipynb`.
3. Jalankan seluruh cell menggunakan **Run All**.
4. Model dilatih selama **10 epoch**.
5. Lakukan training sebanyak tiga kali dengan mengganti nilai `latent_dim` menjadi:

```python
latent_dim = 2
```

Kemudian

```python
latent_dim = 8
```

Kemudian

```python
latent_dim = 32
```

6. Setelah proses training selesai, model akan otomatis disimpan dalam format `.pth`.

Contoh nama file model yang dihasilkan:

```
autoencoder_fashion_mnist_latent2.pth
autoencoder_fashion_mnist_latent8.pth
autoencoder_fashion_mnist_latent32.pth
```


# 3. Cara Menjalankan Rekonstruksi dari Terminal

Pastikan file berikut berada dalam satu folder.

```
reconstruct.py
autoencoder_fashion_mnist_latent2.pth
autoencoder_fashion_mnist_latent8.pth
autoencoder_fashion_mnist_latent32.pth
```

Buka Terminal atau Command Prompt pada folder project, kemudian jalankan salah satu perintah berikut.

Program akan melakukan proses berikut.

- Memuat model hasil training (`.pth`).
- Mengambil satu gambar dari dataset Fashion-MNIST.
- Melakukan proses rekonstruksi citra.
- Menyimpan gambar asli, hasil rekonstruksi, dan gambar perbandingan ke folder `outputs`.


# 4. Contoh Perintah Terminal

## Model dengan Latent Dimension = 2

```bash
python reconstruct.py --model autoencoder_fashion_mnist_latent2.pth --latent_dim 2 --index 10
```

## Model dengan Latent Dimension = 8

```bash
python reconstruct.py --model autoencoder_fashion_mnist_latent8.pth --latent_dim 8 --index 10
```

## Model dengan Latent Dimension = 32

```bash
python reconstruct.py --model autoencoder_fashion_mnist_latent32.pth --latent_dim 32 --index 10
```

Parameter yang digunakan:

- `--model` : file model (.pth) yang akan digunakan.
- `--latent_dim` : ukuran latent dimension yang sesuai dengan model.
- `--index` : indeks gambar Fashion-MNIST yang akan direkonstruksi.


# 5. Daftar File Output

## File Model

Hasil training menghasilkan tiga file model.

```
autoencoder_fashion_mnist_latent2.pth
autoencoder_fashion_mnist_latent8.pth
autoencoder_fashion_mnist_latent32.pth
```

## File Rekonstruksi

Setelah menjalankan `reconstruct.py`, program menghasilkan folder `outputs` yang berisi.

```
original.png
reconstructed.png
comparison.png
```

Keterangan:

- **original.png** : gambar asli dari dataset Fashion-MNIST.
- **reconstructed.png** : hasil rekonstruksi yang dihasilkan oleh Autoencoder.
- **comparison.png** : perbandingan antara gambar asli dan hasil rekonstruksi.

---

# Struktur Folder Project

```text
AmiraFathinah_452024618075_Autoencoder
│
├── autoencoder-fashion-mnist.ipynb
├── reconstruct.py
│
├── autoencoder_fashion_mnist_latent2.pth
├── autoencoder_fashion_mnist_latent8.pth
├── autoencoder_fashion_mnist_latent32.pth
│
├── outputs_latent2
│   ├── original.png
│   ├── reconstructed.png
│   └── comparison.png
│
├── outputs_latent8
│   ├── original.png
│   ├── reconstructed.png
│   └── comparison.png
│
├── outputs_latent32
│   ├── original.png
│   ├── reconstructed.png
│   └── comparison.png
│
└── README.md
```


# Hasil Eksperimen

Model dilatih menggunakan tiga ukuran **latent dimension**, yaitu 2, 8, dan 32.

| Latent Dimension | Final Loss |
|-----------------:|-----------:|
| 2 | 0.029433 |
| 8 | 0.016132 |
| 32 | 0.011415 |

Berdasarkan hasil eksperimen, semakin besar ukuran **latent dimension**, semakin kecil nilai **loss** yang diperoleh dan semakin baik kualitas visual hasil rekonstruksi citra. Model dengan **latent dimension 32** menghasilkan performa terbaik karena mampu mempertahankan informasi visual lebih lengkap dibandingkan model dengan latent dimension yang lebih kecil.
