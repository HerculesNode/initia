## İnitia için yeni bir screen oluşturup orada yeniden başlatacağız. Screen oluşturalım. 
```
screen -S autoinit
```

## AutoRestart dosyası oluşturalım.

```
nano restart_initiad.sh
```

## Alttaki kodu içine yapıştırın. Ctrl x y deyip kaydedin.  300 yazan saniyedir kendinize göre ayarlayın 5 dk olarak ayarlanmıştır.

```
#!/bin/bash

while true; do
    if sudo systemctl restart initiad; then
        echo "initiad services restart success."
    else
        echo "initiad services restart fault."
    fi

    # Geri sayım başlatma
    for ((i=300; i>0; i--)); do
        echo -ne "Kalan süre: $i saniye\r"
        sleep 1
    done
done
```

## Dosya yetkisi verelim.

```
chmod +x restart_initiad.sh
```

## Şimdi çalıştıralım. Çalıştıktan sonra Screen den ctrl a d ile çıkış yapabilirsiniz. Blokları izlemek için oluşturduğunuz initia screen içinden kontrolü yapabilirsiniz.

```
./restart_initiad.sh
```

