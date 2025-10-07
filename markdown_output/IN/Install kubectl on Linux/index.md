Install kubectl binary with curl on Linux\
1.  Download the latest release with the command: [curl
-LO]{style="color: rgb(51,51,51);"}
[[[https://storage.googleapis.com/kubernetes-release/release/](https://storage.googleapis.com/kubernetes-release/release/){.external-link
rel="nofollow"}\`curl]{style="text-decoration: underline;"}]{style="color: rgb(0,0,238);"}
(https://storage.googleapis.com/kubernetes-release/release/\`curl)
[-s]{style="color: rgb(51,51,51);"}
[[[https://storage.googleapis.com/kubernetes-release/release/stable.txt](https://storage.googleapis.com/kubernetes-release/release/stable.txt){.external-link
rel="nofollow"}\`/bin/linux/amd64/kubectl]{style="text-decoration: underline;"}]{style="color: rgb(0,0,238);"}
(https://storage.googleapis.com/kubernetes-release/release/stable.txt\`/bin/linux/amd64/kubectl)\
2. Make the kubectl binary executable. [chmod +x
./kubectl]{style="color: rgb(51,51,51);"}\
3. Move the binary in to your PATH. [sudo mv ./kubectl
/usr/local/bin/kubectl]{style="color: rgb(51,51,51);"}\
4. Test to ensure the version you installed is up-to-date: [kubectl
version]{style="color: rgb(51,51,51);"}
