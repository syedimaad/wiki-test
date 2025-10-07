\

The Linux **Find Command** is one of the most important and much used
command in Linux sytems. Find command used to search and locate list of
files and directories based on conditions you specify for files that
match the arguments. Find can be used in variety of conditions like you
can find files by **permissions**, **users**, **groups**, **file type**,
**date**, **size** and other possible criteria.

\

1.  Find files using name in current directory : **find . -name
    \<file.txt\>**

2.  Find files under home directory : **find /home -name \<file.txt\>**

3.  Find files using name and ignoring case : **find / -iname
    \<FILE.txt\>**

4.  Find directories using name : **find / -type d -name
    \<directory_name\>**

5.  Find php files using name : **find / -type f -name \<file.php\>**

6.  Find all php files in directory : **find / -type f -name
    \<\*.php\>**

7.  Find files with 777 permissions : **find / -type f -perm 777**

8.  Find files without 777 permissions : **find / -type f ! -perm 777**

9.  Find read only files : **find / -perm /u=r**

10. Find executable files : **find / -perm /a=x**

11. Find files with 777 permissions and chmod to 755 : **find / -type f
    -- perm 777 -exec chmod 755 {} \\;**

12. Find and remove single file : **find / -type f -name \<"file.txt"\>
    -exec rm -f {} \\;**

13. Find and remove multiple files : **find / -type f -name \<"\*.mp3"\>
    -exec rm -f {} \\;**

14. Find all empty files : **find / -type f -empty**

15. Find all empty directories : **find / -type d empty**

16. Find all hidden files : **find / -type f -name \<".\*"\>**

17. Find all files based on a user : **find / -type f -user
    \<username\>**

18. Find all files based on a group : **find / -type f -group
    \<groupname\>**

19. Find particular files of a user : **find / -type f -user
    \<username\> -iname \<"\*.txt"\>**

20. Find all files modified 50 days back : **find / -mtime 50**

21. Find all file accessed 50 days back : **find / -atime 50**

22. Find changed files in last 1 hour : **find / -cmin -60**

23. Find modified files in last 1 hour **: find / -mmin -60**

24. Find accessed files in last 1 hour **: find / -amin -60**

25. Find files with size 50mb : **find / -size 50M**

26. Find files within size 50mb and 100mb **: find / -size +50M -size
    -100M**

27. Find and delete files with size 100mb : **find / -size 100M -exec rm
    -rf {} \\;**

28. Find specific files and delete : **find / -type f -name \<"\*.mp3"\>
    -size +10M -exec rm {} \\;**

::: {}
**\**
:::

::: {}
**\**
:::

::: {}
**\**
:::

::: {}
-Seren Jhanwar
:::
