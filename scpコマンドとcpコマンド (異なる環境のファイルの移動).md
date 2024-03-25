キーワード : 踏み台サーバ、秘密鍵、鍵

**scpコマンド**はローカルからリモートへファイルを渡したい(移動したい)時に使う。

```
andouryou@andouryounoMacBook-Pro ~ % scp -i ~/.ssh/skrum_key /Users/氏名/bridge-d540d-c8e276592470.json skrum.development@34.84.252.27:/home/skrum.development
```

※ローカルからリモートへファイルを渡したいので、秘密鍵は必須p

ローカルにある`/Users/氏名`にある`bridge-d540d-c8e276592470.json`ファイルを、

リモートの`skrum.development` ディレクトリ配下に移動させる

```
scp -i ~/.ssh/skrum_key /Users/andouryou/bridge-d540d-c8e276592470.json skrum.development@34.84.252.27:/home/skrum.development/usr
```

ローカルにある`/Users/氏名`にある`bridge-d540d-c8e276592470.json`ファイルを、

リモートの`skrum.development/usr` ディレクトリ配下に移動させる

**cpコマンド**はある環境にファイルを、同じ環境にある別のファイルにコピーしたい時に実行する。(ローカルからローカルへ or リモートからリモートへ)

```
skrum.development@skrum-staging:~$ ls
**bridge-d540d-c8e276592470.json**

skrum.development@skrum-staging:~$ sudo cp bridge-d540d-c8e276592470.json /
ここでbridge-d540d-c8e276592470.jsonファイルを/(ルートディレクトリ)配下にコピーしている

skrum.development@skrum-staging:~$ ls
bridge-d540d-c8e276592470.json

skrum.development@skrum-staging:~$ cd /
skrum.development@skrum-staging:/$ ls
bin  boot  **bridge-d540d-c8e276592470.json**  dev  etc  home  lib  lib32  lib64  libx32  lost+found  media  mnt  opt  proc  root  run  sbin  snap  srv  sys  tmp  usr  var
```

```
管理者ユーザへ変更
[skrum-ando@alugo-mec-web home]$ sudo su
[root@alugo-mec-web home]# cd admin

admin下にあるalugo_prod_masking_20240125.dumpファイルを/homeにコピー
[root@alugo-mec-web admin]# sudo cp alugo_prod_masking_20240125.dump /home

rootユーザをskrum-andoに切り替えを行い、その配下にalugo_prod_masking_20240125.dumpファイルを配置
[root@alugo-mec-web home]# sudo cp alugo_prod_masking_20240125.dump /home/skrum-ando/
[root@alugo-mec-web home]# exit

ユーザskrum-andoの/home下にalugo_prod_masking_20240125.dumpファイルがあるか確認
[skrum-ando@alugo-mec-web home]$ ls
alugo_prod_masking_20240125.dump
```

```
[skrum-ando@alugo-mec-web home]$ ls
admin         alugo_deploy                      centos        khashimoto  pgsql    skrum-ando    skrum-fukushima  skrum-kihara   skrum-tazawa  web
alugo-deploy  alugo_prod_masking_20240125.dump  fabbi-dungvv  mec-data    project  skrum-fujita  skrum-kamei      skrum-maezawa  tmatsumoto    ykamase
[skrum-ando@alugo-mec-web home]$ ログアウト
Connection to 172.31.17.94 closed.
踏み台サーバにいる状態で、サーバ(ip:172.31.17.94)にあるalugo_prod_masking_20240125.dumpファイルを踏み台サーバの/home/skrum-ando下にダウンロード
[skrum-ando@ip-172-31-21-67 ~]$ scp -i ./.ssh/my_private_key skrum-ando@172.31.17.94:/home/alugo_prod_masking_20240125.dump /home/skrum-ando
Enter passphrase for key './.ssh/my_private_key': 
alugo_prod_masking_20240125.dump                                                                                                                                           34%  225MB 103.3MB/s   00:04 ETA
alugo_prod_masking_20240125.dump                                                                                                                                           54%  359MB 106.4MB/s   00:02 ETA
alugo_prod_masking_20240125.dump      
[skrum-ando@ip-172-31-21-67 ~]$ ls
alugo_prod_masking_20240125.dump                                                                                                                                    100%  656MB 112.9MB/s   00:05  
```

```
ローカルにいる状態で、踏み台サーバにあるファイルをローカルにダウンロード
andouryou@andouryounoMacBook-Pro ~ % scp -i ./.ssh/alue_skrum_pub.pem skrum-ando@3.112.168.137:/home/skrum-ando/alugo_prod_masking_20240125.dump /Users/andouryou
alugo_prod_masking_20240125.dump                                                                                                                                          100%  656MB   1.8MB/s   06:04    
```
