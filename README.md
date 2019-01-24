## ソフトウェア

|Name            |Version |Edition |Download |
|----------------|--------|--------|---------|
|VirtualBox      | 5.2.x  | 64-bit | https://www.virtualbox.org/wiki/Download_Old_Builds_5_2 |
|Vagrant         | 2.2.x  | 64-bit | https://www.vagrantup.com/downloads.html |
|Git for Windows | latest | -      | https://gitforwindows.org/ |


## 改行コードの自動変換をOFF
```
[~]$ git config --global core.autoCRLF false
```

## Vagrant環境構築
```
[~]$ git clone https://github.com/inocop/vagrant-ruby.git
[~]$ cd vagrant-ruby
[~/vagrant-ruby]$ vagrant up
```

## VMの操作

#### 起動
```
[~/vagrant-ruby]$ vagrant up
```

#### 停止
```
[~/vagrant-ruby]$ vagrant halt
```

#### 削除
```
[~/vagrant-ruby]$ vagrant destroy
```

#### ログイン
```
[~/vagrant-ruby]$ vagrant ssh
```
