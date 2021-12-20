# Setting SSH Github Untuk Macos

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