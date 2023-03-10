# Aleo-sdk

1. Aleo wallet oluşturuyoruz.
https://aleo.tools adresine giderek giderek “Generate” butonuna basın.

Oluşturmuş olduğunuz cüzdan bilgilerini (Private key, Viewkey ve adres kaydedin.

2. Token almak için Tweet atıyoruz

@AleoFaucet send 10 credits to aleo cüzdan adresiniz

Aleo cüzdan adresiniz yazan kısmına kendi aleo1… aderesinizi yazıyoruz.Tweet için dönüş rastgele yapıyorlar.Biraz denemek gerekiyor.Ben 3.tweetimde dönüş aldım.
Tweete dönüş olursa size keylerin olduğu bir link gönderiyor @AleoFaucet

3. Kurmuş olduğumuz VPS bağlanarak

SnarkOS kuralım

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install

screen -S anasayfa

curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh

git clone https://github.com/AleoHQ/snarkOS.git --depth 1

cd snarkOS
./build_ubuntu.sh
source $HOME/.cargo/env
cargo install --path .

Sonrasında Leo Dilini kuralım

cd

git clone https://github.com/AleoHQ/leo
cd leo

cargo install --path .

leo 

4. Test uygulamanızı dağıtın

cd $HOME
mkdir demo_deploy_Leo_app && cd demo_deploy_Leo_app

WALLETADDRESS="Kaydettiğiniz cüzdan adresini yazın"


APPNAME=helloworld_"${WALLETADDRESS:4:6}"
echo $APPNAME
leo new "${APPNAME}"
cd "${APPNAME}" && leo run && cd -
PATHTOAPP=$(realpath -q $APPNAME)
echo $PATHTOAPP

cd $PATHTOAPP && cd ..

PRIVATEKEY="Daha önce kaydettiğiniz private key yazın"


⚠️ faucet den gelen linke giderek aşağıdaki screenshotda görünen yerdeki record (Ciphertext) kısmını kopyalayıp,
https://aleo.tools/ linke giderek record kısmına tıklayıp 1.adımda oluşturup kaydettiğiniz View Key ve size gelen linkten kopyaladığınız
Record (Ciphertext) yerlerine yazınız. Yazdıktan sonra altta size Record (Plaintext) olarak bir kod verecek.O kodun tamamını kopyalayıp
aşşağıda RECORD="" arasına yazarak konsola yapıştırın.

RECORD="En son alınan kod"

![1](https://user-images.githubusercontent.com/108255403/224249316-98c6c502-11ee-4882-878d-4638921c92d1.png)



snarkos developer deploy "${APPNAME}.aleo" --private-key "${PRIVATEKEY}" --query "https://vm.aleo.org/api" --path "./${APPNAME}/build/" --broadcast "https://vm.aleo.org/api/testnet3/transaction/broadcast" --fee 600000 --record "${RECORD}"

5. Son olarak

işlemler bittikten sonra konsolda ✅ Successfully deployed ‘helloworld_ görmeniz lazım

offical video guide

offical guide
