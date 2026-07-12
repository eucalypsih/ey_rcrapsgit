# ey_rcrapsgit

```
micro README.md
```
```
git rebase -i --root
```
Output:
```
$ git rebase -i --root
error: cannot rebase: You have unstaged changes.
error: Please commit or stash them.
```
Pesan *error* tersebut muncul karena Anda masih memiliki file yang baru saja diubah di komputer Anda, tetapi belum disimpan ke dalam Git (statusnya masih *unstaged*). Git tidak bisa melakukan proses `rebase` jika kondisi repositori Anda masih "kotor".
Mari kita selesaikan masalah ini dengan memilih salah satu dari **dua jalan keluar** berikut:
Pilihan A: Simpan perubahan Anda saat ini ke dalam Rebase (Rekomendasi)

Jika file yang menyebabkan *error* tersebut memang merupakan file yang ingin Anda masukkan ke dalam commit lama (`8743cf5`), maka simpan dulu perubahan tersebut ke tempat penitipan sementara (`stash`):
1. Titipkan perubahan Anda saat ini:
```
git stash
```
2. Jalankan kembali perintah rebase sekarang (pasti berhasil):
Mengubah Beberapa Commit Sekaligus (Commit Lama)
Jika Anda ingin mengubah commit yang sudah tertimbun (misalnya commit `7050d06`, `8743cf5`, dst.), Anda harus menggunakan fitur **Interactive Rebase**.
Jalankan perintah rebase interaktif untuk beberapa commit ke belakang. Misalnya, untuk melihat 6 commit terakhir `git rebase -i HEAD~6`
```
git rebase -i --root
```
(Ubah kata pick menjadi edit pada commit 8743cf5, lalu simpan dan tutup editor).
Teks editor akan terbuka dan menampilkan daftar commit Anda. Urutannya dimulai dari yang paling lama di atas hingga yang paling baru di bawah
```
pick 09f7d16 Create math2.html
pick 5bf7057 Add files via upload
pick 8743cf5 Create README.md
pick 7050d06 Update README.md
pick fcaf8e7 Add files via upload

```
Ubah kata `pick` menjadi `reword` (atau cukup ketik huruf `r`) di depan commit yang ingin Anda ganti komentarnya.
Contoh jika ingin mengubah semua komentar "Add files via upload":
```
pick 09f7d16 Create math2.html
reword 5bf7057 Add files via upload
pick 8743cf5 Create README.md
pick 7050d06 Update README.md
reword fcaf8e7 Add files via upload

```
Simpan dan tutup editor tersebut (Jika menggunakan VS Code cukup *save* & *close*, jika menggunakan Vim tekan `Esc` lalu ketik `:wq` dan `Enter`).
Git akan membuka jendela editor baru satu per satu untuk setiap commit yang Anda tandai dengan `reword`. Hapus teks pesan lama, ketik pesan baru Anda, lalu simpan dan tutup kembali editornya.
Setelah selesai, perbarui riwayat di GitHub karena Anda telah mengubah struktur riwayat Git:
```
git push origin main --force
```

























<br>
