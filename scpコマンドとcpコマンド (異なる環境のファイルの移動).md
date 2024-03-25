キーワード : 踏み台サーバ、秘密鍵、鍵

**scpコマンド**はローカルからリモートへファイルを渡したい(移動したい)時に使う。

```
andouryou@andouryounoMacBook-Pro ~ % scp -i ~/.ssh/skrum_key /Users/氏名/bridge-d540d-c8e276592470.json sample-user@34.84.252.27:/home/sample.development
```

※ローカルからリモートへファイルを渡したいので、秘密鍵は必須p

ローカルにある`/Users/氏名`にある`bridge-d540d-c8e276592470.json`ファイルを、

リモートの`sample.development` ディレクトリ配下に移動させる

```
scp -i ~/.ssh/sample_key /Users/andouryou/bridge-d540d-c8e276592470.json sample-user@34.84.252.27:/home/sample.development/usr
```

ローカルにある`/Users/氏名`にある`bridge-d540d-c8e276592470.json`ファイルを、

リモートの`sample.development/usr` ディレクトリ配下に移動させる

**cpコマンド**はある環境にファイルを、同じ環境にある別のファイルにコピーしたい時に実行する。(ローカルからローカルへ or リモートからリモートへ)

```
sample-user@skrum-staging:~$ ls
**bridge-d540d-c8e276592470.json**

sample-user@skrum-staging:~$ sudo cp bridge-d540d-c8e276592470.json /
ここでbridge-d540d-c8e276592470.jsonファイルを/(ルートディレクトリ)配下にコピーしている

sample-user@skrum-staging:~$ ls
bridge-d540d-c8e276592470.json

sample-user@skrum-staging:~$ cd /
sample-user@skrum-staging:/$ ls
bin  boot  **bridge-d540d-c8e276592470.json**  dev  etc  home  lib  lib32  lib64  libx32  lost+found  media  mnt  opt  proc  root  run  sbin  snap  srv  sys  tmp  usr  var
```

```
管理者ユーザへ変更
[user-ando@alugo-mec-web home]$ sudo su
[root@alugo-mec-web home]# cd admin

admin下にあるalugo_prod_masking_20240125.dumpファイルを/homeにコピー
[root@alugo-mec-web admin]# sudo cp alugo_prod_masking_20240125.dump /home

rootユーザをuser-andoに切り替えを行い、その配下にalugo_prod_masking_20240125.dumpファイルを配置
[root@alugo-mec-web home]# sudo cp alugo_prod_masking_20240125.dump /home/skrum-ando/
[root@alugo-mec-web home]# exit

ユーザuser-andoの/home下にalugo_prod_masking_20240125.dumpファイルがあるか確認
[user-ando@alugo-mec-web home]$ ls
alugo_prod_masking_20240125.dump
```

```
[user-ando@alugo-mec-web home]$ ls
admin         alugo_deploy          centos        khashimoto  pgsql    user-ando    user-fukushima  user-kihara   user-tazawa  web
alugo-deploy  alugo_prod_masking_20240125.dump  fabbi-dungvv  mec-data    project tmatsumoto    ykamase
[user-ando@alugo-mec-web home]$ ログアウト
Connection to 172.31.17.94 closed.
踏み台サーバにいる状態で、サーバ(ip:172.31.17.94)にあるalugo_prod_masking_20240125.dumpファイルを踏み台サーバの/home/skrum-ando下にダウンロード
[user-ando@ip-172-31-21-67 ~]$ scp -i ./.ssh/my_private_key user-ando@172.31.17.94:/home/alugo_prod_masking_20240125.dump /home/user-ando
Enter passphrase for key './.ssh/my_private_key': 
alugo_prod_masking_20240125.dump                                                                                                                                           34%  225MB 103.3MB/s   00:04 ETA
alugo_prod_masking_20240125.dump                                                                                                                                           54%  359MB 106.4MB/s   00:02 ETA
alugo_prod_masking_20240125.dump      
[user-ando@ip-172-31-21-67 ~]$ ls
alugo_prod_masking_20240125.dump                                                                                                                                    100%  656MB 112.9MB/s   00:05  
```

```
ローカルにいる状態で、踏み台サーバにあるファイルをローカルにダウンロード
andouryou@andouryounoMacBook-Pro ~ % scp -i ./.ssh/alue_skrum_pub.pem user-ando@3.112.168.137:/home/user-ando/alugo_prod_masking_20240125.dump /Users/andouryou
alugo_prod_masking_20240125.dump                                                                                                                                          100%  656MB   1.8MB/s   06:04    
```
