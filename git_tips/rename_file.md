<oldname>で予めpushまで終わっているものとする
```
git mv <oldname> <newname>
git commit <oldname>    #<oldname>をdelete
git commit <newname>    #<newname>をコミット
git push
```
の手順でリポジトリにあるファイルをリネームできる

