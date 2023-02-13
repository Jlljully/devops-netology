
**1.** Найдите полный хеш и комментарий коммита, хеш которого начинается на aefea.  
  
>aefead2207ef7e2aa5dc81a34aedf0cad4c32545  
>"Update CHANGELOG.md"  
  
**Результат получен при помощи команды git show aefea**  
  
**2.** Какому тегу соответствует коммит 85024d3?  
  
>v0.12.23  
  
**Результат получен при помощи команды git show 85024d3**  
  
**3.** Сколько родителей у коммита b8d720? Напишите их хеши.  
  
>Два:  
>56cd7859e05c36c06b56d013b55a252d0bb7e158 первый родитель  
>9ea88f22fc6269854151c571162c5bcf958bee2b второй родитель  
  
**Результат получен при помощи команд:**  
`git show b8d720`  
**Видим, что это мёрдж коммит, получаем хэш родителей:**  
`git show b8d720^1`  
`git show b8d720^2`  
**И при проверке третьего родителя получаем оишбку, что его не существует:**  
`jlljully@jlljully-VirtualBox:~/git02begin/HW4_clone_terraform$ git show b8d720^3`  
`fatal: ambiguous argument 'b8d720^3': unknown revision or path not in the working tree.`  
  
*Любопытно, что сам коммит мёрджа пишет "Merge: 58dcac4b79 ffbcf55817", и у Андрея в примере в видео такая же ситуация. При этом я смотрю в своей прошлой домашке - мёрдж подписал правильные хэши родителей:*  

`jlljully@jlljully-VirtualBox:~/git02begin/sshtest$ git show 99d7a84`  
`commit 99d7a84bfe8c3974dee039271273ace188d9b1bc`  
`Merge: 2c79916 0bb645a`  
  
`jlljully@jlljully-VirtualBox:~/git02begin/sshtest$ git show 99d7a84^1`  
`commit 2c799169cf72bc62e71bc183cbc5a433c072917b (bitbucket/main)`  
  
`jlljully@jlljully-VirtualBox:~/git02begin/sshtest$ git show 99d7a84^2`  
`commit 0bb645abb6a1328d5f787f29d6c4e3cb0bf955b7 (origin/git-merge, git-merge)`  
  
  
4. Перечислите хеши и комментарии всех коммитов которые были сделаны между тегами v0.12.23 и v0.12.24.  

`jlljully@jlljully-VirtualBox:~/git02begin/HW4_clone_terraform$ git log --oneline v0.12.24 -20`  
`33ff1c03bb (tag: v0.12.24) v0.12.24`  
`b14b74c493 [Website] vmc provider links`  
`3f235065b9 Update CHANGELOG.md`  
`6ae64e247b registry: Fix panic when server is unreachable`  
`5c619ca1ba website: Remove links to the getting started guide's old location`  
`06275647e2 Update CHANGELOG.md`  
`d5f9411f51 command: Fix bug when using terraform login on Windows`  
`4b6d06cc5d Update CHANGELOG.md`  
`dd01a35078 Update CHANGELOG.md`  
`225466bc3e Cleanup after v0.12.23 release`  
`85024d3100 (tag: v0.12.23) v0.12.23`  
  
  
**Так как результаты в гите можно получать разными способами, я выбрала первый пришедший в голову: вывела историю последних 20 коммитов, начиная с коммита v0.12.24, который, очевидно, был старше из пары, и увидела v0.12.23. Но такой же резутьтат, кроме начального коммита, можно увидеть и в выоде команды:**  
`git log v0.12.23..v0.12.24 --oneline `  
  
5. Найдите коммит в котором была создана функция func providerSource, ее определение в коде выглядит так func providerSource(...) (вместо троеточия перечислены аргументы).  
  
>8c928e8358  
>и была изменена в 5af1e6234a  
  
**Результат получен командой:**  
`git log -S'func providerSource' --oneline`  
  
6. Найдите все коммиты в которых была изменена функция globalPluginDirs.  
  
`jlljully@jlljully-VirtualBox:~/git02begin/HW4_clone_terraform$ git log -S'globalPluginDirs' --oneline `  
**Результат:**  
  
`65c4ba7363 Remove terraform binary`  
`125eb51dc4 Remove accidentally-committed binary`  
`22c121df86 Bump compatibility version to 1.3.0 for terraform core release (#30988)`  
`7c7e5d8f0a Don't show data while input if sensitive`  
`35a058fb3d main: configure credentials from the CLI config file`  
`c0b1761096 prevent log output during init`  
`8364383c35 Push plugin discovery down into command package`  

  
7. Кто автор функции synchronizedWriters?  
  
>Author: Martin Atkins <mart@degeneration.co.uk>  
  
**Таким же образом как в прошлых пунтах находим функцию `git log -SsynchronizedWriters --oneline` и проверяем автора самого старшего коммита: `git show 5ac311e2a9`, убеждаемся, что функция действительно там добавляется.**  

