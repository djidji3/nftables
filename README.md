# nftables
nftables tuzfal configuracio

# atallas a regi iptablesre
for i in iptables iptables6 arptables ebtables ; do update-alternatives --set ${i} /usr/sbin/${i}-legacy ; done

# atallas az uj nftablesre
for i in iptables ip6tables arptables ebtables ; do update-alternatives --set ${i} /usr/sbin/${i}-nft ; done

# nftables telepitese
apt update && apt install nftables

# service lekerdezes, engedelyezes:
- systemctl status nftables
- systemctl enable nftables

# routolas engedelyezese
- vi /etc/sysctl.d/local.conf
	net.ipv4.ip_forward=1
	net.ipv4.conf.default.rp_filter=1
	net.ipv4.conf.all.rp_filter=1
	net.ipv4.tcp_syncookies=1
    net.ipv6.conf.default.forwarding=1
	net.ipv6.conf.all.forwarding=1

- systemctl restart procps
# logikai felosztas
 Az input lanc altalaban nem tul bonyolult egy routeren, ezert ennek a szetbontasaval nem erdemes foglalkozni
#
A csomagok celja alapjan 3 tovabbi chain-re osztom fel a forward-chain nevu lancomat:
- nft add chain inet filter-table forward2lan-chain
- nft add chain inet filter-table forward2dmz-chain
- nft add chain inet filter-table forward2internet-chain

# valtozok deklaralasa
- define VALTOZONEV=ertke
- define DMZ_DEV=enp0s9

# a szabalyok tovabb bontasa fajlokba
- tegyuk a valtozokat egy kulon fajlba
- tegyuk kulon fajlba a tablakat (filter, nat, route)

