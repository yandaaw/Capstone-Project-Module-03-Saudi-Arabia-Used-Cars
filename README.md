# Capstone Project Module 03 - Saudi Arabia Used Cars - Regression

[Sumber data Saudi Arabia Used Cars](https://drive.google.com/file/d/1Tr4YT5dmgwTrXLvIqZ4diBf5z8K6JjrR/view) 

### **Contents**

1. Business Problem Understanding
2. Data Understanding
3. Data Preprocessing
4. Modeling
5. Conclusion
6. Recommendation

****

### **Business Problem Understanding**

**Context**

Saudi Arabia Used Cars adalah sebuah showroom mobil bekas yang berada di Saudi Arabia yang menjual lebih dari 50+ merek mobil. Penjualan mobil tersebar di 27 wilayah negara Arab Saudi. Dataset yang digunakan terdiri dari 5625 records. Setiap baris data mewakili informasi mengenai tipe kendaraan, wilayah dan asal kendaraan, merek kendaraan, tipe transmisi kendaraan atau gear type, opsi kendaraan, tahun pembuatan kendaraan, ukuran mesin kendaraan, mileage, status negosiasi kendaraan, dan harga kendaraan. 

**Problem Statement**

Salah satu tantangan terbesar bagi perusahaan Saudi Arabia Used Cars adalah pemecahan masalah untuk dapat memiliki model bisnis yang menguntungkan secara finansial bagi showroom mobil ini dalam menjual mobil bekasnya, serta dapat memberikan pengalaman positif dan kenyamanan bagi para calon pembeli mobil agar bisa mendapatkan mobil bekas dengan harga yang sesuai.

Mengingat beberapa mobil dinilai over value dan sisa lainnya dinilai under value. Terlebih apabila calon pembeli tidak memiliki pengetahuan atau informasi yang cukup perihal kendaraan mobil bekas, hal inilah yang akan menimbulkan masalah dan tentunya merugikan salah satu pihak. Dengan banyaknya jumlah kendaraan bekas yang dijual serta keragaman fitur-fitur yang melekat pada suatu monil, menentukan harga yang beragam untuk dapat dijadikan bahan pertimbangan bagi calon pembeli mobil bekas Saudi Arabia.

**Goals**

Berdasarkan permasalahan tersebut, kita membutuhkan sebuah 'tool' yang dapat **memprediksi serta dapat membantu calon pembeli dalam menentukan harga mobil yang sesuai atau tepat untuk tiap mobil bekas yang hendak mereka beli**. Adanya perbedaan pada bagian fitur yang terdapat pada suatu mobil bekas seperti tahun produksi mobil, engine size, serta fitur-fitur lainnya dapat menambah keakuratan prediksi harga sebuah mobil, yang mana dapat meningkatkan profitabilitas penjual mobil, dan juga tentunya memberikan kenyamana calon pembeli agar supaya mendapatkan mobil yang tepat.

**Analytic Approach**

Hal yang perlu di lakukan adalah menganalisis data untuk dapat menemukan pola dari fitur-fitur yang ada, yang membedakan satu mobil dengan yang lainnya. 

Selanjutnya adalah membangun suatu model regresi yang akan membantu perusahaan untuk dapat menyediakan 'tool' prediksi harga jual mobil yang tepat dan secara bersamaan dapat berguna bagi pembeli dalam menentukan harga yang tepat untuk mobil bekas Saudi Arabia yang hendak dibeli.

**Metric Evaluation**

Evaluasi metrik yang akan digunakan adalah RMSE, MAE, dan MAPE, di mana RMSE adalah nilai rataan akar kuadrat dari error, MAE adalah rataan nilai absolut dari error, sedangkan MAPE adalah rataan persentase error yang dihasilkan oleh model regresi. Semakin kecil nilai RMSE, MAE, dan MAPE yang dihasilkan, berarti model semakin akurat dalam memprediksi suatu harga sesuai dengan limitasi fitur yang digunakan. 

Selain itu, kita juga bisa menggunakan nilai R-squared atau adj. R-squared jika model yang nanti terpilih sebagai final model adalah model linear. Nilai R-squared digunakan untuk mengetahui seberapa baik model dapat merepresentasikan varians keseluruhan data. Semakin mendekati 1, maka semakin fit pula modelnya terhadap data observasi. Namun, metrik ini tidak valid untuk model non-linear.

### **Data Understanding**
- Dataset merupakan data listing mobil bekas yang dijual pada lokasi asal Saudi Arabia.
- Setiap baris data merepresentasikan informasi terkait kendaraan yang dijual.

**Attributes Information**

| **Attribute** | **Data Type** | **Description** |
| --- | --- | --- |
| Type | Object | Type of used car |
| Region | Object | Region of used car |
| Make | Object | The company name |
| Gear_Type | Object | Gear type size of used car |
| Origin| Object | Origin of used car |
| Options| Object | Options of used car |
| Year | Integer | Manufacturing year |
| Engine_Size | Float | The engine size of used car |
| Mileage | Integer | Mileage |
| Negotiable | Object | Negotiable in dollars |
| Price | Integer | Amount of used car |

<br>

**Feature Importances**
Untuk dapat mengetahui sebenarnya fitur apa saja yang sangat memengaruhi target (Price), kita dapat mengeceknya melalui function feature_importances_.
![image](https://user-images.githubusercontent.com/73176284/169945053-5ee0d5a5-9692-46cd-9096-33a93b7dc151.png)

### **Conclusion**
Berdasarkan pemodelan yang sudah dilakukan, fitur 'Year', 'Engine Size', 'Options', 'Mileage' dan 'Gear_Type : Manual' menjadi fitur yang paling berpengaruh terhadap 'price'.

 Metrik evaluasi yang digunakan pada model adalah nilai RMSE, MAE & MAPE. Jika ditinjau dari nilai RMSE yang dihasilkan oleh model setelah dilakukan hyperparameter tuning lebih besar dibandingkan dengan model sebelum dilakukan hyperparameter tuning. Kita dapat menyimpulkan bahwa bila nanti model yang kita buat ini digunakan untuk memperkirakan harga mobil bekas di Saudi Arabia pada rentang nilai seperti yang dilatih terhadap model, maka perkiraan harganya rata-rata akan meleset kurang lebih sebesar nilai 247.71 dari harga yang mungkin seharusnya. Tetapi, tidak menutup kemungkinan juga prediksinya meleset lebih jauh karena bias yang dihasilkan model masih cukup tinggi bila dilihat dari visualisasi antara harga aktual dan prediksi. Bias yang dihasilkan oleh model ini dikarenakan oleh kurangnya fitur pada dataset yang bisa merepresentasikan aspek-aspek lain dari mobil bekas yang dijual.

### **Recommendation**
Hal-hal yang dapat dilakukan untuk mengembangkan model agar lebih baik lagi, seperti:

1. Mengecek prediksi mana saja yang memiliki nilai error yang tinggi. Kita dapat mengelompokkan error tersebut ke dalam grup overestimation dan underestimation, lalu memilih 5% error paling ekstrim saja untuk tiap grup. Nantinya pengelompokkan akan menjadi 3 grup, yaitu overestimation (5%), underestimation (5%), dan grup mayoritas yang error-nya mendekati nilai mean (90%). Setelahnya kita bisa mengecek hubungan antara error tersebut dengan tiap variabel independen. Pada akhirnya kita dapat mengetahui sebenarnya variabel mana saja dan aspek apa yang menyebabkan model menghasilkan error yang tinggi, sehingga kita bisa melakukan training ulang dengan penerapan feature engineering lainnya.
<br><br>   
2. Jika memungkinkan, penambahan fitur yang lebih korelatif dengan target ('price').
<br><br>   
3. Jika ada penambahan banyak data, dapat dicoba dengan menggunakan model yang lebih kompleks, seperti recursive neural networks (RNN). Namun, kalau jumlah data dan fiturnya masih seperti dataset ini, kemungkinan besar tidak akan mengubah hasilnya secara signifikan.

