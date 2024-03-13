# TUTORIAL 5 ADPRO  (Java Profiling)
#### Daffa Mohamad Fathoni (2206824161)
#### Advanced Programming B / GEN

<hr>

## Results of JMeter Test Plan & Profiling

### 1. Before Optimizing
#### a. HTTP Request for `/all-student`
**JMeter GUI `/all-student`**
![JMeter_GUI_all-student-request](https://github.com/fathonidf-Adpro/exercise-profiling/assets/105644250/6ed7c3e5-33e2-4ff8-a76f-c9aae767b176)

**JMeter CLI `/all-student`**
![JMeter_CLI_all-student-request](https://github.com/fathonidf-Adpro/exercise-profiling/assets/105644250/d2d894ba-f99f-4f22-b341-a6a2232f204d)

**Profiling getAllStudentsWithCourses method**
![Profiling_getAllStudentsWithCourses_before](https://github.com/fathonidf-Adpro/exercise-profiling/assets/105644250/05b6be89-9e1d-4b09-b472-ef401b6593f4)


#### b. HTTP Request for `/all-student-name`
**JMeter GUI `/all-student-name`**
![JMeter_GUI_all-student-name-request](https://github.com/fathonidf-Adpro/exercise-profiling/assets/105644250/cb20135d-7d79-4a98-b72f-6b573e28a814)

**JMeter CLI `/all-student-name`**
![JMeter_CLI_all-student-name-request](https://github.com/fathonidf-Adpro/exercise-profiling/assets/105644250/432b5592-1fbe-4c41-88c7-9c85d383dd67)

**Profiling joinStudentNames method**
![Profiling_joinStudentNames_before](https://github.com/fathonidf-Adpro/exercise-profiling/assets/105644250/a38ad459-07df-41d5-856b-2e4d4c23b2a2)

#### c. HTTP Request for `/highest-gpa`
**JMeter GUI `/highest-gpa`**
![JMeter_GUI_highest-gpa-request](https://github.com/fathonidf-Adpro/exercise-profiling/assets/105644250/07164642-67e8-4f9a-89d1-1ccb2a2cfd79)

**JMeter CLI `/highest-gpa`**
![JMeter_CLI_highest-gpa-request](https://github.com/fathonidf-Adpro/exercise-profiling/assets/105644250/e531465b-96d6-4561-ab95-ad9d3af819ab)

**Profiling findStudentWithHighestGpa method**
![Profiling_findStudentWithHighestGpa_before](https://github.com/fathonidf-Adpro/exercise-profiling/assets/105644250/ff8b68d4-9bd8-4c48-b5f2-90768e350a55)

### 2. After Optimizing
#### a. HTTP Request for `/all-student`
**JMeter CLI `/all-student`**
![JMeter_CLI_all-student-request_optimized](https://github.com/fathonidf-Adpro/exercise-profiling/assets/105644250/f2a7c243-ae81-4215-88b2-bb37f8cf311b)

**Profiling getAllStudentsWithCourses method**
![Profiling_getAllStudentsWithCourses_optimized](https://github.com/fathonidf-Adpro/exercise-profiling/assets/105644250/d4285c0e-17eb-4bdf-aebb-1510f40fb805)

#### b. HTTP Request for `/all-student-name`
**JMeter CLI `/all-student-name`**
![JMeter_CLI_all-student-name-request_optimized](https://github.com/fathonidf-Adpro/exercise-profiling/assets/105644250/060715bf-3ac4-465e-92e8-37b252f9e963)

**Profiling joinStudentNames method**
![Profiling_joinStudentNames_optimized](https://github.com/fathonidf-Adpro/exercise-profiling/assets/105644250/7ebcf910-f5fa-4b02-a326-a9de2285e886)

#### c. HTTP Request for `/highest-gpa`
**JMeter CLI `/highest-gpa`**
![JMeter_CLI_highest-gpa-request_optimized](https://github.com/fathonidf-Adpro/exercise-profiling/assets/105644250/ff980978-7362-4a27-ac63-e775216a0353)

**Profiling findStudentWithHighestGpa method**
![Profiling_findStudentWithHighestGpa_optimized](https://github.com/fathonidf-Adpro/exercise-profiling/assets/105644250/9c617573-d107-4a8b-9925-599c621a35cd)

### Conclusion
Setelah mengoptimisasi kode pada commit *[Refactoring]*, saya melakukan uji performa lagi menggunakan JMeter dan Profiling Intellij
Terdapat peningkatan sebagai berikut

* Pada awalnya saat mengakses endpoint `/all-student` terdapat *execution time* dengan rata-rata 20,582ms lalu menurun
 menjadi 1,634ms pada Intellij Profiler. Lalu pada JMeter test plan dari rataan 152337ms menjadi 10973ms pada JMeter test plan

* Pada awalnya saat mengakses endpoint `/all-student-name` terdapat *execution time* dengan rata-rata 1188ms lalu menurun
  menjadi 512ms pada Intellij Profiler. Lalu pada JMeter test plan dari rataan 3314ms menjadi 194ms pada JMeter test plan

* Pada awalnya saat mengakses endpoint `/highest-gpa` terdapat *execution time* dengan rata-rata 623ms lalu menurun
  menjadi 390ms pada Intellij Profiler. Lalu pada JMeter test plan dari rataan 400ms menjadi 310ms pada JMeter test plan

Terbukti bahwa optimasi dengan *[Refactoring]* memiliki pengaruh yang signifikan dalam hal waktu eksekusi berdasarkan
hasil testing pada Intellij Profiler dan JMeter Test Plan.

## REFLECTION

**1. What is the difference between the approach of performance testing with JMeter and profiling with IntelliJ Profiler in the context of optimizing application performance?**

Pengujian kinerja menggunakan JMeter mengimplikasikan mensimulasikan aktivitas pengguna untuk mengukur respons aplikasi seperti waktu respons, 
throughput, dan penggunaan sumber daya, yang membantu mengidentifikasi titik-titik lemah untuk perbaikan. Namun, fokusnya terutama pada respons tanpa memperhitungkan detail cara kerja aplikasi. 
Di sisi lain, profiling dengan IntelliJ Profiler menganalisis perilaku aplikasi secara rinci, memungkinkan identifikasi bagian program yang memakan waktu lebih lama dan pemahaman yang lebih mendalam terhadap kinerja aplikasi, termasuk pola penggunaan memori dan waktu CPU. Dengan informasi yang diperoleh dari profiling, optimasi pada bagian-bagian kode yang signifikan terhadap kinerja aplikasi dapat dilakukan dengan lebih efektif.

**2. How does the profiling process help you in identifying and understanding the weak points in your application?**

Profiling membantu mengenali dan memahami jalur kode dalam aplikasi dengan memantau perilaku saat runtime, 
termasuk penggunaan CPU, alokasi memori, panggilan metode, dan aktivitas thread. Dengan menganalisis data ini, 
kita dapat mengidentifikasi ketidak efisienan, bottleneck, atau penggunaan sumber daya yang berlebihan. 
Alat-alat profiling menyediakan representasi visual dari jalur runtime aplikasi, 
memudahkan identifikasi kode yang bermasalah dan memungkinkan optimasi yang tepat sasaran.

**3. Do you think IntelliJ Profiler is effective in assisting you to analyze and identify bottlenecks in your application code?**

Ya, IntelliJ Profiler sangat berguna bagi developer untuk menganalisis dan mengidentifikasi masalah dalam kode aplikasi mereka. 
Sebagai contoh, dalam tutorial dan latihan pada modul 5 ini, pengguna dapat melihat bahwa beberapa metode memiliki kinerja yang lebih lambat. 
Dengan melihat informasi tentang durasi baris yang disediakan oleh profiling, pengembang dapat dengan cepat menemukan bagian program yang menyebabkan keterlambatan atau hambatan.

**4. What are the main challenges you face when conducting performance testing and profiling, and how do you overcome these challenges?**

Beberapa tantangan utama adalah melihat dan menganalisis hasil waktu eksekusi tersebut dengan membandingkan sebelum dan setelah optimasi. 
Kita harus melihat data eksekusi tersebut secara tekun dan teliti. Namun, hal ini penting untuk dipelajari untuk membiasakan 
diri dalam melihat respon kerja aplikasi yang kita kembangkan.

**5. What are the main benefits you gain from using IntelliJ Profiler for profiling your application code?**

Dengan Intellij Profiler membantu kita tanpa perlu menginstalasi aplikasi lainnya (**third-party application**) karena
Intellij Profiler sudah terintegrasi pada IDE kita sehingga juga bisa melihat secara langsung kode/method yang diuji.

**6. How do you handle situations where the results from profiling with IntelliJ Profiler are not entirely consistent with findings from performance testing using JMeter?**

Saya belum mengalami ketidaksesuaian dalam pengalaman penggunaan sebelumnya. Namun, jika ada perbedaan hasil antara profil 
dari IntelliJ Profiler dan pengujian kinerja menggunakan JMeter, langkah awal yang harus diambil adalah meninjau kembali 
metode pengujian dan skenario yang diterapkan oleh kedua alat tersebut. Selain itu, perlu membandingkan metrik yang diukur 
oleh kedua alat untuk mengidentifikasi perbedaan fokus atau ruang lingkup, seperti perbedaan perangkat keras atau perangkat lunak yang digunakan.

**7. What strategies do you implement in optimizing application code after analyzing results from performance testing and profiling? How do you ensure the changes you make do not affect the application's functionality?**

Setelah menganalisis hasil dari pengujian kinerja dan pembuatan profil, beberapa strategi dapat diterapkan untuk meningkatkan 
kinerja kode aplikasi. Saya akan memulai dengan meninjau durasi eksekusi program yang diukur menggunakan JMeter. 
Jika saya menemukan bahwa waktu eksekusi terlalu lama, langkah selanjutnya adalah mengidentifikasi bagian kode yang 
menjadi penyebab masalah dan melakukan optimasi. Saya selalu memastikan bahwa perubahan yang saya lakukan tidak memengaruhi 
fungsionalitas aplikasi dengan membandingkan output sebelum dan sesudah perubahan tersebut.