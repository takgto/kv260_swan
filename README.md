# kv260_swan
swan files working on kv260.
## swanで小規模LLMを動かすプロブラム ##   
"言語モデルを高位合成でFPGAに実装してみた"（https://zenn.dev/turing_motors/articles/82505880d27d65）を参考にしてプログラムを作成しています。  
WSL2で適当なディレクトリにおいて、https://github.com/takgto/kv260_swan をgit cloneする。
```bash
git clone https://github.com/takgto/kv260_swan
cd kv260_swan
```
ディレクトリごとkv260に転送する。
```bash
scp -r kv260_swan root@192.168.1.100:/home/root
```
kv260上で以下を実行する。  
```bash
cd kv260_swan
cp -r model /home/root
cp -r swan /lib/firmware/xilinx
cp kv260_swan /home/root
```
実行環境のリストを取る。  
```bash
xmutil listapps
```
![image](https://github.com/user-attachments/assets/5f91c1e9-b2e7-40ad-8bfa-f279d2972607)  
swanを含む３つの環境があり、Active slotは、kv260-banchmark-b4096のみが0、他は-1になっている。  
</br>
全ての環境をunloadする。
```bash
xmutil unloadapp
```
![image](https://github.com/user-attachments/assets/76db36d4-7f3e-4447-ac93-a4d874b6e2d4)
Active slotが全て-1になっていることを確認する。  
</br>
swanの環境のみをActive slotにしてリストを取る。  
```bash
xmutil loadapp swan
xmutil listapps
```
![image](https://github.com/user-attachments/assets/09fb3e81-8ab3-41e5-8c21-974ba1ff3df8)  
swanのみがActive slot 0になっていることを確認する。
</br>
/home/root/kv260_swanの下で次のコマンドを実行すると言語モデルが実行される。  
```bash
./kv260_swan
```
![image](https://github.com/user-attachments/assets/a36a495e-c54f-4c39-a6f7-74c065f43f1e)  
コマンドを実行する度に物語が変わる。  








