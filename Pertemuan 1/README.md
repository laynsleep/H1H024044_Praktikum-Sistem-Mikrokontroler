### Pertanyaan 1A <hr>
1. Pada kondisi apa program masuk ke blok if?

    >Ketika nilai timeDelay kurang dari sama dengan 100

2. Pada kondisi apa program masuk ke blok else?

    >Apabila timeDelay memiliki nilai lebih dari 100

3. Apa fungsi dari perintah delay(timeDelay)?

    >Memberikan jeda diantara perintah dengan durasi waktu sebesar nilai variable timeDelay ms

4. Jika program yang dibuat memiliki alur mati → lambat → cepat → reset (mati),
ubah menjadi LED tidak langsung reset → tetapi berubah dari cepat → sedang →
mati dan berikan penjelasan disetiap baris kode nya dalam bentuk README.md!

    ```c
    print("Hello World!");
    ```

### Pertanyaan 2A <hr>
1. Gambarkan rangkaian schematic 5 LED running yang digunakan pada percobaan!

    ![skematik](#)

2. Jelaskan bagaimana program membuat efek LED berjalan dari kiri ke kanan!

    >Dengan menggunakan pengulangan, indeks ledPin yang di inisialisasi dengan nilai 7 akan menyalakan led pada pin 7 lalu terdapat jeda sebelum akhirnya led tersebut dimatikan.
    Setelah itu nilai ledPin akan di kurangkan/decrement sebanyak satu nilai dan mengulai rangkaian perintah tersebut hingga kondisi ledPin lebih besar dari sama dengan 2.

3. Jelaskan bagaimana program membuat LED kembali dari kanan kek kiri!

    >Sama seperti sebelumnya, dengan perubahan ledPin di inisialisasi dengan nilai 2 lalu menjalankan semua perintahnya dan mengulang lagi dengan penambahan/increment nilai ledPin sebanyak 1.
    Pengulangan akan terjadi terus hingga kondisi ledPin lebih dari 7.

5. Buatkan program agar LED menyala tiga LED kanan dan tiga LED kiri secara bergantian dan berikan penjelasan disetiap baris kode nya dalam bentuk README.md!

    ```c
    print("Hello World!");
    ```
