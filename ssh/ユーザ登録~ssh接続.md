接続先のサーバにユーザが作成されているか

```jsx
cat /etc/passwd
```

ユーザが作成されていなければ、ユーザを作成

```jsx
sudo adduser [ユーザ名]
```

ユーザが作成されていれば、適切なグループに属している確認

```jsx
groups [ユーザ名]
```

適切なグループに属していなければ、所属させる

```jsx
sudo usermod -aG [グループ名] [ユーザ名]
```

.ssh/authorized_keysに公開鍵の設定(.ssh/authorized_keysに設定することで秘密鍵と検証を行う)

sshや.ssh/authorized_keysの所有者、グループに問題ないか確認

```jsx
ls -la [対象ファイル]
```

所有者、グループに問題あれば、変更する

```jsx
sudo chown ユーザ名:ユーザ名 [ファイル名]
```

パーミッションの設定
**`.ssh`** ディレクトリと **`authorized_keys`** ファイルのパーミッションを設定。
        
```bash
chmod 700 ~/.ssh
chmod 600 ~/.ssh/authorized_keys
```
        
SSH設定の確認
**`sshd_config`** ファイルでパスワード認証を無効にしているか確認。**`PasswordAuthentication`** の値が **`no`** に設定されていることを確認。

SSHデーモンの再起動
SSHデーモンを再起動して変更を反映させる。

```
sudo systemctl restart sshd
```

sudo suなど実行時にパスワードを要求される時に、要求されないようにするには
以下のコマンドで、エディタを開き、
```
sudo visudo
```

開いたエディタの以下の箇所を次のように変更する。

変更前
```
## Allows people in group wheel to run all commands
%wheel  ALL=(ALL)       ALL
```

変更後
```
## Allows people in group wheel to run all commands
%wheel  ALL=(ALL)	NOPASSWD: ALL
```
