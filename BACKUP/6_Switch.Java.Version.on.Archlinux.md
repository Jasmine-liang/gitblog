# [Switch Java Version on Archlinux](https://github.com/Jasmine-liang/gitblog/issues/6)

See what's installed:
`archlinux-java status`          
Get a name of version you want to use, then issue this command,
`sudo archlinux-java set JAVA-X-JDK`    **_JAVA-X-JDK_** is the name of the result from the **_status_** command.

---

Then you can use this command to see you java version.
`java -version`