# Užduotis

Žemiau yra info apie servą. Main IP, OS'o root pass, IP adresų bloko informacija.

IPv4: 195.201.141.17
IPv6: 2a01:4f8:c2c:fcd1::/64
User: root
Pass: -

Kiekvieną žingsnį parašyti su Ansible, jo kodą užGit'inti:

* Sukurti du LXC konteinerius: ✔
  * Padalinti šusnį IPv6 IP'ų šiems dviems konteineriams, ne mažiau kai po 4 IP adresus per konteinerį: ❓
  * Konteineriuose suinstaliuoti Squid proxy ✔
    * Squid'as turi išeiti į internetą iš to IPv6 IP'o, į kurį buvo prisijungta ❌
    * Apsaugoti Squid'ą su login/pass ✔
    * Uždrausti squid vartotojams pasiekti google search domenus ✔
  * Konteineriuose suinstaliuoti Dante SOCKS server
    * Dante turi išeiti į internetą iš to IP'o, į kurį buvo prisijungta
    * Apsaugoti Dante su login/pass ✔
    * Uždrausti pasiekti target 25 portą Dante useriui/useriams ✔
* Apsaugoti serverį savo nuožiūra. Jeigu konstruojamas firewall'as, daryti jį tiesiogiai su iptables. ❌
* Pateikti Ansible kodą Git repositorijos formatu.
* Pateikti SSH, Squid, Dante prisijungimus

Visi pakeitimai turi veikti ir po serverio reboot'o.

Requestai į servisus, prisijungimai į SSH bus bandomi iš šių adresų:
78.46.246.153
92.62.140.155
2001:1ab9:f002:1::2
