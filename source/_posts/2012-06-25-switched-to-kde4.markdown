---
layout: post
title: "Switched to KDE4 (1)"
date: 2012-06-25 14:21
comments: true
categories: linux kde4 kubuntu desktop
---
有點諷剌的是沒多久前我才宣稱多愛gnome-shell桌面環境而已..

上禮拜五閒的發慌，想說來換一下用了好一陣子的ambiance blue，可是滿多theme要gnome-shell 3.4以上才會運作正常，於是乎就興起了把linux mint 12升到13的念頭。具體的說應該是改ubuntu套件版本，12.04有gnome-shell 3.4，而11.10則還停在gnome-shell 3.2這樣。

殊不知這就是悲劇的開始啊啊啊啊啊啊啊。雖然說google一下是有看到別人成功的以改source.list裡的版本來升級，但就過去經驗，這方法滿容易出錯的...不過仗著我有的是時間，什麼東西壞了就google修一修就好了，當然也有賭賭運氣的意思，反正我就這樣給它升下去了..

該注意的地方我應該都有作到呀？

1. sudo apt-get update
1. sudo apt-get install apt
1. sudo apt-get upgrade
1. sudo apt-get dist-upgrade

總之不太順利，要移掉linux mint的一個search相關的套件才能繼續；grub有個symlink會不見，要手動建回來；kernel 3.2也裝不起來..!?
解完這些奇奇怪怪的問題，最後再下sudo apt-get upgrade確認一下...

    0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

喔喔！！舒服啊！！不過還是要重開機進桌面環境再確認。

重開機後，嗯，本來裝的gnome-shell的extensions不意外的有不少不相容，最重要的user themes也是其一，所以又變成最初的黑黑醜醜的gnome-shell...修的好吧？再裝回來就好了嘛。首先把舊版本的擴充刪乾淨，再裝回3.4版的擴充套件，重開機。嗯..還是一樣耶？不過算了，再google一下應該會有解的，那再來確認一下本來的全域熱鍵還在不在。

我一直有在用，而且覺得很重要的全域熱鍵，meta+r開終端機，meta+e開家目錄，meta+d顯示桌面，大概就這樣；要執行指令是用alt+f2還是如gnome-do用meta+space，倒是都可以接受。

打開熱鍵設定，嗯..有用到windows key的都顯示為怪怪的「 < Super > + < Mod4 > + ...」之類的東西，其實之前就有看過有人問在gnome-shell 3.4下怎麼用windows key設熱鍵，當時看到的說法是gnome-shell 3.4要把本來 < Super > 改設為 < Mod4 > 還是反過來我忘了。總之又是一陣折騰，開dconf-editor呀、gconf-editor呀，改呀改的，最後好像是家目錄那組熱鍵有設起來，開終端機的還是無法...！？唉唷做gnome的各位高人為什麼會動到那麼基本的東西我實在無法參透啊。

這邊改一下那邊修一下，真是充實的一天。不過在幾次重開後，進不去x windows了？這又是怎樣勒。到這邊我無法了，當然可以再google再修啦，不過還要花很多時間吧。當下我可以選擇的作法

1. 重灌，灌ubuntu 12.04重頭裝gnome3
1. 裝別的桌面環境看能不能進x windows

手頭上沒有usb的情形，果斷選第二條路，sudo apt-get install kubuntu-desktop，收工。
重開後用kdm可以進到x windows了，因為沒想那麼多，我也忘了選session，就還是進到了gnome-shell。疑..那是說我還可以繼續用gnome-shell的意思嗎？先切回lightdm後重開，結果又是一樣，開到一半卡住，進不去x windows；又好像是進了，但gnome-shell當掉。不管是哪個，總之我總算真的決定換到kde4用用看了。
