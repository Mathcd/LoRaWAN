Install Docker

Download ChirpStack Docker (LoRa Server)

https://github.com/brocaar/chirpstack-docker




Download Raspbian

https://www.raspberrypi.org/downloads/raspbian/


2 - Descompactar arquivo zip e gravar a imagem do raspberry no SD utilizando o programa balenaEtcher (pode ser usado versão portable)

https://www.balena.io/etcher/


3 - Inserir o SD raspberry e conectar a um monitor HDMI e teclado USB

4 - Configs básicas

$ raspi-config

- Ativar SSH
- Ativar SPI
- Conectar a Rede

- Anotar endereço IP


=====================================================


Conectar pinagem conforme 

https://www.hackster.io/naresh-krish/getting-started-with-the-rak831-lora-gateway-and-rpi3-e3351d


=====================================================

Baixar arquivos do package forwarder


Fazer devidas alterações (MAC do Gateway, pinout, etc)

=====================================================

>> Script de inicialização

# Resetar o concentrador

$ cd /home/pi/pck_fwd_RPi2_3/lora_gateway
$ ./reset_lgw.sh start 25  


# Iniciar o package forwarder

$ cd /home/pi/pck_fwd_RPi2_3/packet_forwarder/lora_pkt_fwd
$ ./lora_pkt_fwd


=======================================================

- Modificar o arquivo .bashrc para auto inicializar o package forwarder, mas não no SSH


sudo nano /home/pi/.bashrc



# script para identificar se eh ssh
if [ -n "$SSH_CLIENT" ] || [ -n "$SSH_TTY" ]; then
  echo I am logged via SSH.

else
  echo I am not logged via SSH. Starting package forwarder process now...
  sudo sh '/home/pi/startup-pckfwd.sh'

fi


=======================================================


