# Aplikasi Rekomendasi Pekerjaan Berdasarkan CV

Aplikasi ini memberikan rekomendasi pekerjaan berdasarkan CV yang diunggah pengguna. Dengan memanfaatkan model machine learning dan teknik pemrosesan teks, aplikasi ini mencocokkan keterampilan yang tercantum di CV dengan daftar pekerjaan yang tersedia dan memberikan tiga rekomendasi pekerjaan dengan nilai kecocokan tertinggi.

## Cara Kerja File
Setiap file dalam proyek ini memiliki fungsi dan peran spesifik yang mendukung keseluruhan sistem. Berikut adalah penjelasan bagaimana semua file bekerja:

1. **app.py**  
   File utama yang berisi API untuk menjalankan aplikasi.  
   - **Fungsi utama:**  
     - Route `/recommend`: Mengambil CV dalam format teks sebagai input, memprosesnya melalui pipeline (preprocessing, parsing skill, matching score), dan menghasilkan rekomendasi pekerjaan.

2. **matching_model.h5**  
   Model deep learning yang dilatih untuk mencocokkan skor keterampilan di CV dengan skor keterampilan dalam daftar pekerjaan.  
   - **Input:**  
     - Vektor keterampilan yang diproses dari CV dan daftar pekerjaan.  
   - **Output:**  
     - Skor kecocokan untuk setiap pekerjaan dalam daftar.  

3. **tfidf_vectorizer.json**  
   Berisi representasi vektor TF-IDF yang digunakan untuk memastikan pemrosesan teks konsisten selama proses preprocessing dan pencocokan.  
   - **Fungsi:**  
     - Mengonversi teks skill menjadi vektor numerik untuk digunakan dalam model.  

4. **valid_skills.json**  
   File JSON yang berisi daftar keterampilan yang valid.  
   - **Fungsi:**  
     - Parsing bagian keterampilan dalam CV dan memvalidasi keterampilan tersebut berdasarkan daftar keterampilan yang diakui.  

5. **requirements.txt**  
   Berisi daftar pustaka Python yang diperlukan untuk menjalankan aplikasi.  
   - **Digunakan untuk:**  
     - Memastikan semua dependensi diinstal dengan versi yang kompatibel.

## Alur Kerja Sistem
1. **Input CV:**  
   Pengguna memberikan CV dalam format teks melalui endpoint `/recommend`.  

2. **Preprocessing dan Parsing Skill:**  
   - CV diproses untuk mengekstrak bagian keterampilan.  
   - Keterampilan yang diekstrak divalidasi dengan daftar keterampilan dalam `valid_skills.json`.  

3. **Matching Score:**  
   - Keterampilan yang divalidasi diubah menjadi vektor TF-IDF menggunakan `tfidf_vectorizer.json`.  
   - Vektor keterampilan dibandingkan dengan vektor keterampilan dalam daftar pekerjaan menggunakan model `matching_model.h5`.  

4. **Rekomendasi Pekerjaan:**  
   - Tiga pekerjaan dengan nilai kecocokan tertinggi dipilih dari daftar pekerjaan.  

5. **Output:**  
   - API memberikan respons berupa JSON yang berisi:  
     - **Keterampilan yang dikenali dari CV.**  
     - **Tiga pekerjaan yang direkomendasikan beserta skor kecocokan.**
