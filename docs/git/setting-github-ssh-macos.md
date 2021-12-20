# Setting SSH Github Untuk MacOS

Agar bisa menggunakan perintah-perintah git pada private repo github di macos seperti ``git clone``, ``git push``, anda perlu membuat ssh key di macos dengan men-generate private dan public key. Langkah-langkahnya sebagai berikut:

1. Pastikan ada folder `.ssh` di dalam folder home user
```
ls -al ~/
```

2. Jika tidak ada, buat folder dan masuk ke dalam folder `.ssh` dengan perintah
```
mkdir ~/.ssh && cd ~/.ssh
```

3. Gunakan perintah ssh-keygen untuk men-generate ssh key, system akan men-generate 2 buah file yaitu public key dan private key. public key adalah file dengan extensi .pub
```
ssh-keygen -t ed25519 -C "email_yang_digunakan@digithub.com"
```

4. Check ssh-agent telah berjalan
```
eval "$(ssh-agent -s)"
```

5. Tambahkan private ssh key ke `ssh-agent`
```
ssh-add ~/.ssh/nama_key
```

6. Copy public key ke setting github.com

7. Test koneksi dengan perintah `ssh -T git@github.com`

---

## Troubleshoot SSH Github

Beberapa masalah yang sering ditemui apabila menggunakan ssh github karena kesalahan user.

1. Ketika melakukan ```git push```, system meminta untuk memasukkan user dan password github, seharusnya langkah ini tidak perlu lagi dilakukan karena sudah di ```authentificate``` menggunakan ssh. Biasanya terjadi karena clonning repository menggunakan protokol https bukan lewat ssh. Jika terjadi lakukan langkah berikut.
    a) hapus folder .git didalam local repo
    ```rm -rf .git```
    b) inisialisasi kembali repo menggunakan perintah 
    ```git remote add origin git@github.com:nama_user/nama_repo.git```