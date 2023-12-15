# Eclipse

> Tweette detaylar mevcuttur.
> https://x.com/Ruesandora0/status/1735024238535528666?s=20

> İşlemleri herhangi bir sunucumuzda yapalım muhim değil.
> ben islemleri digital ocean sunucusunda yapiyorum. 2 ay gecerli toplam 200$ harcayabilecegim kredi tanimlandi.


## Contrat Deploy:

```console
# 1'i seçelim:
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
source "$HOME/.cargo/env"

# solana cli kurulumu
sh -c "$(curl -sSfL https://release.solana.com/stable/install)"
PATH="/root/.local/share/solana/install/active_release/bin:$PATH"
solana config set --url https://staging-rpc.dev.eclipsenetwork.xyz

# key oluşacak, şifre belirleyip mnemonicleri ve cüzdan adresini kaydediyoruz
solana-keygen new

# cüzdana token alıyoruz
solana airdrop 10

#update sudo
sudo apt-get update
sudo apt-get install bzip2

# bu komut çalışması için 8 ram lazım - github swap space repom ile çözersiniz.
solana-test-validator
# komut çalışınca ctrl c ile durdurabilirsiniz.

# nodejs kurulumu
sudo apt-get install -y ca-certificates curl gnupg
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://deb.nodesource.com/gpgkey/nodesource-repo.gpg.key | sudo gpg --dearmor -o /etc/apt/keyrings/nodesource.gpg

NODE_MAJOR=20
echo "deb [signed-by=/etc/apt/keyrings/nodesource.gpg] https://deb.nodesource.com/node_$NODE_MAJOR.x nodistro main" | sudo tee /etc/apt/sources.list.d/nodesource.list
sudo apt-get update
sudo apt-get install nodejs -y

# kontrat deploy 
git clone https://github.com/solana-labs/example-helloworld
cd example-helloworld
npm install

# burda biraz bekletecek rusttan dolayı
npm run build:program-rust
# program id not edin
solana program deploy dist/program/helloworld.so
npm run start
# success çıktısı verecek en sonda.

```

## Bridge işlemi:

```console
sudo apt update -y && sudo apt upgrade -y
sudo apt install git

git clone https://github.com/Eclipse-Laboratories-Inc/testnet-deposit.git
cd testnet-deposit

# asagidaki komutlarda hata alirsan ilgili posta bak: https://x.com/Ruesandora0/status/1735035324496273902?s=20
npm install --global yarn
yarn install
yarn add ethers

root@avail-node:~/example-helloworld/testnet-deposit# 

# Altta ki komutu düzenleyelim (tırnakları kaldırın):
node deposit.js <solanaAdresi> 0x7C9e161ebe55000a3220F972058Fb83273653a6e 500000 100 <MetamaskPrivateKeyi> https://rpc.sepolia.org
# solana cüzdanı yukarıda oluşturduk onu import edin yeni profilde.
```

> başarılıysa success ve tx çıktısı verecek

> https://explorer.dev.eclipsenetwork.xyz/?cluster=testnet burdan solana cüzdanı kontrol edip eth var mı yok mu bakıyoruz. varsa ok.

> Formu doldurun: https://docs.google.com/forms/d/e/1FAIpQLSfJQCFBKHpiy2HVw9lTjCj7k0BqNKnP6G1cd0YdKhaPLWD-AA/viewform
> form dolduruldu.
