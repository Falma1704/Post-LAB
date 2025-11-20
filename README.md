# Post-LAB
Laporan praktikum matakuliah LAB IV(Basic Analog Electronics).

Nama : Farma Farianda

NPM  : 2410017514001

# 1. Pendahuluan

Sensor suhu LM35 adalah sensor analog yang digunakan untuk mengukur suhu dalam satuan derajat Celcius. LM35 banyak digunakan dalam sistem elektronik, mikrokontroler, IoT, serta aplikasi monitoring lingkungan karena akurasi yang baik, harga murah, dan cara penggunaan yang sederhana.

# 2. Tujuan
~~~
Mengetahui prinsip kerja sensor LM35.

Memahami karakteristik dan spesifikasi teknis LM35.

Melakukan pengujian pembacaan suhu menggunakan LM35.

Menganalisis hasil pengukuran dari sensor.
~~~
# 3. Jenis-Jenis Sensor LM35
~~~
1. LM35 (Standar / TO-92 Package)

Bentuk kecil seperti transistor.

Mudah digunakan pada breadboard dan rangkaian prototipe.

Rentang suhu: −55°C sampai +150°C.

Output analog 10 mV/°C.

Paling sering digunakan untuk praktik dan proyek Arduino.

2. LM35A

Versi dengan akurasi lebih tinggi.

Tingkat kesalahan hanya sekitar ±0.25°C pada 25°C.

Cocok untuk aplikasi presisi.

3. LM35C

Versi yang dapat bekerja pada suhu rendah.

Rentang suhu: −40°C sampai +110°C.

Biasanya digunakan untuk lingkungan luar ruangan.

4. LM35CA

Kombinasi LM35C dengan tingkat akurasi tinggi.

Toleransi kesalahan kecil: ±0.25°C.

Untuk penggunaan industri dengan suhu rendah sampai menengah.

5. LM35D / LM35DZ

Rentang suhu: 0°C sampai +100°C.

Harga paling murah.

Cocok untuk aplikasi sederhana seperti pendeteksi suhu ruangan.
~~~
# 4. Prinsip Kerja LM35
Ketika suhu di sekitar sensor berubah, resistansi internal komponen berubah, menghasilkan perubahan tegangan output. Tegangan tersebut kemudian dibaca oleh rangkaian ADC (Analog to Digital Converter) pada mikrokontroler seperti Arduino, ESP32, atau STM32.

# 5. Alat dan Bahan
~~~
Sensor LM35

Mikrokontroler (misal: Arduino UNO)

Kabel jumper

Breadboard
~~~
# 6. Rankaian
~~~
Koneksi dasar LM35:

Pin 1 (Vs) → 5V

Pin 2 (Vout) → A0 (Analog Input Arduino)

Pin 3 (GND) → GND
~~~
# 7. Program Arduino
~~~
int sensorPin = A0;   // LM35 terhubung ke pin A0

void setup() {
  Serial.begin(9600); // Mulai Serial Monitor
}

void loop() {
  // 1. Baca nilai analog (0–1023)
  int nilaiADC = analogRead(sensorPin);

  // 2. Konversi ADC -> Tegangan
  float volt = nilaiADC * (5.0 / 1023.0);

  // 3. Konversi Tegangan -> Suhu (LM35 = 10mV per °C)
  float suhu = volt * 100.0;

  // 4. Tampilkan hasil
  Serial.print("ADC: ");
  Serial.print(nilaiADC);

  Serial.print(" | Volt: ");
  Serial.print(volt);

  Serial.print(" V | Suhu: ");
  Serial.print(suhu);
  Serial.println(" C");

  delay(500); // jeda 0.5 detik
}
~~~
# 8. Hasil
~~~
Saat suhu ruangan sekitar 27°C:

ADC: 553 | Volt: 2.70 V | Suhu: 27.00 C

ADC: 554 | Volt: 2.71 V | Suhu: 27.10 C

ADC: 556 | Volt: 2.72 V | Suhu: 27.20 C
~~~
~~~
Saat sensor disentuh (suhu naik ~32°C):

ADC: 650 | Volt: 3.18 V | Suhu: 31.80 C

ADC: 652 | Volt: 3.19 V | Suhu: 31.90 C

ADC: 655 | Volt: 3.21 V | Suhu: 32.10 C
~~~
~~~
Saat didekatkan ke sumber panas (sekitar 40–45°C):

ADC: 820 | Volt: 4.00 V | Suhu: 40.00 C

ADC: 845 | Volt: 4.14 V | Suhu: 41.40 C

ADC: 900 | Volt: 4.40 V | Suhu: 44.00 C
~~~

# 9. Kesimpulan
~~~
1. Sensor LM35 mampu mengukur suhu dengan akurasi tinggi dan output yang linier.

2. Penggunaan sangat sederhana karena cukup membaca nilai analog.

3. LM35 cocok digunakan untuk aplikasi monitoring suhu berbasis mikrokontroler.

4. Hasil pengukuran menunjukkan respons cepat dan stabil terhadap perubahan suhu.
~~~
