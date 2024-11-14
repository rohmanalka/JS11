# Laporan Praktikum

## Nama Anggota:
- Ivan Rizal Ahmadi (2341760128)
- Luthfi Putra Mahardika (2341760181)
- Muhammad Rohman Al K (2341760055)
- Meisy Nadia Nababan (2341760031)
- Saria Fauzani (234176)

---

## 2.3 Heterogenous
### class Pegaawai
```java
public class Pegawai {
    public String nip;
    public String nama;
    public Pegawai(){
    }
    public Pegawai(String nip, String nama) {
        this.nip = nip;
        this.nama = nama;
    }
    public void displayInfo()
    {
        System.out.println("NIP: " + nip);
        System.out.println("Nama: " + nama);
    }    
}
```

### class Dosen
```java
public class Dosen extends Pegawai{
    public String nidn;
    public Dosen(){
    }
    public Dosen(String nip, String nama, String nidn){
        super(nip, nama);
        this.nidn = nidn;
    }
    
    public void displayInfo(){
        super.displayInfo();
        System.out.println("NIDN: " + nidn);
    }
    public void mengajar(){
        System.out.println("Membuat rencana pembelajaran");
        System.out.println("Menyusun materi");
        System.out.println("Melaksanakan PBM");
        System.out.println("Melakukan evaluasi");
    }
}
```
### class TenagaKependidikan
```java
public class TenagaKependidikan extends Pegawai {
    public String kategori;
    public TenagaKependidikan(){
    }
    public TenagaKependidikan(String nip, String nama, String kategori){
        super(nip, nama);
        this.kategori = kategori;
    }
    public void displayInfo(){
        super.displayInfo();
        System.out.println("Kategori: " + kategori);
    } 
}
```
### class Demo
#### Instansiasi object Dosen dan TenagaKependidikan
```java
public class Demo {
    public static void main(String[] args) {
        // Membuat objek dosen
        Dosen dosen1 = new Dosen("19940201", "Widia, S.Kom., M.Kom.", "199402");
        Dosen dosen2 = new Dosen("19780165", "Muhammad, S.T., M.T.", "197801");
        // Membuat objek tenaga kependidikan
        TenagaKependidikan tendik1 = new TenagaKependidikan("19750301", "Aida, A.Md.", "Tenaga Administrasi");
        TenagaKependidikan tendik2 = new TenagaKependidikan("19650304", "Rika, S.T.", "Tenaga Laboratorium");
```
#### Buat ArrayList daftarPegawai
```java
ArrayList<Pegawai> daftarPegawai = new ArrayList<Pegawai>(); 
```
#### Polymorhpism
```java
daftarPegawai.add(dosen1);
        daftarPegawai.add(dosen2);
        daftarPegawai.add(tendik1);
        daftarPegawai.add(tendik2);
        System.out.println("Jumlah Pegawai: " + daftarPegawai.size());
```
#### Output dari kode diatas:
![Run Gambar 2.3](img/2.3%20Heterogenous.png)

## 2.4 Object Casting
### Modifikasi main
```java
Dosen dosen1 = new Dosen("19940201", "Widia, S.Kom., M.Kom.", "199402");

System.out.println(dosen1.nip);
System.out.println(dosen1.nama);
System.out.println(dosen1.nidn);
dosen1.mengajar();
```
#### Output dari kode diatas:
![Run Gambar 2.4](img/2.4%20ModifikasiMain.png)

#### Upcasting object dosen1 menjadi object Pegaawai
```java
Dosen dosen1 = new Dosen("19940201", "Widia, S.Kom., M.Kom.", "199402");

Pegawai pegawai1 = dosen1;

System.out.println(pegawai1.nip);
System.out.println(pegawai1.nama);
System.out.println(pegawai1.nidn);
pegawai1.mengajar();
```
#### Output dari kode diatas:
![Run Gambar UpcastingDosen1](img/2.4%20UpcastDosen1-Pegawai.png)

### Upcasting
```java
Dosen dosen1 = new Dosen("19940201", "Widia, S.Kom., M.Kom.", "199402");

Pegawai pegawai1 = dosen1;
System.out.println(pegawai1.nip);
System.out.println(pegawai1.nama);
// System.out.println(pegawai1.nidn)
// pegawai1.mengajar();
pegawai1.displayInfo();
```
#### Output dari kode diatas:
![Run Gambar Upcasting](img/2.4%20Upcasting.png)

### Downcasting pegawai1 ke tendik
```java
Dosen dosen1 = new Dosen("19940201", "Widia, S.Kom., M.Kom.", "199402");

Pegawai pegawai1 = dosen1;
System.out.println(pegawai1.nip);
System.out.println(pegawai1.nama);
pegawai1.displayInfo();

TenagaKependidikan test = (TenagaKependidikan) pegawai1;
```
#### Output dari kode diatas:
![Run Gambar Downcasting](img/2.4%20DowncastTendik.png)

### Downcasting pegawai1 ke dosen
```java
Dosen dosen1 = new Dosen("19940201", "Widia, S.Kom., M.Kom.", "199402");

Pegawai pegawai1 = dosen1;

System.out.println(pegawai1.nip);
System.out.println(pegawai1.nama);
pegawai1.displayInfo();

Dosen newDosen = (Dosen) pegawai1;

System.out.println(newDosen.nama);
System.out.println(newDosen.nidn);
newDosen.mengajar();
```
#### Output dari kode diatas:
![Run Gambar Downcast Dosen](img/2.4%20DowncastDosen.png)

## 2.5 Polymorphic Arguments & instanceOf
### Modifikasi class Demo 
```java
public class Demo {
    public static void main(String[] args) {
        Dosen dosen1 = new Dosen("19940201", "Widia, S.Kom. M.Kom", "199402");
        TenagaKependidikan tendik1 = new TenagaKependidikan("19750301", "Aida, A.Md.", "Tenaga Administrasi");
        train(dosen1);
        train(tendik1);
    }

    public static void train(Pegawai pegawai){
        System.out.println("Memberikan pelatihan untuk pegawai");
        pegawai.displayInfo();
```
#### Kode sebelumnya Upcasting sehingga tidak bisa akses nidn, kategori, dan method mengajar
#### Kode `Hanya Test` akan error :
```java
public class Demo {
    public static void main(String[] args) {
        Dosen dosen1 = new Dosen("19940201", "Widia, S.Kom. M.Kom", "199402");
        TenagaKependidikan tendik1 = new TenagaKependidikan("19750301", "Aida, A.Md.", "Tenaga Administrasi");
        train(dosen1);
        train(tendik1);
    }

    public static void train(Pegawai pegawai){
        System.out.println("Memberikan pelatihan untuk pegawai");
        pegawai.displayInfo();

        //Hanya Test
        System.out.println(pegawai.nidn);
        System.out.println(pegawai.kategori);
        pegawai.mengajar
    }
}
```
#### Modifikasi method train dengan instanceOf  untuk mengetahui dari class mana suatu object diinstansiasi.
```java
public static void train(Pegawai pegawai){
    pegawai.displayInfo();
    System.out.println("Mengenalkan lingkungan kampus");
    System.out.println("Menginfokan SOP/Juknis");

    if (pegawai instanceof Dosen) {
        System.out.println("Memberikan pelatihan padagogik");
    }
}
```
#### Output dari kode diatas:
![Run Gambar InstanceOf](img/2.5%20InstanceOf.png)

## Jawaban
1. Tidak, upcasting hanya dapat dilakukan pada class yang memiliki relasi inheritance. Upcasting memungkinkan objek subclass dikenali sebagai tipe superclass, dan ini tidak berlaku untuk class yang tidak berhubungan.
2. Pada kode program baris kedua, upcasting dilakukan secara implisit, seperti pada baris kedua (Pegawai pegawai1 = new Dosen();).
3. instanceOf digunakan untuk memeriksa apakah suatu objek merupakan instance dari tipe tertentu dalam hierarki inheritance. Ini berguna untuk menentukan jenis asli dari suatu objek ketika berada di lingkungan polimorfisme.
4. Heterogenous collection adalah koleksi yang dapat menyimpan elemen-elemen dengan berbagai tipe data yang berbeda, asalkan elemen-elemen tersebut berada dalam satu hierarki inheritance. Contohnya adalah ArrayList bertipe superclass yang dapat menyimpan instance dari subclass-subclass-nya.
5. Ya, Dapat dilakukan jika object asli adalah instance dari class Dosen.
```java
Pegawai pegawai1 = new Dosen(); // Instansiasi object dari class Dosen
            if (pegawai instanceof Dosen) {
                Dosen dosen = (Dosen) pegawai; // Downcasting ke tipe Dosen
                System.out.println("Downcasting berhasil.");
            } else {
                System.out.println("Downcasting gagal.");
            }
```
