# H3 kotitehtävä
Tein tämän tehtävän HP Elitebook 8460p kannettavalla tietokoneella. Kotitehtävässäni käytin live tikkua, johon olin laittanut  Xubuntu 16.04 LTS amd64 käyttöjärjestelmän. 
## Koneen speksit

              - HP
              EliteBook 8460p
             - CPU: Intel Core i5-2540M CPU @ 3.3GHz
                - GPU: Mesa DRI Intel(R) Sandybridge Mobile 
                  - RAM: 775MiB / 3861MiB




a) Package-File-Server. Asenna ja konfiguroi jokin demoni package-file-server -tyyliin. Tee jokin muu asetus kuin tunnilla näytetty sshd:n portin vaihto.

Tein SSH moduulin, joka tehtiin tunnilla. Käytin hyödyksi http://terokarvinen.com/2013/ssh-server-puppet-module-for-ubuntu-12-04 esimerkkiä. Ensin tein modules, ssh, manifests ja templates kansiot mkdir komennolla. sen jälkeen menin manifests kansioon ja loin init.pp tiedoston.

Aluksi kirjoitin package osion ja testasin moduulia. SSH demonin asennus onnistui. Seuraavaksi tein File osion ja kopioin sshd_config tiedoston /etc/ssh/sshd_config templates kansioon. 

Sitten menin templates kansion ja muutin sshd_config tiedoston sshd_config.erb tiedostoksi komennolla mv sshd_config sshd_config.erb. Muutin sshd_config tiedostosta loglevel arvoksi Verbose, joka näyttää epäonnistuneet kirjautumiset /var/log/auth.log tiedostossa. Viimeiseksi tein service osion. Jonka jälkeen, kun olin ajanut moduulin tuli tällainen virheilmoitus:

`Error: /Stage[main]/Ssh/Service[ssh]: Failed to call refresh: Could not restart Service[ssh]: Execution of '/bin/systemctl restart ssh' returned 1: Job for ssh.service failed because the control process exited with error code. See "systemctl status ssh.service" and "journalctl -xe" for details.
`
## Logitiedostot
[systemd log.txt](https://github.com/LM42/ssh/files/929977/systemd.log.txt)
[Journalctl.txt](https://github.com/LM42/ssh/files/929984/Journalctl.txt)





b) Modulit Gitistä. Tee skripti, jolla saat nopeasti modulisi kloonattua GitHubista ja ajettua vaikkapa liverompulle. Voit katsoa mallia terokarv inen/nukke GitHub-varastosta. 
Linkki, repoon: https://github.com/LM42/ninjascript

# Lähteet
- http://terokarvinen.com/2013/ssh-server-puppet-module-for-ubuntu-12-04
- https://help.ubuntu.com/community/SSH/OpenSSH/Configuring
- http://terokarvinen.com/2017/aikataulu-%E2%80%93-palvelinten-hallinta-ict4tn022-2-%E2%80%93-5-op-uusi-ops-loppukevat-2017-p2#comments
