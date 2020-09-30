# Git-BranchModel-test

## 参考記事
- git pull と git pull –rebaseの違い
https://kray.jp/blog/git-pull-rebase/
- git rabase -i, git rebaseについて
https://kigh-memo.hatenablog.com/entry/2019/12/12/053202
- rebaseの注意点
https://yu8mada.com/2018/08/13/how-to-make-a-history-linear-using-git-rebase-and-the-cautions-when-using-it/
- GitFlow
https://qiita.com/y-okudera/items/0b57830d2f56d1d51692


## メモ
- git stashコマンド
作業ブランチを間違えた時や進行中の未コミットの内容を避難したいときに使う
https://qiita.com/muran001/items/f5746c518bf663f86a79
```
$ git status                                                                                                                                                  
On branch feature/#MD_TWEET-82
Changes not staged for commit:
  (use "git add/rm <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   app/Http/Controllers/ApiController.php
	modified:   app/Http/Kernel.php
	deleted:    app/Http/Middleware/GetResponse.php
	modified:   composer.json
	modified:   composer.lock
	modified:   config/app.php
	modified:   routes/api.php

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	app/Http/Middleware/ApiThrottleRequests.php

no changes added to commit (use "git add" and/or "git commit -a")

# トラック対象ファイルをstashする
git stash                                                                                                                                                   
Saved working directory and index state WIP on #MD_TWEET-82: 9dd7787 [WIP]Middlewareによるレスポンスヘッダの検証

# untracked fileもstashする

$ git stash -u                                                                                                                                                 
Saved working directory and index state WIP on #MD_TWEET-82: 9dd7787 [WIP]Middlewareによるレスポンスヘッダの検証

$ git stash list                                                                                                                                                 
stash@{0}: WIP on #MD_TWEET-82: 9dd7787 [WIP]Middlewareによるレスポンスヘッダの検証
stash@{1}: WIP on #MD_TWEET-82: 9dd7787 [WIP]Middlewareによるレスポンスヘッダの検証

# 最新のstashを反映
$ git stash apply                                                                                                                                                 
Already up to date!
On branch feature/guzzle_dev
Untracked files:
  (use "git add <file>..." to include in what will be committed)
	app/Http/Middleware/ApiThrottleRequests.php

nothing added to commit but untracked files present (use "git add" to track)

# 特定のstashを反映
$ git stash apply stash@{0}                                                                                                                                      
app/Http/Middleware/ApiThrottleRequests.php already exists, no checkout
error: could not restore untracked files from stash

```

### おまけ
- ターミナルのHotkeyを設定している場合、command + enterで全画面と切り替えが可能
戻すときも同じコマンド

- Macの文字変換コマンド

|  変換	| キー  |
| ---- | ---- |
|  ひらがな |	ctrl + j  |
|  カタカナ	| ctrl + k  |
|  全角英数 | ctrl + l  |
| 半角英数 |	ctrl + ;  |
