# LoanPrediction
# Laporan Proyek Machine Learning - Imroatus Sholihah

## Keuangan

Dengan berkembanganya teknologi, peminjaman uang dapat dilakukan dengan mudah. Salah satunya menggunakan teknologi machine learning untuk mengklasifikasikan apakah seseorang beresiko mengalami gagal bayar hutang di masa mendatang. Dengan klasifikasi resiko gagal bayar hutang, dapat membantu pihak peminjaman uang seperti Bank, koperasi, dan lembaga peminjaman untuk mengurangi kerugian akibat nasabah yang gagal membayar. Apalagi dengan banyaknya data nasabah, akan menyusahkan untuk mengklasifikasikan secara manual, sehingga klasifikasi dengan machine learning akan sangat membantu.

## Business Understanding
### Problem Statements

Menjelaskan pernyataan masalah latar belakang:
- Bagaimana cara mengklasifikasikan nasabah yang berisiko gagal bayar hutang?
- Bagaimana kinerja machine learning dalam mengklasifikasi masalah ini?

### Goals

Menjelaskan tujuan dari pernyataan masalah:
- Mengklasifikasikan nasabah yang berisiko gagal bayar hutang atau tidak berdasarkan data nasabah.
- Mengetahui kinerja machine learning dalam mengklasifikasikan risiko

 ### Solution statements
   - Melakukan eksploratori data analisis untuk menentukan fitur/variabel yang digunakan sebagai prediktor
   - Menggunakan 2 algoritma machine learning (random forest) dan deep learning (neural network) untuk membandingkan performance kedua model
   - menentukan model yang lebih baik berdasarkan metriks akurasi

## Data Understanding
Data yang digunakan berasal dari kaggle, yaitu Loan Prediction Based on Customer Behavior dataset. dalam train data, terdiri dari 13 kolom dan 252.000 baris. dataset terdiri dari numerical dan categorical data. 
 dataset diperoleh dari https://www.kaggle.com/datasets/subhamjain/loan-prediction-based-on-customer-behavior?rvi=1

### Variabel-variabel pada loan prediction adalah sebagai berikut:
- income: Income of the user
- age: Age of the user
- experience: Professional experience of the user in years
- profession: Profession
- married: Whether married or single
- house_ownership: Owned or rented or neither
- car_ownership: Does the person own a car
- currentjobyears: Years of experience in the current job
- currenthouseyears: Number of years in the current residence
- city: City of residence
- state: State of residence
- risk_flag: Defaulted on a loan, 0 artinya tidak berisiko, 1 berisiko-> target feature

## Data Preparation
1. load dataset dengan library pandas
2. EDA, melakukan analisis deskriptif, melihat nilai mean, kuartil, dll untuk memastikan apakah ada missing/error value. memastikan jenis data (int, object)
3. mengecek apakah ada outliers pada dataset
3. melakukan analisis univariate dan multivariate untuk menentukan fitur dalam klasifikasi
4. encoding categorical data agar memiliki nilai integer dan dapat diproses oleh model
5. membuat variabel x sebagai fitur dan y sebagai target
6. standarisasi agar nilai mean dan std 0 dan 1
7. train test split data dg rasio 9:1
8. melakukan oversampling untuk menngatasi imbalance data karena nilai 0 (false) dalam target jauh lebih banyak daripada nilai 1(true)

## Modeling
model yg digunakan adalah random forest dan neural network.
1. random forest
    - parameter yang digunakan default parameter, n_estimatorsint =100, criterion = gini, dan random state 42
    - proses : import model -> definisikan model -> train model
2. neural network
    - terdiri dari dense layer dan droput. dense untuk menghubungkan input dengan neuron, atau menghubungkan antar neuron. dense layer pertama 128 neuron dan input_dim 92 karena jumlah fitur 92 kolom. output layer terdiri dari 1 neuron dengan aktivasi sigmoid untuk klasifikasi, aktivasi sigmoid menghasilkan nilai dg range 0-1.
    - optimizer adam, karena saat menggunakan sgd peningkatan akurasi lebih lambat, epoch 20 karena saat meningkatkan epoch tidak ada peningkatan signifikan. 

- model random forest berdasarkan metrik akurasi menghasilkan nilai lebih baik. selain itu model ini lebih sederhana daripada NN. model NN memerlukan pembuatan arsitektur yg melibatkan banyak layer dan parameter, sehingga lebih susah saat hyperparameteer tuning dalam menentukan hyperparameter mana yg berpengaruh pada model. 

## Evaluation
evaluasi yang saya lakukan hanya berdasrkan pada  metrik akurasi meskipun di code terdapat metrik lain.
- random forest menghasilkan akurasi 89.35% pada 25200 test data
- neural network menghasilkan akurasi 88.90% pada 25200 test data 

