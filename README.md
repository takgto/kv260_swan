# kv260_swan
swan files working on kv260.
## swanで小規模LLMを動かすプロブラム ##   
WSL2で適当なディレクトリにおいて、https://github.com/takgto/kv260_swan をgit cloneする。
```bash
git clone https://github.com/takgto/kv260_swan
cd kv260_swan
```
ディレクトリごとkv260に転送する。
```bash
scp -r kv260_swan root@192.168.1.100:/home/root
```
