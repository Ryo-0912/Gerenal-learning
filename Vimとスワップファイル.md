# スワップファイル

Vimが編集中のファイルのバックアップとして作成されるファイル。

Vimがファイルを開くと、そのファイルの編集中の内容や状態を保持するためにスワップファイルが作成される。これにより、予期せぬ障害やクラッシュが発生した場合でも、編集中のファイルの内容を復元できる。

通常、スワップファイルはファイル名の先頭にドットが付いており、元のファイル名に加えて .swp の拡張子が付きます。

swpがあるファイルをvimで開くと次のようなメッセージが出る。
swpファイルを削除すれば、このメッセージ出なくなる。

```
E325: ATTENTION
Found a swap file by the name ".swp_sample.txt.swp"
          owned by: hoge   dated: Mon Jan 23 12:09:39 2017
         file name: ~hoge/swp/swp_sample.txt
          modified: no
         user name: hoge   host name: O-04850-MAC.local
        process ID: 8563
While opening file "swp_sample.txt"
             dated: Mon Jan 23 12:07:24 2017

(1) Another program may be editing the same file.  If this is the case,
    be careful not to end up with two different instances of the same
    file when making changes.  Quit, or continue with caution.
(2) An edit session for this file crashed.
    If this is the case, use ":recover" or "vim -r swp_sample.txt"
    to recover the changes (see ":help recovery").
    If you did this already, delete the swap file ".swp_sample.txt.swp"
    to avoid this message.

Swap file ".swp_sample.txt.swp" already exists!
[O]pen Read-Only, (E)dit anyway, (R)ecover, (D)elete it, (Q)uit, (A)bort: 
書いてある通りですが、それぞのキーを押す事で次の動作を決める事ができ
```
