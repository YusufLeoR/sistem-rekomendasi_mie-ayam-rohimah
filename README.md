# 🍜 Neural Hybrid Recommendation System

Sistem rekomendasi berbasis neural network untuk memprediksi minat pengguna pada video kuliner.

---

## 🚀 Deskripsi Singkat

Model ini memadukan **Collaborative Filtering** (embedding user/video/toko) dan **Content-Based Filtering** (fitur kategori, lokasi, rating, dll) menjadi satu arsitektur hybrid yang kuat.  
Hasilnya, sistem mampu menghasilkan rekomendasi personalisasi Top-N video untuk setiap pengguna.

---

## 🎯 Fitur Utama

- ✅ Embedding multi-entity (user, video, toko)
- ✅ Fitur konten lengkap: kategori, lokasi, jarak, rating
- ✅ Neural network dengan Dense layers
- ✅ Output probabilitas minat user
- ✅ Fungsi rekomendasi Top-N siap pakai

---

## 🧠 Arsitektur Model

**Inputs:**
- Embedding:
  - `user_id`
  - `video_id`
  - `toko_id`
  - `kategori_video`
  - `kategori_toko`
  - `lokasi`
- Numeric:
  - `distance`
  - `latitude`
  - `longitude`
  - `likes_video`
  - `duration`
  - `rating`

**Layers:**
- Concatenate
- Dense (ReLU)
- Output Sigmoid

---

## ⚙️ Cara Pakai

1. **Clone Repository**
   ```bash
   git clone https://github.com/username/repo-name.git
   cd repo-name
````

2. **Install Dependencies**

   ```bash
   pip install -r requirements.txt
   ```

3. **Load Data & Model**
   (Contoh script ada di `sistem_rekomendasi_neural.py`)

4. **Prediksi Rekomendasi**

   ```python
   top_recommendations = recommend_top_n(
       model=model,
       target_user_id=103,
       df_video=df_video,
       df_toko=df_toko,
       le_kategori_video=le_kategori_video,
       le_kategori_toko=le_kategori_toko,
       le_lokasi=le_lokasi,
       scaler=scaler,
       top_n=5
   )
   print(top_recommendations)
   ```

---

## 📝 Contoh Output

| video\_id | toko\_id | kategori\_video | kategori\_toko | lokasi  | prob\_like |
| --------- | -------- | --------------- | -------------- | ------- | ---------- |
| 1003      | 87       | Bakso           | Mie Ayam       | Jakarta | 1.0      |
| ...       | ...      | ...             | ...            | ...     | ...        |

---

## 💡 Catatan Penting

* Pastikan `input_dim` Embedding cukup besar (misal 10,000) untuk mencakup semua ID.
* Input data harus shape `(N,1)` saat inference.
* Model menggunakan TensorFlow >= 2.8.
