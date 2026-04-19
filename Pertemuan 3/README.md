#  Pertanyaan Praktikum
###  3.5.4 Percobaan 3A<hr>
1. Jelaskan proses dari input keyboard hingga LED menyala/mati!

    >Ketika user menginput sebuah angka 1 pada serial, angka tersebut akan masuk ke dalam pengulangan yang ada di dalam program dan kemudian dibaca dan disimpan ke variabel data.
    >Setelah itu terdapat kondisi if-else yang apabila data bernilai '1' akan menjalankan kode untuk menyalakan LED dan menulis teks "LED ON" pada serial.
    >Jika data bernilai '0' maka kode untuk mematikan LED akan dijalankan, lalu serial print teks "LED OFF".
    >Namun apabila nilai dari data bukan '0' atau '1' , serial akan print sebuah warning berupa "Perintah tidak dikenal".

2. Mengapa digunakan Serial.available() sebelum membaca data? Apa yang terjadi jika baris tersebut dihilangkan?

    >available() digunakan untuk mengecek apakah terdapat data input pada serial, Apabila kondisi ini dihilangkan maka program akan terus membaca isi serial meskipun tidak ada input sama sekali dari user sehingga akan memenuhi serial monitor dengan log sampah "Perintah tidak dikenal".

3. Modifikasi program agar LED berkedip (blink) ketika menerima input '2' dengan kondisi jika ‘2’ aktif maka LED akan terus berkedip sampai perintah selanjutnya diberikan dan berikan penjelasan disetiap baris kode nya dalam bentuk README.md!

    ```cpp
    const int PIN_LED = 12;
    unsigned long LAST_MILLIS = 0;  // Menyimpan detik terakhir (millisecond)
    int BLINK = 0;      // State untuk menjalankan blinking LED
    int LED_STATE = 0;  // State untuk menyalakan/mematikan blinking LED
    
    void setup() {
      Serial.begin(9600);  // Menjalankan serial
      Serial.println("Ketik '1' untuk menyalakan LED, '2' untuk mengedipkan LED, '0' untuk mematikan LED");  // Print teks ke serial
      pinMode(PIN_LED, OUTPUT);  // Set PIN_LED ke mode OUTPUT
    }
    
    void loop() {
      unsigned long CURRENT_MILLIS = millis();  // Menyimpan detik sekarang
      if (Serial.available() > 0) {       // Cek apakah ada data dari komputer
        char data = Serial.read();        // Baca 1 karakter
    
        if (data == '2') {  // Jika data == '2'
          BLINK = 1;  // Set BLINKINg ke 1 (true)
          Serial.println("LED BLINK");  // Print teks ke serial "LED BLINK"
          return;     // Paksa berhenti untuk mengulang program dari void loop
        }
        else if (data == '1') {  // Jika data == '1' nyakalan LED
          digitalWrite(PIN_LED, HIGH);
          Serial.println("LED ON");
        }
        else if (data == '0') {  // Jika data == '0' matikan LED
          digitalWrite(PIN_LED, LOW);
          Serial.println("LED OFF");
        }
        else if (data != '\n' && data != '\r') {  // Jika data bukan '\n' dan bukan '\r'
          // Hanya muncul jika bukan 1, 0, atau ENTER
          Serial.println("Perintah tidak dikenal"); 
          return;     // Paksa berhenti untuk mengulang program dari void loop
        }
        
        BLINK = 0;    // Set BLINK ke 0 (false)
      }
      // Jika BLINK == 1 / true dan detik sekarang - detik terakhir >= 1000 (1 detik)
      if (BLINK && CURRENT_MILLIS - LAST_MILLIS >= 1000) { 
        LAST_MILLIS = CURRENT_MILLIS;  // Set detik terakhir ke detik sekarang
        LED_STATE = !LED_STATE;        // Set komplemen LED_STATE agar bisa bergantian HIGH - LOW
        digitalWrite(PIN_LED, LED_STATE);  // Set PIN_LED ke LED_STATE
      }
    }
    ```

4. Tentukan apakah menggunakan delay() atau milis()! Jelaskan pengaruhnya terhadap sistem

    >Gunakan millis() agar program tidak terjeda karena fungsi millis() dapat digunakan seperti interrupt sehingga program akan terus berjalan meskipun terdapat jeda.

### 3.6.4 Percobaan 3B<hr>
1. Jelaskan bagaimana cara kerja komunikasi I2C antara Arduino dan LCD pada rangkaian tersebut!

    >Dua perangkat saling terhubung sebagai Master (Arduino) dan Slave (LCD). Arduino akan memberikan perintah untuk dijalankan oleh LCD dan LCD akan menerima perintah tersebut dan me-acknowledgenya melewati jalur SDA. Di dalam program ditulis alamat memori dari LCD adalah 0x20, hal ini diperlukan agar hanya LCD tersebut saja yang dapat menerima data tersebut.

2. Apakah pin potensiometer harus seperti itu? Jelaskan yang terjadi apabila pin kiri dan pin kanan tertukar!

    >Pin GND dan 5V bisa di tukar posisinya namun akibatnya range potensiometer yang awalnya dari kiri-ke-kanan (0-1023) menjadi terbalik dari kanan-ke-kiri (1023-0). Intinya pin yang dihubungi GND akan menjadi nilai 0 pada potensiometer dan sebaliknya. Akan tetapi pin analog hanya dapat dihubungkan pada pin tengah potensiometer.

3. Modifikasi program dengan menggabungkan antara UART dan I2C (keduanya sebagai output) sehingga:
- Data tidak hanya ditampilkan di LCD tetapi juga di Serial Monitor
- Adapun data yang ditampilkan pada Serial Monitor sesuai dengan table berikut:
    <table>
      <tr>
        <td>ADC: 0</td>
        <td>Volt: 0.00 V</td>
        <td>Persen: 0%</td>
      </tr>
    </table>
    Tampilan jika potensiometer dalam kondisi diputar paling kiri
- ADC: 0 0% | setCursor(0, 0) dan Bar (level) | setCursor(0, 1)
- Berikan penjelasan disetiap baris kode nya dalam bentuk README.md!

    ```cpp
    ```

4. Lengkapi table berikut berdasarkan pengamatan pada Serial Monitor
  
    <table>
      <tr>
        <td>ADC</td>
        <td>Volt (V)</td>
        <td>Persen (%)</td>
      </tr>
      <tr>
        <td>1</td>
        <td></td>
        <td></td>
      </tr>
      <tr>
        <td>21</td>
        <td></td>
        <td></td>
      </tr>
      <tr>
        <td>49</td>
        <td></td>
        <td></td>
      </tr>
      <tr>
        <td>74</td>
        <td></td>
        <td></td>
      </tr>
      <tr>
        <td>96</td>
        <td></td>
        <td></td>
      </tr>
    </table>
