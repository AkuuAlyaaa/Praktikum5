NAMA      : ALYA SEFHIA EKA PUTRI

NIM       : 312210108

KELAS     : TI.22.B1

# Praktikum_5

Repositiry ini dibuat untuk memenuhi tugas Pertemuan 10 - Bahasa Pemrograman (Praktikum 5)

Berikut tugas pada pertemuan ke 10:

1. Soal Latihan yang ada pada module praktikum 5

  ![Latihan_5](https://user-images.githubusercontent.com/115520278/204016955-8f1a830e-db70-41a3-be2d-6edc10c8dea9.png)

  - Berikut adalah program syntax yang saya buat untuk memenuhi latihan module 5

        print("===================================================================")
        print("Nama         :   Alya Sefhia Eka Putri")
        print("NIM          :   312210108")
        print("Kelas        :   TI.22.B1")
        print("Mata Kuliah  :   Bahasa Pemrograman")
        print("===================================================================")

        # Buat dictionary daftar kontak
        print("Buat dictionary nama sebagai key, dan nomor sebagai value")

        isi = {'Ari': '081267888', 'Dina': '087677776'}
        print("Nama | Nomor kontak")
        print(isi)

        print("Tampilkan Kontaknya Ari")
        print(isi['Ari'])

        print("Tambah kontak baru dengan nama Riko, nomor 087654544")
        isi['Riko']= '087654544'
        print(isi)

        print("Ubah kontak Dina dengan nomor baru 088999776")
        isi['Dina']= '088999777'
        print(isi)

        print("Tampilkan semua Nama")
        print(isi.keys())

        print("Tampilkan semua Nomor")
        print(isi.values())

        print("Tampilkan daftar Nama dan nomornya")
        print(isi.items())

        print("Hapus kontak Dina")
        del isi['Dina']
        print(isi)

        print("===================================================================")
      
- Ini adalah output dari syntax latihan module 5

  ![Hasil (1)](https://user-images.githubusercontent.com/115520278/204017879-713f8c7b-4e49-401d-bf37-182acb5b5bc2.png)
  
2. Soal Tugas Praktikum yang ada pada module praktikum 5 adalah sebagai berikut

   ![Latihan_5 (2)](https://user-images.githubusercontent.com/115520278/204018238-baec9ca0-cceb-477b-b3eb-6b6bcdb68dc8.png)
  
  - Berikut hasil yang diinginkan
  
    ![Latihan_5 (3)](https://user-images.githubusercontent.com/115520278/204018521-67997a33-d21e-42ba-b74b-ccbb4aa56c0b.png)
    
    ![Latihan_5 (4)](https://user-images.githubusercontent.com/115520278/204018858-c274214f-11ba-4864-b853-45df058269ee.png)
    
  - Berikut adalah program syntax yang saya buat 
  
            from prettytable import PrettyTable

        print("===================================================================")
        print("Nama         :   Alya Sefhia Eka Putri")
        print("NIM          :   312210108")
        print("Kelas        :   TI.22.B1")
        print("Mata Kuliah  :   Bahasa Pemrograman")
        print("===================================================================")

        baris = []
        x = PrettyTable()

        while True:
            print("[ (L)ihat , (T)ambah, (U)bah, (H)apus, (C)ari, (K)eluar ]")
            tanya = input("Masukkan Pilihan : ")
            if tanya == "L":
                print("==== Daftar Nilai ====")
                no = 0
                no += 1
                x.field_names = ["No", "NIM", " NAMA", "TUGAS", "UTS", "UAS", "AKHIR"]
                if not baris:
                    x.field_names = ["No", "NIM", " NAMA", "TUGAS", "UTS", "UAS", "AKHIR"]
                    print("Not Data")
                else:
                    for data in baris:
                        x.add_row([no, data["nim"], data["nama"], data["tugas"], data["uts"], data["uas"], data["akhir"]])
                    print(x)
            elif tanya == "T":
                print("Tambah Data ")
                nim_v = input("NIM : ")
                nama_v = input("Nama Lengkap : ")
                uts_v = input("Nilai UTS : ")
                uas_v = input("Nilai UAS : ")
                tugas_v = input("Nilai Tugas : ")
                akhir_v = 0.3 * float(tugas_v) + 0.35 * float(uts_v) + 0.35 * float(uas_v)
                baris.append({"nim": nim_v, "nama": nama_v, "tugas": tugas_v, "uts": uts_v, "uas": uas_v, "akhir": akhir_v})
                print()
                print("==== Daftar Nilai ====")
                i = 0
                for data in baris:
                    i += 1
                    x.field_names = ["No", "NIM", " NAMA", "TUGAS", "UTS", "UAS", "AKHIR"]
                    x.add_row([i, data["nim"], data["nama"], data["tugas"], data["uts"], data["uas"], data["akhir"]])
                print(x)
            elif tanya == "U":
                print("Edit File")
                print("Data siapa yang akan diubah ?")
                siapa = input("Masukkan NIM Mahasiswa yang akan diubah : ")

                print("Data apa yang akan diubah ? : ")
                mhs = input(" 1. Nama \n 2. Nilai Tugas \n 3. Nilai UTS \n 4. Nilai UAS\n Pilih dengan angka (1/2/3/4) : ")
                if mhs == "1":
                    ubahnama = input("Silahkan masukan nama yang benar : ")
                    i = 0
                    d = next(item for item in baris if item['nim'] == siapa)
                    d['nama'] = ubahnama
                    x.field_names = ["No", "NIM", " NAMA", "TUGAS", "UTS", "UAS", "AKHIR"]
                    i += 1
                    x.add_row([i, d["nim"], d["nama"], d["tugas"], d["uts"], d["uas"], d["akhir"]])
                    print(x)
                elif mhs == "2":
                    ubahtugas = input("Masukkan Nilai Tugas yang benar : ")
                    i = 0
                    d = next(item for item in baris if item['nim'] == siapa)
                    d['tugas'] = ubahtugas
                    lihatuts = d['uts']
                    lihatuas = d['uas']
                    lihatakhir = 0.3 * float(ubahtugas) + 0.35 * float(lihatuts) + 0.35 * float(lihatuas)
                    d['akhir'] = lihatakhir
                    x.field_names = ["No", "NIM", " NAMA", "TUGAS", "UTS", "UAS", "AKHIR"]
                    for data in baris:
                        i += 1
                        x.add_row([i, data["nim"], data["nama"], data["tugas"], data["uts"], data["uas"], data["akhir"]])
                    print(x)
                elif mhs == "3":
                    ubahuts = input("Masukkan Nilai UTS yang benar : ")
                    i = 0
                    d = next(item for item in baris if item['nim'] == siapa)
                    d['uts'] = ubahuts
                    lihattugas = d['tugas']
                    lihatuas = d['uas']
                    lihatakhir = 0.3 * float(lihattugas) + 0.35 * float(ubahuts) + 0.35 * float(lihatuas)
                    d['akhir'] = lihatakhir
                    x.field_names = ["No", "NIM", " NAMA", "TUGAS", "UTS", "UAS", "AKHIR"]
                    for data in baris:
                        i += 1
                        x.add_row([i, data["nim"], data["nama"], data["tugas"], data["uts"], data["uas"], data["akhir"]])
                    print(x)
                elif mhs == "4":
                    ubahuas = input("Masukkan Nilai UAS yang benar : ")
                    i = 0
                    d = next(item for item in baris if item['nim'] == siapa)
                    d['uas'] = ubahuas
                    lihattugas = d['tugas']
                    lihatuts = d['uts']
                    lihatakhir = 0.3 * float(lihattugas) + 0.35 * float(lihatuts) + 0.35 * float(ubahuas)
                    d['akhir'] = lihatakhir
                    x.field_names = ["No", "NIM", " NAMA", "TUGAS", "UTS", "UAS", "AKHIR"]
                    for data in baris:
                        i += 1
                        x.add_row([i, data["nim"], data["nama"], data["tugas"], data["uts"], data["uas"], data["akhir"]])
                    print(x)
                else:
                    print("Pilihan Salah")

            elif tanya == "C":
                print(" ========== Pencarian Data ==========")
                print(" Pencarian berdasarkan NIM ")
                carinim = input("Masukkan NIM yang akan dicari : ")
                xdata = next(item for item in baris if item['nim'] == carinim)
                print("NIM : ", carinim)
                print("Nama : ", xdata['nama'])
                print("Nilai Tugas : ", xdata['tugas'])
                print("Nilai UTS : ", xdata['uts'])
                print("Nilai UAS : ", xdata['uas'])
                print("Nilai Akhir : ", xdata['akhir'])
            elif tanya == "H":
                print("Hapus Data Berdasarkan NIM")
                datahapus = input("Masukkan NIM data yang akan dihapus : ")
                xhapus = next(item for item in baris if item['nim'] == datahapus)
                del xhapus['nim']
                del xhapus['nama']
                del xhapus['tugas']
                del xhapus['uts']
                del xhapus['uas']
                del xhapus['akhir']
                print("Data Berhasil Dihapus")
                no = 0
                no += 1
                x.field_names = ["No", "NIM", " NAMA", "TUGAS", "UTS", "UAS", "AKHIR"]
                if not baris:
                    x.field_names = ["No", "NIM", " NAMA", "TUGAS", "UTS", "UAS", "AKHIR"]
                    print("Not Data")
                else:
                    for data in baris:
                        x.add_row([no, data["nim"], data["nama"], data["tugas"], data["uts"], data["uas"], data["akhir"]])
                    print(x)

            elif tanya == "K":
                print("Anda Keluar Dari Aplikasi")
                break
            else:
                print("Anda Memilih Pilihan Yang Salah")
                
- Berikut ini adalah hasil run dari syntax diatas akan diuraikan satu persatu
    
- Lihat data sebelum data ditambahkan

  ![Hasil (2)](https://user-images.githubusercontent.com/115520278/204019888-75d093f7-3874-41ff-8309-36736bc7d4c1.PNG)
  
- Tambah data

  ![Hasil (3)](https://user-images.githubusercontent.com/115520278/204019995-fecb72c7-8d79-4693-98a3-978884dddc41.PNG)

- Lihat setelah tambah data

  ![Hasil (4)](https://user-images.githubusercontent.com/115520278/204020114-d1b953e5-bdec-43e3-9213-aff3b5e8afcb.PNG)

- Ubah data, dan pada gambar dibawah adalah hasil dari perubahan data

  ![Hasil (5)](https://user-images.githubusercontent.com/115520278/204020207-8cb8493d-6f2a-4468-8a17-8003cdc12f77.PNG)

- Mencari data yang diinputkan

  ![Hasil (6)](https://user-images.githubusercontent.com/115520278/204020445-f2fb1a39-a08e-4daa-a4f7-6b36f9fe7b91.PNG)
  
- Menghapus data yang di inputkan

  ![Hasil (7)](https://user-images.githubusercontent.com/115520278/204020564-b5f738c4-e1a3-4ccf-bb03-5166b93409ed.PNG)

- Keluar dari program aplikasi

  ![Hasil (8)](https://user-images.githubusercontent.com/115520278/204020681-b980dc56-6cbb-4928-b365-5fa62e1ea2e5.PNG)

Berikut adalah langkah-langkahnya

Terima Kasih...


