# Aplikasi Kasir Kantin Mahasiswa

**Nama:** Yoga Adiguna  
**NIM:** F1D02410028  
**Mata Kuliah:** Pemrograman Berorientasi Objek  
**Materi:** Graphical User Interface (GUI) Eksplorasi Lanjutan

## 1. Deskripsi Program

Program ini merupakan aplikasi kasir kantin mahasiswa sederhana yang dibuat menggunakan bahasa pemrograman Java dengan library Swing. Aplikasi ini digunakan untuk menghitung total harga pembelian makanan atau minuman berdasarkan menu dan jumlah yang dimasukkan oleh pengguna.

Pengguna dapat memasukkan nama pembeli, memilih menu makanan atau minuman, memasukkan jumlah pembelian, kemudian menekan tombol Hitung Total untuk menampilkan total pembayaran. Selain itu terdapat tombol Reset untuk menghapus data yang sudah dimasukkan.

## 2. Top-level Container Class

Top-level Container Class merupakan komponen utama yang digunakan sebagai jendela dasar untuk menampilkan seluruh komponen GUI. Pada program ini Top-level Container Class yang digunakan adalah **JFrame**.

```java
public class KasirGUI extends JFrame implements ActionListener {
```

JFrame digunakan untuk membuat jendela utama aplikasi Kasir Kantin Mahasiswa. Pengaturan seperti judul, ukuran jendela, dan posisi tampilan dilakukan menggunakan method `setTitle()`, `setSize()`, dan `setLocationRelativeTo()`.

## 3. Intermediate Container Class

Intermediate Container Class merupakan komponen perantara yang digunakan sebagai tempat untuk menampung dan mengelompokkan komponen GUI lainnya.

Pada program ini Intermediate Container Class yang digunakan adalah **JPanel**.

```java
JPanel formPanel = new JPanel();
JPanel infoPanel = new JPanel();
```

`formPanel` digunakan untuk menampung komponen input dan tombol seperti JLabel, JTextField, JComboBox, dan JButton, sedangkan `infoPanel` digunakan untuk menampung label total pembayaran dan keterangan status input agar tampilan aplikasi lebih teratur.

## 4. Atomic Component Class

Atomic Component Class merupakan komponen dasar GUI yang digunakan untuk menampilkan informasi atau menerima interaksi langsung dari pengguna.

Pada program ini terdapat beberapa Atomic Component Class yaitu:

**a. JLabel**

Digunakan untuk menampilkan teks atau keterangan pada aplikasi seperti Nama Pembeli, Pilih Menu, Jumlah, Total Pembayaran, dan status pengisian jumlah.

```java
JLabel namaLabel = new JLabel("Nama Pembeli:");
```

**b. JTextField**

Digunakan sebagai tempat pengguna memasukkan data berupa nama pembeli dan jumlah pembelian.

```java
namaField = new JTextField();
jumlahField = new JTextField();
```

**c. JComboBox**

Digunakan untuk menampilkan pilihan menu makanan dan minuman yang tersedia pada aplikasi.

```java
menuBox = new JComboBox<String>(menu);
```

**d. JButton**

Digunakan untuk membuat tombol yang dapat ditekan oleh pengguna yaitu tombol Hitung Total dan Reset.

```java
hitungButton = new JButton("Hitung Total");
resetButton = new JButton("Reset");
```

## 5. Layout Classes

Layout Classes digunakan untuk mengatur posisi dan susunan komponen pada tampilan GUI. Pada program ini digunakan **2 Layout Classes** yang berbeda yaitu **BorderLayout** dan **GridLayout**.

**a. BorderLayout**

Digunakan pada Top-level Container (`JFrame`) untuk membagi area utama jendela menjadi bagian tengah (`CENTER`) untuk `formPanel` dan bagian bawah (`SOUTH`) untuk `infoPanel`.

```java
setLayout(new BorderLayout(10, 10));
add(formPanel, BorderLayout.CENTER);
add(infoPanel, BorderLayout.SOUTH);
```

**b. GridLayout**

Digunakan pada Intermediate Container (`formPanel` dan `infoPanel`) untuk menyusun komponen dalam bentuk baris dan kolom secara teratur dengan jarak horizontal dan vertikal sebesar 10 piksel.

```java
formPanel.setLayout(new GridLayout(4, 2, 10, 10));
infoPanel.setLayout(new GridLayout(1, 2, 10, 10));
```

## 6. Event Listener (Event Listener Interface & Event Adapter Class)

Event Listener merupakan mekanisme untuk menangani suatu aksi yang dilakukan oleh pengguna terhadap komponen GUI. Pada program ini digunakan **ActionListener** (Event Listener Interface) dan **KeyAdapter** (Event Adapter Class).

### A. ActionListener (Event Listener Interface)

ActionListener digunakan untuk menangani aksi ketika pengguna menekan tombol pada aplikasi.

```java
hitungButton.addActionListener(this);
resetButton.addActionListener(this);
```

Event dari kedua tombol tersebut ditangani melalui override method `actionPerformed()`.

```java
public void actionPerformed(ActionEvent e) {
    if (e.getSource() == hitungButton) {
    } else if (e.getSource() == resetButton) {
    }
}
```

Ketika tombol Hitung Total ditekan, program akan menghitung total pembayaran berdasarkan harga menu dan jumlah pembelian, sedangkan tombol Reset digunakan untuk mengembalikan input dan hasil perhitungan ke kondisi awal.

### B. KeyAdapter (Event Adapter Class)

KeyAdapter digunakan sebagai pengganti interface KeyListener untuk mendeteksi aktivitas keyboard ketika pengguna mengetik pada kolom jumlah pembelian. Dengan menggunakan Event Adapter Class, program hanya perlu meng-override method `keyReleased()` tanpa harus menuliskan method kosong lainnya (`keyPressed()` dan `keyTyped()`).

```java
jumlahField.addKeyListener(new KeyAdapter() {
    public void keyReleased(KeyEvent e) {
        if (jumlahField.getText().isEmpty()) {
            infoLabel.setText("Masukkan jumlah");
        } else {
            infoLabel.setText("Jumlah sedang diisi");
        }
    }
});
```

Method tersebut dijalankan ketika pengguna melepaskan tombol keyboard, sehingga program akan memperbarui teks informasi berdasarkan kondisi kolom jumlah pembelian.

## 7. Screenshot Hasil Program

Berikut merupakan screenshot hasil tampilan aplikasi Kasir Kantin Mahasiswa yang telah dijalankan.
![Hasil Program](screenshot/hasil.png)
